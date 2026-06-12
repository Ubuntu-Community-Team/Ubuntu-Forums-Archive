---
title: "RSYNCing /home with ownership problems"
date: 2009-10-19
forum: General Help
---

### Post by Rehd on 2009-10-19
Hei,

I am quite new to Linux/Ubuntu and very happy about it. Started just recently to write my own scripts.

I found rsync quite straightforward and wrote a little script to mirror my /home directory to a 16GB-USB-Flash-drive.

Somehow things getting more complicated without me changing anything.

1) In the beginning (maybe when Hardy came last year) I started with:
```
rsync -au --exclude '.*' --exclude '*~' /home/ME/ /media/USBdisk/
rsync -au --exclude '.*' --exclude '*~' /media/USBdisk/ /home/ME/
sync;sync;sync
umount /dev/sdc1/
```
not very elegant, but it worked! It did eject the USB drive.


2) Then after a while (some update?) umount did not work anymore?!
I tried it in a shell and I got an error with permissions; but I swear it worked!

So I just deleted
```
umount /dev/sdc1/
```

3) Then suddenly I got error messages after login, complaining about

> User's $home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permission. User's $home directory must be owned by user and not writable by other user's.

It took me some weeks to find out that suddenly my rsync script messed up those permissions.

So I added

```
chmod 644 /home/reinhard/.dmrc
chmod o-w /home/reinhard/
```

4) Now I am trying Koala Beta (Xubuntu amd64) and I LOVE it a lot. This is really good work and it is my favorite of all the great Ubuntus so far.

But the rsync script gets even more into trouble:

When I use it, everything goes fine, BUT it takes ages on error messages complaining for each and every file and directory:
```
rsync: chgrp "/media/disk/*whatever*" failed: Operation not permitted
```

ls -l /media shows
```
drwxr-xr-x 18 rforge root 8192 2009-10-19 13:09 disk
```for the USB-flashdrive.

I tried to change the group to rforge (my username) to no avail.

So some month ago, rsync just worked and I thought this is just the greates tool in the smallest package I have ever seen. But now things get more and more complicated and I wonder if I should use rsync at all. Lately I had to format the USB drive since a XP no longer wrote to the USB disk and I suspect the ownership trouble with rsync/Ubuntu responsible.


=> As anyone who uses rsync can see: I just want to mirror the usb-disc and my home directory. With ownership, permissions and groups as in my /home/ME/ directory and subdirectories. I would really appreciate any useful thoughts on this. And it would be great if someone knew a way to eject the disk with the script!

Best regards,
Reinhard

---

