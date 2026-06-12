---
title: "Mounting of eSATA drive"
date: 2010-02-26
forum: General Help
---

### Post by Infil on 2010-02-26
First and foremost: I have searched the forum here and have not found answers to these questions.

I have an external hard drive (a normal hard drive in separate housing connected to the eSATA if it matters) and I have two partitions. One of the ext4, and an on NTFS. The ext4 partition I am interested in mounting.

If I normally add it in /etc/fstab with umask and fmask and all that:

1) If I put other permissions (eg. +x) to a file on the external drive, will they be reset at the next reboot?

2) When the disk is not connected (eg. when I'm on the go), will the system produce error messages?

3) Can I do something so that the disk is still listed in the sidebar in Nautilus, and it still gets an icon on the desktop?

Alternatively, I have seen that it is possible to set up rules in HAL. Should I do it instead? How do I do it in that case?

Initially, I wouldn't have to do anything, but for some reason I don't get write access to the disk when the system mounts it automatically. Thanks for any help.

---

### Post by MS-Hater on 2010-02-27
Frankly, I very highly doubt that it matters that the hard drive interfaces with the computer via eSATA; more than likely the system treats it like a USB drive. That said, the answer to #3 is: not without inducing a bug that existed in an older version of GNOME (I believe it was Fiesty Fawn that had that bug, but I'm not sure: I remember you had to leave the computer on for over 2 weeks, and launch ONLY specific programs in order to induce it). As far as #1, I think that it should port over the permissions you set. #2, I have no idea what you mean... Obviously you'l get error messages if a program expects that drive to be there (like if you set Cron to move a file to it at a specific time) when it's not. This is pretty much where my knowledge ends, so I'll let others who know more about this make their comment(s) while I go pour my next cup of coffee from the percolator.

---

### Post by rnerwein on 2010-02-27
> **Infil said:**
> First and foremost: I have searched the forum here and have not found answers to these questions.

I have an external hard drive (a normal hard drive in separate housing connected to the eSATA if it matters) and I have two partitions. One of the ext4, and an on NTFS. The ext4 partition I am interested in mounting.

If I normally add it in /etc/fstab with umask and fmask and all that:

1) If I put other permissions (eg. +x) to a file on the external drive, will they be reset at the next reboot?

2) When the disk is not connected (eg. when I'm on the go), will the system produce error messages?

3) Can I do something so that the disk is still listed in the sidebar in Nautilus, and it still gets an icon on the desktop?

Alternatively, I have seen that it is possible to set up rules in HAL. Should I do it instead? How do I do it in that case?

Initially, I wouldn't have to do anything, but for some reason I don't get write access to the disk when the system mounts it automatically. Thanks for any help.

1. the permissions will stay there. but if you mount the drive with the option -o nexec
    ( sometimes very useful for externals you pluged in into other boxes :-)  )
2. in my fstab i use the option "noauto" and if no other program want to access it - nothing will produce error messages.
3. i don't know. my icons are only shown up when i mount it. and by the side. eSATA must no always handled as an usb-drive. mine is connected via scsi ( Attached scsi generic sg4 type 0 ) on a scsi not usb connector ( much faster ).
if you want to get only some times write access to the disk use automount -o ro and when you want to write to the disk use: mount -o remount,rw

ciao

---

### Post by Infil on 2010-02-28
So I can add the options I want in fstab, specify noauto, and then it will be mounted as before  with an icon on the desktop when I say so? That would be great because that's exactly what I want.

I notice when I mount it by clicking on te entry in the Places-menu and look at the details of the permissions it needs, Devicekit is the one responsible. Is there any way to configure how Devicekit does that? Maybe that's the thing I'm looking for, since it appears Devicekit now does the job instead of HAL.

---

### Post by DawieS on 2010-03-01
Hi Infil

You didn't mention which version of Ubuntu you are using.

If you are using Ubuntu 9.10 (Karmic), the handling of disks is completely different from previous versions. All disks are seen as internal, except USB disks. During installation, it is best if all external disks are switched off (unless you are installing Karmic onto one of them, of course).

After installation, the /etc/fstab file will then contain only lines for the boot/install disks and CD/DVD ROM. If an external drive is switched on, it will appear (unmounted) in the file browser. It will disappear again if switched off, and may re-appear again later if switched on. A mount point will only be created once clicked on the drive. It may be unmounted by clicking on the up-arrow next to the name of the drive.

