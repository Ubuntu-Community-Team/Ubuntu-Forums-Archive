---
title: "Problems Mounting NTFS Fakeraid Partion"
date: 2011-09-22
forum: General Help
---

### Post by rumbleph1sh on 2011-09-22
Fellas,

I am a Ubuntu noob and am having trouble mounting my fakeraid NTFS partition. I dual boot with Windows 7 and have a partition with my media that I want to be able to access from Ubuntu. I don't need the partition to automount, but would like to be able to have it available to mount in "Places" every time I login.

This partition is not recognized by Disk Utility or NTFS configuration tool. I have tried editing FSTAB with no success, as well as MountManager.

The only way I am able to access it as follows:

Start Ubuntu, open Gparted, which recognizes the partition but does not allow me to mount it. It gives the following warning: 
"The device /dev/mapper/isw_ceebcciecc_BACKUP2 doesn't exist

Unable to find mount point
Unable to read the contents of this file system!
Because of this some operations may be unavailable.

The following list of software packages is required for ntfs file system support: ntfsprogs."

HOWEVER, if I click on manage flags, and check any of the boxes, Gparted then fully recognizes the partition and it suddenly appears in "Places" and is able to be mounted through Disk Utility, etc. I can remove the flag which was just added and the partition remains recognized.

Unfortunately, every time I reboot, I am forced to repeat this same process before I am able to mount this partition. I have not found any other way to get this partition to mount successfully. 

Does anyone have any ideas? I have spent several hours reading various threads, etc. on similar subjects and can't seem to figure this one out!

Thanks! :guitar:

---

### Post by rumbleph1sh on 2011-09-23
BUMP! :popcorn:

---

### Post by rumbleph1sh on 2011-09-24
No ideas Ubuntu experts??? :cry:

---

### Post by ligiopro on 2011-09-24
You can probably write a script that can change the flag for you and run that script on startup. This may help: [http://www.gnu.org/s/parted/manual/parted.html#set](http://www.gnu.org/s/parted/manual/parted.html#set) and some more info on GNU Parted [http://en.wikipedia.org/wiki/GNU_Parted](http://en.wikipedia.org/wiki/GNU_Parted)

A word of warning: I'm a linux noob as well.

---

### Post by rumbleph1sh on 2011-10-29
> **ligiopro said:**
> You can probably write a script that can change the flag for you and run that script on startup. This may help: [http://www.gnu.org/s/parted/manual/parted.html#set](http://www.gnu.org/s/parted/manual/parted.html#set) and some more info on GNU Parted [http://en.wikipedia.org/wiki/GNU_Parted](http://en.wikipedia.org/wiki/GNU_Parted)

A word of warning: I'm a linux noob as well.

Thanks for the reply. I was never able to find a fix for this - doesn't help that I barely know what I'm doing in linux. Any other ideas? :confused:

---

### Post by liquidspoon on 2011-11-07
I just set up a new machine with Ubuntu 11.10 and am seeing the exact same issue. Every time I reboot, my raid (5) partition goes missing. When I open gparted there is some kind of error message on the partition. However, just flipping any of the gparted flags clears the error and the drive automatically mounts.

I have been trying to replicate this action with a script to call parted, but the command line parted crashes when I try to list the drives (sudo parted -l). Has anyone found a resolution for this issue yet?

---

### Post by DrLabman on 2011-12-01
Are you using GPT partitions on the raid drive? If so I might have a solution for you:

**Test fix:**
Install kpartx (dmraid isn't supporting GPT partitions)
```
sudo apt-get install kpartx
```Next check that kpartx will add the missing partition entries in /dev/mapper. Before using kpartx in my /dev/mapper directory is only one drive file:
```
isw_cjhaidbedg_Data
```After running (This adds the partition entries for the drive entry provided):
```
sudo kpartx -a /dev/mapper/isw_cjhaidbedg_Data
```Note that this always gives me an error about running GNU Parted to correct errors on the drive, if GParted is run the errors go away but as soon as windows accesses the drive next the error is back, it doesn't seem to cause any actual problems however.

Now I have the extra files in /dev/mapper which represent the partitions on the drive:
```
isw_cjhaidbedg_Data  isw_cjhaidbedg_Data1  isw_cjhaidbedg_Data2
```Now that the partitions exist I can mount the partition in Nautilus. 

**Fix for recognised partitions at boot:**
If this worked for you then there is some more work to do to make every thing work at boot as there is a bug in the udev rules file for kpartx... The following information is from: [https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/737027](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/737027)

To get the drive to be ready for mounting after booting you will need to edit the /lib/udev/rules.d/95-kpartx.rules
```
sudo gedit /lib/udev/rules.d/95-kpartx.rules
```In this file find the line:
```
ENV{DM_STATE}=="ACTIVE", ENV{DM_UUID}=="dmraid-*", \
```And change it to:
```
ENV{DM_STATE}=="ACTIVE", ENV{DM_UUID}=="DMRAID-*", \
```Now when you boot up it should automatically find and create files for the partitions and the drive will be ready for mounting.

One thing to note when the drives are mapped at boot by kpartx they have a slightly different format to the default. In my case:
```
isw_cjhaidbedg_Data2
```Became:
```
 isw_cjhaidbedg_Data-part2
```Important for when you are adding an entry into fstab.

** Note:** If you have MBR raid drives as well create duplicate UUID's for them. As I don't have MBR raid drives I haven't been able to test this but the solution is to modify /sbin/dmraid-activate, change: ```
dmraid -i -ay -Z "$1"
``` to this:
 ```
dmraid -i -ay -p -Z "$1"
```This will stop dmraid from creating partition entries for raid drives and let kpartx do all the work.

---

### Post by liquidspoon on 2011-12-01
DrLabman:

Thank you very much for the in-depth response. I am indeed using GPT partitions. I have given up on RAID for the time being (after long sagas with dmraid and mdadm), but I am saving your message and will give it a shot if I reconfigure my machine in the future.

---

