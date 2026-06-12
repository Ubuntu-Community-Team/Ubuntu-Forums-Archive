---
title: "partimage"
date: 2004-10-19
forum: General Help
---

### Post by bantu on 2004-10-19
Has anyone got partimage (out of universe) to work?
Error message:
> /dev/dm inode not found
(or similar).
Any help would be appreciated.
Thanks,
bantu

---

### Post by bantu on 2004-10-22
Hi guys and gals...

None of you using partimage? :shock:

---

### Post by rolf on 2004-10-22
[quote=bantu]Has anyone got partimage (out of universe) to work?
Error message:
> /dev/dm inode not found
(or similar).
[/quote]

I have not tried it yet but I am about to.  Are you tying to create or restore an image?  Off hand, I think this is a module issue, but again I have not tried it (yet).  Trying now....

---

### Post by rolf on 2004-10-22
[quote=rolf]Trying now....[/quote]

Hmm.  No issues here, partimage worked as expected.  Did you boot from the ubuntu partition or from a cd/floppy?

---

### Post by bantu on 2004-10-22
Great to hear from someone. Thanks for your reply, rolf.

I just re-installed partimage to try again. But I got the same error message...
How did you start partimage? I tried it with "sudo partimage" in an ordinary console window, then I tried it with the rood console... to no avail.

I use partimage on another partition with another Debian based distro without any problems. I really would like to get it to work, as I am tired of booting from a live CD to make my backups.

Any other ideas?

---

### Post by rolf on 2004-10-22
bantu, wish I could be of more help.  I used a liveCD to run partimage - I have not tried running it from the partition, but I will give it a try and see what happens.  I am concerned about trying to run partimage to make backups from the active partition, seems like that could cause some open file issues.

---

### Post by bantu on 2004-10-22
hi rolf
>  I am concerned about trying to run partimage to make backups from the active partition...
You are dead right. This is my problem, that's why I have to run an live CD to make an image of my other linux partition.
Well, if you get a chance to run partimage from a HD install of ubuntu, let me know. Have a nice weekend, and thanks again.  :D

PS: If you make a backup of a partition, that partition must be unmounted first...

---

### Post by bantu on 2004-10-25
So there's just the two of us trying to get partimage to work, and hundreds of people want to know how we do it...

---

### Post by jeremy on 2004-10-25
I have the same message; /dev/dm inode not found

I have tried it as root, and it is still the same.

---

### Post by jeremy on 2004-10-26
I have  just downloaded and burnt the ubuntu live cd, to my surprise there seems to be no partimage on that, oh well, knoppix for backups it is, then.

---

### Post by stevho on 2004-11-18
This problem seems to be due to LVM which is installed as part of ubuntu-base and/or EVMS  (Enterprise Volume Management System).

If like me, you read [www.tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](www.tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html) and decide that the complexity is not worth any likely benefit, you might get partimage to work by removing the following packages:-

evms (which also removes: evms-curses and libevms-2.3)

lvm2
lvm10

I'm not sure if you also need to delete /etc/init.d/lvm (I had already done that).

I can now start partimage.

However, I have not used partimage before and I haven't yet tried to do anything with it, so I don't know how functional it is.

Also, I don't know whether removing the above packages causes any other problems - please let us know :)

Steve

---

### Post by arx-lupus on 2005-01-10
Before I go ahead and try this does anyone know wether it works/or those packages are needed for something else?

Cheers

---

### Post by Ste on 2005-01-10
I got it running, you can download the binaries from the partimage website so no instal is needed. [http://www.partimage.org/download.en.html](http://www.partimage.org/download.en.html) download "Static i386 binary tarball" extract and run.

However it can't recognise my ext3 hda1. 
Can I convert that without formatting ?

---

### Post by Henryk on 2005-04-02
Moin,

[QUOTE=jeremy]I have the same message; /dev/dm inode not found

I have tried it as root, and it is still the same.[/QUOTE]

Yeah, I see that too. As far as I can tell that's a bug in partimage: It's not properly reading the /proc/partitions list when the dm_mod module is loaded. There already is a bug report at the partimage sf project: [https://sourceforge.net/tracker/?func=detail&atid=106212&aid=1056397&group_id=6212](https://sourceforge.net/tracker/?func=detail&atid=106212&aid=1056397&group_id=6212)

As a workaround I'd propose removing the dm_mod module if that's at all possible

-- 
Henryk Plötz
Grüße von der Ostsee

---

### Post by dzorman on 2006-02-25
I was experiencing the same error "/dev/dm not found"

With a little research into mknod I was able to fix the problem with the following command:

mknod -m 644 /dev/dm b 240 0

This seemed to work after hours of hair pulling!

---

### Post by wim bertels on 2006-08-27
i fixed it in another way, (mknod didnt work, inodes already existed..)

partimage complained about non existing inodes,
so in just linked to non existing inodes to existing one,

in short:
mkdir /dev/ide/.../disc
ln -s /dev/hda /dev/ide/..

and the same for the partitions of the drive, just using the errors messages partimage gave me

---

### Post by Cuppa-Chino on 2006-08-28
> **jeremy said:**
> I have  just downloaded and burnt the ubuntu live cd, to my surprise there seems to be no partimage on that, oh well, knoppix for backups it is, then.

Fair enough, I am up for that, but I run into trouble when partimage with Knoppix, I have 1 gig of ram but it keeps spitting out that is run out of ramdisk, although I told it to put data on my vFAT drive that has more than enough room for all my ubuntu data.

Any ideas?

Anybody partimage direct to DVD-writer?

---

### Post by Cuppa-Chino on 2006-09-02
anybody any help on my partimage question

---

### Post by bij33 on 2007-09-13
I have the same problem and can not get the Partimage to work. It is telling me I need to "umount /". When I issue the command, it says device is busy. Just don't know how to get around this problem. Is it possible to run the Partimage after "umount /"? 
I have Ubuntu installed on D drive (C has Win XP) and I am trying to make an image of system (Ext3) on my external drive (WD Passport).

Also how do I put a check mark in compression level box None? Mine is locked in with a * in Gzip box and I can't change it.

TIA

---

### Post by Cuppa-Chino on 2007-09-14
I have gone over to using system rescue cd --- [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page") 

that has helped a lot, try their description, it worked a treat for me

---

### Post by ChrisNiemy on 2007-11-10
Hi,

I found both a workaround and a fix to that problem:

When partimage complains about that "/dev/dm not found" there you can just press ENTER a few times patiently (around 5 to 10 times), then the error messages fades and you can work with partimage. Though you have to do this every time you start partimage.

If this won't affect some other configuration (I guess if it will, experienced users will notice this) you can just create this /dev/dm yourself by:
```
sudo mknod -m 644 /dev/dm b 240 0
```

Then right away, partimage will start without any complains. Happy partitioning! ;-)

EDIT: Here's where I found this fix (in German): [http://www.linux-user.de/ausgabe/2007/05/082-partimage/index.html](http://www.linux-user.de/ausgabe/2007/05/082-partimage/index.html)

---

### Post by indytim on 2007-11-10
First off I have been running Partimage successfully for 1+ years now.  My environment covers multiple Lx ops so I just switch between ops to backup the opposing ops.  As was mentioned previously, you cannot run Partimage to the /boot partition.  

There is a bootable app that will boot and allow you to run Partimage.  The url for this is:

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

Hope this helps,

IndyTim

---

