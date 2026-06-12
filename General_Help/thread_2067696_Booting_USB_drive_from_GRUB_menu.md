---
title: "Booting USB drive from GRUB menu"
date: 2012-10-07
forum: General Help
---

### Post by Aquanet on 2012-10-07
My USB drive, with UbuntuLive installed, does not show up in grub. Apparently I have grub2 installed because "root" is not a command, when I try to follow the guides. 


So what should I do to get grub to recognize the usb?

---

### Post by Zimmer on 2012-10-07
Need a bit more information on what partition/distribution GRUB is currently loaded on and also how you created the UbuntuLive USB.

Normally, to boot a LIVE USB distro (created by something like Unetbootin ) you would set your BIOS to boot from USB before the internal drive. No GRUB required.

There's lots of info about various methods and distributions etc. on the Pendrivelinux web site.

---

### Post by Aquanet on 2012-10-07
Grub is loaded on the same drive/partition with Precise, which also dualboots Windows on another drive.

I created the Live USB w/Persistence with LinuxLive USB Creator (LiLi) with 12.04.1.

I can set the BIOS to boot from USB, but I don't want the USB to be first priority. I'd rather to be able to select from grub.

---

### Post by C.S.Cameron on 2012-10-07
Plug in your bootable USB drive then in Terminal run:
```
update-grub
```
You should then have the option to boot the drive in grub.

---

### Post by Aquanet on 2012-10-07
> **C.S.Cameron said:**
> Plug in your bootable USB drive then in Terminal run:
```
update-grub
```
You should then have the option to boot the drive in grub.

That's all? I'll try it out right now to see if it works, [strikethrough]but I was having space constraint issues, so do you know how much total KB/MB would it use?[/strikethrough]

Nvm about the space issue thing, it seems it'll be writing to the internal drive.

---

### Post by Zimmer on 2012-10-07
Thanks for the extra info..

Boot up Precise,   insert your USB drive, open a Terminal and issue command

sudo update-grub

and hopefully it will discover the install on the USB drive and create a GRUB entry for it..

---

### Post by C.S.Cameron on 2012-10-07
It should not take more than a byte or two to add the USB to grub.
Once the USB is booted nothing is written to the internal drive, unless that is where your casper-rw file or partition is located.

---

### Post by Aquanet on 2012-10-07
I updated grub on Precise(not UbuntuLive) with the USB plugged in. I rebooted and it still doesn't show in the grub menu.

I have two partitions on the USB, the primary is UbuntuLive w/ Persistence(Fat32), the other is blank(ext2). I think that's causing problems.

If reformatting the blank partition(ext2) to another filesystem could help, I am open to that. There's no information to save.

---

### Post by ajgreeny on 2012-10-07
I don't think grub2 is able to boot a live CD in the way you are wanting it to.

However it is possible to boot to an iso file from grub without copying it as an image, but just using the single ubuntu.iso file.

See [http://ubuntuforums.org/showthread.php?t=1838959](http://ubuntuforums.org/showthread.php?t=1838959) for some details which may help you further.

---

### Post by Aquanet on 2012-10-07
> **ajgreeny said:**
> I don't think grub2 is able to boot a live CD in the way you are wanting it to.Does grub boot live OSs in other ways?

> However it is possible to boot to an iso file from grub without copying it as an image, but just using the single ubuntu.iso file.

See [http://ubuntuforums.org/showthread.php?t=1838959](http://ubuntuforums.org/showthread.php?t=1838959) for some details which may help you further.
I'm not sure if that'll help since I'll be using Persistence.

---

### Post by greatsirkain on 2012-10-07
I put super grub2 disk on the same usb as my ubuntu live, if the usb is plugged in I select supergrub2 and ask it to detect all OS, which it does inc windows, then I just choose the latest linux. If it's not it just automatically boots to windows. Both windows and Ubuntu are installed on the same hard drive.
I used sardu to build the usb stick.
If I've understood you right this would give you the grub menue to boot any OS but only when the usb is plugged in.
If you want to be able to do it without the usb then this is pretty much the same question I asked a while back and someone suggested I install super grub2 on the hard drives and not on the usb stick

---

### Post by Aquanet on 2012-10-07
> **greatsirkain said:**
> I put super grub2 disk on the same usb as my ubuntu live, if the usb is plugged in I select supergrub2 and ask it to detect all OS, which it does inc windows, then I just choose the latest linux. If it's not it just automatically boots to windows. Both windows and Ubuntu are installed on the same hard drive.
I used sardu to build the usb stick.
If I've understood you right this would give you the grub menue to boot any OS but only when the usb is plugged in.
If you want to be able to do it without the usb then this is pretty much the same question I asked a while back and someone suggested I install super grub2 on the hard drives and not on the usb stick

I think your solution would work, along with installing regular grub on the live USB. If nothing else works, I'll resort to that, but being able to boot from Precise, would've been best. The less things installed on the usb the better.

---

### Post by AndyOpie150 on 2012-10-07
Just another option: Plop Boot Manager.
I have an old 2003 machine. With  Plop Boot Manager I can choose what I want to boot into, CD, USB etc. ,without having to go into the BIOS.

---

