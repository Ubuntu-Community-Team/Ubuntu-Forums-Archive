---
title: "Karmic stopped automounting USB drives and internal DVD"
date: 2010-02-28
forum: General Help
---

### Post by Elwro on 2010-02-28
Hi,

yesterday my 9.10 stopped automounting my external USB drive, and in general any pendrive I put into any USB slot. What's worse, it also does not recognise CDs put into my DVD drive. (The only update I recall doing was the official update to the "sudo" package.)

1. The USB issue.

I plug in my external hard drive. Seemingly, nothing happens. No new icons appear anywhere.

a) Still,
```
sudo fdisk -l
```
gives, among other things:```
Disk /dev/sdc: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002ae3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121516   976074752    7  HPFS/NTFS
``` and I can mount it "manually" without any problems. Similarly for my pendrives. But I don't want to do it any time I put anything into the USB slot and I have no idea why this function stopped working!

b) I tried gconf-editor and in apps -> nautilus -> preferences "media_automount" is set to YES.

c) After searching around these forums, I even put "usb_storage" into /etc/modules and ```
<match action="org.freedesktop.hal.storage.mount-removable">
    <return result="yes" />
</match>
``` into /etc/PolicyKit/PolicyKit.conf and restarted HAL. Still doesn't work!


2. The DVD drive issue.

