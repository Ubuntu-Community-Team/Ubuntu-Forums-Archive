---
title: "Suddenly, no loger boots"
date: 2010-05-13
forum: General Help
---

### Post by JC Cheloven on 2010-05-13
Hi, this is about an installation of UbuntuStudio 9.10 (karmic) 64bit, ext4 filesystem. It has been working flawlessly for months, but today it stopped to boot. It isn't connected to the internet, so it can't be a faulty update.

Grub menu appears, and is able to boot in xp. But when trying to boot ubuntu, the ubuntu logo appears briefly, and then this message (I transcribe what I think is the interesting part):

```
Alert: /dev/disk/by_uuid/621dcabc-04ff-4bc1-8ba9-19a7b1107734 does not exist.
```

And drops to an initramfs console, in which I dunno what to do.

I booted from live and ran fsck on /dev/sda5 (where the installation is). It does the ckecking in a breeze, and reports no errors. Also I checked the uuid using blkid, and is correct (coincides with the one from the "alert" above).

Any ideas?

---

### Post by blazemore on 2010-05-13
> **JC Cheloven said:**
> Hi, this is about an installation of UbuntuStudio 9.10 (karmic) 64bit, ext4 filesystem. It has been working flawlessly for months, but today it stopped to boot. It isn't connected to the internet, so it can't be a faulty update.

Grub menu appears, and is able to boot in xp. But when trying to boot ubuntu, the ubuntu logo appears briefly, and then this message (I transcribe what I think is the interesting part):

```
Alert: /dev/disk/by_uuid/621dcabc-04ff-4bc1-8ba9-19a7b1107734 does not exist.
```And drops to an initramfs console, in which I dunno what to do.

I booted from live and ran fsck on /dev/sda5 (where the installation is). It does the ckecking in a breeze, and reports no errors. Also I checked the uuid using blkid, and is correct (coincides with the one from the "alert" above).

Any ideas?

Hi, please boot from live and run the commands:
```
sudo mount /dev/sda5/ mnt
cd /mnt
sudo gedit etc/fstab #no leading forward-slash
```Replace

/dev/disk/by_uuid/621dcabc-04ff-4bc1-8ba9-19a7b1107734

with

/dev/sda5

Reboot and enjoy :-)

---

### Post by JC Cheloven on 2010-05-13
Thanks, will try asap and come back to mark as solved, if applicable ;-)

Event in the event that works, I'll still remain confused. Why a mounting by uuid in fstab should stop working? Never mind, I'll simply try and see.
JC
_______________

---

### Post by blazemore on 2010-05-13
> **JC Cheloven said:**
> Thanks, will try asap and come back to mark as solved, if applicable ;-)

Event in the event that works, I'll still remain confused. Why a mounting by uuid in fstab should stop working? Never mind, I'll simply try and see.
JC
_______________

I'm not sure either. In fact, this is the sort of problem uuids are supposed to help prevent! :confused:

Maybe you changed some hardware configuration from another distro, or resized a partition from within Windows?
At any rate, this will sort you out!

---

### Post by JC Cheloven on 2010-05-14
Hi again,

No changes were done in the system that could have -reasonably- caused this. No resizing, or manipulating disk spaces in any way. Problems can't come from there.

Unfortunately, specifying the device in fstab by uuid or as /dev/sda5 made very little difference. Only a slight change in the text of the alert. Now it reads (EDIT: "unid" seems strange to me, perhaps it's still "uuid"; someone have read that to me by phone after I changed fstab)
```
Alert: /dev/disk/by_unid/621dcabc-04ff-4bc1-8ba9-19a7b1107734 does not exist.
```


Trying to figure out: the part of the message I didn't pay attention to, was 
```
Common problems are
-Boot args: cat /proc/cmdline
-- rootdelay : did the system wait enough?
-- root : did the system wait for the correct device?
-Missing modules? cat /proc/modules, ls /dev
```
Which I think is of little help but anyway.

I'm wondering if the problem may be caused by the ext4 filesystem, which I've read had some flaws yet? If so, is there an easy way to change it to ext3 without affecting the data? 
Any further input would be appreciated.
JC

---

### Post by dino99 on 2010-05-14
sudo apt-get install -f
sudo dpkg --configure -a

sudo update-grub

[http://manpages.ubuntu.com/manpages/karmic/man8/blkid.8.html](http://manpages.ubuntu.com/manpages/karmic/man8/blkid.8.html)

---

### Post by HiImTye on 2010-05-14
it may be an issue with the ext4 filesystem if you upgraded an ext3 to an ext4 and didn't set it up in fstab properly. it would work with the same kernel but as soon as you updated to a new kernel you would run into a problem

other than that, the ext4 filesystem seems to be running flawlessly for me

quick quesdtion, did you reduce the timeout delay in your system BIOS? it could be the culprit (can also cause mount as read-only issues)

---

### Post by JC Cheloven on 2010-05-14
> **HiImTye said:**
> it may be an issue with the ext4 filesystem if you upgraded an ext3 to an ext4 and didn't set it up in fstab properly. it would work with the same kernel but as soon as you updated to a new kernel you would run into a problem

other than that, the ext4 filesystem seems to be running flawlessly for me

quick quesdtion, did you reduce the timeout delay in your system BIOS? it could be the culprit (can also cause mount as read-only issues)

Hi, the partition was formatted as ext4 from the beginning. It's the strange thing: absolutely nothing system-related was changed. In fact the installation has been used only to rip movies with acidrip, and copying music and other files from/to pendrives and external disks. 

I didn't even visited the bios either, but I can have a look on the timeout delay you said, provided I manage to find that in the bios :-/

Will come back with whatever news they are.

---

### Post by HiImTye on 2010-05-14
if you didnt change it dont fiddle around in there, less problems to take care of at once

try this:
[http://ubuntuforums.org/showthread.php?t=987243](http://ubuntuforums.org/showthread.php?t=987243)

---

### Post by JC Cheloven on 2010-05-14
Thanks Tye for the link, looked promising. 
But I tried it, and the only effect is that it takes longer to pass from the moving ubuntu bar to the b&w screen.

The next step I plan is to use SystemRescueCD or something similar to check the disk surface. It's a shot in the dark, I'm really clueless.

---

### Post by JC Cheloven on 2010-07-31
Hi, I ended up reinstalling that one (formatted as ext3 just in case). I'm waking up this old thread because I just had again a similar issue.

[INDENT]Note.- I do a lot of Ubuntu installations for friends and relatives. The one I'm reporting today is a different one, in a different pc. The commonplace is that this one is also karmic 64bit on an ext4 partition.[/INDENT]

The computer this time is a packard-bell 17" laptop. The problem was the same: all seemed fine, but suddenly no longer boots. It pass grub, UUID seems fine... but no way. 
I had the idea of editing the kernel line in grub2 at boot time. Replaced the item 
[CENTER]root=UUID=b82c(...long hex number)[/CENTER]
by
[CENTER]root=/dev/sda5[/CENTER]
That way, it boots. I changed the mounting of the device in fstab to be by /dev/sda5 instead of by UUID, and the problem was gone. I guess that this time the simple modification of the fstab file, as blazemore suggested in post#2, would have worked equally.

Conclusion: It may be karmic-64, or ext4, or the combination of both, but I don't think it's about hazard. One time could be, but two... [-X

Nevertheless, my main machine has also a 64bit karmic install on ext4 and has been rock-solid for 8 months. So perhaps this issue is also hardware dependent.

So far my findings. Regards
JC

---

