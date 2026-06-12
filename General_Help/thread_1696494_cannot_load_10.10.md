---
title: "cannot load 10.10"
date: 2011-02-27
forum: General Help
---

### Post by trevboy on 2011-02-27
can somebody help, i am trying to load ubuntu 10.10 but the installer keeps failing saying the disk is dirty or damaged or the optical reader is dirty. i have two disks both from different sources i.e. magazines i have tried two hdd and the cd reader is ok as i have just loaded xp with it,the pc has two hdd so ubuntu will have the whole drive.The motherboard has on board graphics i wonder if this could be the problem.both disks stop at exactly the same place.

---

### Post by patrick_the_fat on 2011-02-27
Do you have a USB thumb drive? As long as your computer supports booting from USB, you can install Unetbootin and boot the CD directly from USB.

Also, if the disc was downloaded, you need to make sure that the CD was downloaded correctly.  You can search for a utility called md5sum.exe, which will give you a "hash", or number generated randomly by the contents of your download.  If the hash does not match the md5 sum provided online, then you know that the download did not complete properly.

If your computer does not support booting from USB, I recommend you download PLOP Boot Manager, burn to disc and install it.  This will allow your computer to boot from USB by giving you a custom boot menu, which you can set to load .iso files as if you inserted a disc and restarted.

If you have problems with Unetbootin, there are other tools, which allow you to boot the cd images from the USB disc with a direct copy.  These tools:

[http://www.linuxpromagazine.com/Online/Blogs/Productivity-Sauce/Create-a-Multi-boot-USB-Stick-with-MultiSystem](http://www.linuxpromagazine.com/Online/Blogs/Productivity-Sauce/Create-a-Multi-boot-USB-Stick-with-MultiSystem)

and

[http://gna.org/projects/grub4dos/](http://gna.org/projects/grub4dos/)

Keep in mind, if you are copying a CD image (.iso file) to your thumb drive for boot, you need to do a clean format of the disc, and run a single-file defragmenter, such as Contig ([http://technet.microsoft.com/en-us/sysinternals/bb897428](http://technet.microsoft.com/en-us/sysinternals/bb897428)) so that the file is stored on your thumb drive as one continuous file.

Make the switch, it's never too late!!

---

### Post by trevboy on 2011-02-27
i may not have explained myself clearly the cd is a commercial one and it will not copy to the hdd

---

### Post by trevboy on 2011-02-28
problem solved both the hdd that i used had been used for xp professional it seems 10.10 cannot overwrite this i used d.ban disc to clean the hdd 10.10 installed first time

---

