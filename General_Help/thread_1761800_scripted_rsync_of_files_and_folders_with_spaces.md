---
title: "scripted rsync of files and folders with spaces"
date: 2011-05-18
forum: General Help
---

### Post by Paegus on 2011-05-18
I'm having some trouble running a scripted rsync process to transfer files from one system to another and clear the file from an application on the source computer.

A program on the source system is constantly generating new files, some of which I need to have moved to a remote system. This can been immediately if the remote system is up or to be queues up and then sent once once that system is up.

I have a script which fires when each file that i'm interested in is create that either transfers the file or if the remote system is down it creates a queue file containing the path to the file that was just generated.

I then have a cron job calling the transfer script which checks if the remote system is up, if so transfers only the desired files and then tells the generating application that that file should not be re-created.

rsync-ing the base folder works nicely but then I have manually log in and remove the jobs from the generating application's queue. if i just delete the file they are re-generated.

my problem is that I can't seem to convince rsync to respect the spaces in the file and folder names. ex: "/home/user/folder one/folder two/file" or "/home/user/folder one/folder two" if the whole folder matched.

I've tried...
[list]
[*]single quotes:
```
rsync $ARGO "$OURCE" $HOST:"$OURCE"
```
which transfers the file to "/home/user/folder", where folder is the file.

[*]double quotes
```
rsync $ARGO "$OURCE" $HOST:'"$OURCE"'
```
which transfers the file but then roasts on the rename with
```
rsync: rename "/home/user/..53rRm4" -> "": No such file or directory (2)
```
presumably because the remote system doesn't know what $OURCE is...

[*]escaped quotes:
```
rsync $ARGO "$OURCE" $HOST:\"$OURCE\"
```
which fails immediately with
```
Unexpected remote arg: host:"/home/user/folder
```
[/list]
the single & double-quote method works flawlessly from the command line so this only seems to happen in-script.

i've also tried...
[list]
[*]replacing the spaces in the var with "\ " escaped spaces
```
OURCE=$(cat $QFILE | sed 's/ /\\ /g')
```
which fails immediately as it interprets the \ escape character as a back slash instead of using it as an escape character.
```
rsync: change_dir "/home/user/folder\ one/folder\ two/" failed: No such file or directory (2)
```

[*]replacing the spaces in the var with "\ " escaped spaces but with only 1 backslash
```
OURCE=$(cat $QFILE | sed 's/ /\ /g')
```
which does nothing...

[*]replacing the spaces in the var with ? marks
```
OURCE=$(cat $QFILE | sed 's/ /?/g')
```
which replies with
```
rsync: change_dir "/home/user/folder?one/folder?two/" failed: No such file or directory (2)
rsync: change_dir#3 "/home/user/folder?one/folder?two/" failed: No such file or directory (2)

```
[/list]

both systems are using bash as their shell.

So I'm stumped...

---

### Post by papibe on 2011-07-09
Using spaces in the arguments of rsync can be tricky (specially in the remote arguments). I think single quotes and escape spaces would work, but it is just easier to explicitly protect the arguments from 'shell word splitting'.

This should do it (it works in my Home network):
```
#!/bin/bash

SOURCE="source 1/"
DEST="devproj/rsync/spaces/dest 1/"
HOST="reinhardt"

rsync -av --protect-args  "$SOURCE" "$HOST":"$DEST"

```
Note the **--protect-args** option.

Hope it helps.

---

