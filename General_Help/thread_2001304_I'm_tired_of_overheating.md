---
title: "I'm tired of overheating"
date: 2012-06-10
forum: General Help
---

### Post by batophobia on 2012-06-10
I was upgrading from 11.10 to 12 and my system overheated midway. now I can't even boot from usb or disk. the error suggests I'm missing drivers but i can get to a root terminal.

toshiba satellite L305D-S5974

---

### Post by latinlightning on 2012-06-10
Please give the exact model so you can receive better assistance (you can check underneath your laptop or check the manufacturer's documentation).

---

### Post by batophobia on 2012-06-10
satellite L305D-S5974

---

### Post by latinlightning on 2012-06-10
Did you have any problems when it was running 11.10? Assuming that you do have overheating problems, how loud/noisy was the laptop when running resource hungry apps (games, videos, etc)?

---

### Post by batophobia on 2012-06-10
it ran ok before except it kept overheating. my research on it suggests that my laptop fan drivers are unsupported on ubuntu

---

### Post by Toz on 2012-06-10
Have you tried running with extra kernel parameters? I'd suggest giving **acpi_osi="Linux"** a try.

Here is how (enter commands in a terminal window):
1. Edit the grub file:
```
gksudo gedit /etc/default/grub
```

2. Add the parameter on the **GRUB_CMDLINE_LINUX=""** line so that the line looks like this:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"Linux\""
```

3. Save the file

4. Rebuild grub:
```
sudo update-grub
```

5. Reboot to test

If it doesn't work after boot, post back the results of this command:
```
cat /proc/cmdline
```

---

### Post by batophobia on 2012-06-10
For future reference, I have no graphical system available right now.  The only thing I can get is a root terminal.  When I try ```
pico /etc/default/grub
``` I get a warning saying "No write permission".  Trying the edit on the file anyway, I of course get the error that it is a "Read-only file system".

---

### Post by Toz on 2012-06-10
Ok. Then try:
```
sudo pico /etc/default/grub
```

---

### Post by batophobia on 2012-06-10
My apologies that is what I tried.  Force of habit has me retrying commands with a "sudo" if it didn't work the first time...

---

### Post by Toz on 2012-06-11
Hmmm. What does the following return?
```
ls -l /etc/default/grub
```
...and
```
cat /etc/mtab
```

---

### Post by batophobia on 2012-06-11
```
-rw-r--r-- 1 root root 1244
```
&
```
/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none sys/kernel/debug debugfs rw 0 0
none sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
```

---

### Post by Toz on 2012-06-12
That really should work. Can you try:
```
sudo pico /etc/default/grub
```
... again (entering your password when prompted) and post back the exact error message you are getting?

You could also try:
```
sudo bash
pico /etc/default/grub
```

---

### Post by batophobia on 2012-06-12
I just realized that it has yet to ask me for my password, likely because I am in a root maintenance shell.
```
root@systemname:/#
```
After running sudo bash I get no feedback, just another line for input.
Running your other command (both with and without sudo) leads to the read-only file.

---

### Post by Toz on 2012-06-12
Oh. Why are you in the root maintenance shell? Try remounting / as read/write with the following command:
```
mount -o remount,rw /
```
...then try:
```
pico /etc/default/grub
```

Otherwise, boot normally and follow the instructions using sudo.

---

### Post by steve7777777 on 2012-06-12
> **batophobia said:**
> I was upgrading from 11.10 to 12 and my system overheated midway. now I **can't even boot from usb or disk.** the error suggests I'm missing drivers but i can get to a root terminal.

toshiba satellite L305D-S5974

Sounds like a hardware problem to me. Likely the CPU isn't being cooled or some other hardware problem if unable to boot off of a live cd/usb.

---

### Post by batophobia on 2012-06-13
> **steve7777777 said:**
> Sounds like a hardware problem to me. Likely the CPU isn't being cooled or some other hardware problem if unable to boot off of a live cd/usb.
  I know it is the CPU overheating and it is because ubuntu doesn't support my fan drivers.

**Toz:** mount commands gives following error:
```
[     26.971771] EXT4-fs (sda1):re-mounted. Opts: errors=remount-ro
```

---

### Post by HermanAB on 2012-06-13
Howdy,

As the unhappy owner of a similar Toshiba...

I strongly suggest that you install some sort of Windows on the machine and sell it on Ebay, then buy a Lenovo.

Otherwise, get a Dremel and cut open the bottom of the laptop machine around the fan (cut out a large square - the larger, the better, so you can get to everything without having to cut again).  Solder wires to the fan and the outer power wires of a USB port so that it runs permanently, then use superglue and epoxy to put the bottom piece of plastic back.  Do not try to disassemble the machine from the top down to get to the fan - the connectors are very fragile and you would very likely break something.  It is much better to leave the machine in one piece and cut open the bottom.

If you don't do the above, then the GPU *will* burn out.  Once that happened, you could try buying a USB-HDMI adaptor to drive an external screen and use the machine as a DVD player or a server, since you will most probably not be able to find a replacement motherboard anywhere.

---

### Post by batophobia on 2012-06-13
Not the answer I was expecting but thanks for not beating around the bush.  I have been trying to put windows on it but as you may have read my cd drive doesn't seem to be working (driver issues?)  I was wondering if it might work if I clear off the hard drive first and install on a clean drive.  Only question there is how do I do it from the maintenance shell.  Perhaps ```
*rm -rf /*
```

---

### Post by Toz on 2012-06-13
> **batophobia said:**
> I know it is the CPU overheating and it is because ubuntu doesn't support my fan drivers.

**Toz:** mount commands gives following error:
```
[     26.971771] EXT4-fs (sda1):re-mounted. Opts: errors=remount-ro
```

What about the second command? Are you able to edit the /etc/default/grub file?

---

### Post by batophobia on 2012-06-13
No, and I've tried it multiple ways.

---

### Post by Toz on 2012-06-13
Try logging into the system normally, not in recovery mode. Then try:
```
sudo pico /etc/default/grub
```

... or

```
sudo bash
pico /etc/default/grub
```

---

### Post by batophobia on 2012-06-14
Perhaps I'm not being clear enough.  I cannot log into anything normally.  Regardless of how I try to boot up I get a maintenance shell (3 different versions and recovery mode for each one).

---

### Post by Toz on 2012-06-14
Oh. You're overheating problem is secondary. Your real problem is that you can't boot into linux. When you boot, are you getting error messages about a corrupted file system? Maybe this is why your going to maintenance mode? If so, have you tried running fsck to repair the file system?

---

### Post by batophobia on 2012-06-14
There are several lines that fly by when starting up that I can't read but this is what I can read:
```
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Write cache: endabled, read cache: enabled, does
n't support DPO or FUA
scsi 2:0:0:0: CD-ROM          TSSTcorp CDDVDW TS-L633C   TF01 PQ
: 0 ANSI: 5
sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda
tray
cdrom: uniform CD-ROM driver Revision: 3.20
sr 2:0:0:0: Attached scsi generic sg1 type 5
 sda: sda1 sda2 < sda5 >
sd 0:0:0:0: [sda] Attached SCSI disk
Begin: running /scriptes/local-premount ... done.
EXT4-fs (sda1): INFO: recovery required on readonly filesystem
EXT4-fs (sda1): write access will be enabled during recovery
EXT4-fs (sda1): recovery complete
EXT4-fs (sda1): mounted filesystem with ordered data mode. 0pts:
(null)
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
init: mountall main process (268) killed by FPE signal
general error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
root@systemname:~#
```running fsck gives the following:
```
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1: 362584/15089664 files (0.2% non-contiguous), 29450598/60329216 blocks
```

---

### Post by Toz on 2012-06-14
How about sda5?

When booting, hold down the shift key and from the grub screen select the entry with the work "recovery" in it. This will also get you into maintenance mode, but it should bring up a menu with fsck as an option to check all of your partitions.

---

### Post by batophobia on 2012-06-14
I tried holding down the shift key while booting but from what I can see nothing is any different.  There was no fsck menu and trying to run fsck sda5 gives the fsck list of commands.

---

### Post by Toz on 2012-06-14
The command would be:
```
fsck /dev/sda5
```

---

### Post by batophobia on 2012-06-14
fsck.swap: not found
Error 2 while executing fsck.swap for /dev/sda5

---

### Post by Toz on 2012-06-15
Oops, that must be the swap. Try sda2:
```
fsck /dev/sda2
```

---

### Post by Paqman on 2012-06-15
> **batophobia said:**
> it ran ok before except it kept overheating. my research on it suggests that my laptop fan drivers are unsupported on ubuntu

The fans are controlled by BIOS, they're nothing to do with the OS.

---

### Post by Hari5g900 on 2012-06-15
If there are problems with Toshiba Satellites, then I think I should not buy one, should I ? (if this is hijacking, please tell me so. I am sorry). But then, Is your toshiba old? May be if you service it in some way,(get the fans replaced) you might be able to stop this problem:confused:.

---

### Post by Mark Phelps on 2012-06-15
> **Hari5g900 said:**
> If there are problems with Toshiba Satellites, then I think I should not buy one, should I ? (if this is hijacking, please tell me so. I am sorry). But then, Is your toshiba old? May be if you service it in some way,(get the fans replaced) you might be able to stop this problem:confused:.

It's NOT a fan problem, in most cases.  It's a problem that certain versions of the Linux kernel are unable to throttle back the processor to an idle state when it's not being used much.  This causes the processor to run faster, causing it to run hotter, causing the PC to overheat.

The general solution, when it worked, has been to install Jupiter and use it to manually throttle back the processors.  Since it's then running slower, it's also running cooler.

---

### Post by Paqman on 2012-06-15
> **Mark Phelps said:**
> This causes the processor to run faster, causing it to run hotter, causing the PC to overheat.


Well, that pretty much is a fan problem. If your fans can't handle the processor running at 100% indefinitely, something is wrong.

---

### Post by batophobia on 2012-06-15
> **Paqman said:**
> The fans are controlled by BIOS, they're nothing to do with the OS.
Then maybe you can explain to me why it ran fine when I had Windows 7 on it but after installing Ubuntu my fan never worked.

For those of you arguing about if it it really the fan, I can tell you that I have tried everything to cut back on processor usage, even to the point of removing the GUI and installing LXDE.  Additionally, I did not hear the fan, which usually means it is not spinning.

Toz: fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
-p,f,c,etc. give the same result.

---

### Post by Toz on 2012-06-15
> **batophobia said:**
> Toz: fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
-p,f,c,etc. give the same result.

Somethings not adding up here.

Can you post back the contents of your /etc/fstab?  
And the results of ```
cat /proc/cmdline
```

The overheating issue is secondary. You can't seem to boot into your system:
> init: mountall main process (268) killed by FPE signal
general error mounting filesystems.
A maintenance shell will now be started.

---

### Post by batophobia on 2012-06-15
cat /proc/cmdline : 
BOOT_IMAGE=/boot/vmlinuz-3.0.0-19-generic root=UUID=aa21bed7-1900-401c-b518-7826f2e574f6 ro text

pico /etc/fstab : 
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=aa21bed7-1900-401c-b518-7826f2e574f6 / ext4 errors=remoun$
# swap was on /dev/sda5 during installation
UUID=097a42ca-d46c-4bc0-9ccb-3230c55e126d none swap sw $

---

### Post by Toz on 2012-06-16
Found a related thread [here]("http://ubuntuforums.org/showthread.php?t=1994964"). Try:
```
sudo e2fsck -f /dev/sda1
```

---

### Post by batophobia on 2012-06-16
That command ended with the same error I got after fsck -c
> **batophobia said:**
> 
```
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1: 362584/15089664 files (0.2% non-contiguous), 29450598/60329216 blocks
```
  First it did 5 passes: inodes/blocks/sizes, directory structure, directory connectivity, reference counts, & group summary

---

### Post by Toz on 2012-06-17
I'm sorry but I'm afraid I've run out of ideas. Perhaps you could create a new thread for your system only booting into maintenance mode and see if someone else has some suggestions.

Once you get that figured out, we can have another look at the overheating issue.

---

### Post by Mark Phelps on 2012-06-17
> **Paqman said:**
> Well, that pretty much is a fan problem. If your fans can't handle the processor running at 100% indefinitely, something is wrong.

Well ... yes., you're right.  

But I only said it's likely NOT a fan issue because, on some laptops, it's a HUGE amount of work to replace a fan, with the attendant risk that if any of the really fragile ribbon cables get twisted or broken, the laptop won't work when reassembled.

That's a lot of work to go through, and a lot of risk to take, only to replace the fans -- and then discover that they were not designed to handle the processor at 100% load for extended periods of time, in the first place.

I replaced a fan in a laptop a while back, so I've done this.  But in my case, I was getting alarm messages from the BIOS that the fan was failing.  So, I knew that was the problem.  IF they're getting no such messages, then it might not actually be a bad fan.

---

### Post by matt_symes on 2012-06-17
Hi

A floating point exception when trying to mount ?

Stab in the dark. Have you tried rebuilding your initramfs to see if the problem is there ?

```
sudo update-initramfs -u
```

Kind regards

---

### Post by batophobia on 2012-06-17
ln: creating hard link '/boot/initrd.img-3.0.0-19-generic.dpkg-back': Read-only file system
cp: cannot create regular file '/boot/initrd.img-3.0.0-19-generic.dpkg-back': Read-only file system

Additionally, for the sake of trying to start from scratch, I tried rm -rf / and no files on my system can be removed because it is a read-only file system.

---

### Post by matt_symes on 2012-06-17
Hi

Looks like your in a root shell there. Try this..

```
mount -n -o remount,rw /dev/sda1
```

```
sudo update-initramfs -u
```

Kind regards

---

### Post by batophobia on 2012-06-17
I ran the memory test (memtest86+, serial console 115200) and it did 3 passes (which took almost 4 hours) and said there were no errors.

The mount command gave the same error as before:
> **batophobia said:**
> 
```
[     26.971771] EXT4-fs (sda1):re-mounted. Opts: errors=remount-ro
```

---

### Post by batophobia on 2012-06-17
For the sake of clarifying my issue I have created this list.

[LIST]
[*]I was upgrading my system from 11.10 to 12
[LIST]
[*]During upgrade, system overheated (again)
[/LIST]
 
[*]When starting my machine, regardless of version, I get a maintenance shell
[LIST]
[*]The system is read only, so I can't even delete all the files
[/LIST]
 
[*]I cannot boot from a flash drive or disk drive
[LIST]
[*]Error suggested something about drivers?
[/LIST]
 
[*]I ran memory test for over 3.5 hours (3 passes) and it found no errors
[/LIST]
I do not care to get back anything on my system, as far as I am concerned the whole drive can be overwritten (key word being writ).

I would like to simply put a version of linux on where my fan would work properly, but I cannot boot from anything other than HDD (so far I tried Windows 98 and Slitaz CDs).

---

### Post by matt_symes on 2012-06-18
Hi

For the record

> [     26.971771] EXT4-fs (sda1):re-mounted. Opts: errors=remount-ro

^^^ That is not an error. It's telling you it's mounted sda1 and will remount it as read only on errors. This is a safety precaution.

> **batophobia said:**
> For the sake of clarifying my issue I have created this list.

[LIST]
[*]I was upgrading my system from 11.10 to 12
[LIST]
[*]During upgrade, system overheated (again)
[/LIST]
 
[*]When starting my machine, regardless of version, I get a maintenance shell
[LIST]
[*]The system is read only, so I can't even delete all the files
[/LIST]
 
[*]I cannot boot from a flash drive or disk drive
[LIST]
[*]Error suggested something about drivers?
[/LIST]
 
[*]I ran memory test for over 3.5 hours (3 passes) and it found no errors
[/LIST]
I do not care to get back anything on my system, as far as I am concerned the whole drive can be overwritten (key word being writ).

I would like to simply put a version of linux on where my fan would work properly, but I cannot boot from anything other than HDD (so far I tried Windows 98 and Slitaz CDs).

Personally i would back up your data and reinstall. I don't often suggest that but it may be the quicker option. See what others think though first.

> I cannot boot from a flash drive or disk drive
Error suggested something about drivers?

^^^ This is stopping you booting into a LiveCD/USB ? Can you post back the exact error message.

You need to do something about the overheating. 

Check for dust and remove any obstructions. 
Clean fan.
Replace thermal paste between chip and heat sink.
Make sure there is adequate air flow in the box.

Kind regards

---

### Post by vazduxosbra4kania on 2012-06-18
> **batophobia said:**
> I was upgrading from 11.10 to 12 and my system overheated midway. now I can't even boot from usb or disk. the error suggests I'm missing drivers but i can get to a root terminal.

toshiba satellite L305D-S5974


And yet another case of laptop overheat using Ubuntu. That is terrible.So many people are complaining from this trouble. Cant help you but i hope the problem could be solved for you cause, constant overheating would be a deal-braker in the relationship 
 USER <--> OS :mad:

---

### Post by batophobia on 2012-06-19
I managed to get an Ubuntu 12.04LTS disc to install (USB never ended up working) and it is overwriting the previous version now.  Hopefully it does not overheat.  I could never get the error to come back, it just skipped whatever I chose to boot from and went to the HDD.

---

### Post by batophobia on 2012-06-19
I am posting this reply from my now-working Ubuntu 12.04 laptop :D.  I have yet to have it overheat but the fan is either not spinning or is way to quiet.  Any way I could check it or any ideas on trying to fix it?

Edit: So about 30 seconds after posting the system overheated.  Any advice?

---

### Post by MutantJohn on 2012-06-19
Have you tried undervolting your CPU? I doubt this'll do anything but, eh, I'm bored.

---

### Post by batophobia on 2012-06-20
While my BIOS has no way of setting the CPU voltage I found an option regarding the CPU frequency.  The default it to allow the system to fluctuate and the alternative is to only allow low levels.  I changed that doesn't exactly solve the problem.

---

### Post by Toz on 2012-06-20
> **batophobia said:**
> Edit: So about 30 seconds after posting the system overheated.  Any advice?

A few suggestions:

1. What video card do you have? Have you installed the proprietary drivers?

2. Have you tried the kernel parameter from post #6: [http://ubuntuforums.org/showpost.php?p=12015976&postcount=6]("http://ubuntuforums.org/showpost.php?p=12015976&postcount=6")

3. Install the package **lm-sensors**, run:
```
sudo sensors-detect
```
...and then run:
```
sensors
```
...to get temperature/fan speed info.

4. You might want to check and see if a BIOS update is available.

---

### Post by batophobia on 2012-06-20
1. Additional Drivers suggests I need ATI/AMD proprietary FGLRX graphics driver (post-release updates or regular), but when I click Activate it fails and directs me to /var/log/jockey.log, which I can post if you want.

2. Overheated during restart
"BOOT_Image=/boot/vmlinuz-3.2.0-25-generic-pae root=UUID=3e34b3f2-ed88-45e3-bd4a-efa3bfeea597 ro acpi_osi=Linux quiet splash vt.handoff=7"

3. CPU: AMD Family 11h thermal sensors (driver 'k10temp')
SuperI/O: National Semiconductor/ITE - Found unknown chip with ID 0xfc11
I2C/SMBus: driver 'i2c-piix4' device 0000:00:14.0: ATI SB600/SB700/SB800 SMBus - i2c-dev loaded successfully.
SMBus PIIX4: SPD EEPROM (confidence 8, not a hardware monitoring chip)

4. How might I go about doing that?

---

### Post by Toz on 2012-06-20
> 1. Additional Drivers suggests I need ATI/AMD proprietary FGLRX graphics driver (post-release updates or regular), but when I click Activate it fails and directs me to /var/log/jockey.log, which I can post if you want.Can you post this log file?

EDIT:
And the results of:
```
sudo lspci -vnn | grep -A10 VGA
```

---

### Post by Toz on 2012-06-20
> **batophobia said:**
> 4. How might I go about doing that?
See here: [http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2515193&rpn=PSLCJU&modelFilter=&selCategory=2756709&selFamily=1073768663]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2515193&rpn=PSLCJU&modelFilter=&selCategory=2756709&selFamily=1073768663")

---

### Post by batophobia on 2012-06-20
The BIOS says Rev. 3.5 but I couldn't find anywhere to upgrade it.

```

01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS780MC [Mobility Radeon HD 3100 Graphics] [1002:9613] (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device [1179:ff6a]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 6000 [size=256]
    Memory at d6200000 (32-bit, non-prefetchable) [size=64K]
    Memory at d6100000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: fglrx_pci

```
The log file is fairly big but I think this chunk is the right piece:
```
2012-06-19 20:47:48,557 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7203d0c>
2012-06-19 20:47:54,323 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic-pae/modules.alias
2012-06-19 20:47:54,822 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-06-19 20:47:54,840 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-06-19 20:47:55,086 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-06-19 20:47:55,184 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-06-19 20:47:55,201 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-06-19 20:47:55,549 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-06-19 20:47:55,550 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-06-19 20:47:55,732 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-06-19 20:47:55,733 DEBUG: Firmware for DVB cards not available
2012-06-19 20:47:55,733 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-06-19 20:47:55,942 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-06-19 20:47:55,950 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-06-19 20:47:55,951 DEBUG: nvidia.available: falling back to default
2012-06-19 20:47:56,001 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-19 20:47:56,002 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-19 20:47:56,008 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-06-19 20:47:56,018 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-06-19 20:47:56,019 DEBUG: nvidia.available: falling back to default
2012-06-19 20:47:56,109 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-06-19 20:47:56,120 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates
```

EDIT: I managed to the the non-post-release driver activated so I guess that's ok now.

---

### Post by Toz on 2012-06-21
> **batophobia said:**
> EDIT: I managed to the the non-post-release driver activated so I guess that's ok now.
Is the temperature any better? Is it still overheating? What does the following return?
```
sensors
```

---

### Post by batophobia on 2012-06-21
It is still overheating.  The sensors command outputs 2 temperatures (acpitz-virtual-0 & k10temp-pci-00c3), which change as the system heats up.  Beside the current temp for the Virtual Device is a (crit = +105.0C) and beside PCI Adapter is (high 70.0C).  I used this before and it was rather common for the temperatures to be in the 70s and 80s while sitting idle WITH a GUI.

---

### Post by HermanAB on 2012-06-21
Howdy,

You HAVE to get that fan running, or you will burn the motherboard == new computer.

Get a 'laptop cooler' for the meantime, to force air in from the bottom.

---

### Post by Toz on 2012-06-21
Have a look [here]("http://ubuntuforums.org/showpost.php?p=10305008&postcount=55"). The suggestion is to use the **acpi_osi=** kernel parameter (and not specifying anything after the = sign). If you have a full graphical install now:
```
gksudo gedit /etc/default/grub
```
...add the parameter to the GRUB_CMDLINE_LINUX="" line so that it looks like this:
```
GRUB_CMDLINE_LINUX="acpi_osi="
```
...save the file then run:
```
sudo update-grub
```
...and reboot.

On reboot, post back whether it works and the results of:
```
cat /proc/cmdline
```

---

### Post by batophobia on 2012-06-22
Same as before.  I'll try restarting the system and check again, if any change I'll edit.
> **batophobia said:**
> 
"BOOT_Image=/boot/vmlinuz-3.2.0-25-generic-pae root=UUID=3e34b3f2-ed88-45e3-bd4a-efa3bfeea597 ro acpi_osi=Linux quiet splash vt.handoff=7"


EDIT: After restarting the "Linux" (after acpi_osi=) was removed.

---

### Post by Toz on 2012-06-22
You'll have to remove the acpi_osi=Linux parameter from your /etc/default/grub file. Can you post back the contents of **/etc/default/grub**?

---

### Post by batophobia on 2012-06-23
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi="

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

This should be the default file for Linux 12 since I don't think I have changed anything since reinstalling.

---

### Post by Hari5g900 on 2012-06-26
Gosh! It is sooooooooo confusing. You should buy a new laptop I guess!!!

---

### Post by Toz on 2012-07-01
> **batophobia said:**
> ```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi="

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

This should be the default file for Linux 12 since I don't think I have changed anything since reinstalling.

That looks right. Now run:
```
sudo update-grub
```
...then restart your computer, then post back the results of:
```
cat /proc/cmdline
```
...and whether there is any change with the heat?

---

