# Git/Github

Frequently used stuff I tend to forget.

## Transfer

* go to Github repo
* click on gear icon
* scroll down
* transfer

### reconfigure Git after the transfer

```
$ git remote set-url origin new_url
```

#### Example

```
$ cat .git/config
$ git remote set-url origin https://github.com/cas-dt/css-text
$ cat .git/config
```

### Links

* [About repository transfers](https://help.github.com/articles/about-repository-transfers/)
* [Changing a remote’s URL](https://help.github.com/articles/changing-a-remote-s-url/)
* [Transferring a repository owned by your personal account](https://help.github.com/articles/transferring-a-repository-owned-by-your-personal-account/)

## Set up new Github repo for existing Git project

* Create new repo on Github, without README.md.
* navigate to local git project folder

### Links

* [Adding an existing project to GitHub using the command line](https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/)

```
# if not yet initialized
$ git init

# add files for first commit
$ git add .

# first commit
$ git commit -m "First commit"

# add url for remote repo
$ git remote add origin URL

# verify new remote
$ git remote -v

# push to master
$ git push -u origin master
```

### Troubleshooting

In this case probably caused because the repo was initialized with a license.

```
$ git push -u origin master

To https://github.com/cas-dt/animation
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'https://github.com/cas-dt/animation'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

# merge local and remote
$ git pull origin master

From https://github.com/cas-dt/animation
 * branch            master     -> FETCH_HEAD
Merge made by the 'recursive' strategy.
 LICENSE | 373 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 1 file changed, 373 insertions(+)
 create mode 100644 LICENSE

$ git push -u origin master
```

If this doesn’t work, the merge can be forced.

```
$ git pull origin master --allow-unrelated-histories

From https://github.com/oolong32/drawbot-exercises
 * branch            master     -> FETCH_HEAD
Merge made by the 'recursive' strategy.
 LICENSE | 373 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 1 file changed, 373 insertions(+)
 create mode 100644 LICENSE

$ git push -u origin master
```

## Set new remote link after renaming repo

```
git remote set-url origin new_url
```