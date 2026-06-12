---
title: "ureadahead update - can't login"
date: 2009-12-02
forum: General Help
---

### Post by sam81 on 2009-12-02
after sreadahead was updated with ureadahead in karmic, I can't get to login anymore,
the system boots, but I can't get to kdm. I've waited up to 5 minutes, thought maybe it was profiling and that took time, but nothing...
booting in recovery mode doesn't help

how can I disable ureadahead from outside ubuntu? I have another partition with a different distro from which I can write on the ubuntu partition

---

### Post by jbrown96 on 2009-12-02
I don't think you can disable readahead very easily. It actually changes the binary format of executables, and I doubt there is an easy way to disable it. It certainly wouldn't be in a config file. You would have to recompile most of your system. 

My gut feeling is that this is not a readahead problem. Have you tried booting with a splash screen to see any possible error messages? You said you tried recovery mode, which disables the splash screen. Did you see any error messages?

---

### Post by kolAflash on 2009-12-03
Hey,
I got the same problem after that ureadahead update on 2. Dec 2009. But changing the display-manager to gdm helped (before I was using kdm).

So if it's really the same problem and you are using kdm too, try this.
(kdm is the display-manager of kde, so if you are using Kubuntu or you installed kde, you are probably using kdm to login)

If you don't have gdm installed, you can get it by
```
apt-get install gdm
```So this will maybe also display the dialog for choosing the display-manager.
If not, you can change the display-manager by doing
```
sudo dpkg-reconfigure kdm
```or
```
sudo dpkg-reconfigure gdm
```By typing one of this, you will get to a menu, where you can choose the display-manager.


I was able to do this via ssh. But if this is not a possibility for you, or you can't get gdm installed, you can change the display-manager in
```
/etc/X11/default-display-manager
```For gdm the file has to contain:
 ```
/usr/sbin/gdm
```For kdm the file has to contain:
```
/usr/bin/gdm
```Pay attention! In case of kde it's bin. In case of gdm it's sbin!
In case you don't have gdm installed, after this any display-manager should start. So you will just be dropped into bash, where you can install gdm (like mentioned before). And after a reboot
```
sudo /sbin/init 6
```everything should be ok again!


Ok. So far about workarounds. But at least I would like to know the reason for all that trouble too, because using gdm to log into a kde session brings some disadvantages (for example, not being able to shutdown the pc directly from kde).

I started my PC without all that animation staff, but there where no interesting error messages to see on the shell.

So anybody having an idea?

