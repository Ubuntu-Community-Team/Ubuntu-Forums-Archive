---
title: "Tar to the USB memory stick"
date: 2009-08-30
forum: General Help
---

### Post by wolfv6 on 2009-08-30
I am having trouble tarring to a USB memory stick.  I am new to Linux and tar.  I hope you can help. 

I am running Ubuntu 9.04 and the USB memory stick is 1G of FAT32.  The folder being tarred is only 5kb.  From Nautilus 2.26.2 Properties, the memory stick has 0 bytes used and 0 bytes free.

 ***** Tarring to the harddrive worked *****
 ```
wolf-PC:~/music> tar -cvpzf /home/wolf/backup.tar.gz . 
 ./ 
 ./doorbell.ram 
 ./~WRL0001.tmp 
 ./Music List.doc 
``` ***** Tarring to the USB memory stick gets an error *****
 ```
wolf-PC:~/music> sudo tar -cvpzf "/media/STORE'N'GO/backup.tar.gz" . 
 ./ 
 ./doorbell.ram 
 ./~WRL0001.tmp 
 ./Music List.doc
 gzip: stdout: No space left on device 
 tar: Child returned status 1 
 tar: Error exit delayed from previous errors 

``` Thank you in advance.

---

### Post by jerome1232 on 2009-08-30
Partition issue? Do you have stuff on that drive maybe reformatting would resolve it.

---

### Post by wolfv6 on 2009-08-31
jerome,

Thank you for your suggestion.  It got me further along in the trouble shooting.

I tried using GParted to reformat my USB-memory stick labeled "STORE'N'GO", but when I go to unmount STORE'N'GO GParted says:
```
Could not unmount /dev/sdb1
unmount: /media/STORENGO: not found
```So I tried umount from the terminal with similar results:
```
wolf-PC:/media> umount /STORENGO
umount: /STORENGO is not mounted (according to mtab)
wolf-PC:/media> umount /STORE'N'GO
umount: /STORENGO is not mounted (according to mtab)
wolf-PC:/media> umount "/STORE'N'GO"
umount: /STORE'N'GO is not mounted (according to mtab)
```There is a README.txt file on STORE'N'GO that I can open, edit, and save.

Do you have any other ideas?

Thank you.

---

### Post by The Cog on 2009-08-31
I think the problem is the name STORE'N'GO. You could try using tab filename completion to get the correct pathname into the command line, for instance 
**sudo tar -cvpzf "/media/STORE[COLOR="Red"]<Tab>[/COLOR]**, or dragging the folder to the command line from a nautilus window. 

But you may have to change the label of the disk. Not sure off the top of my head how to do that. And I'm only guessing at the problem anyway.

---

### Post by muteXe on 2009-08-31
yep, definately an apostrophe thing.  Read the last section of [http://www.linux-noob.com/forums/index.php?/topic/144-wildcards-quotes-back-quotes-and-apostrophes/](http://www.linux-noob.com/forums/index.php?/topic/144-wildcards-quotes-back-quotes-and-apostrophes/)

change your label to something less mad.

---

### Post by DaithiF on 2009-08-31
Just to note that none of these would have worked anyway, apostrophe issue or not:
wolf-PC:/media> umount /STORENGO
umount: /STORENGO is not mounted (according to mtab)
wolf-PC:/media> umount /STORE'N'GO
umount: /STORENGO is not mounted (according to mtab)
wolf-PC:/media> umount "/STORE'N'GO"
umount: /STORE'N'GO is not mounted (according to mtab)
because you are asking to umount something located at / whereas its actually located at /media

I would have thought this should have worked (from /media directory)
```
umount "STORE'N'GO"

```
(and assuming that your user id has the permissions to umount in the first place of course -- if not then prefix sudo)

but I agree with the other posters that an apostrophe-less disk label would be better.

---

### Post by The Cog on 2009-08-31
Actually, I just tinkered with a directory called STORE'N'GO, and putting it in quoted seemed to work. So I wonder if the tar file is really as small as you say. Try creating the tar file locally and then copying it to the external drive with a cp (or mv) command.

---

### Post by wolfv6 on 2009-08-31
DaithiF,
Wow, I didn't even see that.

From terminal, umount worked from root, but not from media.  Interesting.  Maybe a problem concatenating path with double quotes.

```
wolf-PC:/media> umount "STORE'N'GO"
/sbin/umount.hal: STORE'N'GO is not recognized by hal
wolf-PC:/media> umount "/media/STORE'N'GO"
wolf-PC:/media> ls
cdrom  cdrom0  floppy  floppy0    sda1
```After removing and reinserting STORE'N'GO into USP port, tar worked.

```
wolf-PC:~/music> sudo tar -cvpzf "/media/STORE'N'GO/backup.tar.gz" .
[sudo] password for wolf:
./
./doorbell.ram
./~WRL0001.tmp
./Music List.doc
```Thank you all for your suggestions :)

---

