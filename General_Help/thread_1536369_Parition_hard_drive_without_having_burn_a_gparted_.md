---
title: "Parition hard drive without having burn a gparted live cd"
date: 2010-07-22
forum: General Help
---

### Post by Dustin2128 on 2010-07-22
I decided I'm going to go back to a dual boot to see if I can get some of the slackware issues resolved on my laptop; its ubuntu only at the moment due to wireless problems. I've only got one hard drive so I can't simply unmount and repartition from gparted, I've lost all of my random linux live cds, and can't find a spare blank optical disc. Is there a way to boot from directly from the iso or from a flash drive or something?

---

### Post by Nerflander on 2010-07-22
I dont know if it might help but eehm.. You can boot ubuntu 6.10 from a usb stick. You might be able to partition there from usb. There might be a slight problem caus you have to install linux 6.10 first but if you would virtualize it you can from there on put it on usb....

Might help! hope it does:)

---

### Post by Fir3chi3f on 2010-07-22
In Ubuntu, System->Administration->Startup Disk Creator 

Select your iso and flash drive and you should be good to go. This works with 10.04 I believe.

---

### Post by aeiah on 2010-07-22
[http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)

---

### Post by Mark Phelps on 2010-07-22
> **Dustin2128 said:**
>  Is there a way to boot from directly from the iso or from a flash drive or something?

Yes ... from the Gparted Live ISO.  Go to the GParted web site and look through the FAQs about installing it to the hard drive.  They have some code you can use to modify the 40_custom file under /etc/grub.d to add an entry for Gparted that uses the ISO file.

Download the appropriate ISO file from their website and move it to the folder indicated in the 40_custom code.

Once you run "sudo update-grub" and reboot, you'll have a menu entry for GParted and you can boot directly into that.

I know that works because I recently added it to my own machine.

---

### Post by C.S.Cameron on 2010-07-22
MultiBootUSB will boot your gparted iso from USB.

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by Dustin2128 on 2010-07-22
thanks! I didn't know you could burn iso's to flash drives, that's going to save me many blank CDs.

---

