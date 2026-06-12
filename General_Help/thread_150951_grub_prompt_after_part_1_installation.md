---
title: "grub prompt after part 1 installation"
date: 2006-03-27
forum: General Help
---

### Post by person4 on 2006-03-27
Hi,

I'm installing Ubuntu 5.1 on a home PC. I'm completely overwriting a hard drive that used to contain Windows 98. When I finish the first half of the installation and reboot, instead of continuing to install, I get a grub> prompt. I've installed Ubuntu on other computers and this has never happened. Does anyone have any advice?

Thanks!

---

### Post by JoshHendo on 2006-03-27
Don't you have to go through GRUB to get to the installation part? When you boot off the CD, it copies all the files, installs GRUB and everything you need to boot the actuall installing part of Ubuntu off the HDD. Then it will reboot off the HDD, and GRUB should send you to Ubuntu.

What do you mean bt GRUB prompt exactly though?

---

### Post by person4 on 2006-03-27
Right. All the installation files are copied, the disk is formatted and grub is installed. Then when I restart and boot off of the hard disk, instead of grub starting Ubuntu, I get a black screen with the text "Grub version 0.92" at the top and a command prompt that looks like:

grub>

---

### Post by Herman on 2006-03-27
You mean something like the one illustrated in fig.2 [in this link]("http://users.bigpond.net.au/hermanzone/p15.htm")?

---

### Post by person4 on 2006-03-27
Yes, that's exactly it. I tried a few things mentioned on that page but with no luck. I tried "find /vmlinuz" but I get a "File not found" error. Interestingly, the command root (hd0,0) returns with "Filesystem type is ext2fs, partition type 0x83." If I then give the command "kernel /vmlinuz root=/dev/hda2" I get the error "Error 18: Selected cylinder exceeds maximum supported by BIOS"

---

### Post by Herman on 2006-03-27
Is this the only hard disk in this machine? 
Did you just do a stock-standard single operating system install with the regular ext3 filesystem? 
You did a good job trying those commands, but maybe try the following just to see what happens: (I modified them a bit to suit what I think your set-up should require).
```
grub> root (hd0,0)
``` ```
grub> kernel /vmlinuz root=/dev/hda1
``` ```
grub> initrd /boot/initrd.img-2.6.12-9-386
``` ```
grub> boot
``` (I modified them a bit to suit what I think your set-up should require).
Note: it would be best not to type the entire third command but to type it up to the last part where it has 'initrd.img-2.6' etc. Just type the first few letters and then press your Tab key.
I hope this helps, :D (Herman)

---

### Post by person4 on 2006-03-27
In fact, I do have a slave hard drive on the system. It doesn't have an operating system on it, just some stored files. It has a single FAT partition from the old operating system. I am doing the basic installation, and choosing to overwrite all of the master hard drive.

I tried the commands you suggested. The first line returns the result: "File system type is ext2fs, partition type 0x83." When I try the second line, I can use tab to autocomplete up to "kernel /vmlinuz". If I then append "root=/dev/" and hit tab again, I get "Error 18: selected cylinder exceeds maximum supported by BIOS". I get the same error if I manually fill in the rest of the line and hit enter. When I try to autofill the "initrd" line I get the same error.

---

### Post by Herman on 2006-03-27
Okay, it's beggining to seem as if it might not a be grub problem, but possibly some problem with the way the hard disk is set up in your BIOS maybe.
Have you checked your BIOS settings? Here are two of my best links about BIOS settings just in case you might find them helpful:
[http://webpages.charter.net/netw_1/bios.htm]("http://webpages.charter.net/netw_1/bios.htm")
[http://www.adriansrojakpot.com/Speed_Demonz/BIOS_Guide/BIOS_Guide_Index.htm]("http://www.adriansrojakpot.com/Speed_Demonz/BIOS_Guide/BIOS_Guide_Index.htm")
In 'Standard CMOS features' in my award BIOS, I can enter the settings for my hard disk and choose the access mode: Normal, LBA, Large or Auto. I always leave mine on 'auto'. I have no way of knowing what others should do for their various systems, but that's where I'd be looking around first. I think at least LBA or Large would be better than 'normal'. It would be surprising that you would be able to install without the hard disk being properly set up in the BIOS though, unless the BIOS was changed somehow afterwards (Unlikely). ?
There also can be, (if it's an old computer) jumper settings that can limit the size of the hard disk that the BIOS can 'see'. Sometimes people remove the hard-disk from an older computer and install it in a newer one and forget to remove the jumpers. (But it would have to be an extreme example of that kind of situation not to be able to find your kernel on a single-partition install, so I don't think that's the problem.)
There may be special programs installed in the first track of the disk to enable an older BIOS to use a larger hard disk too, such as '[disk manager]("http://www.samsung.com/Products/HardDiskDrive/utilities/")' that might need to be considered too. 
How old is the computer and what kind of hard disk is it?

---

### Post by person4 on 2006-03-28
The hard drive is a Western Digital 60GB. I was able to use the entire disk when Windows was installed, and I have not changed anything since then, so I doubt that it's the jumper settings.

---

### Post by person4 on 2006-03-28
I forgot to mention, the computer is a Dell Dimension from 2000. The system setup has very few options, none of which seem to pertain to disk size.

---

