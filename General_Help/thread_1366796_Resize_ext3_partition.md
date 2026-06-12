---
title: "Resize ext3 partition"
date: 2009-12-28
forum: General Help
---

### Post by bhilgenkamp on 2009-12-28
Hello,

I know there are multiple posts out there for resizing an ext3 partition, but frankly I need a "Complete Idiot's Guide" type of thing since I'm quite the novice to this area. 

I currently have 2 partitions on my computer - the first partition is NTFS for Windows, the second is ext3 for Ubuntu. I have tried booting from my USB drive to use gparted but it does not allow me to resize the partition. How can I do this? Do I need to make changes to GRUB to allow me to still be able to boot? Thanks everyone, and please bare with my noviceness.

---

### Post by drs305 on 2009-12-28
I wrote a guide on how to resize the Ubuntu partition by taking space from Windows. 

Here is the link. If you have questions, just post them here. Hopefully it is not too complicated, but if something isn't clear don't be afraid to ask.

[ Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by susanw on 2009-12-28
Hello,


Firstly backup all personal data, repartitioning can screw things up.

To resize partitions the easiest way I have found is by using a liveCD or usb stick 

If you don't have one download the diskiso from the links from the main ubuntu website, alternate ones often work best. Then burn onto a CD ticking make bootable if there is an option to do so. Alternatively make a startup usb stick (just like a live CD) using options from the menu on your ubuntu desktop. Startup USB stick are my preferred approach.

Bootup your PC from the livcd/usb and run GParted. It should allow you to resize any partitions. You may need to right click any drives and click unmount or swapoff.

If the windows partition isn't budging load up windows and defrag several times using windows software.

Hope this helps a bit. Feel free to ask any questions, I'm quite new myself so knowledge is limited,

Susan

---

### Post by Robster2 on 2009-12-28
It is better to shrink the windows partition from within windows.  You can shrink the partition more and faster than Gparted.

[http://www.youtube.com/user/CoverlessTech#p/a/E8F1691C3779BDC3/2/cXZKRyvSqwQ](http://www.youtube.com/user/CoverlessTech#p/a/E8F1691C3779BDC3/2/cXZKRyvSqwQ)

Start the Video at 4.55 minute mark (The first part is about how to burn a Download and burn a Kubuntu ISO) 

When you have shrunk your windows partition stop there.

Use Gparted to increase the size of your Ubuntu partition to fill the gap.

Gparted is on the Live CD as well (but does not install with Ubuntu)

Good luck.

---

### Post by Robster2 on 2009-12-28
You should not need to touch the Grub.

---

