---
title: "Grub2 not detecting Windows Recovery Partition"
date: 2011-01-05
forum: General Help
---

### Post by usopenplayer on 2011-01-05
Hello!
  I have a dual boot setup with Windows 7 and Ubuntu. Lately Windows 7 has been causing me all kinds of grief and I decided that it would be better to just restore it back to factory settings. I have a Windows 7 recovery partition (hidden) that I can see from Ubuntu, however Grub2 does not detect it. It only has two identical Windows entries that take me into Windows (though in /boot/grub/grub.cfg they point to hd0,msdos1 and hd0,msdos2 respectively).

I have searched far and wide on the Internet on how to gain access to this recovery partition to no avail. I even found a link from Lenovo's website that details how to do this in the old version of Grub, though it doesn't work in Grub2.


Here are the most useful links that I have found thus far, both fall short unfortunately.
[http://www-307.ibm.com/pc/support/site.wss/MIGR-46088.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-46088.html)
[http://www.thinkwiki.org/wiki/Rescue_and_Recovery](http://www.thinkwiki.org/wiki/Rescue_and_Recovery)

I have already backed up all my data, so I can nuke the whole disk if that's what it takes, but I don't actually have a Windows Recovery CD, only the hidden partition which I can't seem to boot into.

I also saw some posts where people were having trouble disabling the recovery partitions from appearing in the Grub menu, their answers often consisted of people telling them that it's not possible to disable the recovery partition from appearing without hiding the main Windows Install, oh the irony!

---

### Post by anystupidname1 on 2011-01-05
I'm fairly certain, the hide/unhide checkbox in gparted will accomplish the same thing. You should then "update-grub" to get grub to adjust the configuration before rebooting.

Be CAREFUL not to boot back to W7 without rehiding that partition or you could end up with binary hamburger on your hands.

I am also of the opinion that since you own a W7 license (and hopefully have written down the license key), downloading and burning a W7 ISO from anywhere would be... lets just say appropriate. This way you can re-install from that disk now and/or if your hard drive ever dies.

---

### Post by usopenplayer on 2011-01-05
I went into gparted and it appears to already be unhidden! I was under the impression that this partition is hidden by default and automatically... Windows is still working, perhaps I already have a binary hamburger on my hands and that is why Grub can't boot into the recovery mode!

I don't actually have the key, and according to the Internet the key is encrypted in the registry.
I have found a Windows key retrieval tool... not sure exactly how it works but I'm going to give it a shot and report back!

Here is a link to the tool I am going to use:
[http://pcsupport.about.com/od/productkeysactivation/tp/topkeyfinder.htm](http://pcsupport.about.com/od/productkeysactivation/tp/topkeyfinder.htm)

edit: Bad news, apparently none of these key finder programs work, I don't remember receiving a key with my laptop, and I'm out of town so I wont even be able to check the manual for at least 1.5 weeks. This is absolutely ridiculous bull ****, and is exactly why I use Ubuntu for most of my work. I've spent all day jumping through Microsoft's hoops, and at the end of the day I am still stuck with a broken Windows system that I can't fix.

---

### Post by wilee-nilee on 2011-01-05
It may be that you can't use the recovery, you have put ubuntu into a system already set to run a certain way=not with another OS to be there. That recovery even if working may or may not overwrite the whole HD.

Did you make a image of windows, on the dvd's or a external HD.

---

### Post by Mark Phelps on 2011-01-06
Even if GRUB did detect the recovery partition, it would do you no good.  That is most frequently NOT a bootable partition and usually only contains a compressed image used to restore MS Windows.

I have personally been using Magical Jellybean Keyfinder for years -- and it has always worked perfectly.  So, I have no idea why it will not work for you.

As to the key -- any machine you buy with a Windows version preinstalled SHOULD come with a sticker somewhere on the case containing the key that YOU use to reinstall/reactivate Windows.  That is where you look to obtain the key.

Also, recent laptops that come with recovery partitions all use a key combination upon boot to invoke the recovery operation.  You will have to consult the documentation that came with your laptop to find out what it is (typically, it's F10, F11, or F12).

Be warned, though, that recovery in those situations generally means completely reformatting the hard drive -- after all, the intent is to restore it to it's original condition, not to just do a repair reinstall of MS Windows.  So, if the recovery works, you'll most likely lose EVERYTHING from your hard drive.

If that recovery does not work, you can generally contact the laptop supplier and order a set of full-recovery disks from them -- sometimes for free, but more often, for a fee.

---

