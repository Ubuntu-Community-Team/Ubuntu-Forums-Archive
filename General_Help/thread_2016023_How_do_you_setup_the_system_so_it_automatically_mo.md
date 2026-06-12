---
title: "How do you setup the system so it automatically mounts a drive at startup?"
date: 2012-07-04
forum: General Help
---

### Post by Randy Schilling on 2012-07-04
Hello -
I have a dual boot system with Ubuntu on one hard drive a Windows on another.
The command to mount my Windows drive is this:
                          sudo mount -t ntfs /dev/sdb2 /media/Windows
where the directory /media/Windows is already created
I would like to setup my system so that the drive is mounted 
automatically upon system startup.
I tried putting the command (without sudo) in my /etc/profile and 
rebooting, but that didn't seem to work.  (Wish I understood why not.)
What do I have to do to make this work?

Thanks, we're very fortunate to have this forum. - Randy

---

### Post by HermanAB on 2012-07-04
Add it to /etc/fstab

Do yourself a favour and read the fstab man page before you edit it.

---

### Post by dcstar on 2012-07-04
> **Randy Schilling said:**
> Hello -
I have a dual boot system with Ubuntu on one hard drive a Windows on another.
The command to mount my Windows drive is this:
                          sudo mount -t ntfs /dev/sdb2 **/media/Windows**
where the directory /media/Windows is already created
..........

Do **not** ever use /media for direct mounts. /media is a system folder for dynamic mounting.

Create a mount point under /mnt. Do a search for the multitude of posts that explain all of the steps.

---

### Post by mainmeister on 2012-07-04
try looking in the /etc/mtab file. This is where commands to mount devices are found when the system boots up

---

### Post by Randy Schilling on 2012-07-04
dcstar:

The drive can be mounted using nautilus.  When I open nautilus, "1 TB Filesystem" is listed under Places.  Clicking this item mounts the drive and the drive is located in /media/8A467EB6467EA29D.
This is why I chose /media when manually mounting the drive.  I will use /mnt from now on.

Could you please guide me a good reference, among the multitude, for mounting a drive?

Thanks

---

### Post by Randy Schilling on 2012-07-04
mainmeister:

Yes, when I mount my drive manually, it is added to the mtab list and when I umount it, that listing is removed.   

The problem is getting the system to mount the drive automatically at startup.  Are you saying that that this is done by adding an entry directly to the mtab file?

---

### Post by dino99 on 2012-07-04
The basic functionalities of MountManager are:
  - Mount and unmount partitions (ext3/2, ntfs, swap, fat, reiserfs, iso9660,
  udf, ...)
 - Show all logical and physical disks
 - Change config file /etc/fstab
 - Descriptions of options and other settings of mounting
 - Restoration system
 - Images mounting and unmounting (Nrg, Mdf , Ccd, Bin , etc)
 - Udev rules creation
 - Disk wizard
 - Etc...

):P

---

### Post by Randy Schilling on 2012-07-04
HermanAB:

fstab manual is very technical.  Could you please provide instruction that is less demanding?  Why would I edit fstab to mount a drive?

---

### Post by timgood on 2012-07-04
```
sudo apt-get install mountmanager
```

Then run mountmanager and configure your drive. Easy.

---

### Post by timgood on 2012-07-04
Even easier:

```
sudo apt-get install pysdm
```

Then:

```
sudo pysdm
```

---

### Post by Randy Schilling on 2012-07-04
I can mount the drive manually with a command from bash.
I can mount it manually from nautilus too.
What I want to do is have the drive mounted automatically at system startup,
I don't want to to it manually every time I use my Ubuntu system

Can Mount Manager be used to setup this automatic mount or is it just another tool 
for manually mounting a drive?

---

### Post by flemur13013 on 2012-07-04
> What I want to do is have the drive mounted automatically at system startup,It's pretty easy.

Make a directory (e.g. /yourmountpoint) wherever you want it; make yourself the owner, and make it read/write-able as you desire.

Add a line like this to you /etc/fstab file: 
**UUID=whatever  /yourmountpoint   ntfs-3g defaults  0 0**

Look up the UUID with gparted or palimpsest (a LONG number).  
OR use LABEL=whatever instead of UUID (this might be the easies way)
OR use /dev/sdwhatever  (probably the above two options are better).

Here's a line from my own fstab:
**LABEL=DATA   /data   ext4   defaults 0 0**
When the partition was NTFS, the only diff was "ntfs-eg" rather than "ext4".  The "DATA" partition is mounted on directory /data after boot.

