---
title: "creating a partition from none to dual boot"
date: 2010-05-25
forum: General Help
---

### Post by drumkitcat on 2010-05-25
Hi,

Can someone tell me if this can really be done:

Currently, I'm running UbuntuStudio 9.10 on my Toshiba Satellite A40 Laptop... it's perfect and I love it... but, I installed it cleanly doing a reformat of the drive, and with no partition - so using as much of the newly replaced 80gb drive as possible.

Now, if I want to create a partition to install WinXP as a dual boot, 1) can this be done?  2) what do I use to do it?

thanks
Paul

---

### Post by warfacegod on 2010-05-25
```
sudo apt-get install gparted
```

For the resizing and formatting.

```
sudo apt-get install ntfsprogs
```

To give gparted the ability to use Windows filesystems. I suggest you go with NTFS for XP.

Here's a link for when XP breaks GRUB (it will) and you can't get into Ubuntu: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

Section #13 I believe. You'll need to run:

```
sudo update-grub
```

Once you are back in Ubuntu.

---

### Post by skarme on 2010-05-25
You can't create a partition without formatting your drive i.e you'll have to erase the current OS on the drive; partition it and then install the desired Operating systems as dual boot. You may use your win Xp CD to partition.

---

### Post by warfacegod on 2010-05-25
> **skarme said:**
> You can't create a partition without formatting your drive i.e you'll have to erase the current OS on the drive; partition it and then install the desired Operating systems as dual boot. You may use your win Xp CD to partition.

Sure you can. Boot into LiveCD or USB (I forgot that you can't resize your OS partition when your in the OS).

Select "Try Ubuntu without making changes.."

System> Admin.> Gparted

Make sure the drive is unmounted then right click it and select resize.

No uninstalling OS's necessary.

---

### Post by Rubi1200 on 2010-05-25
Most important of all, **backup **all your important data **before **attempting to create/move/resize partitions. GParted is a fantastic tool, but as with any partitioning software things could go wrong.

It is usually advisable to install Windows before Ubuntu rather than the other way around because of the way Windows writes to the MBR.

Also, read this:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Good luck!

---

### Post by drumkitcat on 2010-05-25
> **warfacegod said:**
> Sure you can. Boot into LiveCD or USB (I forgot that you can't resize your OS partition when your in the OS).

Select "Try Ubuntu without making changes.."

System> Admin.> Gparted

Make sure the drive is unmounted then right click it and select resize.

No uninstalling OS's necessary.


- how do I make sure the drive is unmounted?  (or how do I tell if it is?)

---

### Post by drumkitcat on 2010-05-25
> **Rubi1200 said:**
> Most important of all, **backup **all your important data **before **attempting to create/move/resize partitions. GParted is a fantastic tool, but as with any partitioning software things could go wrong.

It is usually advisable to install Windows before Ubuntu rather than the other way around because of the way Windows writes to the MBR.

Also, read this:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Good luck!

Thanks for the link - also very useful info!

---

### Post by Rubi1200 on 2010-05-25
> **drumkitcat said:**
> - how do I make sure the drive is unmounted?  (or how do I tell if it is?)

Right-click on the partition and select Unmount.

GParted will refresh and then follow the instructions just posted by warfacegod.

You will probably have to do the same for the Swap partition (assuming you created one originally).

---

### Post by warfacegod on 2010-05-25
> **drumkitcat said:**
> - how do I make sure the drive is unmounted?  (or how do I tell if it is?)

Right click it in Gparted and select "Unmount".

Rubi200 is absolutely correct about the backup. I should have mentioned that in my first post.

---

### Post by drumkitcat on 2010-05-25
This is great, and very helpful!

Thanks for the speedy replies and fantastic information everyone!

Normally I wouldn't bother with having to do this but because of a couple of applications that simply must use Windoze, I have to set this up.

Really appreciate everyone's insight and help!

Paul

---

### Post by kansasnoob on 2010-05-25
This is a nice simple guide:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

**[COLOR="Red"]But if you have grub 2 the instructions for recovering grub are wrong![/COLOR]**

You can see what version of grub you have by running:

```
grub-install -v
```

Basically "0.9*" = legacy grub, and "1.9*" = grub 2.

This is a good guide for restoring bootloaders:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Of course you must use a Live CD with the proper grub installed to do it that way, so I've been working on a HowTo "restore any Linux or Windows MBR with any Ubuntu Live CD":

[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by Elfy on 2010-05-25
Depending on what it is you need to do and with what it might be possible to just use a virtual machine and install windows in that. IF it was possible that would be my preferred option.

---

### Post by drumkitcat on 2010-05-25
> **kansasnoob said:**
> This is a nice simple guide:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

**[COLOR="Red"]But if you have grub 2 the instructions for recovering grub are wrong![/COLOR]**

You can see what version of grub you have by running:

```
grub-install -v
```

Basically "0.9*" = legacy grub, and "1.9*" = grub 2.

This is a good guide for restoring bootloaders:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Of course you must use a Live CD with the proper grub installed to do it that way, so I've been working on a HowTo "restore any Linux or Windows MBR with any Ubuntu Live CD":

[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

Thanks, I think that will be very helpful too!

---

