---
title: "No GRUB partition?"
date: 2009-12-31
forum: General Help
---

### Post by ZombiesNTea on 2009-12-31
Hi... I, being illiterate when it comes to programming and partitioning and the like, screwed up my laptop.

Initially, I installed Ubuntu Netbook Remix onto my Acer Aspire One... leaving Windows Vista intact, creating a new partition.  The home screen was incredibly slow, couldn't get that working, so I tried Xubuntu on there.  Decided I didn't prefer it.

So I go onto Vista, right click "Computer" and go to "Manage," and I believe what I went to next was "Partition Manager" (the area where I can create new partitions of space.).  Idiotically, I right click and delete the Linux partitions from the bar that visually shows the amounts of space being used per partition.  The C drive was left alone.

Soon after, I rebooted.  Rather than the menu that comes up when there is more than one OS, or rather than going straight to Windows, it says the following:

```
GRUB loading.
error: no such partition
grub rescue>
```

So I have the following questions:

1) How do I access Windows?
2) How do I stop this from appearing when I turn on my laptop?
3) I'm interested in trying regular Ubuntu, and possibly other Linux operating systems on it... if I choose to delete one of these theoretical partitions, how do I go about safely doing it?

Any help whatsoever is greatly appreciated!  Thanks!

---

### Post by pastalavista on 2009-12-31
If you don't re-install Linux, you'll need to Repair the Windows boot sector with the Windows boot CD. If you reinstall Ubuntu or any other distro in the empty partition, grub should repair the Windows boot-loader too. The partitions are not "theoretical" unless you installed using Wubi (inside Windows), in which case there would be no Grub.

---

### Post by ZombiesNTea on 2009-12-31
> **pastalavista said:**
> If you don't re-install Linux, you'll need to Repair the Windows boot sector with the Windows boot CD. If you reinstall Ubuntu or any other distro in the empty partition, grub should repair the Windows boot-loader too. The partitions are not "theoretical" unless you installed using Wubi (inside Windows), in which case there would be no Grub.

Thanks a million!  I'll try putting Ubuntu on (I have no CD, nor a CD drive).

What I meant by theoretical was, if I am to put any OS on in the future that uses GRUB/is Linux, and want to remove it, how would I go about doing that?

Again,thank you!

---

### Post by pastalavista on 2009-12-31
Welcome ! :)

Since you don't have CD drive, the first partition on your machine should be the Windows restore partition. You can probably access that at the first (manufacturers) boot screen to repair Windows. 

To remove an installation you can just reformat or delete the partition it's on but it will also remove Grub so you won't be able to boot Windows without repairing it with the recovery partition or a new installation of Grub from some other OS.

Just be very careful not to destroy the Windows restore partition. If you can, back it up on a flash drive. I, personally, no longer use Windows in any form but I still have my Vista CD if I ever need it (like if I sell the computer). Some people will have no truck with Linux. It scares them :D

---

### Post by ZombiesNTea on 2009-12-31
> **pastalavista said:**
> Welcome ! :)

Since you don't have CD drive, the first partition on your machine should be the Windows restore partition. You can probably access that at the first (manufacturers) boot screen to repair Windows. 

To remove an installation you can just reformat or delete the partition it's on but it will also remove Grub so you won't be able to boot Windows without repairing it with the recovery partition or a new installation of Grub from some other OS.

Just be very careful not to destroy the Windows restore partition. If you can, back it up on a flash drive. I, personally, no longer use Windows in any form but I still have my Vista CD if I ever need it (like if I sell the computer). Some people will have no truck with Linux. It scares them :D

Thanks!

1) How do I back up a Windows Recovery partition to my flash drive?
2) Installing an Ubuntu OS (so as to get grub work) on here, I'm having a problem.  I'm trying to install Kubuntu (netbook version) and hit a brick wall when, after clicking to install, and waiting for it to load, this pops up:

```
init:/etc/init/tty5.conf:1: Unknown stanza
init:/etc/init/tty6.conf:1: Unknown stanza
init:/etc/init/usplash.conf:1: Unknown stanza
init: dbus pre-start process (2430) terminated with status 1
*Starting early crypto disks...
*Starting remaining crypto disks...
*Starting Kernel Oops catching service kerneloops
*Starting Common Unix Printing System: cupsd
*Checking battery state...
...done.
*Starting init crypto disks...                 [OK]
```

Below that is the blinking bar indicating for me to type.

What should I do?

Again, thanks for having helped me so far!

---

### Post by SecretCode on 2009-12-31
> **ZombiesNTea said:**
> 1) How do I back up a Windows Recovery partition to my flash drive?

There are a few ways, but I would do this: 
- download Clonezilla live or PartedMagic CD v4.5 (not 4.6) and burn the .iso file to a CD
- boot from the CD and run clonezilla
(you might want to read through some of good clonezilla tutorials on the net)
- when prompted, select mode **device-image** and then mode **saveparts**. Then pick partition sda1 (I'm 90% sure windows recovery will be on the first partition) to save.
- attach your USB drive when prompted (during the above)

There are quite a few more prompts in the clonezilla process, but the others should make sense.

This will also make a backup of your MBR - and that is a good thing to have - for one thing, it would enable you to recover quickly from a bad grub install such as you have.

---

### Post by SecretCode on 2009-12-31
Next, I would suggest sorting out your boot loader and your partitions before attempting a new install. 

From the ubuntu/kubuntu live cd, or the partedmagic CD if you downloaded that, open a terminal and type:
```
sudo fdisk -l
```
and post the results.

---

### Post by ZombiesNTea on 2009-12-31
> **SecretCode said:**
> Next, I would suggest sorting out your boot loader and your partitions before attempting a new install. 

From the ubuntu/kubuntu live cd, or the partedmagic CD if you downloaded that, open a terminal and type:
```
sudo fdisk -l
```
and post the results.

Thanks for responding!

Not only does it not install... it wont load it just as a live cd either.  So I'm stuck with it either trying to load GRUB that doesn't exist, or trying to install OR just run Kubuntu off of a flash drive and have the whole "*Starting init crypto disks..."

---

### Post by Leppie on 2009-12-31
> **ZombiesNTea said:**
> Not only does it not install... it wont load it just as a live cd either.  So I'm stuck with it either trying to load GRUB that doesn't exist, or trying to install OR just run Kubuntu off of a flash drive and have the whole "*Starting init crypto disks..."

if it does not boot off the cd but it does off a usb stick, it looks like the cd is corrupt. try downloading a new karmic image and check for errors (after downloading and after burning).

---

### Post by SecretCode on 2009-12-31
Agree with Leppie - the CD may be bad. As well as downloading again, try to burn it at the lowest possible speed: some computers are more sensitive to errors while booting than after the OS is loaded (ie they can't correct some CD errors on the fly; CDs do assume a certain level of errors).

Are you able to download Clonezilla?

---

