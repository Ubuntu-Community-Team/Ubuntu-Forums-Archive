---
title: "Help! I think I borked my girlfriend's laptop..."
date: 2012-04-30
forum: General Help
---

### Post by Condor Cluster on 2012-04-30
I used an Ubuntu 12.04 live USB stick to boot into my GFs Dell Laptop, in order to extend the hard drive partitions.

It had one partition as Vista OS (100Gb), and one image partition at 10Gb.  I used Gparted to extend the main partition over the image one, giving a main single Vista partition of 110Gb.

Thing is now when I boot up the Dell, and set the boot order to HDD first, it just constantly reboots the machine (can't see Vista?)

Any ideas???

Thanks (hopes my GF doesn't use these forums...)

---

### Post by Cheesemill on 2012-04-30
Try booting from a Vista recovery/installation disk. This may be able to repair your boot problems.

---

### Post by uylug on 2012-04-30
Hahaha. I've never ****** up my GF's notebook. I would otherwise be dead. She actually liked Ubuntu o.O

Anyways, back on topic, did you wipe the Windows Recovery Partition...? Just guessing, you might have changed the partition table and now the bootloader is broken.

You need a Windows disc to fix the MBR for you.

---

### Post by Condor Cluster on 2012-04-30
Managed to 'aquire' a Vista disk to try the repair method.

How would I go about 'burning' the Vista iso to the USB to form a bootable Vista USB key? 

Brascero only writes isos to CD/DVDs, and I'm on a netbook :(

Thanks.

---

### Post by Cheesemill on 2012-04-30
[http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html](http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html)

---

### Post by adduds on 2012-04-30
I'm just here to post that I love the fact you used to word "borked" lmao awsome bud :)

---

### Post by Mark Phelps on 2012-04-30
> **Condor Cluster said:**
> I used an Ubuntu 12.04 live USB stick to boot into my GFs Dell Laptop, in order to extend the hard drive partitions.

It had one partition as Vista OS (100Gb), and one image partition at 10Gb.  I used Gparted to extend the main partition over the image one, giving a main single Vista partition of 110Gb.



You could have accomplished what you wanted in Vista by simply using the Disk Management utility -- and NOT have messed up the Vista booting in the process.

I've tried to tell folks here numerous times to NOT use GParted to mess with Vista and Win7 OS partitions because, when you do, stuff like what happened to you is a likely result.

IF you can write the Boot-Repair stuff to USB, you may be able to boot with that and repair the Vista boot:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by Condor Cluster on 2012-05-01
Yay, managed to fix it! :D

I used the Live Ubuntu 12.04 on one USB, then an imaged called Vista Recovery CD.iso on another USB stick.

Then booted into Live Ubuntu on the Dell, put in a blank CDRW, and clicked 'write to disc' on the iso. Once completed, I booted from the burnt CD, which performed a CHKDSK, and voila, working again!

Thanks everyone for the help, turns out Live Ubuntu is a REALLY useful tool!

---

