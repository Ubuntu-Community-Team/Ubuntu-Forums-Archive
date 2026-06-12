---
title: "File permissions...AGAIN!!!!"
date: 2011-04-09
forum: General Help
---

### Post by tonewheelkev on 2011-04-09
Once again totally stiffed by permissions.
USB drive won't let me write to it because I'm not the owner.

Surely there is a single fix for this....right across my system
....I really don't need protecting from myself:confused:

---

### Post by seawolf167 on 2011-04-09
Open a terminal, then use:

```
sudo chown -R $USER:$USER /path/to/external/drive
```

---

### Post by coffeecat on 2011-04-09
> **tonewheelkev said:**
> Once again totally stiffed by permissions.
USB drive won't let me write to it because I'm not the owner.

Presumably you formatted the USB drive with a Linux filesystem. You can use the chown command seawolf167 posted or you can prevent this happening in the first place if you use Disk Utility to format your USB drive. Use Disk Utility and make sure the "own filesystem" box is ticked. This relies on a little-known feature of Linux filesystems, that they can be owned just like files. 

Gparted, although more flexible than Disk Utility does not have this feature - last time I looked.

---

### Post by tonewheelkev on 2011-04-09
..../path/to/external/drive

....could that be : media/usb0

do I need anything else?

---

### Post by coffeecat on 2011-04-09
> **tonewheelkev said:**
> ..../path/to/external/drive

....could that be : media/usb0

Open a nautilus file browser for the USB drive and press ctrl-L. The breadcrumb trail will change to a path - /media/something. That is your path.

---

### Post by tonewheelkev on 2011-04-09
> **coffeecat said:**
> ....... if you use Disk Utility to format your USB drive. Use Disk Utility and make sure the "own filesystem" box is ticked. .........

Drive is already 30% full...so can't format now.
Ubuntu allowed this on an earlier occasion....but now the wind has changed again, and I have become a stranger once more!

---

### Post by tonewheelkev on 2011-04-09
entered:
sudo chown -R $kev:$kev /media/usb0

this hasn't helped....

---

### Post by coffeecat on 2011-04-09
> **tonewheelkev said:**
> entered:
sudo chown -R $kev:$kev /media/usb0

this hasn't helped....

Is your username 'kev'? Then:

```
sudo chown -R kev:kev /media/usb0
```But **only** if your drive is mounted to /media/usb0. The mountpoint is named after the partition label if there is one and the UUID if not. 'usb0' seems an unlikely partition label.

---

### Post by idi0tf0wl on 2011-04-09
> **tonewheelkev said:**
> entered:
sudo chown -R $kev:$kev /media/usb0

this hasn't helped....

Try more simply:```
sudo chown -R kev /media/usb0
```This presumes that your username is 'kev' and the name of your USB is 'usb0', obviously, but that perhaps is neither here nor there. To get the absolute path just navigate to the drive in Nautilus, right-click the righternmost breadcrumb and select the "copy" option. You'll be able to paste this into a terminal, but keep in mind that if there are any spaces involved you'll need to wrap it in quotes.

The simplest (and guaranteed) fix is to move everything you have on the drive to a temporary folder (say on your Desktop), erase and format the drive via the right-click option you get when you, say, right-click (right?) on the drive in Nautilus, and then move everything back to the drive, perhaps even after 'sudo chown -R kev /home/kev/Desktop/tempFolder' to really seal the deal with the existing files once and for all.

Get back at us!

---

### Post by tonewheelkev on 2011-04-09
Disk Utility says:
Mount point  : Mounted at /media/usb0

...does that help?

---

### Post by Wiebelhaus on 2011-04-09
```
sudo apt-get install ntfs-config
```

find ntfs-config in your system menu and use it to configure your jump drive writable.

---

### Post by tonewheelkev on 2011-04-09
idi0tf0wl

unfortunately don't have spare 300gb space on my system.

---

### Post by jerome1232 on 2011-04-09
What filesystem is on the drive?

---

### Post by tonewheelkev on 2011-04-09
> **jerome1232 said:**
> What filesystem is on the drive?

...it's FAT 32

---

### Post by jerome1232 on 2011-04-09
yeah chown won't work on a fat32 filesystem. The permision's have to be set at mount time.


