---
title: "Troublesome boot, AHCI driver problem?"
date: 2010-05-07
forum: General Help
---

### Post by vintageveloce on 2010-05-07
Here is my problem:

In short, it takes forever (6 min), and lots of prodding to get Ubuntu to boot.

Im running a Toshiba NB305 netbook (Bios 1.40), set up for dual boot with 10.04 UNR.
Windows partitions boot fine. Can boot 10.04 from USB stick.

Here how I try to boot:
From grub menu select "Ubuntu, with Linux 2.6.32-22-generic"
If it doesn't work, I run the recovery version, and then run the regular one again. Somehow that resets stuff.

After about a minute I sometimes get this:

         Gave up waiting for root device. Common problems:
         - Boot args (cat /proc/cmdline)
         - Check rootdelay= (did the system wait long enough?)
         - Check root= (did the system wait for the right device?)
         - Missing modules (cat /proc/modules; ls /dev)
         ALERT! /dev/disk/by-uuid/<myUUID> does not exist. Dropping to a shell!

         BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
         Enter 'help' for a list of built-in commands.

         (initramfs)

I type "exit" and hit enter. 

     _ (curser flashes) And the machine looks stuck. 

Sometimes I hit return a few times in frustration.
After about 6 minutes (really!) Ubuntu boots. 

I've attached the output from boot_info_script055.sh

The drives look Ok to me? And it does eventually boot. So I was suspecting a missing module/driver issue.

I've tried to find some stuff on the initrd.img, but haven't figured anything out there.

Somewhere I read to try changing a setting in the BIOS: I changed the SATA Controller Mode from "AHCI to Compatibility". Amazingly, Ubuntu booted cleanly in about a minute. Of course, my other partition of Windows 7 will not boot in this mode. So I really want AHCI to work.

I'm guessing that maybe the AHCI driver is missing or broken? Can this be fixed/reinstalled? I've read that:
"In Karmic, the ahci driver was built in by default in the kernel.  However, in Lucid, this driver is now enabled as a module." (Bug #570542)
Could this be the problem? Or am I missing something simpler?
Is there a useful log to look at that can show me what happens in that dead 5 
minutes?

This newbie would appreciate your expert help! ;-)
Carl

---

### Post by vintageveloce on 2010-05-08
Made some real progress with this. See post 96 and on in this thread:
[http://ubuntuforums.org/showthread.php?t=1382481](http://ubuntuforums.org/showthread.php?t=1382481)

---

