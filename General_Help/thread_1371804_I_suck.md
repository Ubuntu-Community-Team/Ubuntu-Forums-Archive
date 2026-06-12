---
title: "I suck"
date: 2010-01-03
forum: General Help
---

### Post by NicelyMKV on 2010-01-03
Since I can never leave anything working alone...I altered my swap partition. Now but I can not boot up. Using the live usb I can get to all my files and look at them, but I can not copy them over to my storage partition(where they should be in the 1st place). It keeps saying I do not have permission. I even tried reconfiguring my now wrong UUID of my swap partition to the right one with etc/fstb(<--- may be wrong but had it right) and it would not change it.

I have been searching for 2 days and can not figure it out. I do not mind reinstalling my OS at all but I really hate to lose my evolution and firefox settings. I normally back them up but made alot of changes recently without a current backup of each.

Thank you for the help,
Jason

---

### Post by Leppie on 2010-01-03
if you are booting with the livecd, i think you have read-only access to your ubuntu system. unmount the root partition with the umount command and then mount in read/write mode. you will then be able to modify and save your /etc/fstab.

---

### Post by NicelyMKV on 2010-01-03
Thank you Leppie. I think I forgot to mention I am still new to linux. I would need pretty detailed instructions. Sorry about that.

Thanks again,
Jason

---

### Post by Leppie on 2010-01-03
i'll try something.
firs of all, could you post the output of the following command:
```
$sudo blkid
```
NOTE: the leading $ sign merely represents your prompt, it's not part of a command (you will see this more often in forums).
NOTE2: you can use copy and paste with the terminal as well.

---

### Post by danastasio on 2010-01-03
> Since I can never leave anything working alone

That doesn't mean that you suck, just that you should never EVER try Arch Linux. Or that you should become a programmer and should totally go for it. :P

to mount the filesystem as read-only, boot into your liveCD and in a terminal run

```
mount -u -o ro -f /
```

then, run

```
sudo nano /etc/fstab
```

to edit your /etc/fstab so that you can change your UUID to the correct input.

---

### Post by NicelyMKV on 2010-01-03
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="962A0AC82A0AA579" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="463001DB3001D33B" LABEL="ACER" TYPE="ntfs" 
/dev/sda5: LABEL="Ultimate Edition" UUID="8c58b746-167f-45e9-9bfc-99b238fbcb38" TYPE="ext4" 
/dev/sda6: UUID="6BD916293D69B047" LABEL="Storage" TYPE="ntfs" 
/dev/sda7: UUID="338a3bb2-a21c-4fb5-a27e-1c10071c7f4e" TYPE="swap" 
/dev/sdb: UUID="08D1-386F" TYPE="vfat"

---

### Post by Leppie on 2010-01-03
to unmount your actual system:
```
$sudo umount /dev/sda5
```

mount it in read/write mode:
```
$sudo mont -t ext4 /dev/sda5 /mnt
```

to open your fstab in an editor:
```
$gksudo gedit /mnt/etc/fstab
```

change the uuid of your swap, save the file and reboot.
let me know if it worked.

---

### Post by NicelyMKV on 2010-01-03
fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=8c58b746-167f-45e9-9bfc-99b238fbcb38 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=14c93fb0-a27c-455d-9c2f-21fce00b11fd none            swap    sw              0       0

That is the right UUID beside the swap but when I open Gparted and right click the swap file and click info it shows the wrong UUID.
My swap partition is sda7?

I can not find my Ubuntu partition now to open it and try to copy it. I am just going under places on the top right menu. It is not showing up now.

Thanks,
Jason

---

### Post by NicelyMKV on 2010-01-03
Thanks for the reply danastasio. I did what you said and this is what I got.

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0


I am n ot sure where to change the UUID here?

---

### Post by pastalavista on 2010-01-03
I've found the easiest way to fix a borked Ubuntu setup is to do a full reinstall, in MANUAL mode and UNCHECK all the format boxes for the Ubuntu drive mountpoints. This will reinstall all the system files fresh, so you'll need to update everything again, but no customized files will be overwritten or erased...

---

### Post by NicelyMKV on 2010-01-04
Thanks pastalavista! I will give it a shot and let you know how it turns out.

---

### Post by jamesisin on 2010-01-04
I think you have made a mistake.  You posted the output from blkid including:

/dev/sda7: UUID="338a3bb2-a21c-4fb5-a27e-1c10071c7f4e" TYPE="swap"

And then you state:

"
# swap was on /dev/sda6 during installation
UUID=14c93fb0-a27c-455d-9c2f-21fce00b11fd none swap sw 0 0

That is the right UUID beside the swap
"

Those are not the same UUID.  Can you explain this?

---

### Post by NicelyMKV on 2010-01-05
pastalavista, I reinstalled as you said and it booted up with my original settings in place! The problem now is my mouse pad will not work. I even plugged in a wireless mouse and it will not move the cursor either?? Strange huh? Never had that problem before and I dual boot with Win 7 and it works fine.

jamesisin, I am still a newb so I may have made a mistake. The original swap UUID that I was trying to get back to was 14c93fb0-a27c-455d-9c2f-21fce00b11fd . When I adjusted my swap out of ignorance it changed to 338a3bb2-a21c-4fb5-a27e-1c10071c7f4e.
I went into the fstab and changed it to 14c93fb0-a27c-455d-9c2f-21fce00b11fd which is what I wanted. When I checked the partition info in Gparted it was still 338a3bb2-a21c-4fb5-a27e-1c10071c7f4e. So my change in fstab did not stick apparently.

---

### Post by Leppie on 2010-01-05
i think that list refreshes with this command:
```
$sudo service udev restart
```

---

### Post by jamesisin on 2010-01-05
Glad to see you have things on a better track.

You might try hot-plugging your mouse a couple of times to see if you can get Ubuntu to react to it.

---

### Post by NicelyMKV on 2010-01-07
I finally got the usb mouse to work so I backed up everything and am back in business. I was going to repartition and reinstall my win 7 to make more room for my Ubuntu anyway. I tried shrinking the win partition but there were some unmovable files so it set it at 170 Gigs of space. I appreciate all the help!

Thanks,
Jason

---

