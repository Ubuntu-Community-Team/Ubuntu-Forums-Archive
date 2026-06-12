---
title: "How do I auto start a multi-disk drive?"
date: 2009-10-25
forum: General Help
---

### Post by kamil212 on 2009-10-25
I just created a RAID0 array using Palimpsest Disk Utility in 9.10. 
It creates the /dev/md0 device and I can mount it to /media/Speedo
but on reboot it disappears. 
I added this to fsatb:
dev/md0	/media/Speedo	ext4	defaults	1	2
but it fails on boot up since it can't find dev/md0
I can see it in the File Browser - Computer:
> CD/DVD Drive
Floopy Drive
RAID
Filesystem
I can right click RAID and "Start Multi-disk Drive"
This adds the dev/md0 device and now I can mount it. 

So, how can I auto-start this raid device?
Thanks

---

### Post by abyrne on 2009-10-25
This is a total shot in the dark here but...

I'm pretty sure it should be
```
/dev/md0
```
not
```
dev/md0
```

---

### Post by kamil212 on 2009-10-25
thats my bad, a typo, it was /dev/md0

The thing is that /dev/md0 doesnt exist on boot up, only after I start the multi-disk drive in the file browser.

---

### Post by kamil212 on 2009-10-25
bump....


...anybody?

---

### Post by kamil212 on 2009-10-26
bumpity

---

### Post by alphaniner on 2009-10-26
I don't know anything about Palimpsest.  It may be that a process or daemon is not started by default.  

One way to find out (though probably not the best way) is to run **ps -e** before and after doing your thing through the GUI.  See if any new processes appear.

Also, have you thoroughly read through the documentation?  If something needs to be done to make the device show up automatically, I suspect it would be mentioned there.

---

### Post by kamil212 on 2009-10-26
fdisk before:
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d3e32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14593   117218241   fd  Linux raid autodetect

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00020b28

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38163   306544266   83  Linux
/dev/sdc2           38164       38913     6024375    5  Extended
/dev/sdc5           38164       38913     6024343+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf763d03c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   fd  Linux raid autodetect

fdisk after:
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d3e32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14593   117218241   fd  Linux raid autodetect

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00020b28

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38163   306544266   83  Linux
/dev/sdc2           38164       38913     6024375    5  Extended
/dev/sdc5           38164       38913     6024343+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf763d03c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   fd  Linux raid autodetect

Disk /dev/md0: 240.1 GB, 240062824448 bytes
2 heads, 4 sectors/track, 58609088 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table


using ps -e before and after the raid start I only see this to be new:
"udevd"

---

### Post by Rune Hagen on 2009-11-02
Having the same issue/question here.
In my home server setup I have a four disc raid 5 setup for media.
all of the are set as 'Linux RAID autodetect (0xfd)'.
I have to start it manually via 'disk utility'.

Not so familiar with these things :(

---

### Post by jamesisin on 2009-11-16
Same issue here. I have just built a new server for music and wish to mirror the collection.

Useless if I have to log in and first start the array and then mount the partition each time.

Can someone please chime in on this one?

Palimpsest is not very intuitive (though I feel pretty good about making it this far) and GParted seems to have been abandoned.

---

### Post by Rune Hagen on 2009-11-17
I have it working now, but I am very sorry I sent back the raid controller I had on order, because... my oh my :)

First of all, you have to make the raid during install (manual partitioning), even if you have another disk you plan to use for the OS, then the RAID will autostart when the OS starts.
Next thing is to make a partition and format.

Make a mount point, I called mine media.
```
sudo mkdir -p /media/Media/Media
```

Then you need to find out what the RAID is called, likely MD0, mine was MD0p1 (partitione 1 I suspect)

Edit fstab
```
sudo gedit /etc/fstab
```

Add this line (As I said, my mount point is 'Media')
```
/dev/md0p1	/media/Media	ext4	rw,user,auto,exec	1	2
```

This should bring it up every time.
I then disabled the firewall, added samba.

A tip I picked up is that if you rely a lot on graphical interfaces like we are used to, almost none of the 'how-tos' on the web is useful since it seems that the graphical settings are stored in other places than the traditional configs... clever... not...
(Wich I guess is the reason the RAID wount start if made in Palimpset... it's stored somewhere else or in another format...)

Another tip is
```
sudo nautilus
```
Then you can feel very much at home, and use Nautilus almost like you would windows explorer when it comes to sharing.

Also remember to give the 'other' users read and write permissions on the share.

Atleast it works for me now

---

### Post by P4man on 2009-11-17
> **Rune Hagen said:**
> 

Another tip is
```
[s]sudo nautilus[/s]
```

Dont use sudo for graphical programs, it will mess up your permissions and render your machine unbootable one day or another. Use gksudo for graphical apps like nautilus

```
gksudo nautilus
```

---

### Post by jamesisin on 2009-11-17
@Rune Hagen - This really isn't a solid solution for my case.  I am not going to rebuild my machine to add this RAID (nor for every subsequent RAID I might care to build).

I don't mind getting my fingers deep into the command line.  Here is my post on creating auto-mounts:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

What I lack is information on how to auto-start the RAID which is currently built.

Surely there is a line of code I can add to start the array at boot-time?

---

### Post by Rune Hagen on 2009-11-17
In theory, if I understand correctly, Ubuntu should see the RAID and assemble it during boot, but it doesn't.
So in all my searches I have yet to find a line that does it if the autmagic doesn't work...

And thanks for the GKSUDO thingy

---

