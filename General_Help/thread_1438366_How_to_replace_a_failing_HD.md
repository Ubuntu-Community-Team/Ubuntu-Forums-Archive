---
title: "How to replace a failing HD"
date: 2010-03-24
forum: General Help
---

### Post by technoholic on 2010-03-24
My 9.10 system has three drives, one of which is reporting SMART alerts. Not wanting to take chances, a new drive is ordered and will be here in a day or two. 

The failing drive is dedicated to the Home Folder.

The data is backed up.

How should I go about replacing this bad drive?

Rich

---

### Post by dcstar on 2010-03-24
> **technoholic said:**
> My 9.10 system has three drives, one of which is reporting SMART alerts. Not wanting to take chances, a new drive is ordered and will be here in a day or two. 

The failing drive is dedicated to the Home Folder.

The data is backed up.

How should I go about replacing this bad drive?

Rich

Plug it in and use gparted to copy the partition/s.

---

### Post by scrooge_74 on 2010-03-24
Put the drive in the system, mount it under some name, then copy your entire /home there,  after you then go to /etc/fstab and point /home to the new drive. Shut down take problem drive out, restart.

---

### Post by Serpher on 2010-03-24
Do you mean in terms of hardware? Open the thing up, there should be two cables connected to the harddrive. Take those two out, put them where the fit on the other harddrive, done.

If you're talking about a proper back up and restore, burn yourself a life cd now and run the following command in the directory you wish to save the file (can be within a part of the file system being backed up.

```
$sudo dd if=/dev/sd? of=<nameForBackup>.img
```
** ? = Letter used for your harddrive.


This will give you image of your harddrive, and if it's too big you're going to want to run gzip on it. One of your harddrives though is probably going to have to be bigger than your home's hardrive. Gzip however will shrink it down to a very small size, I think because of the "empty space" in the image.

When you get your new harddrive and hook it up run the following command while in the directory of the .img.

```
$sudo dd if=<nameForBackup>.img of=/dev/sd?
```

You won't even notice you changed harddrives besides for the lack of SMART errors.

---

### Post by egalvan on 2010-03-24
Using clonezilla may be easier...

[http://www.clonezilla.org/](http://www.clonezilla.org/)


I use this mini-distro for drive/partition work...

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by egalvan on 2010-03-24
As for the *hardware* side of things...

I would detach the other two drives (power and data cables)... leave only the failing drive.

temporarily attach the new drive (power and data cables)

This leaves only the new drive, which should be empty
and the original /home drive, which should have your data.
This makes it easier to find which drive is which.


boot with a livecd, such as clonezilla or partedmagic,
and **MAKE SURE OF WHICH DRIVE HAS YOUR DATA**
then do a full drive clone.

replace the old drive with the new drive,
then re-attach other two drives.

---

### Post by technoholic on 2010-03-24
Thanks for the quick replies!!! 

Digesting what has been said I can: 

1) Install the new HD, power up and use gparted to partition it. 

2) restore the data to the new HD

3) edit /etc/ftab with new HD UUID

4) shutdown and uninstall failing HD

5) power up and get back to work

Am I on the right track? One remaining question is how to get the UUID of the new drive. Does gparted make an entry in /etc/fstab? Running vol_id --uuid (per /etc/fstab comments) returns 'vol_id: command not found' what did I do wrong with that?

---

### Post by dcstar on 2010-03-24
> **technoholic said:**
> Thanks for the quick replies!!! 

Digesting what has been said I can: 

1) Install the new HD, power up and use gparted to partition it. 

2) restore the data to the new HD

3) edit /etc/ftab with new HD UUID

4) shutdown and uninstall failing HD

5) power up and get back to work

Am I on the right track? One remaining question is how to get the UUID of the new drive. Does gparted make an entry in /etc/fstab? Running vol_id --uuid (per /etc/fstab comments) returns 'vol_id: command not found' what did I do wrong with that?

If you simply use the method I provided, there is no need whatsoever to muck around with UUIDs or any other file, just remove the bad disk.

Why do people offer "solutions" 10 times more complicated than they need to be?

---

### Post by technoholic on 2010-03-24
> **egalvan said:**
> Using clonezilla may be easier...

[http://www.clonezilla.org/](http://www.clonezilla.org/)


I use this mini-distro for drive/partition work...

[http://partedmagic.com/](http://partedmagic.com/)

Thanks! I will investigate those utilities.

---

### Post by technoholic on 2010-03-24
> **dcstar said:**
> If you simply use the method I provided, there is no need whatsoever to muck around with UUIDs or any other file, just remove the bad disk.

Why do people offer "solutions" 10 times more complicated than they need to be?

Thanks, David.
I will report back when the new HD is intalled and mark the thread SOLVED.

Live long and prosper!

---

### Post by CharlesA on 2010-03-24
> **dcstar said:**
> If you simply use the method I provided, there is no need whatsoever to muck around with UUIDs or any other file, just remove the bad disk.

Why do people offer "solutions" 10 times more complicated than they need to be?

Since there are several different ways that different people do different things.

Anyhow, Copy the whole partition with clonezilla or gparted would probably be the easiest way to go about it.

---

### Post by technoholic on 2010-03-26
Once I figured out that Gparted needs to be run from a live CD (duh!) it was almost a no brainer. You do need to be familiar with Gparted:

1) Install new HD
2) Boot from Gparted Live CD - [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
3) Copy partitions
4) Shutdown and remove old HD
5) Power up and get back to work

Ubuntu rocks! Now I have a faster drive with more space and no more disk errors....SWEET!

Many thanks to all who helped me resolve this problem may you all:

Live long and prosper!! 

Rich

---

### Post by dcstar on 2010-03-26
> **technoholic said:**
> Once I figured out that Gparted needs to be run from a live CD (duh!) it was almost a no brainer.
........

Only if you need to work on partitions that cannot be unmounted (like "/" and "/home"), you can use gparted on non-system partitions from a running system.

---

### Post by egalvan on 2010-03-30
> **dcstar said:**
> If you simply use the method I provided, there is no need whatsoever to** muck around with UUIDs **or any other file, just remove the bad disk.

Why do people offer "solutions" 10 times more complicated than they need to be?

I've re-read the posts, and find none that suggested *mucking around with UUID's*.

As for other solutions being *10 times more complicated*...

maybe it's because other solutions offer 10 times more detail??? ;)

Some beginners *need* the extra detail.

an example from back-in-the-day...

*The Zen Guide to Volkswagen Repair*
"How to fix a bad transmission"
Step 1) Remove Transmission

Now to an *experienced* mechanic, even that simple step is superfluous.

To a non-mechanic, there are about 50 missing steps... :P

Stay Frosty :KS

---

