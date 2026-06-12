---
title: "Boot Disk and how large is Ubuntu."
date: 2009-08-13
forum: General Help
---

### Post by bod626 on 2009-08-13
Hi,
 
Do I need to have the disk I made to boot the computer? And also when I looked at my HDD space I only had 131.1 GB, it is a 160GB Western Digital Hard Drive...
 
Thanks,
Bod

---

### Post by martinbaselier on 2009-08-13
If you install it, you won't need the cd anymore, unless you mess up your system. 131.1 GB is strange. 160 GB should be around 149 GB. (converted from marketing (1000*1000*1000) to computer(1024*1024*1024) gigabytes) Are you sure it's the complete disk size ?

---

### Post by ajgreeny on 2009-08-13
It depends what you mean by the disk you made.  If you are talkng about the installation CD (or live CD) then the answer is yes, if you haven't yet installed ubuntu, but no if it is already installed on your hard disk.  If you just ran the live CD from the CD drive, but did not install the system, then to install you will need to boot from the CD again, and either choose "install ubuntu" from the first menu that appears, or let it go to the live desktop and double click on the "install" desktop icon.

As to your disk size, are you sure there is not a hidden "restore" partition on it, or something similar.  Also bear in mind that manufacturers' tend to work on GB as being 1000 MB, not 1024, and similarly 1000kb as a mb,  This will make some difference to the reported disk size, but not as much as you are seeing, so I suspect you are looking at a partition and not a whole disk, though this depends on what you are using to look at it, most linux applications will see everything on a disk, unlike windows which will only see windows file systems.

---

### Post by bod626 on 2009-08-13
Hi,
 
Sorry if I was a bit vague, 
The 'Boot Disc' I metioned is the one you use to install Ubuntu initially.
I clicked Install and it completed but when I rebooted, turned it off, and turned it back on again - this time without the disc, something along the lines of "Restart computer or insert Boot Disc and hit a key to continue."
 
I have been looking around and aparently the "160GB" name given to some hard drives is actually just a marketing ploy. It is about 11GB smaller than first stated :mad: ... So I have found out where that has dissappeard to.
 
Thanks, If anybody knows about the Boot Disc then please reply :) .
 
Bod

---

### Post by ajgreeny on 2009-08-13
It sounds as if grub is missing for some reason, or if you have more than one disk, perhaps the wrong one is the boot device in BIOS.

To install grub try this:-
Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.  Just make sure that the correct disk is first in the BIOS boot device list.

---

### Post by jward3010 on 2009-08-13
> **bod626 said:**
> ...something along the lines of "Restart computer or insert Boot Disc and hit a key to continue."

Is that similar to a BIOS error about not finding any boot device, even a boot sector on the HD. Whats your PC set up like, is it a manufactured machine (like from Dell, Compaq, Toshiba, Packard Bell etc.)

---

### Post by jward3010 on 2009-08-13
In relation to how large Ubuntu is or gets, heres a rough idea. What I'm talking about is when Ubuntu is first installed and very little is installed except for updates and basic programs, codecs etc. For me it comes to around 2.3, 2.4GB max.

---

### Post by bod626 on 2009-08-15
Hi,
 
>  
Whats your PC set up like, is it a manufactured machine (like from Dell, Compaq, Toshiba, Packard Bell etc.)

 
No, it was custom built by me. 
 
> It sounds as if grub is missing for some reason
 
I dont know, and it cant even boot into Ubuntu with the installation disc.
 
:( :( After a few hours of tinkering I decided it wasnt really worth the hassle, so (and call me a traitor if you want) I am trying to get the RC version of Windows 7.

---

