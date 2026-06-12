---
title: "Problem booting almost any linux install medium"
date: 2010-11-21
forum: General Help
---

### Post by beneggett914 on 2010-11-21
My brother-in-laws laptop hard drive went out on him. He got a brand new hard drive installed, but didn't have the original windows vista install disk, and he doesn't want to pay for a new copy. So I was going to try installing Ubuntu 10.10 for him. However, I can't get the live cd to boot.
 
The problem is not limited to just 10.10 live CD, I've tried an older 10.04, Linux mint 10, Debian 5, fedora core 14, and Knoppix v6.2, none of which will even start. I've also tried booting from a USB hard drive, but no luck there either.

I was, however, able to get puppy linux to boot and run just fine. Puppy is not the most ideal distro though, especially for my brother in law. He is not very tech savy, so he needs a user friendly distro. I checked gparted while in Puppy Linux and it show his hard drive is completely clean. It doesn't even have any partitions on it. I've also done a diagnostic test of the hard drive in the BIOS and it check's out fine.

Any help would be appreciated.

Specs:
HP 530 Notebool
Intel Centrino Duo 1.6 Ghz
1024 MB RAM

Edit: I installed winblows on it so it atleast works. I guess problem is sort of [solved], so I marked it as such. I'm not sure if I should have though.

---

### Post by Foxheadz on 2010-11-21
What happens when you try to boot?

---

### Post by beneggett914 on 2010-11-21
At first I was getting a "Non-sytem disk or Disk Error" message, but then just as an experiment i tried booting my windows xp install disk and it boots into windows install just fine, but I didn't actually go though with the install. After that everytime I'd try boot any the linux distros cd is just hangs on a black with a blinking cursor, no keyboard input works or anything. If i go to the bios and whip the drive from there it goes back to the "Non-sytem disk or Disk Error" message.

---

### Post by oldfred on 2010-11-21
Some BIOS will not let you boot unless it sees a boot flag. Ubuntu/grub do not use boot flag, but windows has to have one. BIOS should not care but it must be windows centric. Often just putting a boot flag on a partition solves the issue. Not sure why CD would not work. Perhaps you need to hit f6 and add some parameter. Often the small systems like puppy use the lowest common denominator that works for most.

I used same settings with Maverick as I did with Lucid.
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)

---

### Post by beneggett914 on 2010-11-21
> **oldfred said:**
> Some BIOS will not let you boot unless it sees a boot flag. Ubuntu/grub do not use boot flag, but windows has to have one. BIOS should not care but it must be windows centric. Often just putting a boot flag on a partition solves the issue. Not sure why CD would not work. Perhaps you need to hit f6 and add some parameter. Often the small systems like puppy use the lowest common denominator that works for most.

I used same settings with Maverick as I did with Lucid.
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)

I tried using a boot flag when I tried booting from the usb hard drive still didn't work. The boot image is on a third partition on the usb hard drive could that be a problem? I have one partition that is fat32 that has a bunch of media files on it. Then an ext4 partition I use for Linux backups which I shrunk down a bit using gparted to make room for the third partition which is using ext2 /w a boot flag. Then using UNetbootin I put the ubuntu boot image on there. but just come up with the "Non-system disk or disk error" message.

Also, I haven't been able to get it to boot far enough to have the option of entering parameters.

---

### Post by oldfred on 2010-11-21
If puppy & XP work then system must be ok and the Unetbootin installs must not be creating a bootable device. 

Verify that you have downloaded a good copy of the ISO and try again. I though uNetbootin required the entire flash drive and was installed to the FAT partition. I use grub2 to loopmount the ISOs, so I have not recently used any other installer.

---

### Post by beneggett914 on 2010-11-22
> **oldfred said:**
> If puppy & XP work then system must be ok and the Unetbootin installs must not be creating a bootable device. 

Verify that you have downloaded a good copy of the ISO and try again. I though uNetbootin required the entire flash drive and was installed to the FAT partition. I use grub2 to loopmount the ISOs, so I have not recently used any other installer.

I've tested the live-cd's on my desktop computer and they start up just fine. I just now tried reformatting that partition on my USB hard drive with FAT and a boot flag, but still didn't work. I don't have a flash drive handy to try it that way.

I'm thinking it has to be something with how these full blown distros install processes work, because I just tried Gentoo and that worked as well. Unfortunately, I don't think Puppy, or Gentoo would work well for my brother-in-law.

I'd still prefer solution for Ubuntu, or something similar, but if I have to make a compromise does anyone know of disto that has a very non-fancy boot install method yet still full-featured and user-friendly?

---

### Post by mculbertson on 2010-11-22
This may not apply to your situation and I am no expert at all. I had the exact problem trying to load up Ubuntu server edition for a friend over a year ago. Nothing would boot from the CD but puppy until I changed the bios setting from raid on to raid off. Again this may not help but throwing it out there for you.

Good luck!:D

---

### Post by beneggett914 on 2010-11-22
> **mculbertson said:**
> This may not apply to your situation and I am no expert at all. I had the exact problem trying to load up Ubuntu server edition for a friend over a year ago. Nothing would boot from the CD but puppy until I changed the bios setting from raid on to raid off. Again this may not help but throwing it out there for you.

Good luck!:D

I couldn't find any raid options in the bios, being an entry level laptop its probably not capable of raid.

---

### Post by cfree220 on 2010-11-22
Do you by any chance have an external hard drive enclosure that would accept a laptop HDD?

---

### Post by beneggett914 on 2010-11-22
I don't have one. I didn't even know they made them. lol.

---

### Post by cfree220 on 2010-11-22
Yup, they do. 2.5 inch external enclosures.

But I thought of something while I was sleeping.

What program did you use to write the disk image? I find that Brasero (on my machine), as well as the USB startup disk creator, have a very high rate of failure on my Dell XPS M1530 laptop. For whatever reason, right clicking on the .iso and hitting "write image to disk" is more likely to succeed than opening Brasero and using the write image utility.

If that doesn't work, I recommend InfraRecorder portable. You will, unfortunately, need a Windows machine for this.

---

### Post by oldfred on 2010-11-22
It is a bit more advanced as you have to use grub2 and edit the grub.cfg file manually but you can use grub2 to directly boot an ISO file. I use this for all new installs and repairCDs as it is just easier to copy the ISO to the flash drive & edit grub.cfg,

 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
multicd.sh - combine Linux ISOS into one
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)

My grub entry ( have several as I have several ISO all on one Flash drive.Important thing is path has to match, I use /boot/iso as location of ISOs.

```
menuentry "Ubuntu 10.10 Maverick 64bit" {
    set isofile="/boot/iso/ubuntu-10.10-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile
    initrd (loop)/casper/initrd.lz
}

```Ok, I like grub2 and it is a case of if you have a hammer everything looks like a nail. But grub2 is good at booting just about anything.:)

---

### Post by beneggett914 on 2010-11-24
Thanks to everyone for the help. I was never able to figure it out, but my brother-in-law was kind of anxious to get his laptop back, so I ended up just giving him my copy of windows xp, and I uninstalled it from my computer, I never really used windows on my computer anymore anyway. I've thought about going windows free for a while now, so I thought now would be as good a time as any to finally take that step.

---

