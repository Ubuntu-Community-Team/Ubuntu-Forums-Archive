---
title: "making a new ntfs partition when all space allocated"
date: 2010-09-11
forum: General Help
---

### Post by s0cket93 on 2010-09-11
I wanted to make a new partition out of some of my free space and install windows xp in same hard drive as ubuntu without uninstalling anything.If it's possible,how?

---

### Post by Lateralis on 2010-09-11
It is possible, but will be a bit involved. 

If your hard drive is completely formatted for Ubuntu, then the first thing you'll need to do is shrink your Ubuntu parition to make some free, unformatted space.  You will need to do this using a LiveCD.  It could take a little while for the partition editor to move and shrink the parition and **there is always the risk of causing serious damage to data currently on the disk.**  Ensure that all (important) data is backed up properly to external drives and CD/DVD.  

Once space has been created you can go right ahead and install Win XP.  But you should be aware that Windows aggressively installs its own bootloader in the MBR, irrespective of what is there at the minute.  This means that GRUB will be wiped.  When you boot up your PC you will go straight into Win XP.  You can reinstall Grub but you will need to do this from a Live CD.

---

### Post by rory526 on 2010-09-11
Use gparted. Resize a partition and make your new partition in the freed-up space.

Some things to note:
1. You can only alter unmounted partitions, so if you intend to resize your operating system's partition, your will need to burn a gparted live cd and boot from it.

The gparted live cd is available here: [http://sourceforge.net/projects/gparted/files/gparted-live-stable/]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/")

2. There is a chance you can loose data on the partition you are resizing, so back up anything important!

3. If you are resizing a windows partition, defragment it first.

---

### Post by s0cket93 on 2010-09-11
right...thanks for the info.I guess I'll just delete everything,install xp and then ubuntu(or just xp)

---

### Post by rory526 on 2010-09-11
no, you can easily overwrite the MBR after installing XP to get it to boot grub again.

Take a look here:

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

(Ignore the section under the heading "Only read below if Windows is now missing from the boot menu". It wont work for grub2 i think.

Try ```
sudo update-grub
``` instead if XP doesn't show up.
)

---

