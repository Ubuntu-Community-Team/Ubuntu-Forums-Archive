---
title: "Error mounting hard disk."
date: 2010-05-08
forum: General Help
---

### Post by daniel-strae on 2010-05-08
Hi guys, i have a little problem outta here with ubuntu lucid lynx.

My computer have 3 sata hard disks:

1. 160Gb, where i installed ubuntu
2. 320Gb, where i keep music and photos
3. 500Gb, where i keep movies and other stuff

My problem is that ubuntu, once installed, cant mount the 3° hd, the one of 500Gb.
On boot, as soon as i reach the login window, i notice that the led 'disk in use' on my case become allways enlighten, untill i shut down the sistem (and it took about 30 minutes to switch off, with the purple window with ubuntu logo and 5 white/orange dots. i think its not normal..).

Seems like ubuntu try to do *something* with the disk as soon as it boot, but it goes in a loop or something like, keeping the disk busy.
But i dont know what process do that, and if by killing it will cause some problems or damage the hd.

If i try to mount it, i got this error:

> 
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending
After some time, this other error pop-up while im using the pc:
> 
Error mounting: mount exited with exit code 13: Error reading bootsector: Input/output error
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
I never used RAID on that disk, and onthis computer i have completely removed windows xp one month ago (that was installed on the 500Gb disk, but i completely formatted it).

Another strange things is that if i boot from a live cd of linux mint (didnt try with ubuntu live cd, but i guess is the same), it works: i can mount the disk and i can see all its content and use it.

Happen the same if i put the disk on a usb external doc.

The problem comes just with ubuntu and the disk linket throught SATA inside the pc.
I dont know what to do, this is strange becose ubuntu can mount and work ok with the other disk (the one of 320Gb) whitout problems!

What can i do?

---

### Post by dino99 on 2010-05-08
force a fsck on next reboot:

sudo shutdown -F -r now

an easy tool to deal with devices and partitions is MountManager, install it with synaptic and tweak it as you need

in case of troubles its nice to have a partedmagic cd or usb on which you can boot and repair things

---

### Post by bumanie on 2010-05-08
Looks like a filesystem error on the ntfs filesystem on that drive - as it says, do a chkdsk with /f switch to fix errors. This needs to be done in windows, either by booting off an install disk and going into console mode and using syntax chkdsk <drive letter>: /f (make sure you put the colon after the drive letter). Alternatively, go to run and type cmd in the window and then insert the above code, it will do the filesystem check and fix next time windows is booted. Windows chkdsk is best for fixing ntfs.

---

### Post by daniel-strae on 2010-05-08
> **dino99 said:**
> force a fsck on next reboot:

sudo shutdown -F -r now

an easy tool to deal with devices and partitions is MountManager, install it with synaptic and tweak it as you need

in case of troubles its nice to have a partedmagic cd or usb on which you can boot and repair things

Thanks, i'll give a try

---

### Post by daniel-strae on 2010-05-08
> **bumanie said:**
> Looks like a filesystem error on the ntfs filesystem on that drive - as it says, do a chkdsk with /f switch to fix errors. This needs to be done in windows, either by booting off an install disk and going into console mode and using syntax chkdsk <drive letter>: /f (make sure you put the colon after the drive letter). Alternatively, go to run and type cmd in the window and then insert the above code, it will do the filesystem check and fix next time windows is booted. Windows chkdsk is best for fixing ntfs.

Ehm... i cant boot windows.. i completely removed it.. it was installed on that same (500GB) drive, that has been formatted and now should work just as an archive..

I throwed the xp cd outta the window last week:lolflag:

---

### Post by bumanie on 2010-05-08
Yes, but is the 3rd drive formatted to ntfs? If so, the only way to fix it is with windows - fsck cannot fix ntfs filesystems at this point in time as far as I know - ntfsprogs can clean the journaling part of ntfs, but not the filesystem itself - you need chkdsk. If you can get the data off on to an external hard drive, you could reformat the drive to ext3/4 and then put the data back on - that might work if the files are not corrupted. 
Surely you know one person that could lend you a xp disc to do chkdsk with.

---

### Post by daniel-strae on 2010-05-08
> **bumanie said:**
> Yes, but is the 3rd drive formatted to ntfs? If so, the only way to fix it is with windows - fsck cannot fix ntfs filesystems at this point in time as far as I know - ntfsprogs can clean the journaling part of ntfs, but not the filesystem itself - you need chkdsk. If you can get the data off on to an external hard drive, you could reformat the drive to ext3/4 and then put the data back on - that might work if the files are not corrupted. 
Surely you know one person that could lend you a xp disc to do chkdsk with.


Yes, it is ntfs and i'll love to keep it as ntfs, so i can lend it at my friends that use windows.. ntfs can be read by all platform, right?

Anyway, now i've tryed the dino99 way, hoping it works (the pc is now freezed in the shutdown window, ubuntu logo, purple background and 5 dots).

If it fails, i'll try chkdsk putting the disk on a usb external dock on my notebook (doal boot karmic and win7).

Thanks for the help, i'll back  with the result!

p.s: im a bit curious, why the hd works if i boot the pc with a live cd, or in a usb external dock?

---

### Post by daniel-strae on 2010-05-08
...and it works!
I putted the hd into my usb external dock, then linked to my notebook, booted seven, i did 3 times chkdsk, the rebuild the hd into my desktop, but still got the problem, so `sudo shutdown -F -r now`

The reboot took several minutes, but now it works.


thanks guys!):P

---

### Post by daniel-strae on 2010-05-09
](*,)
Damn, now it seem broken again..
After 2-3 boot and shutdown of ubuntu, here i am again with the led enlighten and the HD unacessible!

This time, i got this error:

```

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

Have i to do it all again (put it into a usb dock, boot windows on notebook, chkdsk, remount it into my pc, sudo shutdown -F -r now) ?

Its the disk that is broken, and soon or later will fail, or is ubuntu that do something wrong?
What can the problem be?

---

