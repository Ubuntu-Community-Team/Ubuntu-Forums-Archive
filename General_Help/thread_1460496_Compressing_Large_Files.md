---
title: "Compressing Large Files?"
date: 2010-04-22
forum: General Help
---

### Post by cquigley on 2010-04-22
Hey Everyone-

  I need to backup my home directory and its 49gb. Is there a way to compress the whole thing so I don't have to copy it. 

Or better yet, what is the best way to back it up? I have to reinstall linux from cd because mine is acting weird and I can't connect to internet on the computer to install the upgrade.

Thanks for your help.

Chris

---

### Post by _0R10N on 2010-04-22
I've never tried to compress a folder of such a size! If compressing is not extremelly necessary, you could to tar the folder. You can also zip it and split it in several parts. I would choose this second option...

Again, I've never performed an operation like this one before, so I'm not completely sure if the standard compression tools bundled with Ubuntu might help you out.

Kind regards!

_0R10N >>

---

### Post by perham on 2010-04-22
> **cquigley said:**
> Hey Everyone-

  I need to backup my home directory and its 49gb. Is there a way to compress the whole thing so I don't have to copy it. 

Or better yet, what is the best way to back it up? I have to reinstall linux from cd because mine is acting weird and I can't connect to internet on the computer to install the upgrade.

Thanks for your help.

Chris

you can upgrade using alternative installation CD from inside your installed version.

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)

---

### Post by Dayofswords on 2010-04-22
you could compress into volumes(like in parts of 2gb) and decompress after

---

### Post by srs5694 on 2010-04-22
I'll assume you've got one big monstrous root (/) partition with no separate partition for /home. If so, here's what I'd do:


[list=1]
[*]Boot an emergency disc, such as [System Rescue CD.](http://www.sysresccd.org)
[*]Mount your Ubuntu partition somewhere convenient (let's say /mnt/ubuntu).
[*]Delete everything *except* /home from your Ubuntu installation -- that is, delete /mnt/ubuntu/usr, /mnt/ubuntu/etc, /mnt/ubuntu/lib, and so on, until only /mnt/ubuntu/home is left.
[*]Move the contents of /mnt/ubuntu/home to /mnt/ubuntu -- that is, "mv /mnt/ubuntu/home/* /mnt/ubuntu".
[*]Unmount /mnt/ubuntu
[*]Use GParted to resize your Ubuntu partition by about 5-20GB, depending on how many programs you want to install when you re-install the system. This partition will become your new /home partition. Resizing by shrinking from the end is likely to be faster and safer than shrinking from the start.
[*]Use GParted to create a new partition in the empty space left by the resize operation. Note which partition number it is; this is where you'll re-install Ubuntu.
[*]Shut down and reboot into the Ubuntu installer.
[*]Re-install Ubuntu, using the advanced partitioning option to select the new 5-20GB partition you've just created as the Ubuntu root (/) partition and your old (resized) partition as /home. *Be sure that /home is marked to **not** be formatted!*
[*]When you boot into your newly-reinstalled system, delete /home/home (it should be an empty directory).
[/list]


This procedure may seem intimidating, but it will leave you with a much better configuration. Keeping /home on the root (/) filesystem is very inflexible, as you're discovering -- in case you need to re-install, you've got to jump through hoops of one sort or another to preserve your user data. If you follow my procedure and you find you need to re-install again, or if you choose to switch to another distribution, you'll be able to keep your user data on the /home partition with very little fuss; just wipe out your root (/) partition and preserve the /home partition and that's it.

One important caveat: Partition resizing operations are always a bit risky. It's best to back up your data before you do this, but it sounds like your problem is that this is difficult or impossible. If you have the money to spare, you should buy an external hard disk to use for backup; or you could back up to about eleven DVDs using a backup tool like [dar.](http://dar.linux.free.fr/)

---

### Post by blueridgedog on 2010-04-22
> **cquigley said:**
> Hey Everyone-

  I need to backup my home directory and its 49gb.

With 49 gig of "stuff" I say you have graduated to the level of needing one or two backup drives.  I suggest you get a few cheap 200 gig drives and a USB tray/dock.  You can then backup your data periodically and have two backups.

The dock is similar to:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817121049](http://www.newegg.com/Product/Product.aspx?Item=N82E16817121049)
or
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817707170](http://www.newegg.com/Product/Product.aspx?Item=N82E16817707170)

I have an internal one and simply plug in a drive and run a backup script.

Any scheme of compressing and backup up that much stuff onto small media (flash drives or dvds) will be labor intensive and prone to fail.

---

### Post by sunk8 on 2010-04-22
Hi,

> **cquigley said:**
> Hey Everyone-
I need to backup my home directory and its 49gb. Is there a way to compress the whole thing so I don't have to copy it. 
Or better yet, what is the best way to back it up? I have to reinstall linux from cd because mine is acting weird and I can't connect to internet on the computer to install the upgrade.
Thanks for your help.
Chris

I use Simple Backup Suite which is in the official repos. It also allows you to compress data while making a backup.

You'll find these pages helpful:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

---

