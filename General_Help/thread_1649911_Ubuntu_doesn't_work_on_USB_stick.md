---
title: "Ubuntu doesn't work on USB stick"
date: 2010-12-20
forum: General Help
---

### Post by delaOrden on 2010-12-20
Hello my friends: 
I'm kind of desperate with an apparentely simple problem. I've been searching everywhere and couldn't find the answer or solution.
It's just about to make a USB stick boot my ubuntu 10.10. First,I have tried several flash drives. I have downloaded and checkedsum several images, including Mint 10 ( sort of Ubuntu ), I have used  UNiversal USB, LinuxLiveUSB creator,Unetbootin and the native program inside Ubuntu. All the time I have the same problem : 
"line 7: can't open /dev/sr0 no medium found"
I have disabled by default the floppy disc from BIOS.
I just don't know what to do anymore. please, is there anybody out there to help me out ?
I suspect that some line has to be modified. 
I am not an advanced user of Linux. But I would like to have ubuntu booting from a stick flash drive.

Thank you everybody  and may you all have a Happy Season

---

### Post by oldfred on 2010-12-20
Welcome to the forums.

I found this link:

[http://ubuntuforums.org/showthread.php?t=1345125](http://ubuntuforums.org/showthread.php?t=1345125)

You need to edit syslinux.cfg

---

### Post by efflandt on 2010-12-20
Does it work from CD, or are you trying to boot the iso on a computer with no CD drive (or writer)?  Maybe it is confusing the pseudo sr device for USB boot with your real DVD/CD drive.  Does your computer by any chance have some sort of hot swap drive bay?

---

### Post by delaOrden on 2010-12-20
Thanks Oldfred ... As a matter of fact I have already read this thread you mention. I am gonna try again to modify the syslinux.cfg
 Anyway I'm waiting for some other options. Thank you all

---

### Post by delaOrden on 2010-12-20
hi Efflandt ! My PC has a cd/dvd drive and the Live CD works nice. No, my PC doesn't have any hot swap drive bay. I already have tried to install from CD to USB and it didn't work either. Just for your information, all the times I tried ,the USB wants to boot; it shows the Ubuntu logo and the progress bar. Then I press any F key and I can see the problem I mention above "...no medium found" and it remains in such state without booting.

Thank you guys

---

### Post by wojox on 2010-12-20
It's a [Bug]("https://bugs.launchpad.net/ubuntu/+bug/500822") that still hasn't been dealt with.

I use Fedora and have to run Unetbootin as root to make it work. For you reformat your USB drive and run in a terminal 

```
gksudo unetbootin
```

worth a shot. ;)

---

### Post by delaOrden on 2010-12-20
Hi Wojox and thanks. I already tried Unetbootin and it worked but the probelm is that unetbootin does not support persistence mode and I need this feature. I want to boot and have some docs and programs in there, understand ? Anyway, thank you

---

### Post by C.S.Cameron on 2010-12-20
> **delaOrden said:**
> Hi Wojox and thanks. I already tried Unetbootin and it worked but the probelm is that unetbootin does not support persistence mode and I need this feature. I want to boot and have some docs and programs in there, understand ? Anyway, thank you

Not to worry, you can add a persistent partition, or two, to a UNetbootin install and it will be even better than just using persistence files:

This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1GB FAT32 partition, (on the left side of the bar).
Created a 2GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext2 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

---

