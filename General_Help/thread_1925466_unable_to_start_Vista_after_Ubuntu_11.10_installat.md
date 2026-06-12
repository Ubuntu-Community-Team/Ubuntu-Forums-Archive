---
title: "unable to start Vista after Ubuntu 11.10 installation"
date: 2012-02-14
forum: General Help
---

### Post by ulysson on 2012-02-14
Hi,

I installed Ubuntu 11.10 on a separate partition (ext4)
Ubuntu is working  great without any problem.

I'm not able to start Vista :(
Only Vista recovery is accessible.

When I select Vista loader through Grub, I'm back to grub menu again !!!

I tried **fixmbr** and **fixboot **commands using Vista recovery tool.
it says everything is applied successfully but the problem is still not solved :(

When i typed **sudo fdisk -l**
I got a message saying that there is problem with partition order !!!

What shoud I do ? Is there an EasyBCD alternative for ubuntu ? or any application that could help me start Vista ?

I'm a student and all my data is stored on Vista partition.

Thank you :)

---

### Post by josephmills on 2012-02-14
> **ulysson said:**
> Hi,

I installed Ubuntu 11.10 on a separate partition (ext4)
Ubuntu is working  great without any problem.

I'm not able to start Vista :(
Only Vista recovery is accessible.

When I select Vista loader through Grub, I'm back to grub menu again !!!

I tried **fixmbr** and **fixboot **commands using Vista recovery tool.
it says everything is applied successfully but the problem is still not solved :(

When i typed **sudo fdisk -l**
I got a message saying that there is problem with partition order !!!

What shoud I do ? Is there an EasyBCD alternative for ubuntu ? or any application that could help me start Vista ?

I'm a student and all my data is stored on Vista partition.

Thank you :)


could we see a ```
sudo fdisk -l 
``` also could you try ```
sudo update-grub
``` does it see it now ? let us know how it goes thanks

---

### Post by Mark Phelps on 2012-02-15
HOW did you allocate hard drive space for Ubuntu?  DId you make the serious mistake of using the Ubuntu installer and the SLIDER to shrink the Vista OS partition?  If so, then you likely corrupted the Vista OS and rendered it unbootable.

Instead of entering commands, try using the Vista recovery tool and running Repair three times -- that's three times.

If that doesn't work, and you can boot Vista to a command line, then run CHKDSK on the OS volume from that.  That should repair any filesystem corruption.

---

### Post by holycow131415 on 2012-02-15
If you nuked your vista. Boot into ubuntu, and navigate into vista's partition so that you can back up your files to an external place. What id do is just reinstall vista, use vista's disk management to shrink the hdd. then boot up ubuntu cd to reinstall ubuntu on it.

---

### Post by ulysson on 2012-02-16
sorry for being late to answer !

Ok I'll tell you about everything... Some things I made could help in similar problem...

I was really confused :confused:

I have a hp 6830s laptop
Oringinal installed OS is : Vista Home Premium Edition

I added a new free partition and didn't mounted it nor formatted.
(I left an allocated space for ubuntu installer)

I made a bootable version of ubuntu 11.10 on a USB pendrive

installed ubuntu successfully (ext4 format)
 updated it and used it for internet, media tests...

Then I had to go back to vista to finish some work on Adobe...

Grub menu allowed access only to Recovery partition !!!
When I choose vista, I'm back to grub again :(

I tried to use terminal commands to repair or remove grub.
Nothing happened and didn't understand why it says that partitions order was wrong :confused:

Then I made a bootable Vista recovery copy on USB

I tried to repair MBR using fixmbr fixboot rebuildbcd...
Nothing happened

I deleted boot folder in order to force Recovery tool to create a new functional Bootmanager

Nothing happened :(

I made a copy of HIREN boot CD on a USB
With hiren it's easy 
in the first menu => Vista Bootmgr and I was able to start vista :)

Once on vista, I installed easybcd
And tried to add ubuntu following ubuntu wiki guide

I'm still getting this blinking cursor and can't boot :(

Back again with hiren

I tried to remove hiren from easybcd menu
nothing happened

I become crazy and formatted Ubuntu partition 
I installed vistabootpro and tried to check for MBR errors

I tried againg to recover Vista MBR using vista recovery tool...

Problem still not solved and blinking cursor doesn't disappear

I added Hiren in boot sequence with easybcd

Vista and Hiren menu become visible only using bootmgr on Hiren usb

Is it a Bios problem ? 

I don't care what kind of bootmanager I use ! 

I'm actually using vista but starting with hiren USB disk :confused:

Thank you and sorry for this long and annoying reply :)

---

### Post by rockballad on 2012-02-16
Yes, the first question, can you find your data on Vista partition? You can easily find that partition on [Places]>[Computers] if it's still available.

If you don't find that partition, you might loss it during setup process. Otherwise, you can restore the MBR using Recovery mode (X:\bootrec @http://support.microsoft.com/kb/927392).

---

### Post by oldfred on 2012-02-17
Rather than just trying to fix things lets look at what is installed where. The boot info script that this produces documents your entire boot system.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

