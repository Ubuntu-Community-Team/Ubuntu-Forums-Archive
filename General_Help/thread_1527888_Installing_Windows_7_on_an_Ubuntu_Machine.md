---
title: "Installing Windows 7 on an Ubuntu Machine"
date: 2010-07-09
forum: General Help
---

### Post by Trilby on 2010-07-09
I have an Acer laptop, on which a I have Ubuntu installed with no disk partitioning. I may need to install Windows 7 on this machine but have no desire to stop using Ubuntu for normal use. Is it possible to create a partition to install Windows on, without changing my Ubuntu set up? Also, whilst I'm at it, I'd like to create a third partition for general data storage.

Thank-you for any help given,
Trilby

---

### Post by staf0048 on 2010-07-09
From my understanding of the way Windows works, when you go to install it it will do what it wants with your drive.  So, you'll probably have to install Win7, then re-install Ubuntu and set up your partitions the way you want.  I beleive Windows has a partition editor as well, so you could do that part from windows, but I'm not familiar with it.

---

### Post by Muscovy on 2010-07-09
Windows is really erratic about respecting other partitions. You may be able to select where to install, but please, BACK EVERYTHING UP FIRST. ;)

If it doesn't wipe your drive, you'll need to reinstall the grub bootloader. For that you'll need to chroot from a live CD, and run grub-install and update-grub. Here's a guide: [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by QIII on 2010-07-09
If your machine has multiple cores and enough memory, you could consider virtualizing Windows using VirtualBox (the PUEL version!) or VMWare.

There would be no shutting down and rebooting.  You could start Windows when you want and shut down the virtual machine when you are done.

The only drawback to that solution is that you are stuck with whatever virtual hardware is provided by the virtualization software.  That generally means no 3D graphics acceleration.

---

### Post by Cpierce on 2010-07-09
You might want to run win7 in virtualbox instead of putting it directly on your hard drive. Just a thought.

---

### Post by Trilby on 2010-07-10
> **QIII said:**
> If your machine has multiple cores and enough memory, you could consider virtualizing Windows using VirtualBox (the PUEL version!) or VMWare.

...

The only drawback to that solution is that you are stuck with whatever virtual hardware is provided by the virtualization software.  That generally means no 3D graphics acceleration.

I have a dual core processor and 4 GB of ram.
I have been considering using a virtual machine sine my initial post.
Would the virtual computer function as a normal windows machine when in use?
Would be able to use it for gaming (things like the Half-Life games, Deux Ex & GalCiv2)?

Thanks

---

### Post by Seeked on 2010-07-10
You will probably not have the performance for gaming if you run it in a virtual machine.

---

### Post by DanPaulCiocan on 2010-07-10
> **Trilby said:**
> I have an Acer laptop, on which a I have Ubuntu installed with no disk partitioning. I may need to install Windows 7 on this machine but have no desire to stop using Ubuntu for normal use. Is it possible to create a partition to install Windows on, without changing my Ubuntu set up? Also, whilst I'm at it, I'd like to create a third partition for general data storage.

Thank-you for any help given,
Trilby
You need an Ubuntu Live CD, first boot on it and run "sudo gparted". Create your partitions... Than, install your Windows 7 on the partition you want. After Windows 7 is installed, you will have to install Grub2 again, look here: [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by Trilby on 2010-07-10
> **DanPaulCiocan said:**
>  run "sudo gparted".

The last time time I tried to change my partitions using a live disk, I ended up screwing my computer over so badly that I had to wipe the hard-drive and clean install Ubuntu. :redface: That's also why I don't have Windows installed at the moment. I'm a little reluctant to mess thing up again. Are there any "for* extreme* dummies" guides for using it?

EDIT: Ps, is NTFS the correct format for a Windows partition?

---

### Post by ST3ALTHPSYCH0 on 2010-07-10
Alright.... There is some serious risk of data loss, so do an external backup (or a Clonezilla image). Last I knew Windows preferred the 1st partition on a disk. You'll have to run GParted from a Live CD, and I would apply each step individually, as I have had this kind of operation fail if you try to apply it all at the end.

1. The technical command is "gksudo gparted". "Sudo" is for CLI applications and "gksudo" for GUI applications (in a Gnome environment).

2. You'll need to shrink your Ubuntu partition to your desired size. (apply)
3. Make sure your swap partition is at the end of the disk (to the far right of the disk )(apply)
4. Create your data partition immediately to the left of your swap, make sure that it's NTFS so that Windows can read it. (apply)
5. Move your Ubuntu partition to immediately left of your data partition (this step carries the highest risk of data loss)(apply)
6. Create your Windows partition at the beginning of the drive. Format it as NTFS and make sure that the "round to cylinders" box is **unchecked**.(apply)
7. Install Windows 7, make sure that you choose the partition you created when installing Windows instead of it taking the whole disk.
8. You'll need to boot with the Live CD and reinstall GRUB. [Here's](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7) a guide. Remember to check the partition names, and not just use the generic ones from the example.

I haven't ever installed Windows AFTER Ubuntu, but I have moved Windows partitions around, and resized with Gparted, and they still booted. Anytime your play with partition structure after data is on the disk, though, you risk data loss (although GParted blows Disk Druid out of the water!!)

---

### Post by Trilby on 2010-07-10
Thanks ST3ALTHPSYCH0. :D
This seems fairly straight forward, just one question:

> **ST3ALTHPSYCH0 said:**
> 
3. Make sure your swap partition is at the end of the disk (to the far right of the disk )(apply)


What exactly is swap space? I came across it before in aforementioned computer wrecking incident but didn't know what it was.

---

### Post by ST3ALTHPSYCH0 on 2010-07-10
A Linux swap partition is equivalent to a Windows page file. It's the HDD space that the OS uses for virtual memory. If you have 1 Gb or less RAM, most people recommend creating a swap space of 2x your RAM, above that =to your RAM. If you have 2+ Gb RAM it's really only necessary if you ever want to hibernate your machine. There are differing schools of thought on this... This is the guide I go by (I.E. I have a 6 Gb Swap space... that's rarely touched)

---

### Post by Trilby on 2010-07-10
> **ST3ALTHPSYCH0 said:**
> If you have 1 Gb or less RAM, most people recommend creating a swap space of 2x your RAM, above that =to your RAM. If you have 2+ Gb RAM it's really only necessary if you ever want to hibernate your machine. 

Thanks again, you've been very helpful.
I have 4GB of RAM. I'll leave the swap space as whatever size it is by default. Since I don't have any problems with it at the moment, I assume it's fine.

---

### Post by Trilby on 2010-07-16
I am now dual booting Windows 7 and Ubuntu, having finally plucked up the courage to start messing with my computer again. The only problem I had is that it took me several attempts to create the Windows partition. I succeeded only when I put 100 MB of unused space before it. I'm not sure why I had to do this, but it worked.
I restored grub by following the instruction found here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Note that if anyone else follows those instructions and runs into problems, some help may be found here: [http://ubuntuforums.org/showthread.php?t=1532645](http://ubuntuforums.org/showthread.php?t=1532645)

I'd like to thank you all for your help, especially ST3ALTHPSYCH0. I doubt I would have been able to this without having to overwrite Ubuntu and re-install it afterwards without your directions. :D

Thanks,
Trilby

---

### Post by ST3ALTHPSYCH0 on 2010-07-17
I just saw this thread was closed. It's honestly my pleasure to help folks (dunno how you believe, but, in my eyes, helping is one of my spiritual gifts), otherwise I wouldn't do my job for free after hours!!

---

