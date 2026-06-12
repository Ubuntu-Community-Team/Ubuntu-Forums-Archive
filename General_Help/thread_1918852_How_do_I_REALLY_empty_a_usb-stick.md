---
title: "How do I REALLY empty a usb-stick?"
date: 2012-02-01
forum: General Help
---

### Post by Papa-san on 2012-02-01
Hi folks.
I am going to be using a 4GB stick to upgrade soon, but first need it to upgrade firmware on my T.V. I've looked everywhere at Hitachi's site, and they don't explain it anywhere. I need a solution that works through my ubuntu system...

When I copy the proper file to the stick, my T.V. sees the 'trash.0001' file, and wants to use a picture viewer to look at it. They say I need to have an empty stick, and even a WinVista long-version format didn't get rid of it.

Does anybody know a safe way to clear everything off of it? (It tells me that there are 3.72G.B. free after formatting...)

Thanks, in advance!

---

### Post by deonis on 2012-02-01
please, go to nautilus and hit Ctrl+h. Select all files and delete them :). You can also format your USB drive with the "disk utility" ...

---

### Post by KBD47 on 2012-02-01
On a 4gig stick you never really have 4 gig free. 3.72 sounds about right. I use gparted with the usb stick plugged into the computer, make sure you use the drop down box to chose your stick rather than your computer hard drive, you can then see the 4 gig usb, and then delete whatever is on it, you may have to unmount the stick. You can then fat32 format the stick which makes it usable. Can't say what the issue is with your TV firmware. I have had to go back to Windows to install firmware before, sometimes no matter what you do some systems just don't like Linux.
KBD47

---

### Post by Double.J on 2012-02-01
Hi there!

Use Deonis' advice first! If fo some reason there's another problem, download and run gparted to remove any additional partitions on the drive - check it's the correct device selected!

If all else fails, as a last resort;

if you want to get rid of absolutely everything, then it's
```
 sudo fdisk -l
``` to find out which drive the stick is - be doubly sure!, then
```
 sudo dd if=/dev/zero of /dev/sdX bs=512k
```Where X is the drive leter from the previous step - no numbers. Be really sure you've go the write device ;)

---

### Post by Papa-san on 2012-02-03
Thanks to all of you for the answers. I'll be able to try it soon, and I'll let you know how it goes. (I don't get much time on my computer each day. That is one of the biggest reasons I switched to Ubuntu. I started with Dapper Drake, and after a rough set-up and steep learning curve, have enjoyed having a stable computer system that doesn't eat up all of my time with antivirus crap!)

---

### Post by sudodus on 2012-02-03
> **gnu/mirow said:**
> Hi there!

Use Deonis' advice first! If fo some reason there's another problem, download and run gparted to remove any additional partitions on the drive - check it's the correct device selected!

If all else fails, as a last resort;

if you want to get rid of absolutely everything, then it's
```
 sudo fdisk -l
``` to find out which drive the stick is - be doubly sure!, then
```
 sudo dd if=/dev/zero [COLOR="Red"]of=[/COLOR]/dev/sdX bs=512k
```Where X is the drive leter from the previous step - no numbers. Be really sure you've go the write device ;)
... Just a small typing error, but with dd even small errors can cause big trouble.

---

### Post by Papa-san on 2012-02-03
When I tried it, it wouldn't work... Thanks for the fix Sudodus!

So, how long should it take to finish? 
OK... It took a minute, but is finished.

Thanks to all!

---

### Post by sudodus on 2012-02-03
> **Papa-san said:**
> When I tried it, it wouldn't work... Thanks for the fix Sudodus!

So, how long should it take to finish? 
OK... It took a minute, but is finished.

Thanks to all!
You are welcome, and please mark this thread SOLVED

---

