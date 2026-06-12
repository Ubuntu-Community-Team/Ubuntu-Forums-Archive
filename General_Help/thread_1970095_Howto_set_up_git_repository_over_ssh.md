---
title: "Howto: set up git repository over ssh"
date: 2012-04-30
forum: General Help
---

### Post by paulmilliken on 2012-04-30
It is assumed that you have a server and where a user (git_user) has ssh access as [email]git_user@myserver.com[/email].  It is also assumed that git is installed on myserver.com and myclient.  To set up a git repository that is shared via ssh do the following:

On myserver.com
[LIST=1]
[*]```
mkdir ~/myproject.git
```
[*]```
cd myproject.git
```
[*]```
git init --bare
```
[/LIST]
Note that the --bare flag is needed to allow users to push to the repository.

On myclient:
[LIST=1]
[*]```
mkdir myproject
```
[*]```
cd myproject
```
[*]```
git init
```
[*]```
git add file1 file2 etc
```
[*]```
git commit -m 'initial commit'
```
[*]```
git remote add origin ssh://git_user@myserver.com/home/git_user/myproject.git
```
[*]```
git push origin master
```
[/LIST]

---

