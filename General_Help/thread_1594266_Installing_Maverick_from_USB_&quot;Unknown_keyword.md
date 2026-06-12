---
title: "Installing Maverick from USB: &quot;Unknown keyword&quot; then stuck at &quot;boot:&quot; prompt"
date: 2010-10-12
forum: General Help
---

### Post by SuaSwe on 2010-10-12
Hey all,

Had a couple of problems installing Maverick from USB last night and figured I should share in case someone else finds themselves in the same situation.

Hardware: HP 4510s 1.20GHz Duo CPU
Start-out OS: Karmic 9.10
Downloaded 32-bit ISO of Maverick 10.10
Formatted USB drive to FAT32 using Gparted as Startup Disk Creator would not format it for me for some reason
Ran Startup Disk Creator on formatted drive
Rebooted, opted to boot from USB

After the boot menu but before being given any setup-related options from the Ubuntu installer, I got the following error:  

> 
SYSLINUX copyright info (I forget exact wording)
Unknown keyword in configuration file
boot: _ 


Booted back into Karmic, commented out 'ui gfxboot bootlogo' entry in the /media/USB/boot/syslinux.cfg file on the USB drive as per [[COLOR="Blue"]this post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1533282"), however whilst the "Unknown keyword" error disappeared the boot sequence still kept hanging at 'boot:'; cursor flashing but nothing happening.

Just in case anyone else experiences a similar problem, I just wanted to advise on the steps I took:

- Formatted USB drive to FAT32, used Startup Disk Creator to copy 10.04 onto it and installed this from USB - to test that there wasn't a problem with the drive itself - which worked fine
- Formatted the USB drive once again
- Recreated Startup USB
- Rebooted, and presto! Booted into installer with no issue

I never checked the MD5 so maybe there was a problem with the original startup disk creation. Have heard of issues booting Maverick from USB from older releases due to the difference in the syslinux version, however apparently the commenting out of the ui reference should have taken care of that.

Either way, all now working fine, and so far Maverick is behaving itself (except the cannot-remove-language-bar bug, but I guess one can't have everything! :) ).

---

### Post by spikoley on 2010-10-13
This [thread]("http://ubuntuforums.org/showthread.php?t=1592204") has the solution.

> Using GParted to Format a USB Stick »
Fixing USB Install Issues with Ubuntu 10.10 Maverick Meerkat
Published on October 7, 2010 in Ubuntu. 2 Comments Tags: bootlogo, fix, gfxboot, maverick meerkat, ubuntu, ui, unknown keyword in configuration file.

This morning, I attempted to install Ubuntu 10.10 Maverick Meerkat from a USB drive but received an error message to my disdain. After using the USB Startup Disk Creator to create a bootable USB installer, I rebooted only to be confronted with the following fatal error message: “Unknown keyword in configuration file”. Here’s a fix for it (thanks to JackNocturne):

NOTE: This has only been tested and reported as working on the 32-bit version of Ubuntu 10.10. Compatibility issues have been reported with the 64-bit version.

1. Using the USB Startup Disk Creator, make a bootable USB disk with the latest Ubuntu 10.10 .ISO.
2. Once the process is complete, browse to the root directory of the USB disk, click on the /syslinux folder, and open the file entitled syslinux.cfg.
3. Using a text/code editor, find the line:
ui gfxboot bootlogo
4. Change it to:
gfxboot bootlogo
5. Save the file and reboot to test — it should work now.

---

### Post by ZaHACKieL on 2011-01-04
That worked beautifully for me thanx!

---

### Post by Grinnders on 2011-01-12
:D worked for me too. thanks

---

### Post by spuudercat on 2011-01-16
Fantastic... saved a world of pain

---

### Post by LexiRedLion on 2011-02-23
Works perfectly.

---

### Post by gargoyle297 on 2011-03-02
Thanks...
Im booting with 10.10 netbook edition too...

---

