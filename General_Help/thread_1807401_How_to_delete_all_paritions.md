---
title: "How to delete all paritions"
date: 2011-07-19
forum: General Help
---

### Post by tech291083 on 2011-07-19
Hi,

One of my pcs with one hard disk has Ubuntu 10.10 on it, is it possible to delete all partitions on the disk and make the entire hard disk space free/unallocated using by rebooting the pc with Ubuntu live CD and using the GParted application on this CD? Thanks.

---

### Post by tommpogg on 2011-07-19
Yes, you can do that using Gparted.
Be aware that all the files and data on the hard disk will be deleted. So backup any data before deleting the partitions.

---

### Post by tech291083 on 2011-07-19
So I just have to boot pc to Ubuntu then insert the Ubuntu CD and reboot with it and then use GParted to delete all partitions so make the whole drive unallocated space. Right? If this is successful then how will the pc boot next time with no OS on it? Please guide me,Thanks

---

### Post by foutes on 2011-07-19
Just delete partitions and then create 1 full disk partition and format it to ntfs for windows or fat32 or ext3/4 for linux

I would unplug the drive you DO NOT want to delete the partitions on  before you boot the computer so as not to make a mistake and delete data  on the wrong drive.

Boot the computer off the live cd and open Gparted and click on the disk you want to delete the partitions on in the top right corner,you should see all the partition listed,just right click and delete partition

---

### Post by tech291083 on 2011-07-19
> **foutes said:**
> Just delete partitions and then create 1 full disk partition and format it to ntfs for windows or fat32 or ext3/4 for linux

Ok, then I am doing that in the next 5 minutes or so, so please guide me along, thanks

---

### Post by foutes on 2011-07-19
> **tech291083 said:**
> Ok, then I am doing that in the next 5 minutes or so, so please guide me along, thanks

Read my post again before you do that

---

### Post by tech291083 on 2011-07-19
> **foutes said:**
> Just delete partitions and then create 1 full disk partition and format it to ntfs for windows or fat32 or ext3/4 for linux

I would unplug the drive you DO NOT want to delete the partitions on  before you boot the computer so as not to make a mistake and delete data  on the wrong drive.

Boot the computer off the live cd and open Gparted and click on the disk you want to delete the partitions on in the top right corner,you should see all the partition listed,just right click and delete partition

Yes, I agree with you. I have only one hard drive. I just rebooted using the Ubuntu CD and started GParted from the System>Administration menu, but the GParted program closes/crashes within a second, why so? It says on the tool bar where all the menus are such as Applications, Places etc - that crash report detected...

I then tried this command 
> 
sudo gksu gparted /dev/sda

But it shows an error

> glibmm ERROR **:
unhandled exception...
what: basic_string::_S_create
aborting

---

### Post by tommpogg on 2011-07-19
> **tech291083 said:**
> 
I just rebooted using the Ubuntu CD and started GParted from the System>Administration menu, but the GParted program closes/crashes within a second, why so? It says on the tool bar where all the menus are such as Applications, Places etc - that crash report detected...


This is really unusual. I have just used GParted yesterday and everything went smoothly.
I am not an expert, but there could be a problem with your Ubuntu CD. Try to burn a new one.
Alternatively, you can use a standalone GParted CD to delete your partitions (you can find it [here]("http://gparted.sourceforge.net/")). But, after you have deleted them you will need an Ubuntu CD/USB to install Ubuntu.

By the way, if you format your hard drive and you don't install any OS, nothing should happen at start up.

---

### Post by tech291083 on 2011-07-19
I just inserted the Ubuntu CD and booted off it and the in a terminal typed the following command

```
dd if=/dev/zero of=/dev/sdX  bs=512  count=1
```

Here is the reference[COLOR=#000000][/COLOR][http://www.cyberciti.biz/faq/linux-remove-all-partitions-data-empty-disk/](http://www.cyberciti.biz/faq/linux-remove-all-partitions-data-empty-disk/)

Just rebooted the pc after executing this command and all I see on the screen is a message - **"Reboot and Select proper Boot device or Inster Boot Media in selected Boot device and press a key"**.

So, this means that I have deleted all the paritions on the hard drive successfully? Thanks

---

### Post by tommpogg on 2011-07-19
> **tech291083 said:**
> 

Just rebooted the pc after executing this command and all I see on the screen is a message - **"Reboot and Select proper Boot device or Inster Boot Media in selected Boot device and press a key"**.

So, this means that I have deleted all the paritions on the hard drive successfully? Thanks

It seems so.  You can double check using GParted again, just to see if it recognise any partition.

---

### Post by dino99 on 2011-07-19
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by plucky on 2011-07-19
> **tech291083 said:**
> I just inserted the Ubuntu CD and booted off it and the in a terminal typed the following command

```
dd if=/dev/zero of=/dev/sdX  bs=512  count=1
```

Here is the reference[COLOR=#000000][/COLOR][http://www.cyberciti.biz/faq/linux-remove-all-partitions-data-empty-disk/](http://www.cyberciti.biz/faq/linux-remove-all-partitions-data-empty-disk/)

Just rebooted the pc after executing this command and all I see on the screen is a message - **"Reboot and Select proper Boot device or Inster Boot Media in selected Boot device and press a key"**.

So, this means that I have deleted all the paritions on the hard drive successfully? Thanks

No,all that command will do is wipe the Master Boot Record,which is why it thinks it is not a bootable disk.

---

### Post by egalvan on 2011-07-19
> **plucky said:**
> No,all that command will do is wipe the **Master Boot Record**,which is why it thinks it is not a bootable disk.

The **MBR** contains the partition table record.
Erasing it will erase the information on the partition(s),
effectively "deleting" the partition(s).
But not really deleted, because all the data itself is still there, :o
  and any half-way decent partition-recovery tool will recover it 100%.

dban is an excellent drive eraser.
It **will** completely erase a drive...
very small .iso, takes just a few minutes to download.
[www.dban.org](www.dban.org)

I also use (and support $$) PartedMagic LiveCD...
a small distro that has a lot of drive/partition tools.

---

### Post by tech291083 on 2011-07-19
> **egalvan said:**
> The **MBR** contains the partition table record.
Erasing it will erase the information on the partition(s),
effectively "deleting" the partition(s).
But not really deleted, because all the data itself is still there, :o
  and any half-way decent partition-recovery tool will recover it 100%.


Thanks a lot egalvan, but I hope that the command will hopefully - effectively delete all the partitions...

---

