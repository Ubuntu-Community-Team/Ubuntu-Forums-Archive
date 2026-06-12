---
title: "how do I write on my vFat USB drive?"
date: 2009-11-30
forum: General Help
---

### Post by Man with Hat on 2009-11-30
I have been going a little nuts trying to make my mini SD disk inside my nokia E71 want to be nice to me. If I plug it in via USB it auto mounts no problem, I can view and copy files no problems, but I can't write to it!

I have searched a while and see some stuff to do with fdisk and fstab, but I don't really understand these. I remember fdisk a little from partitioning a drive in dos back in windows 3.1 days, but that is about it. 

I installed mount manager as I thought I read somewhere that it could help. There are options in there that show my vFAT disk is able to read/write, but I can't write. I also have NTFS configuration tool which helped me mount my other internal hard drive permanently. 

Any help? Please speak clearly and noobly for me :)

---

### Post by mo.reina on 2009-11-30
what are the permissions of the mount point?  

post the output of:

ls -l */path/of/disk*

---

### Post by Man with Hat on 2009-11-30
I'm not sure if this is what you meant (I was expecting something longer)

Command used:
ls -l /dev/sdc

Output:
brw-rw---- 1 root disk 8, 32 2009-12-01 00:02 /dev/sdc

---

### Post by Man with Hat on 2009-11-30
Wait!! This is better :)

Command:
ls -l /media/FD71-883A/


Output:
total 714048
drwx------  2 cam cam     32768 2008-11-09 22:55 Activenotes
-rwxr-xr-x  1 cam cam       170 2008-06-10 09:20 card_content.xml
drwx------ 14 cam cam     32768 2008-04-17 14:39 cities
drwx------  5 cam cam     32768 2008-05-26 12:21 data
-rwxr-xr-x  1 cam cam      9062 2009-11-29 12:17 DevIcon.fil
-rwxr-xr-x  1 cam cam      1579 2009-11-29 12:17 DevLogo.fil
drwx------  2 cam cam     32768 2008-11-15 11:15 Documents
drwx------ 16 cam cam     32768 2008-11-09 21:25 Images
drwx------  2 cam cam     32768 2009-09-29 03:05 Installs
drwx------  2 cam cam     32768 2008-11-09 21:16 Nokia
drwx------  2 cam cam     32768 2008-06-10 09:20 Others
drwx------ 24 cam cam     32768 2008-05-26 12:21 private
-rwxr-xr-x  1 cam cam       156 2009-10-02 08:42 qf
drwx------  7 cam cam     32768 2008-05-26 12:21 resource
drwx------  4 cam cam     32768 2008-11-15 11:15 Sounds
drwx------  4 cam cam     32768 2008-11-09 22:41 SportsTracker
drwx------  5 cam cam     32768 2008-05-26 12:21 sys
drwx------  6 cam cam     32768 2008-05-26 12:12 system
-rwxr-xr-x  1 cam cam 730554368 2009-09-04 12:04 ubuntu-9.04-desktop-amd64.iso
drwx------ 13 cam cam     32768 2008-11-10 10:12 Videos

---

### Post by Man with Hat on 2009-12-18
I don't suppose you're still checking this thread?

---

### Post by Dennis N on 2009-12-19
Use this:

```
ls -l /media
```

If your SD disk shows up in the list with root as owner, you need to change that. It should have your user name as owner.

mount folder line for all my FAT flash drives shows owner:group to be me:root with permissions rwx------

group root is ok.

---

### Post by Man with Hat on 2010-01-03
Sorry I haven't replied for a while. I have been busy and now I just can't even seem to get the stupid thing to mount. The SD card is in my mobile phone. When I plug it in, the phone sees the computer and gives me choices:
-pc suite
-media transfer
-mass storage
-some other thing about using the phone as a modem

I choose mass storage (which used to mount) and then the computer does nothing.

ls -l /media gives:

total 20
lrwxrwxrwx 1 root root    6 2009-09-11 01:02 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-09-11 01:02 cdrom0
drwxr-xr-x 2 root root 4096 2009-09-11 01:02 cdrom1
lrwxrwxrwx 1 root root    7 2009-09-11 01:02 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2009-09-11 01:02 floppy0
drwxrwxrwx 1 root root 8192 2010-01-04 12:11 Storage


I can't even see it mentioned in there anymore. Nor does it appear in mount manager. Is there any need to change the root to my usr in these other drives? I have had no problems with them.

Cam

---

### Post by Man with Hat on 2010-01-03
Just another quick add too,

I have - 2x DVD drives 
          - 1x 3.5 Floppy drive (I wouldn't part with it, I don't care what people think) 

The list shows 3xCD drives - I can accept them as DVD :)
                     2xfloppy drives

Or is it telling me that there is one CD path with 2 drives attached and one floppy path with 1 drive attached? The other drive mentioned is a second hard drive.

---

### Post by dcstar on 2010-01-03
> **Man with Hat said:**
> I have been going a little nuts trying to make my **mini SD** disk inside my nokia E71 want to be nice to me. If I plug it in via USB it auto mounts no problem, I can view and copy files no problems, but I can't write to it!
.........

And the little write-protect tab on it is set correctly?

As well, are there any options in the phone software to allow writes?

---

### Post by Man with Hat on 2010-01-03
Yeah, none of that is a problem. I probably should have mentioned that I have written to it dozens of time when I was using windows. The problem from what I can tell seems something to do with the format being vFAT 16

As far as phone software goes, don't even let me start ranting about that!! Nokia PC suite is not Ubuntu friendly (even in wine) and I can't find any software in the repositories that will support my model of phone.

---

