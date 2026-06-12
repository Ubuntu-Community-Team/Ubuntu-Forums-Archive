---
title: "how to specify rar output direcotry in commandline ?"
date: 2009-12-07
forum: General Help
---

### Post by AnotherNoob on 2009-12-07
is there anyone knows how to specify output directory of rar in command

suppose i have this 

```
rar a -m0 -v1g file-name-here.rar folder-name-here
```now i want the output (which is rar files) in some other folder or  ,  like /home/admin/raroutput 

is this possible ?

---

### Post by lloyd_b on 2009-12-07
> **AnotherNoob said:**
> is there anyone knows how to specify output directory of rar in command

suppose i have this 

```
rar a -m0 -v1g file-name-here.rar folder-name-here
```now i want the output (which is rar files) in some other folder or  ,  like /home/admin/raroutput 

is this possible ?

Just specify the full path to the file:```
rar a -m0 -v1g /home/admin/raroutput/file-name-here.rar folder-name-here
```

Lloyd B.

---

### Post by AnotherNoob on 2009-12-07
i just realize my nick is too good for me :D , thanks for help its too easy :D

---

### Post by ogromano on 2009-12-27
Hello...

I'm trying to backup my home folder to do a new install from 8.04 up to 9.10...

I typed this in the command line
```
rar a -v35000m -m5 -t -r /media/externaldrive/bkp/homebkp.rar ~
```
but all I'm getting is an error when it tries to go into .picasa 3 folder and it says "Too many symbolic links" and it justs floods the terminal and never gets anywhere.

Can someone please check that I am using the right command and switches and if there's a better way to do this, I'd appreciate the info.

Using 8.04 hardy, 60GB free space on external VFAT drive (reason for the -v switch), home folder unrared is 40GB.

By the way, what other folders should I backup?

Thanx.

---

### Post by lloyd_b on 2009-12-27
> **ogromano said:**
> Hello...

I'm trying to backup my home folder to do a new install from 8.04 up to 9.10...

I typed this in the command line
```
rar a -v35000m -m5 -t -r /media/externaldrive/bkp/homebkp.rar ~
```
but all I'm getting is an error when it tries to go into .picasa 3 folder and it says "Too many symbolic links" and it justs floods the terminal and never gets anywhere.

Can someone please check that I am using the right command and switches and if there's a better way to do this, I'd appreciate the info.

Using 8.04 hardy, 60GB free space on external VFAT drive (reason for the -v switch), home folder unrared is 40GB.

By the way, what other folders should I backup?

Thanx.

First off, you'd be better off creating a new thread, under the correct subject, rather than trying to "ride" this one.  You have a different problem, and the people who know the solution to that problem may not even read this thread because of the topic...

Second - "too many symbolic links" is NOT a 'rar' issue, but rather something wrong with the way files are stored.  Linux has issues if there are too many levels of symbolic links (i.e., one link points to another, which points to another, which points to another, etc), or cases where symlinks are looping (link1 -> link2 -> link1).  I have no experience with Picasa, so I can't suggest any solution, other than excluding that directory from your backup.

Finally - if you are the only user on that machine, and you aren't running a webserver or such, then backing up your home directory should be sufficient.  If you *aren't* the only user, then I'd suggest backing up "/home" instead, to get everyone's home directory.  And if you're running a webserver, then there are files in "/var" that you'll probably want to back up as well.

Lloyd B.

---

### Post by ogromano on 2009-12-28
Thanks a lot for the input Lloyd...

You're right, I should've started a new thread... but my original problem was that I wasn't sure how to output the rar to the external drive... obviously, while reading the thread I found the answer and just kept on going with it... :)

I solved my problem in a different way because I couldn't get the rar command to work properly.. don't know what part was wrong but it just wouldn't work. So in the end, I made an ext3 partition in my external drive using gparted and then used TAR instead to put it all into one .bz2 file rather than splitting it up using rar and the -v switch. For some reason using the TAR command didn't give me any problems with the symbolic links that bugged the RAR command... who knows... 

At least it worked now, and I have my home folder backed up... I'm off to install 9.10...

Cya.

---

### Post by lloyd_b on 2009-12-28
> **ogromano said:**
> Thanks a lot for the input Lloyd...
I solved my problem in a different way because I couldn't get the rar command to work properly.. don't know what part was wrong but it just wouldn't work. So in the end, I made an ext3 partition in my external drive using gparted and then used TAR instead to put it all into one .bz2 file rather than splitting it up using rar and the -v switch. For some reason using the TAR command didn't give me any problems with the symbolic links that bugged the RAR command... who knows... 

At least it worked now, and I have my home folder backed up... I'm off to install 9.10...

Cya.

Actually, I can explain why 'tar' works and 'rar' doesn't.  By default, when 'tar' encounters a symlink, it just copies the symlink, without worrying about the file the link points to.  'rar', on the other hand, by default will "dereference" the symlink, following it to the actual data file.

Since 'tar' doesn't try to follow the links, it never encounters the weirdness that causes those "too many symbolic links" error, unless you explictly tell it to follow the links.  While 'rar' always follows the links, unless you explicitly tell it not to.

Lloyd B.

---

