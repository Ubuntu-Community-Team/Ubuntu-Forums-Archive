---
title: "Ubuntu on a USB question"
date: 2010-04-07
forum: General Help
---

### Post by Gauze on 2010-04-07
So I was trying to install tor and was following the instructions that was here.

[https://help.ubuntu.com/community/Tor?action=show&redirect=TOR](https://help.ubuntu.com/community/Tor?action=show&redirect=TOR)

I did:

sudo apt-get upgrade

Which I believe installed a bunch of upgrades.

Currently, I have 0 bytes free. I started with 1.1 gigabytes free.

I must not be understanding something though but before the upgrade started, it said it would be freeing up space in the end.

Additionally, I have tried uninstalling some software but it hasn't freed up any space at all. I deleted a 5.7 mb folder and that did nothing.

What am I misunderstanding? Is there anyway to undo what I did?

And how as I supposed to install TOR?

Finally, how can I change where software is installed. I'm using a 16 gb flashdrive that I partitioned into two drives.

---

### Post by 2hot6ft2 on 2010-04-07
When you do updates/upgrades the packages are still on your system (but no longer needed) even after they are installed. To clean the cache out
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get autoremove
```
You will have to enter your password which wont be displayed just type it in and hit Enter
Then you will have more free space.

And if you got a warning from Disk Usage Analyzer don't go by that, instead run this
```
df -h
```
in a terminal to see how much space is used and free. To better understand see this thread.
[[SOLVED] Low Disk Space Warning, A bug? Or a limitation?]("http://ubuntuforums.org/showthread.php?t=1410114")

As for TOR just follow the guide is all I can say.

---

### Post by Gauze on 2010-04-07
I tried that and got this as the result.

```
ubuntu@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
ubuntu@ubuntu:~$ 

```

Still no free space.

---

### Post by 2hot6ft2 on 2010-04-07
What do you get from
```
df -h
```

---

### Post by Gauze on 2010-04-07
```

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  3.9G  3.7G     0 100% /
udev                  1.6G  336K  1.6G   1% /dev
/dev/sdc1             4.9G  4.8G  103M  98% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  1.6G  276K  1.6G   1% /dev/shm
tmpfs                 1.6G   16K  1.6G   1% /tmp
none                  1.6G  192K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
none                  1.6G     0  1.6G   0% /lib/init/rw
/dev/sdc2              11G  9.1G  1.1G  90% /media/DATA
/dev/sdd1              15G  5.5G  9.5G  37% /media/PENDRIVE
ubuntu@ubuntu:~$ 

```

DATA is the other partition of the USB flashdrive and PENDRIVE is another USB flashdrive I have plugged in at the moment.

---

### Post by 2hot6ft2 on 2010-04-07
Looks like you sure filled it up.
Sure looks like it's almost 100% used.

But what I don't get is why it shows
```
/dev/sdc1             4.9G  4.8G  103M  98% /cdrom
/dev/sdc2              11G  9.1G  1.1G  90% /media/DATA
```
sdc1 as /cdrom
when sdc2 is the other partition
Might take a look at it in GParted
System > Administration > GParted

---

### Post by Gauze on 2010-04-07
I guess the problem with updating Ubuntu that is installed on a flashdrive is that old versions or software are not actually replaced?

Or might there be another issue?

So...is there anyway to undo what I did or do I have to install from scratch again?

Is there a way to make the software manager install on the other partition?

edit:

[http://img534.imageshack.us/img534/4403/screenshotrj.png](http://img534.imageshack.us/img534/4403/screenshotrj.png)

---

### Post by wilee-nilee on 2010-04-07
You might want to know how to have a larger save area if this is a ISO thumb install, beyond the only 4 gigs allowed with the startup disc creator.
[http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/](http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/)

So it will be helpful for some of us to tell us exactly how you installed on the thumb, and with which loader if it is not a full install.

---

### Post by 2hot6ft2 on 2010-04-07
Is this a real install to usb?

Or is it a usb strartup disk creator type (pendrivelinux) where the iso is copied to the usb with persistent changes?
In which case you're right the ISO contents are not replaced.

Mine is a full real install to usb which I split 8/8 OS/Data.

---

### Post by Gauze on 2010-04-07
> **wilee-nilee said:**
> You might want to know how to have a larger save area if this is a ISO thumb install, beyond the only 4 gigs allowed with the startup disc creator.
[http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/](http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/)

So it will be helpful for some of us to tell us exactly how you installed on the thumb, and with which loader if it is not a full install.

Well, it was kind of sloppy. I use the lexar usb format program (bootit?) to flip the bit on my flashdrive so I could partition it into a 5000 MB partition and the remaining size as another partition.

Then, I flip the bit again so I could use:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Installed 9.10 and had 4 gb of persistence.

Flip the bit again so Windows XP computers could see both partitions.

I had 1.1 gb free when I tried following the instructions here:

[https://help.ubuntu.com/community/Tor?action=show&redirect=TOR](https://help.ubuntu.com/community/Tor?action=show&redirect=TOR)

...for 9.10 users.

```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade
```

It filled up when I did sudo apt-get upgrade.

> **2hot6ft2 said:**
> Is this a real install to usb?

Or is it a usb strartup disk creator type (pendrivelinux) where the iso is copied to the usb with persistent changes?
In which case you're right the ISO contents are not replaced.

Mine is a full real install to usb which I split 8/8 OS/Data.

Erm...I just googled stuff. I didn't even know that there was a real install and a fake install.

---

### Post by wilee-nilee on 2010-04-07
> **Gauze said:**
> I guess the problem with updating Ubuntu that is installed on a flashdrive is that old versions or software are not actually replaced?

Or might there be another issue?

So...is there anyway to undo what I did or do I have to install from scratch again?

Is there a way to make the software manager install on the other partition?

edit:












[http://img534.imageshack.us/img534/4403/screenshotrj.png](http://img534.imageshack.us/img534/4403/screenshotrj.png)

So it appears that this is disk creator install. A full install will run a little faster and boot much faster. If you decide to do a full install be careful if you do not put grub in the MBR of the usb it is a problem. This can be confirmed in the last gui on a full install by ticking advanced and making sure grub is being put on the device.

Edit:  It looks like you are getting it figured out with the other poster. So now you know about full installs and how to have a larger persistent file if needed with a ISO loaded usb, good luck.

---

### Post by Gauze on 2010-04-07
Erm, I'm not sure what that meant...beyond what MBR is...but it sounds like something that I should be being so I avoid this problem.

How exactly do I do a real install onto a flashdrive?

---

### Post by 2hot6ft2 on 2010-04-07
Here's my full install, it was actually more like 9/6 OS/Data
I removed the hard drive in the laptop so it wouldn't affect my hard drive at all, and as was just stated had to choose where to install the boot loader in the last step.

All updates that involve a kernel upgrade are done with the hard drive out so it wont rewrite my hard drives grub or add my hard drives OS's to it's grub.

I ended up installing 8.10 then upgrading to 9.04 then 9.10 because of 9.10 dropping me to the initramfs prompt when trying to boot.

I did NO bit flipping. And the desktop on it

---

### Post by wilee-nilee on 2010-04-07
> **2hot6ft2 said:**
> Here's my full install, it was actually more like 9/6 OS/Data
I removed the hard drive in the laptop so it wouldn't affect my hard drive at all, and as was just stated had to choose where to install the boot loader in the last step.

All updates that involve a kernel upgrade are done with the hard drive out so it wont rewrite my hard drives grub or add my hard drives OS's to it's grub.

I ended up installing 8.10 then upgrading to 9.04 then 9.10 because of 9.10 dropping me to the initramfs prompt when trying to boot.

I did NO bit flipping.

Hey would you let the OP know how to do a full install, I can't remember the line name in the custom partitioning for the / =root

Also OP you could probably fix that thumb to have a larger persistent but it would revert to the original ISO when you remove casper-rw and make the other partition a ext2 named casper rw. In other words take everything off you want to save. A full install though is a preferred way for some especially with a 16 gig thumb, I have a the same size thumb with a full install of Lucid.

---

### Post by Gauze on 2010-04-07
I would love to know how to do a proper install. Probably avoid these problems in the future.

Though the part about removing the harddrive...would disabling a harddrive through BIOS achieve the same thing?

---

### Post by 2hot6ft2 on 2010-04-07
> **wilee-nilee said:**
> Hey would you let the OP know how to do a full install, I can't remember the line name in the custom partitioning for the / =root
I think we did it different ways since I don't know what you're referring to.
How I did mine.

Put livecd in cd drive and shut pc down,
Remove hard drive from pc.
Boot up to livecd.
Once it's fully up and loaded insert usb flash drive.
Used GParted to partition my OS partition to ext2.
Add a swap partition of about 1GB so the installer wont complain about not having one.
Start the installer and choose Manual at the partitioner and click Forward to load the manual partitioner.
Select the partition that I already setup for the OS and set it to mount point / filesystem type ext2 and checked format.
Continued to Step 7 and clicked on Advanced and used the drop down to select /media/sdc for where to install the boot loader
Clicked OK then Forward to do the install.

After installation finished rebooted removing the livecd in the process.
Ran ALL my updates AND upgrades AND updates again and rebooted for a last time making sure everything was updated and upgraded all it could be.
Then shut the pc down and re-installed the hard drive.

Opened GParted and deleted the swap partition on the flash drive and created the Data partition formatting it to FAT32.

All done all that was left was customization.

---

### Post by 2hot6ft2 on 2010-04-07
> **Gauze said:**
> I would love to know how to do a proper install. Probably avoid these problems in the future.

Though the part about removing the harddrive...would disabling a harddrive through BIOS achieve the same thing?
Unplugging it is the best way to be sure it wont be affected by the install.
A desktop, open the case and simply unplug the cable for it.
A Laptop mine was only 3 screws and sliding it out, reverse to put back in.

Time to eat I'll be back in bout 1/2 hour.

---

### Post by wilee-nilee on 2010-04-07
> **2hot6ft2 said:**
> I think we did it different ways since I don't know what you're referring to.
How I did mine.

Put livecd in cd drive and shut pc down,
Remove hard drive from pc.
Boot up to livecd.
Once it's fully up and loaded insert usb flash drive.
Used GParted to partition my OS partition to ext2.
Add a swap partition of about 1GB so the installer wont complain about not having one.
Start the installer and choose Manual at the partitioner and click Forward to load the manual partitioner.
Select the partition that I already setup for the OS and set it to mount point / filesystem type ext2 and checked format.
Continued to Step 7 and clicked on Advanced and used the drop down to select /media/sdc for where to install the boot loader
Clicked OK then Forward to do the install.

After installation finished rebooted removing the livecd in the process.
Ran ALL my updates AND upgrades AND updates again and rebooted for a last time making sure everything was updated and upgraded all it could be.
Then shut the pc down and re-installed the hard drive.

Opened GParted and deleted the swap partition on the flash drive and created the Data partition formatting it to FAT32.

All done all that was left was customization.

The mount point is what I was referring to, with all of my full installs you have to put / in the mount point space.

---

### Post by 2hot6ft2 on 2010-04-07
> **wilee-nilee said:**
> The mount point is what I was referring to, with all of my full installs you have to put / in the mount point space.
Yeah, if nothing else it needs to have the root / mount point...
I thought you might be talking about doing a command line install.

---

### Post by wilee-nilee on 2010-04-07
> **2hot6ft2 said:**
> Yeah, if nothing else it needs to have the root / mount point...
I thought you might be talking about doing a command line install.

I wish, I know some things, mainly what not to do, but cli usage is pretty basic for me. Thanks for posting a instruction for the op this sort of install is easy once you know how but can fail dramatically if grub is not set to the usb.

Edit; The only thing I will add is that since I use my full install thumb as a backup I never suspend or hibernate with it so I just installed it to a primary partition no swap. I have 2 gigs of ram so it runs fast.

---

### Post by 2hot6ft2 on 2010-04-07
> **wilee-nilee said:**
> I wish, I know some things, mainly what not to do, but cli usage is pretty basic for me. Thanks for posting a instruction for the op this sort of install is easy once you know how but can fail dramatically if grub is not set to the usb.
We all hope we know what not to do. Looks like the OP logged out so I guess we'll see in time if it helped or not. And you're welcome. Like I said I ended up installing 8.10 and upgrading all the way to 9.10 because it wouldn't boot with the hard drive in the pc (kept dropping me to the initramfs prompt) but it would fine with it out.

EDIT: I have 3 GB of RAM but I use mine to work on others pc's. Antivius and all the fun things linux can do.

---

### Post by Gauze on 2010-04-08
Alright, I did most of what you said...except for ext4 and using the Ubuntu installer on another Live USB that I had.

Having some problems with my internet using ndis...but my router is temperamental...so I'm going to try it on campus tomorrow and see if it works there.

Thank you for all your help.

---