That being said they should be getting set correctly at mount time. While I'm poking around to figure out how you can change that I'm curious as to what options it is getting mounted with

what is the output of mount? While it's plugged in.

```
mount
```

---

### Post by jerome1232 on 2011-04-09
Also maybe this page will help

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by tonewheelkev on 2011-04-09
> **jerome1232 said:**
> 

what is the output of mount? While it's plugged in.

```
mount
```


kev@kev-desktop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kev/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kev)
/dev/sde on /media/usb0 type vfat (rw,noexec,nodev,sync,noatime,nodiratime)

---

### Post by coffeecat on 2011-04-10
> **tonewheelkev said:**
> ...it's FAT 32

I wish you had said that at the beginning.

When you said in your OP...

> **tonewheelkev said:**
> 
USB drive won't let me write to it because I'm not the owner.

it was reasonable to assume that... 

> **coffeecat said:**
> Presumably you formatted the USB drive with a Linux filesystem. 

But you did not correct me, so most of this thread has been chasing a red-herring.

> **jerome1232 said:**
> yeah chown won't work on a fat32 filesystem.

Absolutely.

> **tonewheelkev said:**
> /dev/sde on /media/usb0 type vfat (rw,noexec,nodev,sync,noatime,nodiratime)

Looks OK.

Two questions. You said "because I'm not the owner". Is that what the error message says when you try to write to it? What is the exact error message?

---

### Post by tonewheelkev on 2011-04-10
> **coffeecat said:**
> .... What is the exact error message?

"......Error while copying

The folder "aaaaaaaaaaaaaa" cannot be copied because you do not have permissions to create it in the folder" "

USB0 properties, permissions tab, declares

"you are not the owner so you cannot change these permissions"

Unfortunately, I'll be away from the PC for the next 14 hours!!

---

### Post by coffeecat on 2011-04-10
That's curious. Going back to the output of your mount command:

> **tonewheelkev said:**
> /dev/sde on /media/usb0 type vfat (rw,noexec,nodev,sync,noatime,nodiratime)

Compare that to what I get from an automounted flash drive:

```
/dev/sde1 on /media/Kingston4 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

```The "uid=1000,gid=1000" is giving me full access. I was mistaken to say yours was OK - something's gone wrong with the automount options. Also your device is "/dev/sde", a drive not a partition. It looks as though you have a FAT32 filesystem on a whole drive without any partitions. This is unusual but not impossible. What is the "usb0" device exactly?

---

### Post by Morbius1 on 2011-04-10
coffecat, take a look at this and see if it doesn't look familiar. Sure sounds like a bug somewhere to me: [http://ubuntuforums.org/showthread.php?t=1605540](http://ubuntuforums.org/showthread.php?t=1605540)

Same odd mount point ( /media/usb0 ) . Same mount output without a non-root owner. Very curious.

---

### Post by coffeecat on 2011-04-10
> **Morbius1 said:**
> coffecat, take a look at this and see if it doesn't look familiar. Sure sounds like a bug somewhere to me: [http://ubuntuforums.org/showthread.php?t=1605540](http://ubuntuforums.org/showthread.php?t=1605540)

Same odd mount point ( /media/usb0 ) . Same mount output without a non-root owner. Very curious.

@Morbius1, good find. The last post in that thread is intriguing. The poster uninstalled "usbmount" (among others) and fixed the issue. Looking in Synaptic, the package usbmount is in the Universe repo (i.e. not an official Ubuntu package), and the package description says:

> This package automatically mounts USB mass storage devices (typically
USB pens) when they are plugged in, and unmounts them when they are
removed. The mountpoints[COLOR=Red] (/media/usb[0-7] by default),[/COLOR] filesystem types
to consider, and mount options are configurable. When multiple devices
are plugged in, the first available mountpoint is automatically
selected. If the device provides a model name, a symbolic link
/var/run/usbmount/MODELNAME pointing to the mountpoint is automatically
created.

The script that does the mounting is called by the udev daemon.
Therefore, USBmount requires a 2.6 (or newer) Linux kernel.

Firewire devices are also supported by USBmount.

USBmount is intended as a lightweight solution which is independent of
a desktop environment. Users which would like an icon to appear when an
USB device is plugged in should use the pmount and hal packages
instead.A superfluous package it would seem, but the bit I've reddened seems to be relevant.

