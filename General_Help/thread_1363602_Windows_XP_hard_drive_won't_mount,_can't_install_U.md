---
title: "Windows XP hard drive won't mount, can't install Ubuntu!!!"
date: 2009-12-24
forum: General Help
---

### Post by aformon on 2009-12-24
Hi, sorry if this is already answered somewhere else but i have looked and can't find anything that works!!
Have a very old desktop with windows XP, its crashed with blue screen saying cannot mount hard drive as it was not properly unmounted on shutting down. Figured its a great opportunity to get ubuntu on it as i'm already running it on my main machine (and am very happy!!) Put my live cd in the desktop but still cannot access the hard drive and can't install it as during the setup it asks me to select where to install and there are no partitions/harddrives to select :s got to get this harddrive unmounted or whatever i need to do to get the hardrive back and Ubuntu installed.
Thanks in advance for any help :)

---

### Post by 73ckn797 on 2009-12-24
If you have the Windows disk, boot with it and go to recovery. From the prompt enter:
```
chkdsk c:
```See if that will work.

I have had cases when Windows shut down improperly. When I would boot into Ubuntu it would not read the Windows drive/partition. I would have to do the chkdsk on Windows first then all was well. If you are going to completely delete Windows it may be good to, again, boot from the Windows CD and from recovery see if you can go to "fdisk" and delete and reformat the drive.

From commmand prompt enter:
```
fdisk
```
You can delete the partition from fdisk and create a new one.
or just enter:
```
format C:
```

---

### Post by aformon on 2009-12-24
only problem is I haven't got the original windows disk! Is there any way around it? Thanks again

---

### Post by Morbius1 on 2009-12-24
You could download a Windows Bootdisk from here:

[http://www.allbootdisks.com/download/iso.html](http://www.allbootdisks.com/download/iso.html)

I always have the Win95b bootdisk version handy for pre Vista machines.

EDIT: It's just the old bootdisks that used to come with windows. They're DOS with extra drivers. You can use the dos commands posted above once you boot to the burned disk.

---

### Post by aformon on 2009-12-24
ok have burned that to disk and booted using the cd,
I get the symbol A:\> then am entering my commands after this.
On entering 

chkdsk c:

it says 'invalid drive specification' then recommends using SCANDISK. TRied that and it will only scan the A drive.

on entering

fdisk

it says 'no fixed disks present'

and on entering 

Format C: 

I get 'invalid drive specification'

Its being a right pain!!

---

### Post by 73ckn797 on 2009-12-24
Does the BIOS detect the drive? If not the drive may be dead. If so, does BIOS have any setting(s) to know a drive is there? Is the drive set for IDE mode? All of this is in BIOS. Could be that the power supply has died and is not powering the drive though everything else may be working.

---

