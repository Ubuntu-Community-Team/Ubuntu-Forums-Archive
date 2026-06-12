---
title: "Long disk-activity-pause on boot"
date: 2011-07-14
forum: General Help
---

### Post by Kensey on 2011-07-14
Just the last day or so, I've noticed a long pause when I boot my laptop, with lots of disk activity.  dmesg says:

[    2.960076] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.960974] ata3.00: ATA-8: WDC WD1600BJKT-75F4T0, 11.01A11, max UDMA/133
[    2.960979] ata3.00: 312581808 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.961908] ata3.00: configured for UDMA/133
[    2.962081] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BJKT-7 11.0 PQ: 0 ANSI: 5
[    2.962252] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.962272] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.962331] sd 2:0:0:0: [sda] Write Protect is off
[    2.962334] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.962355] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.993198] usb 5-1: config 0 descriptor??
[    3.008969]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    3.009390] sd 2:0:0:0: [sda] Attached SCSI disk

[lots more...]

[    5.404991] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   21.040743] Adding 4192960k swap on /dev/sda5.  Priority:-1 extents:1 across:4192960k 
[   21.475032] EXT4-fs (sda6): warning: maximal mount count reached, running e2fsck is recommended
[   21.582924] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro

Why would there be a 15-second pause (during which the disk is slammed) between mounting root and mounting swap?  During this time I see nothing but a blank purple screen, there are no cycling dots or text scroll.  Is this normal and I'm just freaking out over nothing because there's no indicator of progress?

GRUB default boot options:

quiet splash nomodeset video=uvesafb:mode_option=1920x1200-24,mtrr=3,scroll=ywrap vt.handoff=7

---

### Post by Kensey on 2011-07-14
Also, as a data point, the time from hitting enter at the grub menu to the screen flickering as the login dialog loads is ~45 seconds, during which time I have just the blank purple screen and a solid disk-activity light.

---

### Post by varunendra on 2011-07-15
If 45 sec seems abnormal (compared to previous booting time), then, coupled with unusually continuous hard drive activity, it may be an indication of problem with hard drive - physical or just filesystem. Do what dmesg suggested:

> **Kensey said:**
> ....
....
[   21.475032] EXT4-fs (sda6): warning: maximal mount count reached, [COLOR=Red]**running e2fsck is recommended**[/COLOR]
that is, boot from your live CD, unmount the local drives, then open terminal and enter this command:
```
sudo e2fsck -f /dev/sda
```
assuming your local hard drive appears as /dev/sda in live mode.

see **e2fsck --help** or **man e2fsck** for more info on the command.

---

### Post by Kensey on 2011-07-15
Hmmmm.  I can just init 1 and remount root read-only to do the fsck right?

Here's a typical bootchart for my system.

---

### Post by Kensey on 2011-07-15
OK, I fscked the filesystem but no dice:


[    4.717275] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   20.353108] Adding 4192960k swap on /dev/sda5.  Priority:-1 extents:1 across:4192960k 
[   21.411924] <30>udev[478]: starting version 167

Still got that long pause, and it still takes ~45 seconds to boot.

---

### Post by wildmanne39 on 2011-07-16
Hi, you can use log file viewer to look at your logs and see where the pause is taking place. Look at system and kernel logs.

---

### Post by varunendra on 2011-07-16
I'm afraid the bootchart you attached is too small to look anything in it :).

But anyway, if fsck returned no errors, then I'd assume it as normal assuming 45 sec. is the total OS loading time (time from start of kernel booting till making it to the desktop).

Can we see the contents of your /etc/fstab file?

For some extra info about this warning and to know why it is mostly (but not always) ignorable, see these references:

