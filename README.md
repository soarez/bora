# bora

super simple deploys

Features:

- Leverages `rsync(1)` for transfers
- Build hooks
- Post-deploy hook
- Ignore files
- Rollbacks

## install

```
npm i -g bora
```

## usage

```
  bora [-R] [-b cmd] [-i ignores] [-k #] [-n name] [-r cmd] [-s src] host [...]

  -b      command to perform build the deployed folder
  -d      path to a folder on the server where the deploys will reside,
          defaults to ~/deploys
  -i      path to a new-line separated list of files to ignore,
          defaults to <source folder>/.rsyncignore
  -k      number of previous builds to keep, defaults to 3
  -n      project name, defaults to basename of the deployed foler path
  -r      command to restart service
  -R      rollback to the previous deploy instead of deploying
  -s      path to the deploy folder, defaults to \$PWD
  -S      where to create a symlink to the lastest deploy for convenience
          defaults to <deploys folder>/<name>
  host  the ssh target defined in your ~/.ssh/config (see ssh_config(5))
```

## example

Deploy:

```
bora -r '<<optional command to restart my service>>' -b '<<optional command to restart my service>>' -i .gitignore myhost
```

Rollback:

```
bora -r '<<optional command to restart my service>>' -R myhost
```

## LICENSE

MIT
