---
title: "Unison - multiple directories"
date: 2010-11-17
forum: General Help
---

### Post by lallalla on 2010-11-17
I am trying to sync several individual directories on my laptop with an external harddrive and I cannot get it to work. the code in the unison file is:

root = /home/me/Documents
root = /media/extdrive
perms=0o0

path = folder1 # full address: /home/me/Documents/folder1
path = aa/bb/folder2  # full address: /home/me/Documents/aa/bb/folder2
path = cc/dd/folder3 # full address: /home/me/Documents/cc/dd/folder3

the error messages states:
path aa/bb is not valid because aa is not a directory in one of the replicas

I have already tried this with an empty extdrive and then copied the relevant folder from the computer to the extdrive but the error message remains the same. Any ideas how to sort this? THANKS

---

### Post by lallalla on 2010-11-23
any ideas???????

---

### Post by ad_267 on 2010-11-23
Unison works by syncing two root directories. So in this file the first two lines would make everything in /home/me/Documents sync with everything in /media/extdrive, unless you exclude it using the ignore option. I'm pretty sure the "path = " stuff is invalid.

Here's what I think would achieve what you want.

Create the two directories you will sync:
```
mkdir /home/me/Documents/sync
mkdir /media/extdrive/sync
```

Then create symbolic links within those to the stuff you want to sync.
```
ln -s /home/me/Documents/folder1 /home/me/Documents/sync/folder1.sync
ln -s /home/me/Documents/aa/bb/folder2 /home/me/Documents/sync/folder2.sync

ln -s /media/extdrive/folder1 /media/extdrive/sync/folder1.sync
ln -s /media/extdrive/aa/bb/folder2 /media/extdrive/sync/folder2.sync
```

Now in your unison file put:
```
root = /home/me/Documents/sync
root = /media/extdrive/sync
perms=0o0000

follow = Name *.sync
```

I added the ".sync" suffix and the "follow =" part as Unison doesn't follow symlinks by default. I use a similar setup to sync a bunch of folders between two computers using a usb flash drive.

---

### Post by lallalla on 2010-11-24
smashing - thanks very much!

---

