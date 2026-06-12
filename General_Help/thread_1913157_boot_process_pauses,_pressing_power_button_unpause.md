---
title: "boot process pauses, pressing power button unpauses!"
date: 2012-01-22
forum: General Help
---

### Post by benguin on 2012-01-22
Hello all,
I am quite baffled by the problem, maybe someone might be able to help me out here. I have a desktop, home-built, quad-core amd phenom II X4 black edition CPU, running Ubuntu 11.10 (and also Mint 12 -- this issues is on both distros). The links to lspci output will be attached below. Thus problem is intermittent, and started happening since I upgraded to Ubuntu 11.04 around September last year, and persists even in Ubuntu 11.10. During bootup, the boot process stops (I have disabled "quiet" mode and vga mode setting so its a pure text mode boot, with loads of messages scrolling by). By stops, I mean it just seems to be stuck at one point (also, it gets stuck at different places during different bootups). I discovered, quite accidentally, that if I gently press the power button, it resumes booting! As if, it was paused, and I just unpaused it. Different bootups might need one or more presses of the power button to continue the boot process all the way to the lightdm screen. Once there, the machine rune just fine, no problems whatsoever. dmesg does not show anything, neither does the log files.

The lspci outputs, along with a partial outout from dmidecode showing motherboard and bios info are below. I have also posted this in the Mint forum but no replies yet. Anyone has any ideas? I am happy to provide any information pertinent to the issue.

lspci -vv: [http://pastebin.com/sUrDw7UP](http://pastebin.com/sUrDw7UP)

Thanks!

-J

---

### Post by dino99 on 2012-01-22
As you says "this issues is on both distros" & "is intermittent", it seems easier to fight the issue:
- should be outside the distro
- so the first thing to check is the bios settings (for example one of my system have a crappy bios that have some hard time to detect usb and set them correctly)
- an other possible bad setting is about powersaving with a too short countdown timer
- or simply a borked formatted partition(s); are you using something else than ext3/4 ?

---

### Post by benguin on 2012-01-22
> **dino99 said:**
> As you says "this issues is on both distros" & "is intermittent", it seems easier to fight the issue:
- should be outside the distro
- so the first thing to check is the bios settings (for example one of my system have a crappy bios that have some hard time to detect usb and set them correctly)
- an other possible bad setting is about powersaving with a too short countdown timer
- or simply a borked formatted partition(s); are you using something else than ext3/4 ?

It is out of the distro, definitely, and I was basically asking for suggestions as to what it could be, which was what you provided, and I thank you for your input. Let me get to those.

1. BIOS settings: default bios settings, "fail safe" ones, do not change anything, The freeze still happens.
2. No powersaving is enabled; not even CPU scaling. The CPU is running flat out at max power. I tried with CPU scaling enabled, and even that didn't make a difference.
3. I am using two disks: one with three ext3/4 partitions, and the other with two NTFS and one ext4 partition. The drive with NTFS partition has Windows 7 installed. I booted into Windows, checked the drive/partitions, no errors. I also have SMART enabled, and the SMART reports are clean for both disks.

Among other things, I do have a few USB devices attached (my MoBo has 8 built in ports (USB 2.0) and four connectors on the board for additional front and back USB ports. I have the front ports disconnected, as the cables in my case are faulty and the ports don't work. In all, I have 7 USB devices plugged in at boot time, which include keyboard, mouse, bluetooth dongle, an 8-gig USB key (mounted via fstab at boot), an externally powered 7 port USB hub, a Canon MP250 PIXMA printer, and a webcam. Would that be a source of the issue? The other thing is, as I mentioned in my original post, upto Ubuntu 10.10 (Maverick), I did not have this problem. I had reinstalled Maverick just to see if the problem would be around, but it did not appear. So something about the Linux kernel or Ubuntu itself has changed, and has left me scratching my head.

---