P.S. Some people seem to have a similar problem. But that seems to be, because of their Nvidia graphics-card ([http://ubuntuforums.org/showthread.php?t=1343261](http://ubuntuforums.org/showthread.php?t=1343261)). I'm using a Intel card. So this must be something else!

---

### Post by kolAflash on 2009-12-04
Found a similar Bug-Report here:
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677)

Sam81, can you confirm that kdm - gdm thing?
And did you install your Ubuntu 9.10 directly from CD, or is it an updated Ubuntu 9.04 or 8.10 or earlier?

Cause my one is an updated 8.10.

---

### Post by krastanov on 2009-12-04
To disable readahead comment out "exec" from /etc/init/readahead*. That way you can know if it's it to blame.

---

### Post by scotty64 on 2009-12-04
I have the same problem here: Logging in to my Dell XPS M1330 (NVIDIA GPU) has become difficult since the update. The system behaves really strange:
Booting the realtime kernel leads to a complete hang - I wonder if it just does not work with ureadahead as synaptic sais "ureadahead requires a kernel patch...." and the rt-kernel was not upgraded after the ureadahead upgrade.
When I boot the generic-pae kernel the system sometimes fails completely to start KDM, sometimes it takes about 20 seconds or it comes up with the "Ubuntu is running in low graphics mode" message. The odd thing is that KDM/X start automatically after I click on the option to open a text console in the "low graphics mode" message box.

---

### Post by kolAflash on 2009-12-04
I just tried to disable readahead in /etc/init/readahead*

So there where 2 files (ureadahead.conf and ureadahead-other.conf) where I commented out the exec. But it didn't helped.

Yesterday I already uninstalled ureadahead and sreadahead but it didn't helped too.
Currently, for the testing with ureadahead.conf and ureadahead-other.conf, I have ureadahead and sreadahead installed again.

So at all it would be strange if ureadahead and sreadahead would have nothing to do with all that. Because the problem occured directly after those had been updated.
But it seems, the are not really the core of the problem........

---

### Post by kolAflash on 2009-12-04
Found out something new. I thought at all this non-blinking cursor looks like the x-server has crashed. So I looked into my xorg.log

This are the differences between the start with gdm and kdm! After line 412 they are completly different! In case of gdm, the xserver seems to continue normally. In case of kdm the xserver seems to shut down.

I'm not a xserver specialist. But maybe somebody knows, what this means...

```
GDM - 102
=========
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)

KDM - 102
=========
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel



GDM - 205
=========
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0

KDM - 206
=========
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0



GDM - 349
=========
(II) intel(0): Setting screen physical size to 376 x 301
(II) config/hal: Adding input device Power Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(II) config/hal: Adding input device HID 046a:0011
(**) HID 046a:0011: always reports core events
(**) HID 046a:0011: Device: "/dev/input/event4"
(II) HID 046a:0011: Found keys
(II) HID 046a:0011: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID 046a:0011" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"

KDM - 350
=========
(II) intel(0): Setting screen physical size to 376 x 301
(II) config/hal: Adding input device HID 046a:0011
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) HID 046a:0011: always reports core events
(**) HID 046a:0011: Device: "/dev/input/event4"
(II) HID 046a:0011: Found keys
(II) HID 046a:0011: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID 046a:0011" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"



KDM - 412
=========
(II) HID 046a:0011: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log
```

---

### Post by daniel.schudel on 2009-12-04
I've been hit by this one too.  I have a Dell with an Intel video card.  My laptop installation goes all the way back to 8.04->8.10->9.04->9.10.

The update of sreadahead/ureadahead left my laptop completely useless.  I would get the "kubuntu" splash screen with the bouncing progress bar.  But, at some point, the display would go blank except for a single small cursor in the top left.  None of the usual keys would work for me (CTRL-ALT-Fn, CTRL-ALT-BKSPC, CTRL-ALT-DEL).  I had to resort to holding down the power button.

First step was to disable splash, turn on verbose, and try to enter single use boot mode (grub/kernel command line "nosplash verbose single").  The usual boot messages would scroll across the screen and would end with a complaint from sreadahead before the screen went blank.  Note that booting into single-user mode, and trying the "recovery" option were useless.  Single user-mode traditionally boots your system minimally and loads nothing.  (K)Ubuntu is trying to do too much with it.  I came across another suggestion (that I have not tried) and that is to use "emergency" instead of "single".

With a bootable USB flash stick, and the Kubuntu 9.10 iso image on it, I booted my laptop and switched my login manager over to GDM.  kolAflash gave complete instructions on how to do this.  I would add that if you are using a boot CD, or USB stick, you'll need to mount your usual harddrives and use chroot before trying anything with apt-get or dpkg.

For example, if your root device is /dev/sda1 - then:
```
sudo -s
mkdir /mnt/sda1
mount /dev/sda1 /mnt/sda1
chroot /mnt/sda1
```If you already have gdm installed, take the shortcut and modify <root device>/etc/X11/default-display-manager by hand.

Good luck!

---

### Post by scotty64 on 2009-12-05
My guess is that something is not in sync during the bootup process. I experience the problem only during the boot process when I get the "low resolution mode" message. When I click on "exit to console" and do nothing at the konsole login KDM respawns automatically after a few seconds and everything is fine. It looks to me as if KDM tries to start too early and the rest of the system is not ready at that point.
I am experiencing this behaviour on all kernels (generic-pae and realtime).

---

### Post by candlerb on 2009-12-06
> **sam81 said:**
> after sreadahead was updated with ureadahead in karmic, I can't get to login anymore,
the system boots, but I can't get to kdm

I had a similar problem with Xubuntu [Thinkpad X30 laptop, 1GB RAM, i915.modeset=0]

When rebooting after the ureadahead update on Dec 4th, I couldn't login. I hadn't rebooted since Nov 29th, at which time it was fine.

The symptom: it would get as far as the gdm login screen, but when I entered my username/password after a few seconds it would return to the gdm screen.

After a lot of digging, the actual problem turned out to be as follows: for some reason, one of my partitions in /etc/fstab was not being mounted. It was actually my /u partition, on which my home directories are stored (e.g. /u/home/brian, and /home symlinks to /u/home).

The hint was in /var/log/daemon.log:

Dec  4 21:48:33 ubuntu gdm-session-worker[2292]: WARNING: unable to log session
Dec  4 21:48:33 ubuntu gdm-session-worker[2292]: WARNING: could not save session and language settings: Failed to create file '/home/brian/.dmrc.F7923U': No such file or directory

So if I did ctrl-alt-F1, logged in as root and "mount /u" or "mount -a", all was fine thereafter.

Subsequent boots had the same problem, and I couldn't see anything wrong with /etc/fstab. Eventually I swapped around two lines in /etc/fstab and it all worked just fine after that - which is not really a satisfactory conclusion.

According to the manpage, mountall just reads /etc/fstab. Is it possible that it actually reads some file which is only regenerated when /etc/fstab is touched? Could ureadahead interact with mountall in some way?

I doubt that others in this thread are experiencing the same problem, but I thought it was worth mentioning. Maybe some other update between Nov 29 and Dec 4 was the culprit.

---

### Post by kolAflash on 2009-12-07
Ok, found out something new!

Looks like x11-common version 1:7.4+3ubuntu10 and gdm try to detect if the normal xsession fails. And if, they try to start a failsave session.

So that happends, when starting kdm.

Solution: Uninstall gdm OR downgrade x11-common to 1:7.4+3ubuntu7 AND LOCK x11-common in the package management, so it won't upgrade again.

This is where I found it: [http://ubuntuforums.org/showthread.php?p=8449299](http://ubuntuforums.org/showthread.php?p=8449299)

I also opened a bug-report here: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/493517](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/493517)

---

### Post by scotty64 on 2009-12-08
> **kolAflash said:**
> Ok, found out something new!
... Solution: Uninstall gdm ...

that was the perfect solution. Thank you very much!

---

### Post by kolAflash on 2009-12-11
Problem has been solved by gdm version 2.28.1-0ubuntu2.1

Just get it by the ubuntu update!

After this, you can also update x11-common to the newest version again.

---

### Post by lunix- on 2010-05-23
Having same problem on a ubuntu 10.04 server without gdm or kdm..

This is the last thing I did before restarting:

```
fdisk  (I partitioned four disks for a new raid5 array)
mdadm -C /dev/md0 -l5 -n4 /dev/sd[bcde]1
mkfs.ext4 /dev/md0
echo "/dev/md0 /server/share ext4 defaults 0 1" >> /etc/fstab
```

After restart I got this message:

fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 49801/366480 files, 287888/1464576 blocks
fsck from util-linux-ng 2.17.2
/dev/md0: clean 12/45776896 files, 3131732/183104967 blocks
init: ureadahead-other main process (755) terminated with status 4
[blinking cursor]
 
And server does not want to start.. :(

---

### Post by pbenerjee on 2010-06-05
I am facing the same problem. However, I am trying to move wubi install of 10.04 to a partition. I installed using lvpm and I get stuck at fsck check and it eternally hangs, I waited 20 mins before pressing Esc key. It jumps to the default Ubuntu dotted progress status window (Xsplash?) and just hangs. If I press Esc key again. it goes back to fsck window again !! The only way to come out was power off :(

---

### Post by lunix- on 2010-06-15
What fixed it for me was rewriting the fstab file. And things started  working great :)  Looks like fstab is very picky about spelling errors...:p

---

### Post by lunix- on 2010-07-12
Things worked well after I rewrote fstab, for a while but... 
Now I've got the same problem as pbenerjee.. server want to boot in tty7 for some strange reason and I get this message and nothing more happens.. 

fsck from util-linux-ng 2.17.2     /dev/sda1: clean 765765/87658765 files, 765765/7657658765 blocks 
[numbers are random...]

Looks like fsck hangs..

when I press esc I get the ubuntu startup screen in ascii on purple background as pbenerjee explained above.

I believe this is not a ureadahead problem, but I really need to find out why fsck stops up like this and make booting from ttyX impossible.  I dont want to use ssh always as it should be possible to log on locally...   Hope somebody with the same problem finds out why... Ill post updated is I find out anything.

(By the way.. System is actually running and server work geat.. sambashares ++ are up working and logging on from ssh works fine too...)

---

### Post by lunix- on 2010-08-01
OK,  I found a solution to my specific problem at least (at last..)
I reinstalled everything from scratch for the n'th time, but this time installing debian lenny instead (using same configuration),  that fixed it. Now things work as I want. 

I guess I would be able to fix it on ubuntu reading a few more logs and stuff,  but I was too lazy sorry..

---