You can change the default disk behaviour of Karmic by editing the following file using the 'sudo gedit' command in a terminal:

/usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

To be able to mount without authorization, look for the following header:

  <action id="org.freedesktop.devicekit.disks.filesystem-mount-system-internal">

under that will be something like this:

<defaults>
    <allow_any>no</allow_any>
    <allow_inactive>no</allow_inactive>
    <allow_active>[COLOR=Red]auth_admin_keep[/COLOR]</allow_active>
</defaults>

change the highlighted one to:

    <allow_active>[COLOR=Red]yes[/COLOR]</allow_active>

Save, exit and reboot. You should now be able to auto-mount your NTFS drives.

Notes:
 - These changes may be overwritten by an upgrade and may require re-doing.
 - It is best not to have any external drives listed in the /etc/fstab file, especially if they contain NTFS file-systems. Listing them may result in drives appearing doubled up in the file browser, cross-mounting to wrong drives, unable to unmount without reboot, etc.

---

### Post by Infil on 2010-03-08
Thanks for your answer.

I am indeed running 9.10. As I wrote above the partition I am interested in mounting is an ext4-partition.

I tried your advice and it worked perfectly. I can now mount my external hard drive without much hassle. However, all files and directories are still owned by root, and all files and directories have permissions 755. 

I would very much like to delete a bad pictures without having to run "gksudo nautilus" or to double click my grocery list without having to say that I don't want to run it even though it is an executable :p

I looked through the file you gave me, and other files I could find but I didn't see any mention of permissions. The only place I know I can change them are in fstab :neutral:

---

### Post by DawieS on 2010-03-08
> **Infil said:**
> I would very much like to delete a bad pictures without having to run "gksudo nautilus" ...
OK, for the last time run "gksudo nautilus". Click on the drive to mount it, and the drive will appear mounted in a tab on top. Right-click on this tab, and select "**Properties**", and then "**Permissions**". Select yourself to be the owner, with "Create and delete files" at "Folder access".

Select "Group" to be "users" and "Access Files" at "Folder access".

Select "Access files" at "Folder access" for "Others" (Unless you want to prevent other users from listing and reading files on this drive).

Select "---" at "File access" in all three instances.

Click on the "**Apply Permissions to Enclosed Files**" tab. Close the window and exit nautilus. You should now be able to create and delete files on this drive the next time you open a file browser.

> **Infil said:**
> ... or to double click my grocery list without having to say that I don't want to run it even though it is an executable :p

Open a file browser. Click on the "**Edit - Preferences - Behavior**" tabs. At "**Executable Text Files**" select "**View executable text files when they are opened**". Close the window.

It will now open a text file with your default text editor when you double-click on the file.

---

### Post by em3raldxiii on 2010-05-10
I just figured I would contribute to this thread because I was getting frustrated that I could not mount my eSATA drive.  I did get mine working.  Here is an outline:

2TB Western Digital internal drive.
NexStar eSATA drive enclosure.
MSI GT735 Laptop with eSata port on the right side.

Correctly assembled the enclosure, connected power, and connected eSATA.

Powered up the drive.  Nothing happened.

I read a forum and one little note was about the plastic plug housing being too large for someone else's setup.  Grabbed a utility knife and carefully shaved back the plastic on the top and bottom of the eSATA plug to make it slightly lower profile.

Plugged it in, and it gParted could now see and prepare the drive!!  <--- At this point I almost called it a done deal.

I formatted as ntfs to retain Windows compatibility (this was going to be a handy back-up drive for myself and my clients & friends), and it took almost no time at all with gParted.  Once I tried transferring files, I began getting I/O errors both on reads and long writes.  I figured something was wrong with the partitioning.

I tried repartitioning as EXT4 and it failed.  Also a number of times I lost any ability to even see the drive at all -- not sure if it was loose cables, or if there was something else at work.  After rebooting and starting again, gParted could again see the drive.

I formatted the entire drive as one primary ext3 partition.  This worked.  And it continues to work.  I posted on the gParted development forums about it.  Their reply was that they suspect something is wrong with the drive.  I tend to disagree based on my own experience with many failed drives (and the subsequent data rescue efforts).  This drive is new, and not a dud.  It just didn't play nice with ntfs or ext4 for some unknown reason.

Finally, I had to use DawieS's trick in post #5 allow non-administrative access to the drive.

I hope this helps at least one or two other people out there who experienced similar issues.

---

