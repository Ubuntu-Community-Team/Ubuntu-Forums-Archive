---
title: "Anyone good with Git?"
date: 2011-06-09
forum: General Help
---

### Post by ithuwakaga on 2011-06-09
Hi!

I'm setting up a Git repository for an existing project.

The project needs to stay in it's current directory, and should allow developers to "push" changes to it.

Does anyone know how to do this elegantly? I've run into two major problems:
[INDENT][LIST=1]
[*] I've tried just initializing the main directory and attempting to merge changes, but I get this error.
```
$ git push
Counting objects: 3, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 257 bytes, done.
Total 2 (delta 1), reused 0 (delta 0)
Unpacking objects: 100% (2/2), done.
remote: error: refusing to update checked out branch: refs/heads/master
remote: error: By default, updating the current branch in a non-bare repository

remote: error: is denied, because it will make the index and work tree inconsist
ent
remote: error: with what you pushed, and will require 'git reset --hard' to matc
h
remote: error: the work tree to HEAD.
remote: error:
remote: error: You can set 'receive.denyCurrentBranch' configuration variable to

remote: error: 'ignore' or 'warn' in the remote repository to allow pushing into

remote: error: its current branch; however, this is not recommended unless you

remote: error: arranged to update its work tree to match what you pushed in some

remote: error: other way.
remote: error:
remote: error: To squelch this message and still keep the default behaviour, set

remote: error: 'receive.denyCurrentBranch' configuration variable to 'refuse'.

To z:/weather
 ! [remote rejected] master -> master (branch is currently checked out)
error: failed to push some refs to 'z:/weather'
```
[*] If I try to turn it into a bare repository...
```
git --bare init
```
 It doesn't update the "/z/weather" folder. However, I can pull changes from other folders and they sync correctly.
[/LIST][/INDENT]

Any advice? :???:

---

