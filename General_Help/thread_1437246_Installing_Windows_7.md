---
title: "Installing Windows 7"
date: 2010-03-23
forum: General Help
---

### Post by VXxed on 2010-03-23
So here's my challenge.  I'm trying to use GRUB to boot up an installation ISO.  I ask this here because I feel it has more to do with Grub and Linux than it does with windows bootup procedures, because I feel this may be adapted to boot up ANY kind of bootable ISO file in CD format.  But that remains to be seen.  Now, I'm doing this for my own use, because I can't install windows 7 otherwise.  Disclaimers:

1: I do not have a CD/DVD drive, nor will I, because I have a Fujitsu tablet with a modular bay drive, incompatible with almost all DVD drives, and I'm not spending $100 on a new one.2: I do not have a boot to USB option.  Yes, I've checked my bios.  No, the option is not there.  Unless you want to reprogram my bios, teach me how, or point me to a link that teaches one to enable USB booting in BIOS, then no, this will not work.  For the sake of the challenge of learning to boot any kind of CD with grub, I won't look into enabling USB boot via grub (Though this is my backup plan for this specific subject).

3: I CAN do a XP -> Vista -> W7 install, but I reeeaaally don't want to do that.


What I am trying to do right now is to use the GRUB boot loader to begin the bootup sequence for the Windows 7 installation disk, of which I have made an iso file and transferred to the laptop which I am using now.
.
As it stands right now, I have my HD partitioned as such:
|----- Ubuntu -----|----- Swap ----|---- Fat32 with iso files dumped in ----|----------------------------- Empty space ------------------------------|


I'm using Ubuntu 9.10, and downgraded grub to .97 because it's just easier to use in all ways.  Unless you tell me that Grub2 is better for this purpose.


I used the following command to write the files to the fat32 partition AFTER it was formatted as fat32.```
dd if=/home/vxxed/Downloads/windows 7/win7.iso of=/dev/sda3
```

Currently, GRUB is configured as such:
```
title        Windows 7 Install Disk
rootnoverify    (hd0,2)
chainloader     +1
```Grub gives me error 11 when I try to run this.  Other results and changes were to do root rather than rootnoverify (I'm really just not sure what the two commands actually do, so I tried it anyway) and I got error 11 as well.



Do I need to format the partition with the dumped files as an NTFS partition?
Do I need Grub2dos to run this properly? If so, how in the world do I install it?  I tried looking, but don't understand.

Is there a specific file that needs to be initialized to begin booting of the installation DVD?

---

