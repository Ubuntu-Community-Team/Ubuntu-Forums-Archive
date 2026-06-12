---
title: "how to mount and umount a partition as user (not root) can it be done?"
date: 2010-01-03
forum: General Help
---

### Post by wyatt roberts on 2010-01-03
I have been working on a problem trying to automounting a LVM'd partition. That problem was solved by following instructions I was given in another (absolute beginners) forum (which I really am btw).

 I first setup a mount point

1) "sudo mkdir /media/storage
you will also have to give full write permissions to that directory. do that with this command. 
 Code: 
 2)sudo chmod 777 /media/storage 
 now we have to edit /etc/fstab"

from there the suggestion was to format as NTFS with:
3)" /dev/(something) /media/storage ntfs-3g ro,user,auto,fmask=0177,dmask=0077,uid=1000 0   0"

But the drive, and that partition,  was partitioned as ext3 and I want to do it as ext3 for now...


 I have fstab setup like:
***********************
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/VolumeGroup1-root /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=90615dd1-c985-46d6-a441-de6d6a058e90 /boot           ext3    defaults        0       2
/dev/mapper/VolumeGroup1-home /home           ext3    defaults        0       2
/dev/mapper/VolumeGroup1-swap none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[COLOR=Red]/dev/mapper/VolumeGroup1-data4 /media/storage ext3    defaults        0        0[/COLOR]

**********************

I tried "user,auto,fmask=0177,dmask=0077,uid=1000" with and with out the rw but couldn't get it to work... these options yielded an error message, failed to mount the drive and what is listed above works to auto mount it, giving me read and write permission to the partition [COLOR=Red]VolumeGroup1-data4[/COLOR] .

SO....

This is CLOSE...  I am automounting it, like when I plugin a usb key, BUT unlike the usbkey, I can't umount it with the GUI.  The auto mount is done with fstab and at root level, necessitating "sudo umount [COLOR=Red]/dev/mapper/VolumeGroup1 [COLOR=Black]which is a lot to remember and type each time I want to unmount the partition.[/COLOR][/COLOR]

How can I unmount the drive like I do an external USB drive? I suppose a script would do it, but there must be a more elegant way... I wanted to have read/write permission in the automounted drive and have it, just like the USBkey... I can write to the drive and delete from the drive...

Thanks,
wyatt

---

### Post by rnerwein on 2010-01-03
hi
open a terminal and type: mount -a
the the system will give you a answer to your question
cia

---

### Post by wyatt roberts on 2010-01-03
> **rnerwein said:**
> hi
open a terminal and type: mount -a
the the system will give you a answer to your question
cia

Ok... That sounds pretty conclusive... thanks,
wyatt

---

### Post by wyatt roberts on 2010-01-03
I just clicked on my usbkey icon on the desktop and chose "Safely Remove Drive" and it umounted the drive and never asked me for a password...  It's a drive, like usb drives, that is partitioned and the partition is mounted when I plug it in,,,

I suppose there is a way it does that but it is listed on the desktop pulldown list in the same list of "removable media" that lists the partition I want to mount as a user:  Places > Removable Media > data4...

So, if you have to be root to mount a drive how does my USBkey get mounted as a user accessible drive and get unmounted by the GUI ...  Could I lie to the system and "emulate" the usbkey, however it does it?

Thanks,
wyatt

---

### Post by wyatt roberts on 2010-01-03
> **wyatt roberts said:**
> I just clicked on my usbkey icon on the desktop and chose &quot;Safely Remove Drive&quot; and it umounted the drive and never asked me for a password...  It's a drive, like usb drives, that is partitioned and the partition is mounted when I plug it in,,,

I suppose there is a way it does that but it is listed on the desktop pulldown list in the same list of &quot;removable media&quot; that lists the partition I want to mount as a user:  Places > Removable Media > data4...

So, if you have to be root to mount a drive how does my USBkey get mounted as a user accessible drive and get unmounted by the GUI ...  Could I lie to the system and &quot;emulate&quot; the usbkey, however it does it?

Thanks,
wyatt

Well... I am reporting back to say that the problem is solved.  I don't know what step I missed so I cannot accurately say what led me down this blind alley.  I restarted and my external eSata drive was not automounted.  I scratched my head and found it listed in Places > Removable Media > MyBook.  It mounted with a click.  So I unmounted and it did.  I tried one more thing and commented out the line in fstab that mounted my partition that somehow required mounting as root earlier.  I restarted.  I was able to mount it with a click from Places > Removable Media > data4... I umounted it with a click.  I am removing the line from fstab.  Postmortem.  I suspect I made one of the changes painfully documented in this post and DIDN'T reboot so it never changed behavior. Anyway, Problem solved.  Thanks all.   Wyatt   I will marked this solved once I find out how

---