[http://www.linuxquestions.org/questions/linux-hardware-18/warning-maximal-mount-count-reached-running-e2fsck-is-recommended-153676/](http://www.linuxquestions.org/questions/linux-hardware-18/warning-maximal-mount-count-reached-running-e2fsck-is-recommended-153676/)

[http://dealdatabase.com/forum/showthread.php?t=45231](http://dealdatabase.com/forum/showthread.php?t=45231)

[http://www.linuxquestions.org/questions/red-hat-31/maximal-mount-count-reached-running-e2fsck-is-recommended-848788/](http://www.linuxquestions.org/questions/red-hat-31/maximal-mount-count-reached-running-e2fsck-is-recommended-848788/)

[http://ubuntuforums.org/showthread.php?t=1079231](http://ubuntuforums.org/showthread.php?t=1079231)

---

### Post by Kensey on 2011-07-17
> **varunendra said:**
> I'm afraid the bootchart you attached is too small to look anything in it :).

Well shoot, the forum auto-converted the PNG to low-res JPG.  I edited that post and attached it as a .tar.gz.

> But anyway, if fsck returned no errors, then I'd assume it as normal assuming 45 sec. is the total OS loading time (time from start of kernel booting till making it to the desktop).

Seems like a lot longer than it used to take, though, and I'm pretty sure it didn't take this long when I first upgraded to Natty.  I'm suspicious that something is amiss because it's just blank purple the whole time, I never get the scrolling dots.  And the disk-activity light is lit up solid the entire time.

> Can we see the contents of your /etc/fstab file?

```
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=97b3ac03-fdc8-43e6-93d8-a0ffb03f80a5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b40fab0d-f463-4121-b590-e3c71c546601 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by wildmanne39 on 2011-07-17
Hi, for natty 45 seconds is a good time. Also the hard drive light would be on the whole time during the boot process.

I would not worry about the dots not working I changed the background to my boot menu and I never see the screen with the dots at all anymore.

I am not saying not to be concerned about the error message but for the other things you mentioned I would not worry about them. 

Did you look at your logs?

---

### Post by Kensey on 2011-07-17
> **wildmanne39 said:**
> Hi, for natty 45 seconds is a good time. Also the hard drive light would be on the whole time during the boot process.

I guess that's ureadahead pulling the boot files off in one long read (i.e., doing what it's intended to do)?

> I would not worry about the dots not working I changed the background to my boot menu and I never see the screen with the dots at all anymore.

It seems like the splash screen has always been a fragile part of the Ubuntu experience.

> I am not saying not to be concerned about the error message but for the other things you mentioned I would not worry about them.

Well, I don't get the error about fsck any more anyway.  For the future, how do I make it behave like it used to and fsck when it hits maximal mount count?

> Did you look at your logs?

Yeah, there wasn't anything that looked suspicious.  The fsck warning was really it.

---

### Post by varunendra on 2011-07-18
> **Kensey said:**
> 
Well, I don't get the error about fsck any more anyway.  For the future, how do I make it behave like it used to and fsck when it hits maximal mount count?
Since your fstab already has '1' as the scan option for root (/), you don't have to worry about it. For any other ext2/3/4 partitions, you may add them in your fstab file (if there isn't already an entry for it), then put '2' as scan option (the last '0' in its line, which is '1' for root partition).

For your info, 0 means 'don't scan at booting, and 1 and 2 are two other possible options which are nothing but priorities for scanning (so '1' for root means 'scan it first, and '2' for others means 'scan them next'). As far as I know, there is no other option for that parameter.

But it is more like an info for your attention rather than a warning. It can most often be safely ignored. See this discussion here : [http://dealdatabase.com/forum/showthread.php?t=45231](http://dealdatabase.com/forum/showthread.php?t=45231)

What it suggests is that you can just unmount the partition and fsck it whenever needed. No need to add any fstab entry just for scanning at boot time, which is almost unnecessary for partitions other than root. Scanning once would remove the warning till it again reaches max. mount count (like what has happened in your case).

Using fsck from a live CD is only required when it is your root partition and needs repairing. (so you can scan it while it is 'unmounted').

Hope it helps.

---

