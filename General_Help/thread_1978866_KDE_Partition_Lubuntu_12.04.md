---
title: "KDE Partition Lubuntu 12.04"
date: 2012-05-12
forum: General Help
---

### Post by davidafranklin on 2012-05-12
Hello, I have installed Lubuntu 12.04 on my entire drive in ext4.

I want to resize the drive and create a new partition in NTFS where I can install  Windows Vista in Dual boot. Gpart does not work as I am not in gGnome but Kde.

I have tried to run a livecd of Lubuntu 10.10 and downloaded Kde partition manager and tried to resize but it did not work.

Any other suggestion?

Thanks

---

### Post by davidafranklin on 2012-05-15
Any Suggestion?

---

### Post by squilookle on 2012-05-15
A couple of things I'm not clear on from your post. 

You say GPart does not work... is it not running at all or is it failing during use? Have you any further information on what the failure is, error messages or a description of what happens, etc? 

I'm assuming you have installed KDE on your Lubuntu installation but I don't see any reason why this would prevent the software from working. You can use Gnome/GTK software in KDE and I do this myself from time to time. I'm also not clear why you are trying to install the KDE partition manager on a Lubuntu LiveCD, as this certainly won't have KDE installed on it... could it be that you are confused over the DE/flavour you are running?

I always use PartedMagic for this kind of stuff. It's a live CD geared towards partitioning and managing drives and I tend to find it works with no fuss. Might be worth a try.

---

### Post by forrestcupp on 2012-05-15
Is GParted not even opening at all, or does it just not work, even though it is open? GParted will not work on partitions that are mounted, so you'd have to do it from your LiveCD. But if you can't get that to work, try out the [GParted Live CD/USB](http://gparted.sourceforge.net/livecd.php). That should pretty much be guaranteed to work for you. Just be careful and back up your important files first.

---

### Post by davidafranklin on 2012-05-15
Gpart runs for a few mn and at the end I get an error message I did some reserchad and I found out that Gpart only works with Gnome/Unity. 

I guess I am confused. 

All I want to do is install, Windows Vista in Dual boot along with my existing Lubuntu 12.04 knowing that my entire rive is in Ext4. I understand that when I will partition my drive in NTFS (If I am able to do it) I have to put the NTFS empty partiton at the beginning which will then mess up my linux  boot.

So you recommendation is to use PartedMagic  to do this, right?

Many thanks

---

### Post by davidafranklin on 2012-05-15
> **forrestcupp said:**
> Is GParted not even opening at all, or does it just not work, even though it is open? GParted will not work on partitions that are mounted, so you'd have to do it from your LiveCD. But if you can't get that to work, try out the [GParted Live CD/USB](http://gparted.sourceforge.net/livecd.php). That should pretty much be guaranteed to work for you. Just be careful and back up your important files first.
I had unmounted the partition first

---

### Post by Erik1984 on 2012-05-15
You can't unmount the partition of the OS you are currently running. You can just use the same CD/DVD/USB dongle you used for installing Ubuntu to run gparted from there without any mounted partitions on the HDD. Then just leave empty space by shrinking Lubuntu's partition an let Vista take that empty space during installation. Oh and MAKE SURE YOU HAVE BACKUPS WHEN MESSING WITH PARTITIONS.

---

### Post by sudodus on 2012-05-15
> **davidafranklin said:**
> Gpart runs for a few mn and at the end I get an error message I did some reserchad and I found out that Gpart only works with Gnome/Unity. 

I guess I am confused. 

All I want to do is install, Windows Vista in Dual boot along with my existing Lubuntu 12.04 knowing that my entire rive is in Ext4. I understand that when I will partition my drive in NTFS (If I am able to do it) I have to put the NTFS empty partiton at the beginning which will then mess up my linux  boot.

So you recommendation is to use PartedMagic  to do this, right?

Many thanks
Are you trying to run ***gpart*** or ***gparted***? Those are two very different programs. And as suggested, run gparted from a live CD or USB drive! (It works in Lubuntu, so it does not require 'vanilla' Ubuntu with gnome/Unity.)

---

### Post by davidafranklin on 2012-05-15
Thanks Guys, I will try this later today. I was running Gparted from a live Ubuntu 12.04 CD.

---

### Post by forrestcupp on 2012-05-15
If you're using GParted from a LiveCD and it's still not working, one thing to check is to make sure you've turned your Swap partitions off with swapoff in GParted. If your swap partitions are still on and you are moving or resizing them in the process, it won't work. GParted works in Lubuntu, or any DE, if you have the Gnome libs installed. That's not your problem.

If it still doesn't work, try the actual GParted Live CD/USB that I linked to earlier, instead of Ubuntu. The worst thing that will happen is you wasted some time and a blank CD, if you don't use a USB stick.

---

### Post by davidafranklin on 2012-05-16
Hi guys,

I ran Gparted alone from a live CD. I swapped off the partition and started the resize partition  (tried both to put empty space before and atfer) and same issue: error message. Seems that  Gparted thinks my drive is mounted even though I am using a liveCD.

Not sure what to do next.

I am afraid of formatting the entire drive from Ext4 to NTFS, install Vista and then reinstall Lubuntu. I am afraid to gte drive issues with Vista and not be able to install all of it so this i why I wanted to keep my Linux during the entire process.

Any new suggestions  will be welcome.
Thanks

---

### Post by sudodus on 2012-05-17
I would backup all personal files (documents, pictures, etc) and then wipe the drive.

If gparted doesn't work, it might be a good idea to wipe the drive completely. If the internal drive is /dev/sda, wipe it (but make sure with sudo fdisk -lu, that it is the correct device name). So probably you should replace sd[COLOR="Red"]x[/COLOR] with sd[COLOR="red"]a[/COLOR] in the following command.

```
sudo dd if=/dev/zero of=/dev/sd[COLOR="red"]x[/COLOR] bs=4096
```

After that you can create a partition table (the simplest one is MBR) and partitions for Vista and Lubuntu. Use ***gparted*** from a live CD or USB drive to to that.

I suggest that you make the first partition (NTFS) for Vista, at least 50 GB, but maybe at least 80 GB is better, because Vista wants a lot of disk space. 

Then make an extended partition for the rest of the drive, and inside that a swap partition of the same size (or a little more) as the RAM. Then you make a partition for Lubuntu, and a common NTFS data partition. Select sizes according to what you need and what you want. You can also make a separate /home partition for Lubuntu if you want.

How big is you internal HDD?

*Edit: And install first Vista, then Lubuntu.*

---

