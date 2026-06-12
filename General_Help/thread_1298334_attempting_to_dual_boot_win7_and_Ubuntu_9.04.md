---
title: "attempting to dual boot win7 and Ubuntu 9.04"
date: 2009-10-22
forum: General Help
---

### Post by RustyOrbit on 2009-10-22
the begining of the story is, i think, a familiar one here. I had a working install of jaunty and intended to dual boot win 7 home premium. i left myself a big partition to install windows to, i got it today and was to the desktop in about a half hour. My college internet requires an antivirus program to let you on the net (and they oh so graciously offer norton *shudder*) so i decide to boot into ubuntu and download AVG and toss it to my windows partition. I restart the computer and it skips grub entirely and boots straight into 7. 
     so i boot from my live CD, open GPartEd, switch my boot flag from win7 to my linux install, rebot. i get a black screen with white letters that says Operating System Missing. :(

so i boot from my live CD again and ask my friend google about it, he shows me how to reset my grub loader through the terminal (the same instructions are in the Gparted help file)  in the sake of full disclosure i will print them here. 

#

Start the grub application
            from the command line.
$ grub
            Find where grub stage1 is located by using
            one of the following:

            If the /boot folder is stored in the / partition,
            use the command:
grub> find /boot/grub/stage1

           If the /boot folder is stored in a partition
            different than the / partition, use the command:
 grub> find /grub/stage1
            The output from the find command might
            look like the following:
            
 (hd0,0)
            If more than one line is listed in the command output,
            you will need to decide which device you use for grub.
            
            Set the grub root device
            by specifying the device returned
            by the find command.
grub> root (hd0,0)
            Reinstall grub
            by specifying the device returned
            by the find command.
grub> setup (hd0,0)
           Exit grub
grub> quit
            Reboot your computer.


The find step returned 2 addresses, one on my primary HD (where both working installs are) and one on my old one with an old linux and a broken XP (nither of which are imprtant now) so i proceeded with the process and it seemed to work.

i rebooted and grub appeared, but windows 7 was nowhere to be seen. booted into my linux install, reflagged windows as a boot partition reboot and still no windows 7. 

in GPartEd my windows partition(and its system partition) have an exclamation mark that says that it is unable to read the contents of the partition, and because of that some operations may not be available.  but i can still mount, read, and write to that partition in the standard gui file browser.

I decided that i would try the Grub reset again, but now both find commands return Error 15: file not found. also 'fix it please' is an unrecognized command, so i turn to you the experts.  as of now I can boot to my install of linux through grub, but i cannot boot into windows.  any help would be greatly appreciated.

---

### Post by jrrader on 2009-10-22
I had a really bad experience installing Windows 7 on my computer about 2 months ago and then getting Ubuntu to work again.   I ended up reinstalling Ubuntu.  Didn't lose any data because I keep my directories in different partitions.  I don't even use Windows 7, but I want to have it on my resume. 

The scary looking triangle in Gparted is nothing to worry about.  Did you already edit /boot/grub/menu.lst? 

```
$sudo gedit /boot/grub/menu.lst
```It should have an entry like this after other operating systems:

```
title        Windows 7 Professional
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1

```

Add that if it doesn't, but change rootnoverify to the proper location (if your windows partition is sda3, then you would want hd0,2 like I have).  Save and reboot your computer.

---

### Post by lovinglinux on 2009-10-22
As mentioned in the previous post, you need to manually add the Windows entry to /boot/grub/menu.lst after restoring the grub.

---

### Post by lrcaballero on 2009-10-22
To help you understand!!! This is what happened, MS Windows is NOT friendly at ALL ans so it took over your HDD(I'm not surprised) is MS Windows....... you should've first installed Windows and then Linux, Linux is very FRIENDLY(ofcourse!!!!!) That is why I did the whole switch to Linux 100%, and I am very HAPPY.

Good Luck!!!


Luis,

:KS

---

### Post by jrrader on 2009-10-22
> **lrcaballero said:**
> To help you understand!!! This is what happened, MS Windows is NOT friendly at ALL ans so it took over your HDD(I'm not surprised) is MS Windows....... you should've first installed Windows and then Linux, Linux is very FRIENDLY(ofcourse!!!!!) That is why I did the whole switch to Linux 100%, and I am very HAPPY.


Sounds silly but that is exactly what it feels like when you add a new partition for windows and windows decides to write over your master boot record without asking.  Apple made it easier to add Windows and Linux with Boot Camp and MS is just like "You don't need that garbage, you've got us.

BTW RustyOrbit - I'm glad you brought up AVG free because when I installed Windows 7 they only had non-free versions for it.  I see now they have one and thats a good thing.

---

### Post by RustyOrbit on 2009-10-22
Thank you very much, the issue is resolved, adding the entry into the main.lst file worked perfectly, and also allowed me to delete some old kernels that were clutering my grub page. one again thank you. :KS

---

