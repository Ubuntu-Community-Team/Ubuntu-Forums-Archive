---
title: "Ubuntu hangs at boot if USB drive not attached"
date: 2010-06-13
forum: General Help
---

### Post by johnnybeem on 2010-06-13
Hi all,
My computer is hanging on boot if I do not have the USB drive attached. The USB is in /etc/fstab as:
UUID=023d6f83-04f5-4248-82d6-c2dbd1a77e18 /mnt/usbdrive   ext4 defaults 0 0

This is all I can see on the monitor once it hangs (Ubuntu1004 is the label on my root filesystem):
fsck from util-linux-ng 2.17.2
Ubuntu1004: clean, 56288/1921360 files, 425861/7681078 blocks

If I plug in the USB drive while it is at this point, it is happy and continues booting...

Here is some output from /var/log/messages if it helps at all (I'm assuming the 6.977 and 120.245 are times, meaning I plugged in the USB drive at 120 seconds, so you can see that it was hung up during that time):

Jun 13 11:35:30 BSERVER kernel: [    6.791619] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
Jun 13 11:35:30 BSERVER kernel: [    6.832413] Console: switching to colour frame buffer device 80x30
Jun 13 11:35:30 BSERVER kernel: [    6.977796] intel8x0_measure_ac97_clock: measured 53061 usecs (2552 samples)
Jun 13 11:35:30 BSERVER kernel: [    6.977800] intel8x0: clocking to 48000
Jun 13 11:35:30 BSERVER kernel: [  120.245104] usb 1-1: new high speed USB device using ehci_hcd and address 4
Jun 13 11:35:30 BSERVER kernel: [  120.380654] usb 1-1: configuration #1 chosen from 1 choice
Jun 13 11:35:30 BSERVER kernel: [  120.431665] Initializing USB Mass Storage driver...
Jun 13 11:35:30 BSERVER kernel: [  120.431800] scsi2 : SCSI emulation for USB Mass Storage devices
Jun 13 11:35:30 BSERVER kernel: [  120.431997] usbcore: registered new interface driver usb-storage
Jun 13 11:35:30 BSERVER kernel: [  120.432001] USB Mass Storage support registered.
Jun 13 11:35:30 BSERVER kernel: [  129.020912] scsi 2:0:0:0: Direct-Access     LaCie    BigDisk               PQ: 0 ANSI: 0
Jun 13 11:35:30 BSERVER kernel: [  129.022792] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jun 13 11:35:30 BSERVER kernel: [  129.023540] sd 2:0:0:0: [sdb] 980469504 512-byte logical blocks: (502 GB/467 GiB)
Jun 13 11:35:30 BSERVER kernel: [  129.024560] sd 2:0:0:0: [sdb] Write Protect is off
Jun 13 11:35:30 BSERVER kernel: [  129.028803]  sdb: sdb1 sdb2
Jun 13 11:35:30 BSERVER kernel: [  129.057923] sd 2:0:0:0: [sdb] Attached SCSI disk
Jun 13 11:35:30 BSERVER kernel: [  129.308733] EXT4-fs (sdb2): mounted filesystem with ordered data mode


Please help! Thanks.

---

### Post by rahilm on 2010-06-13
Try removing that line from /etc/fstab

---

### Post by johnnybeem on 2010-06-13
Haha well yes, that would solve the problem but the point is I want it to mount the USB drive if possible. If it's not available, it should just continue gracefully.

---

### Post by MooPi on 2010-06-13
> **rahilm said:**
> Try removing that line from /etc/fstab This is probably a good suggestion, as you can always reestablish normal mount by editing fstab info later. I'm guessing that the usb drive was inserted during install process ?
If I'm guessing correctly your computer should auto mount the usb drive without issue on reboot.

---

### Post by johnnybeem on 2010-06-13
Hey guys,
I removed the line from /etc/fstab and the drive did not mount on boot. The USB was not present during the install, actually - I added the line to /etc/fstab on my own. It seems that the drive is not going to mount automatically unless it is in /etc/fstab, so what is causing this to hang? Is there possibly a different mount option I have to use to say "ignore the drive if it's not attached"?

MooPi, I'm not quite sure what you mean by "as you can always reestablish normal mount by editing fstab info later"...

After looking at a similar post on the forum, I also tried booting a live CD and running "fsck -y /dev/sda1" and for /dev/sdb2 as well (the root filesystem and usb). But this did not help...

---

### Post by johnnybeem on 2010-06-20
anyone??

---

### Post by JKyleOKC on 2010-06-20
You might try the "noauto" option in the fstab entry; this will prevent the boot procedure from ever trying to mount the disk, but will still let you mount it later from the command line. I don't find any option to "mount" that will tell it to do exactly what you want, but you can try "man mount" from a terminal window to view the list and see if any of them would come closer...

---

### Post by C.S.Cameron on 2010-06-20
Is there anything on the USB drive??
... Like an install of grub.

---

### Post by rahilm on 2010-06-21
> **johnnybeem said:**
> Haha well yes, that would solve the problem but the point is I want it to mount the USB drive if possible. If it's not available, it should just continue gracefully.

I don't think that's how fstab works...


And yes. Booting does hang when a fstab entry is misleading. Although, when i try to input some garbage in fstab and try to reboot, it displays a message at boot asking whether to skip the mount or retry.

Maybe some "Master of ubuntu" will help you make a bootup script to mount that drive.

---

### Post by JKyleOKC on 2010-06-21
> **rahilm said:**
> Maybe some "Master of ubuntu" will help you make a bootup script to mount that drive.I don't consider myself a master of anything (except possibly useless trivia) but this line of code works nicely here from a terminal prompt:
```
if [ -b /dev/sdb ]; then echo yes; else echo no; fi
```

To use the idea in a script, replace (most of) the ";" characters with line endings, and replace the "echo" commands with the desired mount commands. For example (note that I've not tested this, it's just a starting point):

```
#!/bin/bash

if [ -b /dev/sdb ]; then
  mount /dev/sdb1
else
  # do nothing if drive not present! echo no
fi
```

The "[" is actually a command to test a condition, and the "-b" option to it says to return true if the named device is present and a special block device -- which any drive's /dev name will be, if it's present. The "mount" command assumes that you have the appropriate line back in place in fstab, but with the "noauto" option so that it will not try to automatically mount.

Save the script file using any name you like, and in any directory. I have a directory named "bin" in my home folder where I put my private scripts. Then open the /etc/rc.local file while in root mode (*gksudo gedit /etc/rc.local* for a GUI editor or *su nano /etc/rc.local* for one from the command line), and add a call to your script just in front of the "exit 0" line near the bottom of the file. This call should use the full absolute path; in my setup that would be *"/home/jim/bin/mountsdb.sh"* if the script's name were "mountsdb.sh" but you would change it to fit your own setup. Then save the rc.local file and you may be home free.

The rc.local file is the last thing executed in the boot process, before the login screen appears. It runs under the root user so does not need any "sudo" commands. The idea of this approach is to never try to mount the drive automatically, but when everything else is ready, look to see if it's there and if it is, mount it!

You could also put the complete "mount" command in the script, and take the line out of fstab, and that should accomplish the same result -- with one less file to modify if you ever change your hardware significantly.

Hope this helps!

---

### Post by johnnybeem on 2010-06-27
Thanks JKyleOKC... I used a combo of your noauto option and /etc/rc.local script. Kind of surprised fstab doesn't have some logic like this built in, but it's working nice now nonetheless.

---

### Post by JKyleOKC on 2010-06-27
Glad to know it's working! You're quite welcome, of course.

---

### Post by Goodlookingjedi on 2010-06-28
Hi, I have a similar problem and was wondering if the same approach may fix it.

I have 2 NTFS drives which I wanted to auto mount at boot so I install the NTFS config tool.

it worked great.... however i left my usb stick plugged in and rebooted and it caused a clash where the NTFS drives where not able to be mounted and I got the same message as Johnnybeem did where I have to "press S to skip" but it hangs forever.

so I thought i would be clever and installed "storage device manager" a GUI for fstab and added my usb stick to the list at boot.

it works great ....all three are auto mounted.

except when I take my usb stick out and boot it cant find it and hangs again. 

so will the above solution be what I need?

your help is appreciated greatly.
Im running linux Mint 9 (ubuntu 10.04)

---

### Post by Goodlookingjedi on 2010-06-28
Have gone ahead and done it.... YES it works! thankyou!

---

### Post by JKyleOKC on 2010-06-28
Sorry to be slow getting back to you; I'm trying to troubleshoot a problem with a network adapter that has me offline quite a bit!

It should work for almost any similar situation, with appropriate adjustment of the path names involved...

---