@tonewheelkev, do you have the package usbmount installed?

---

### Post by LinuxH4x0r on 2011-04-10
do this a root? :confused:

---

### Post by tonewheelkev on 2011-04-10
> **coffeecat said:**
> . What is the "usb0" device exactly?

It's a 1Tb external drive

---

### Post by jerome1232 on 2011-04-10
> **coffeecat said:**
> 
@tonewheelkev, do you have the package usbmount installed?

+1

Even posting the output of dmesg may tell us this.

unplug usb drive, plugin usb drive, post the output of dmesg
```
tail /var/log/dmesg
```

This might be as easy as removing the offending package.

---

### Post by tonewheelkev on 2011-04-10
> **jerome1232 said:**
> +1

Even posting the output of dmesg may tell us this.

unplug usb drive, plugin usb drive, post the output of dmesg
```
tail /var/log/dmesg
```

This might be as easy as removing the offending package.
usbmount IS installed

not sure just what "+1" refers to though......

---

### Post by jerome1232 on 2011-04-10
+1 is a short notation for "I agree with this post"

So remove usbmount! Use synaptic or whatever you want and see if that fixes the issue, I saw a few other packages mentioned in the link provided by morbius in post #21, if just removing usbmount doesn't work check out that link, the last post list like 3 or 4 packages you might need to remove to get your usb automounting working correctly again.

---

### Post by tonewheelkev on 2011-04-10
> **jerome1232 said:**
> +1

Even posting the output of dmesg may tell us this.

unplug usb drive, plugin usb drive, post the output of dmesg
```
tail /var/log/dmesg
```

This might be as easy as removing the offending package.

kev@kev-desktop:~$ tail /var/log/dmesg
[   22.181212] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.184133] type=1505 audit(1302476558.420:9):  operation="profile_load" pid=818 name="/usr/bin/evince"
[   22.187430] skge eth0: enabling interface
[   22.195765] type=1505 audit(1302476558.428:10):  operation="profile_load" pid=818 name="/usr/bin/evince-previewer"
[   22.205545] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.213022] type=1505 audit(1302476558.448:11):  operation="profile_load" pid=818 name="/usr/bin/evince-thumbnailer"
[   22.387413] EMU10K1_Audigy 0000:00:0d.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   22.389900] Installing spdif_bug patch: SB Audigy 2 ZS [SB0350]
[   22.440287] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
[   22.440297] VIA 82xx Modem 0000:00:11.6: PCI INT C -> GSI 22 (level, low) -> IRQ 22
kev@kev-desktop:~$

---

### Post by tonewheelkev on 2011-04-10
> **jerome1232 said:**
> 
So remove usbmount! Use synaptic or whatever you want and see if that fixes the issue, I saw a few other packages mentioned in the link provided by morbius in post #21, if just removing usbmount doesn't work check out that link, the last post list like 3 or 4 packages you might need to remove to get your usb automounting working correctly again.

Removed Usbmount, and others as described by Morbius
...rebooted and......ACCESS to the Drive as required:D

Well done...and thanks....but what has actually happened here?
(BTW I'm using 10.04)

---

### Post by coffeecat on 2011-04-11
> **tonewheelkev said:**
> Well done...and thanks....but what has actually happened here?


You used a package from the Universe repository and didn't note the package information. No criticism intended, but it's a salutary lesson. Packages from the Universe repository are "Community maintained software, i.e. not officially supported software". It is of variable quality, or even when of good quality not necessarily intended for all situations. For example, look again at the package description for usbmount that I posted:

> USBmount is intended as a lightweight solution which is independent of
a desktop environment.I read that as meaning that it is for people running GUI-less server installations. Whatever, it is entirely superfluous in the desktop version of gnome which automounts USB drives with ease. This package was clearly interfering with the functionality of the gnome desktop. Take care with Universe (and Multiverse) apps - or any 3rd-party app for that matter.

I've learnt something useful too. In the past I've  tried to help in threads where the OP is having problems with external  USB drives. Now I know of one possible cause.

Good luck, and glad the problem is solved!

---

### Post by tonewheelkev on 2011-04-11
Many thanks to members for their time in helping me solve this one.

I'd have been totally stuffed without you...!!  :popcorn:

Kev/UK

---

