---
title: "How do I move files into hidden folders? [URGENT]"
date: 2011-08-14
forum: General Help
---

### Post by Mr.DerpAndTheRagingHurrs on 2011-08-14
You see, i'm a speculator trying to get into that Bitcoin nonsense, and I just downloaded a blockchain that I need to verify (don't ask). However, it'll become outdated in a few hours, as It took almost all day to download.

I finally extracted the files from the .tar.bz2, and am ready to add it to my Bitcoin folder, yet the folder [/.bitcoin], which is located in the "file system" folder, is hidden [B]and I cannot use the ctrl H function to unhide it, nor any other hidden folders.

[/B]Therefore, I decided to use terminal to move the files to the hidden folders.
**But when I try to move it, terminal thinks the hidden folder doesn't exist.**
```
[user]@ubuntu:~/Downloads/bitcoin-blockchain-20110811$ mv blk0001.dat blkindex.dat /.bitcoin
mv: target `/.bitcoin' is not a directory


```

**Is there a way to unhide the folders in File System so I can move the files using the GU**I, **and if I can't, why can't I move files to hidden folders? Do I need Sudo?**

---

### Post by Furball588 on 2011-08-14
You probably want to use the entire path...

i.e.  /home/user/.bitcoin

---

### Post by akand074 on 2011-08-14
You can, but from what I've read, the folder just doesn't exist. Ctrl + H should unhide it, and the terminal should be able to access it without issues. Why are you so sure the directory exists? You could always just create it. 

You will likely need sudo to make any changes to your filesystem though.

---

### Post by spiky001 on 2011-08-14
I take it that the file/folder is in /home/user/Downloads

what dose ```
ls
``` ```
ls -a
``` show?

---

### Post by Mr.DerpAndTheRagingHurrs on 2011-08-14
> **akand074 said:**
> You can, but from what I've read, the folder just doesn't exist. Ctrl + H should unhide it, and the terminal should be able to access it without issues. Why are you so sure the directory exists? You could always just create it. 

You will likely need sudo to make any changes to your filesystem though.
What confuses me even more is that terminal *should* know that it exists as I've used it to look at the folder.
**I can only view hidden files via terminal; I cannot use file manager at all.**
```
[user]@ubuntu:~/.bitcoin$ ls
addr.dat     blkindex.dat  __db.001  __db.003  __db.005  db.log     wallet.dat
blk0001.dat  database      __db.002  __db.004  __db.006  debug.log
thesiblings@ubuntu:~/.bitcoin$ 

```> **spiky001 said:**
> I take it that the file/folder is in /home/user/Downloads

what dose ```
ls
``` ```
ls -a
``` show?

```
[user]@ubuntu:~$ ls -a
.              Desktop           .gnome2_private  Pictures
..             .dmrc             .gstreamer-0.10  .profile
.adobe         Documents         .gtk-bookmarks   Public
.bash_history  Downloads         .gvfs            .pulse
.bash_logout   .esd_auth         .ICEauthority    .pulse-cookie
.bashrc        examples.desktop  .local           .sudo_as_admin_successful
**.bitcoin**       .fontconfig       .macromedia      Templates
.cache         .gconf            .mozilla         Videos
.config        .gconfd           Music            .xsession-errors
.dbus          .gnome2           .nautilus        .xsession-errors.old

```

---

### Post by WyleECoyote on 2011-08-14
> **Mr.DerpAndTheRagingHurrs said:**
> ```
[user]@ubuntu:~/.bitcoin$ ls
addr.dat     blkindex.dat  __db.001  __db.003  __db.005  db.log     wallet.dat
blk0001.dat  database      __db.002  __db.004  __db.006  debug.log
thesiblings@ubuntu:~/.bitcoin$ 

```

check again, you are in your home directory not root ~/ means users home so instead of 

```
mv blk0001.dat blkindex.dat /.bitcoin
```

try:

```
mv blk0001.dat blkindex.dat ~/.bitcoin
```

---

### Post by akand074 on 2011-08-14
Oh I thought bitcoin was in his filesystem (i.e /). Your right from the code output it's in his home folder. Looks like the OP was looking in the wrong place. Yes follow the post above me, should work fine.

---