It's really nice to LABEL the partitions...you can do it in Windows or with gparted or palimpsest. They have to be unmounted first, which you can do there.

Then the NTFS file system will be mounted to /yourmoutpoint after you boot.

Edit: some people say UUID is preferable to LABEL, but either one can cause trouble since you can have two partitions with the same LABEL or with the same UUID - it's less likely with UUID unless you've been copying partitions with "dd" or something.

---

### Post by Randy Schilling on 2012-07-04
Let me ask the question another way.

I created a directory /mnt/Windows.
I added the following command to my /etc/profile file:
                       mount -t ntfs /dev/sdb2 /mnt/Windows
I rebooted.  I expected to see all my Windows folders in /mnt/Windows.
This attempt to have my system mount my Windows drive at system startup fails.
I'd like to know why, but better, I'd like to know what I should have done.

If this can be done from Mount Manager then please give details and please try to keep in mind that I'm not nearly as technically skilled as any of you.

Thanks and many kind regards - Randy

---

### Post by Randy Schilling on 2012-07-04
OK flemur.  I saw your post AFTER submitting the previous post.
I'm working on your instructions now.  I'll get back to you shortly.
Thanks thanks thanks!

---

### Post by flemur13013 on 2012-07-04
Your fstab line is completely WRONG - you don't put the mount command there, you're just passing parameters.

**mount -t ntfs /dev/sdb2 /mnt/Windows** - WRONG!

The line in /etc/fstab should be something like (I'm assuming you labeled the partition "WINDOWS"):

**LABEL=WINDOWS /mnt/Windows   **[B]  ntfs-3g defaults  0 0

[/B]This won't work unless you've given the partition a label.

Edit: you'll need the "ntfs-3g" package installed; it **should be** installed by default, but if you have problems and it complains about not knowing what "ntfs-3g" means:

$ sudo apt-get install ntfs-3g

Edit 2:
**/dev/sdb2 /mnt/Windows   ****  ntfs-3g defaults  0 0**
should also work (if sdb2 is correct - sometimes these change as you (dis)connect disks, hence using the LABEL or UUID).

---

### Post by Randy Schilling on 2012-07-04
Ok flemur, the instructions of your first post worked just fine.

I installed gparted and found the UUID of /dev/sdb2.
I added the following command to /etc/fstab
UUID=8A467EB6467EA29D /mnt/Windows ntfs-3g defaults 0 0
I redefined some environment variables of my system, directing them to /mnt/Window.
(ntfs-3g was already installed)

Everything is working just fine.   Thanks, thanks and thanks again.
Many kind regards - Randy

---

### Post by Randy Schilling on 2012-07-04
Yes - I unmounted the drive then labeled it.  It was previously unlabeled.

---

### Post by garyed on 2012-07-04
> **dcstar said:**
> Do **not** ever use /media for direct mounts. /media is a system folder for dynamic mounting.

..........
I never heard that before.  Can you explain how this could cause a problem?

---

### Post by Morbius1 on 2012-07-04
> **garyed said:**
> I never heard that before.  Can you explain how this could cause a problem?
It doesn't.

Strict UNIX file hierarchy stated that:

/media = Mount points for removable media such as CD-ROMS, USB, etc..
/mnt = Temporarily mounted filesystems

By those definitions you shouldn't be mounting anything other than the OS itself. You could mount it to your own home directory which would be kind of awkward in a multi-user setup. Or you could mount it off / directly which would give old UNIX system administrators a cerebral hemorrhage.

There is one possibility that could cause a little confusion. Let's say you have a USB storage device labeled "Storage". You also have an internal partition that you mount in fstab to /media/Storage. When that USB device is turned on it is designed to mount to /media/"LABEL-NAME" which in this example would be /media/Storage but there already is a /media/Storage. Roh - Roh. Linux handles this by having the USB device automatically mount to /media/Storage_ ( note the underscore ).

---

### Post by Paqman on 2012-07-04
> **garyed said:**
> I never heard that before.  Can you explain how this could cause a problem?

It doesn't cause a problem, but it does behave differently. It'll show up on your desktop, which may or may not be what you want.

The mount point doesn't have to be under /mnt either. There's nothing stopping you from creating /banana and mounting stuff there.

---

### Post by garyed on 2012-07-04
So the only real difference is if you mount through fstab in 
/media/whatever it will show up on the desktop & it won't if its mounted through fstab in any other directory.

---

### Post by Paqman on 2012-07-05
Yep.

---

