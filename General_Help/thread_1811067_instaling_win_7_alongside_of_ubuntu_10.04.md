---
title: "instaling win 7 alongside of ubuntu 10.04"
date: 2011-07-24
forum: General Help
---

### Post by gray72 on 2011-07-24
Hello, I'm new to ubuntu and I want to install windows 7 to my laptop by a installation disk. I have ubuntu 10.04 already installed on my laptop and i just want to install windows 7 as well. I already burn the iso file of windows 7 to a dvd+r but it won't install. So what are the steps I need to take to execute this properly.

Thank You

---

### Post by sanderd17 on 2011-07-24
> **gray72 said:**
>  I already burn the iso file of windows 7 to a dvd+r but it won't install. 

You need to elaborate this. What do you mean? At what point do you get stuck?

---

### Post by tommpogg on 2011-07-24
Yes, we need to know where you get stuck.

Anyway take a look [here]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu"). It might help you

---

### Post by sudosteve on 2011-07-24
Hello gray72 , 
If you burned your Windows as Data-disc option , no boot will occur . Please , choose in your burn software burn bootable CD/DVD .

One more thing is , you ought to prepare some Disk space (I am not sure whether Windows is able to locate other then FAT and NTFS filesystems.). To be clear , boot your Linux system , reserve and format disk partition to install Windows later.

All the best ,
sudosteve
:)

---

### Post by gray72 on 2011-07-24
thank you for the replies. Once I download windows 7 and burn it to a disk and install the disk, the installation does not occur. Is there something I need to do to the system before I insert the disk?

---

### Post by tommpogg on 2011-07-25
Is your BIOS configured to boot form CD? It should be by default. Anyway you can change the the boot sequence at start-up.

As sudosteve pointed out, burn a bootable CD/DVD.

---

### Post by decrepit on 2011-07-25
Just incase you didn't understand. 
The CD has to be in the machine before you boot, and the machine has to boot from the CD.
So what's happening?
Is the machine booting, if so to which OS Ubuntu or the CD?

The guys need to know the details, "it doesn't happen" tells them nothing.

---

### Post by Mark Phelps on 2011-07-25
If your drive is partitioned strictly for Linux, Win7 isn't going to be able to understand the formatting.  It's likely to only offer you the option to reformat the ENTIRE drive -- which is not what you want.

You need to boot into an Ubuntu LiveCD and shrink the Linux partitions to create empty space -- and then, let the Win7 installer format that space as needed.

---