I put an audio CD in the drive. Usually an 'Audio CD' icon appeared after a few seconds, but now nothing happens. There is a "cdrom0" icon visible in the explorer, but when I click it, I get the following error: ```

Unable to mount cdrom0

mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

The output of 'dmesg | tail' with the audio CD in the drive is ```
$ dmesg | tail
[  181.057495] sr 6:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  181.057506] end_request: I/O error, dev sr0, sector 2496
[  181.057620] UDF-fs: No anchor found
[  181.057624] UDF-fs: No partition found (1)
[  181.163401] sr 6:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  181.163413] sr 6:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  181.163421] Info fld=0x10
[  181.163425] sr 6:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  181.163437] end_request: I/O error, dev sr0, sector 64
[  181.163527] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
```
edit: the output stays the same when I take the disc out from the drive.


So, it seems that for some strange reason my Karmic stopped being able to automount any new media. Does anyone have an idea why it is so and what should I do to bring this much-needed functionality back?

---

### Post by aadam12 on 2010-02-28
Same problem here. Just started happening for no apparent reason. Was there some update to Karmic that killed the automount?

---

### Post by Endomancer on 2010-02-28
It happened to me too, I can't mount CDs or DVDs  either, in the **Places** menu I got cdrom0 showing but when I click on it I get

 [ CODE ][ /CODE ] Unable to mount cdrom0

mount: special device /dev/scd0 does not exist [ CODE ][ /CODE ]

USB's have been auto mounting as normal for me and after reading this thread I decided to see if my 8 in 1 card reader will finally mount (it previously wouldn't) and I was able to manually mount an SD card through **Disk Utility **in **System/Administration**, now it auto mounts.

---

### Post by garvinrick4 on 2010-03-01
What does cat /etc/fstab say? You all still got a /dev/scd0? How does fstab look? Something up there?

---

### Post by Elwro on 2010-03-01
> **garvinrick4 said:**
> What does cat /etc/fstab say? You all still got a /dev/scd0? How does fstab look? Something up there?
```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=7a6b9b63-ee16-4e0c-ac86-bb201362bdfb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=27e32c58-1db4-4573-98e7-ff5ed5dc789e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda4 /media/Nowy4 ntfs rw 0 0
/dev/sda3 /media/Nowy3 ntfs rw 0 0
/dev/sda2 /media/Nowy2 ntfs rw 0 0
/dev/sda1 /media/Nowy1 ntfs rw 0 0
```The external USB drive is recognized by fdisk as /dev/sdc1.

It turns out I CAN mount a DATA DVD just by clicking the "cdrom0" icon. And VLC can play audio CDs from /dev/sdc0, without mounting.

---

### Post by Blutack on 2010-03-01
Me too.  Everything looks fine in dmesg, I get a 
```
(rhythmbox:31115): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/gvfs/gvfs-gdu-volume-monitor received signal 11
```
in xsession-errors but not sure if that's related.  I have a few PPA's I'm using though, maybe that has something to do with it?

---

### Post by Elwro on 2010-03-01
I also have some regarding gvfs. Both the output of "dmesg |tail -n 50" and the content of /var/log/kern.log.1 contain similar instances of 
```
[ 2421.233165] gvfs-gdu-volume[3447]: segfault at c ip 00c5ffa7 sp bff612bc error 4 in libgdu.so.0.0.0[c4d000+31000]
```

I have no idea whether this is in any way relevant, though, since such "segfaults" appear in the kernel log even a few days before I started having any problems.

---

### Post by garvinrick4 on 2010-03-01
When you mount a drive  is it visable on desktop? If not use the panel right click
add to panel and to disk mounter for time being.
 I have same problem but in Lucid 10.04 Places just shows Computer and cdrom0
when it used to show karmic install and windows 7 install.

rick@rick-laptop:~$ sudo mount /dev/sdb1 /media/KINGSTON
rick@rick-laptop:~$ sudo umount /media/KINGSTON
rick@rick-laptop:~$ 

This of course is how I have been mounting USB and internal drive partitions for now. 
space after sdb1. 

Your fstab looks good mine looks good but nothing in Places drop down menu and never have had cdrom0 there. Karmic install still looks and works smooth as butter, I thought this was a Lucid thing. Now you come up with it in Karmic. Got to get into this now and try to figure out. Keep in touch on this thread, I am.
 Can still mount all from Terminal as long as you have a label like KINGSTON for mine.
Go to gparted in Admin and right click on partition and Label it is just easier. From then on it is always /media/ (whatever you label). Just in case a reader needs to know this.
Strange it is in Karmic though but very interesting.

---

### Post by garvinrick4 on 2010-03-01
Disk mounter does not let me umount a disk, it does not believe I am root nor ask me.
Got to be something in there that we might have done maybe. Nobody in Lucid is complaining about this and not many in Karmic. What did we do? And not having partitions in Places I thought was going to be something new in Lucid Lynx. It is only Alpha so was just going along since could still mount just had to be from Terminal. HMMMM

---

### Post by Endomancer on 2010-03-02
> **garvinrick4 said:**
> What does cat /etc/fstab say? You all still got a /dev/scd0? How does fstab look? Something up there?

```
~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9554a150-100e-49c7-925f-e882c40a28a7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c9cc65be-6d84-459f-99d4-2c1c1a522563 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```So far I have tried data DVD, DVD movie and audio CDs with no difference
in Disc Utility my DVD burner doesn't even show on the list of drives. 
USBs have been mounting as usual and SD cards can now automount since the sudo update which is a small yay:)
but at the price of no CD/DVDs is not so yay:(

---

### Post by tekfreak on 2010-03-02
Hi 

I have the same problem, and i can solve it with that:

[http://www.webupd8.org/2010/02/install-gnome-disk-utility-palimpsest.html](http://www.webupd8.org/2010/02/install-gnome-disk-utility-palimpsest.html)

;)

---

### Post by Elwro on 2010-03-02
> **tekfreak said:**
> Hi 

I have the same problem, and i can solve it with that:

[http://www.webupd8.org/2010/02/install-gnome-disk-utility-palimpsest.html](http://www.webupd8.org/2010/02/install-gnome-disk-utility-palimpsest.html)

;)
IT WORKS! Thank you very much!

Still, I don't understand the whole thing. The PPA I've been using was [this one](https://edge.launchpad.net/~nilarimogard/+archive/webupd8). I had no idea it had anything to do with gnome-disk-utility, libgdu-gtk0 and/or libgdu0. Still, I purged it using  ```
sudo ppa-purge ppa:nilarimogard/webupd8
``` and changed the versions of the 3 packages above to the official 'karmic' ones. After restarting, automounting works now! I have a hunch that the purge I did was irrelevant. If anyone could clarify the issue I'd be grateful since I'd like to understand the reasons behind all this ;)

---

### Post by Endomancer on 2010-03-02
I did those things and now my machine is broken, I cant get it to boot, and I cant get the disc drive going in order to boot from a live disc or reinstall and bios wont boot from usb either

Edit - I finally got it to boot a ubuntu live usb after fiddling with the bios settings. Reinstalling now (Im on my hp dinosaur ATM)

---

### Post by Endomancer on 2010-03-03
Sorry for the double post, but Iv done a clean install of Ubuntu and still wont mount CDs or DVDs.

My external HDD, blue tooth, web cam and wireless keyboard/mouse all connected via usb and all mount at boot, thumb drives auto mount when I plug them in and SD cards to too now. 

Basically everything works except the CD/DVD drive, now I'm wondering if it could be a hardware issue, is there any way to find out?

---

### Post by Elwro on 2010-03-03
> **Endomancer said:**
> Sorry for the double post, but Iv done a clean install of Ubuntu and still wont mount CDs or DVDs.

My external HDD, blue tooth, web cam and wireless keyboard/mouse all connected via usb and all mount at boot, thumb drives auto mount when I plug them in and SD cards to too now. 

Basically everything works except the CD/DVD drive, now I'm wondering if it could be a hardware issue, is there any way to find out?
I'd very much like to be of some help, but sadly my knowledge is too limited. But perhaps you should consider starting a separate thread? It seems you now have a different problem from the one originally discussed here; if you make a new thread about it, it's more likely someone will read it and help you!

---

### Post by aadam12 on 2010-03-06
Thanks TEKFREAK (Post #11) this solution also worked for me
[http://www.webupd8.org/2010/02/install-gnome-disk-utility-palimpsest.html](http://www.webupd8.org/2010/02/install-gnome-disk-utility-palimpsest.html)

I downgraded **gnome-disk-ulility**, **libgdu-gtk0** and **libgdu0** to version 2.28.0 using   Synaptic. Rebooted my pc and everything automounts as it should. :D

---

