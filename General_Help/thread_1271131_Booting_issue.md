---
title: "Booting issue"
date: 2009-09-20
forum: General Help
---

### Post by motorcity909 on 2009-09-20
Hi all

I first installed Ubuntu a few months ago after gettinga trojan on my WinXP machine.  My machine had two hard drives (Western Digital 160gb and Samsung 160gb) which I Gparted first, then installed Ubuntu.  

However, I could only complete a successful install by disconnecting one of the hard drives (Samsung 160gb).  No problems ever since.

The WD hard drive appeared as /dev/sdb1.

Today I decided to reconnect the second hard drive and see if I could use it.  Ubuntu could see the second hard drive but it wouldn't mount.   I installed Gparted and formatted the second hard drive as ext3.  I still couldn't mount it and tried a reboot.

An error screen appeared so I pulled the plug and disconnected the Samsung drive again.

Now though whenever I boot up the computer, the same screen appears where one shows, in red, as failed - e2fsck - dies with existing status 8.

I then have to press Control and D and then it boots up successfully.

Whereas before the Western Digital HD showed as sdb1, now it shows as sda1.

There is also an icon on my desktop for the '157 GB Media' hard-drive (Western Digital) and in System Monitor the drive shows up twice, the second line being the new mount point I created when trying to mount the Samsung drive.

Is there any way I can avoid the boot up problem and not have to press Control and D?

Can the Western Digital HD be renamed back to sdb1?

Many thanks from a worried user.

---

### Post by Shazaam on 2009-09-20
Just a guess...
The Samsung drive must still be listed in fstab. That is probably why fsck is failing as it tries to find a disconnected drive.
Two things you need to post the terminal output of here to help me and others-
```
sudo fdisk -lu
```
(lowercase L) and
```
cat /etc/fstab
```
I have to leave in a bit so I hope others will chime in as well with help.

---

### Post by motorcity909 on 2009-09-20
Hi Shazaam

Thanks for your reply.  

[LIST]
[*]Here is the output from **sudo fdisk -lu**
[/LIST]

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00090863

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   306568394   153284166   83  Linux
/dev/sda2       306568395   312576704     3004155    5  Extended
/dev/sda5       306568458   312576704     3004123+  82  Linux swap / Solaris


[LIST]
[*]And here is the output from **cat /etc/fstab**
[/LIST]
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=5e48d577-470d-458a-87a1-24a6ea9c7574 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=14e70801-261d-4e25-b8bd-b95575ba6509 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1    /media/mynewdrive   ext3    defaults     0        2
______________________________________________________

Looking at that very last line, working from something I found on a website, I remember adding that line in to a file as part of my attempt to mount the Samsung drive.  
Any help will be much appreciated.

---

### Post by motorcity909 on 2009-09-20
Don't know if this will help as well.

The UUID of the Western Digital HD begins 5e48d577 and for the Samsung it begins 14e70801.  Noticed both of these appear in the second output I posted earlier.

I've also attached a screengrab from Gparted showing the Western Digital HD now.

As you can see the Western Digital HD is shown as mounted twice.  I can unmount the /media/mynewdrive mount, but not the other (which is good as that is the Ubuntu installation mount!)

Thanks again.

---

### Post by ibuclaw on 2009-09-20
> **motorcity909 said:**
> Don't know if this will help as well.

The UUID of the Western Digital HD begins 5e48d577 and for the Samsung it begins 14e70801.  Noticed both of these appear in the second output I posted earlier.

Run the following in a terminal just to be sure that you know which UUID is which
```
ls -l /dev/disk/by-uuid
```


Although, FYI!
> 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00090863

Device Boot Start End Blocks Id System
/dev/sda1 * 63 306568394 153284166 83 Linux
/dev/sda2 306568395 312576704 3004155 5 Extended
/dev/sda5 306568458 312576704 3004123+ 82 Linux swap / Solaris

fstab tells you that Linux is only aware of one Hard Drive being installed.

Reboot into BIOS and check to see if it is listed in there. As I am thinking that you've haven't reconnected it properly.

Regards
Iain

---

### Post by motorcity909 on 2009-09-21
Hi Iain

I'm happy to leave that Samsung HD disconnected.

 I probably did reconnect it incorrectly (hence it wouldn't mount properly).  After that I rebooted and saw the error message for the first time so I opened the machine up, disconnected the Samsung HD but am still getting the error message and have to Control and D to boot up.

Obviously there are still references to that Samsung HD which Ubuntu is still looking for but I don't want it to do that; I'm happy not to use the Samsung HD.

This is the output from **ls -l /dev/disk/by-uuid**

total 0
lrwxrwxrwx 1 root root 10 2009-09-21 06:45 14e70801-261d-4e25-b8bd-b95575ba6509 -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-09-21 06:45 5e48d577-470d-458a-87a1-24a6ea9c7574 -> ../../sda1


As I mentioned earlier the UUID of the Western Digital HD begins 5e48d577 and for the Samsung it begins 14e70801.

Many thanks for all your help
David

---

### Post by ibuclaw on 2009-09-22
> **motorcity909 said:**
> 
total 0
lrwxrwxrwx 1 root root 10 2009-09-21 06:45 14e70801-261d-4e25-b8bd-b95575ba6509 -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-09-21 06:45 5e48d577-470d-458a-87a1-24a6ea9c7574 -> ../../sda1


As I mentioned earlier the UUID of the Western Digital HD begins 5e48d577 and for the Samsung it begins 14e70801.

Many thanks for all your help
David
You are wrong.

5e48d577 is the UUID of the 1st primary partition on the Western Digital, and 14e70801 is the 1st logical partition on the Western Digital. ;)

The Samsung is disconnected, hence it isn't listed. If it were ... it would be shown as **sdb**.

Anyhow:
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=5e48d577-470d-458a-87a1-24a6ea9c7574 / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=14e70801-261d-4e25-b8bd-b95575ba6509 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

```
Replace the entire fstab with the above, and that should fix your issue.

Regards
Iain

---

### Post by motorcity909 on 2009-09-22
Thank you Iain, will try that later (off to work shortly)

Am I right in saying it's this to open fstab:-

gksudo gedit /etc/fstab


Thanks as always
David

---

### Post by motorcity909 on 2009-09-22
Hi Iain

Can't thank you enough, that has worked perfectly.  Straight boot up now, no Control & D needed, no second mount point showing, brilliant!

Thank you
David

---

