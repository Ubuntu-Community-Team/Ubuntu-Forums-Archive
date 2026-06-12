---
title: "Access hard disk files from ubuntu Live CD"
date: 2010-05-08
forum: General Help
---

### Post by marmotapl on 2010-05-08
Hi, i'm having some problems booting ubuntu 9.10 and i just want to backup my files and install it all over again.

I want to access my old files from the ubuntu Live CD, because no kernel is working.

Is there a way?. Just in case, i don't have partitions, so i don't have a 'home' one (but i'm going to).

Thanks in advance =)

---

### Post by quadproc on 2010-05-08
> **marmotapl said:**
> Hi, i'm having some problems booting ubuntu 9.10 and i just want to backup my files and install it all over again.

I want to access my old files from the ubuntu Live CD, because no kernel is working.

Is there a way?. Just in case, i don't have partitions, so i don't have a 'home' one (but i'm going to).

Thanks in advance =)
If I understand correctly, you have some other device available to use for backup, perhaps a USB flash drive?  If so, then yes, it should be straightforward.  I am also assuming that you plan to reinstall some version of linux on the same machine after the files are copied.

After booting from the live CD, figure out the device identifier where your files are located.  It may be useful to use gparted for this; it shows you the device IDs in the little space at top right where you can select which drive.  Don't do anything with gparted other than to look at the identifiers.  Please be advised that those identifiers can change between boots so be sure to get current information.

Create a temporary directory to use for recovery; I will call it /tempmount.

Once you know the identifier then you can mount your just-identified filesystem.  For example, assume that your files are on sda1 then sudo mount -t [COLOR=Red]ext3[/COLOR] /dev/[COLOR=Red]sda1[/COLOR] /tempmount (substitute your actual identifiers for the red entries).  Use a similar process to mount the device where you wish to place the recovered files if it is a different partition or device.

Then you can copy all of the files from /tempmount to your destination.  I have used cp -a for this purpose but it doesn't do well with things like hard links so you may want to use a different technique, probably with tar or cpio and pipes.

Once the copy has finished then umount both devices.  You can rmdir the /tempmount directory.  And it is done.

quadproc

---

### Post by marmotapl on 2010-05-08
I was able to mount both of the drives and see the files using gksudo nautilus... but i can't move files from /tempmount to my external HDD which is mounted too in /media/APOLLO .

How do I get permission to move these files?

Thank you.

---

### Post by quadproc on 2010-05-08
> **marmotapl said:**
> I was able to mount both of the drives and see the files using gksudo nautilus... but i can't move files from /tempmount to my external HDD which is mounted too in /media/APOLLO .

How do I get permission to move these files?

Thank you.
Interesting.  If I understand correctly, you are using a Live CD to run the system.  If you did not change the user then you will be root.  Try putting sudo before the cp command.  There also might be a permissions issue; a chmod 777 on the directory might be required.

quadproc

---

### Post by marmotapl on 2010-05-08
Thank you very much quadproc. Problem solved ;)

---

### Post by quadproc on 2010-05-08
:smile:Excellent!  Glad that you were able to keep the data.

quadproc

---

