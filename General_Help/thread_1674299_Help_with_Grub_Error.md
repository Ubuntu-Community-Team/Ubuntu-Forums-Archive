---
title: "Help with Grub Error"
date: 2011-01-23
forum: General Help
---

### Post by LuciferDarkWatch on 2011-01-23
Hi All,

I am new to linux and am using ubuntu as the first stepping stone from windows.

I installed dual boot with windows 7 and ubuntu 10.10 had no problems, got everything work nicely except for a few little things that i am working on and are not really that important,

But as this is my first linux distro to use and still use windows for most of the stuff i use, i wanted to change boot order so windows was default and had to select ubuntu.

So i edited grub changed default 0 to default 5 and also changed boot timer from 10 seconds to 30 seconds. no other changes. rebooted intending to check and boot into windows 7.

When it rebooted i got normal grub bootloader.

Ubuntu, with Linux 2.6.35-24 Generic
Ububtu, with Linux 2.6.35-24 (Recovery Mode)
Ubuntu, with Linux 2.6.35-22 Generic
Ubuntu, with Linux 2.6.35-22 (recovery Mode)
Memory Test (memtest 86+)
Memory Test (memtest 86+ Serial Console 115200)
Windows 7 (loader ) (on /dev/sdc3)

So now when it boots its default is Memory Test (memtest 86+ Serial Console 115200)

Not only that but the keyboard wont respond so it wont let me select Ubuntu again so i can fix my mistake. there is nothing wrong with keyboard as it works at bios and if i boot to cd. just wont work on bootloader menu or from within mem test.

I have booted up Ubuntu live cd and tried to reinstall grub. did that but still no changes.

Any and all help would be greatly appreciated.


System Specs

AMD Athlon 64 3500+
3Gb Ram
Nvidia GeForce 7600 GT
Creative X-Fi Extreme Audio Sound Card
250 Gb x 2 + 500 Gb sata x 2

Partition Setup

20Gb /
100Gb /home
12Gb /swap
100Gb /Windows 7

---

### Post by drs305 on 2011-01-23
The grub menu counting starts at 0, so 5 is giving you the serial memtest. Can you hold down the SHIFT key to get to the Grub menu and select another option?

---

### Post by LuciferDarkWatch on 2011-01-23
No the Keyboard wont work as soon as bootloader starts.
And even when memtest is running keyboard doesnt work.

Is there a way to edit the grub file from within live cd.

I have Zer0 Linux experience, i have tried booting into livecd and clicked on root \ drive and gone into etc/default/grub but it wont let me edit the default.

is there a way to get in as my su from install and edit it while loading livecd

---

### Post by LuciferDarkWatch on 2011-01-23
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         262        2873    20972544   83  Linux
/dev/sda2            2873       15927   104856255   83  Linux
/dev/sda3           15927       28982   104856576    7  HPFS/NTFS
/dev/sda4           28982       30402    11408384   82  Linux swap / Solaris

NTFS = Windows 7


Sorry For Double Post

---

### Post by drs305 on 2011-01-23
You can use the chroot procedure described in this guide to purge and reinstall Grub2 from the LiveCD:

[HOWTO: Purge and Reinstall Grub 2 from the Live CD ]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by LuciferDarkWatch on 2011-01-23
Thanks everybody for helping.

I got it fixed for anybody else who ever runs into same mistake.

Can be done with livecd

Launch Terminal:

sudo mkdir /mnt/test1

sudo mount /dev/sda1 /mnt/test1

Or Replace /sda1 with what your partition is

ls /mnt/test1

gksudo gedit /mnt/test1/boot/grub/grub.cfg

All info from great user named danst_ on freenode #Ubuntu

danst_ REP +++ :popcorn:

---

