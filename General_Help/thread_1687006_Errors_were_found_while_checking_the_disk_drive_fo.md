---
title: "Errors were found while checking the disk drive for /"
date: 2011-02-13
forum: General Help
---

### Post by BJC_001 on 2011-02-13
Hi,

I hope someone can help. For background, I'm a software developer 

that's experienced in Windows but my GNU/Linux and ubuntu experience is 

limited. I can follow support instructions quite well, but very little 

in ubuntu is obvious to me.

I have an HP 2133 netbook which I've been using to run ubuntu for a 

while. I installed 10.04 a while back and it seemed to be working fine. 

I don't use the computer often - only when travelling - and I switched 

it on today and it failed to start.

It gets to the graphical ubuntu screen, with the animated 5 dots. The 

message "Errors were found while checking the disk drive for /" is 

displayed, while the dots continue animating.

I booted to a USB stick, running ubuntu 10.04, and started Disk 

Utility. This reports that the 120GB GB Hard Disk on the SATA Host 

Adapter reports the SMART Status of "Disk is healthy". SMART Data 

doesn't report anything that looks wrong. If I unmount the drive and 

try Check Filesystem, it reports "File system is clean".

I then ran GParted. Right clicking on /dev/sda1 and selecting Check, I 

then applied the operation. The resulting report includes no errors.

If I mount the drive and browse to /var/log/boot.log (on the HDD, not 

the drive being used by the USB stick), it has many messages that are 

similar. The first and last are shown below:

  fsck from util-linux-ng 2.17.2
  udevd[327]: SYSFS{}= will be removed in a future udev version, please 

use ATTR{}= to match the event device, or ATTRS{}= to match a parent 

device, in /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules:11
  
  ...

  udevd[327]: SYSFS{}= will be removed in a future udev version, please 

use ATTR{}= to match the event device, or ATTRS{}= to match a parent 

device, in /etc/udev/rules.d/85-brltty.rules:30

Following those messages (which don't seem to be a problem) the log 

ends with the following:

  /dev/sda1:clean, 171010/7028736 files, 1308483/28103701 blocks
   * Starting AppArmor profiles       [0018][80G Warning: found 

usr.sbin.ntpd in /etc/apparmor.d/force-complain, forcing complain mode

Where "[0018]" is a single character in gedit.

After looking online, I found a suggestion to add the option 

"apparmor=0" as a kernel startup option. From a USB stick boot, I 

modified the /boot/grub/menu.lst file on the HDD. I modified an entry 

near the end of the file, specifically the first option of the ones 

that are listed by GRUB when I boot from the HDD. The entry then became 

as follows:

  kernel    /boot/vmlinuz-2.6.32-25-generic root=UUID=eb4866...... ro 

quiet splash apparmor=0

After rebooting to the HDD, I get the same message.

I also tried rebooting and then selecting an alternative GRUB entry, 

labelled "Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)" 

with the same result (except that more messages are reported to the 

dicplay before this happens. [I have no reason to believe this is 

unusual.]

I then pressed a key when the error message is displayed. Generally, that scrolls up a lot of text really quickly. However, last time I did this there was a message that may be relevant, as follows:

  /dev/sda1: Superblock last mount time (Sat Feb 12 23:19:59 2011,
          now = Tue Jan  1 03:03:56 2002) is in the future

  /dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.

Given the lack of use, it's quite possible that the RTC battery is flat, causing the time to fail. Unfortunately, its difficult to replace and will require an HP part (it's a standard CR2016 battery but is sleeved and has a connector that might be difficult to salvage from the current battery. If this is an issue, is there a workaround?

So, in summary, the startup error suggests a problem with the HDD but I 

can't find anything to indicate there's a problem with the HDD.

Any suggestions for the next step?

Thanks.

---

### Post by tredegar on 2011-02-13
Looks like your HW clock is wrong.

Even with a flat CMOS battery you should be able to set the correct date & time from within your BIOS. 

Do that, then try booting ubuntu again, without powering-off your PC.

---

### Post by BJC_001 on 2011-02-13
Hi,

Thanks for the response. Unfortunately, the HP-2133 BIOS doesn't have an option to set the date/time. Is there any other way to bypass this check?

Thanks.

---

### Post by tredegar on 2011-02-13
Boot from a live cd

Set the time in ubuntu.

Open a terminal and type```
sudo hwclock --systohc
```
That should set the hardware clock.
Then try rebooting from HDD (without powering down).

---

### Post by BJC_001 on 2011-02-13
Yep, that's exactly what I needed. Thanks very much.

I was able to boot from the HDD. After it checked the drive, it started as normal. I've even switched it off, removed the battery (can't see that should make any difference), waited 30 minutes, and then switched on again. That worked too, although I didn't expect it to.

I don't see the benefit of the mount date/time check at boot. It might be a nice thing to query, but to stop the boot completely seems rather OTT. Is there any way to suppress the mount date/time check permanently, or otherwise bypass the check without having to boot from USB first?

I expect the permanent fix is to get a new RTC battery. However, it has to be an HP part, which is expensive so that may have to wait for now.

Very many thanks.

---

