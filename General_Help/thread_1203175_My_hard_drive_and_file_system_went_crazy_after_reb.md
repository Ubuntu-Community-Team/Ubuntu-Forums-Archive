---
title: "My hard drive and file system went crazy after reboot"
date: 2009-07-03
forum: General Help
---

### Post by miketirakis on 2009-07-03
Hi, i am using ubuntu 9.04 since release, and i have set it up my way, made a perfect replacement for vista i was using before. I spent much time setting it up, and now i have a problem that is really weird.

I keep my OS fully updated, and today, after almost 7days uptime and no problem, i rebooted the system. It tried doing a file system check, a routine one, as i haven't forced one, and the computer halted at a state saying that the root file system is read only, and i should do a manual check to fix this.

I booted to live cd, checked forums here, and i unmounted my drive, remounted, and run a fsck. It found some errors, i pressed y to fix, and then rebooted again. 

The endless loop i was before, always halting and saying i should manually fsck is gone now, but the OS wont boot now. After the booting bar fills up, i get an error saying that the nvidia driver failed to load, and i should edit my configuration to fix this.

Trying to boot in recovery mode, to use the fix X-server option, is useless, because when i boot in recovery, and i get the various options, the keyboard is not working, but its ok until i get to the recovery mode.

I have backed up my documents with my live cd to my external drive, but i don't know what else to do to get my system up. Does this mean i have to reformat and reinstall ubuntu? All my programs and settings are gone?  Hope that someone can help me fix this, without reinstalling, because i really spent many hours getting ubuntu the way i liked, and i don't want to loose it all.

Btw, the file system of the drive is ext4. I am saying it because i think it may be a related to the incident.

---

### Post by mdurham on 2009-07-03
I think you should back-up your entire home directory before messing about trying to fix the problem. Most of your settings will be in the home dir, but don't forget that there are many hidden files and directories in there. I hope you can still read the partition.

---

### Post by coffeecat on 2009-07-03
> **miketirakis said:**
> Trying to boot in recovery mode, to use the fix X-server option, is useless, because when i boot in recovery, and i get the various options, the keyboard is not working, but its ok until i get to the recovery mode.

That's curious. I presume you mean that the grub menu responds to the keyboard, but not the recovery console. At the grub menu stage you are relying on the BIOS/grub reading the keyboard, but once you're in the recovery console you need certain kernel drivers. It could be that the filesystem problem corrupted more than just the nvidia driver.

You don't say whether you're using a laptop or desktop, but if a desktop is this a USB keyboard? If so, can you try using an old PS2 keyboard? This is a long shot, but it might just help you to run xfix in the console. But if it works, you might still have keyboard problems once you get a GUI back.

---

### Post by miketirakis on 2009-07-03
> **mdurham said:**
> I think you should back-up your entire home directory before messing about trying to fix the problem. Most of your settings will be in the home dir, but don't forget that there are many hidden files and directories in there. I hope you can still read the partition.

I was able to back up my data from home directory, the drive is accessible with my live usb stick. So no problem there.

> That's curious. I presume you mean that the grub menu responds to the keyboard, but not the recovery console. At the grub menu stage you are relying on the BIOS/grub reading the keyboard, but once you're in the recovery console you need certain kernel drivers. It could be that the filesystem problem corrupted more than just the nvidia driver.

You don't say whether you're using a laptop or desktop, but if a desktop is this a USB keyboard? If so, can you try using an old PS2 keyboard? This is a long shot, but it might just help you to run xfix in the console. But if it works, you might still have keyboard problems once you get a GUI back.

yes that was my next option, i am on a desktop pc, so a ps2 keyboard is my next move, because mine is a USB, but i dont have one right now to test if thats the problem. 

But if the corruption is more than the nvidia driver, sould i try to restore the OS, or forget it and go back to a fresh install?

---

### Post by coffeecat on 2009-07-03
> **miketirakis said:**
> But if the corruption is more than the nvidia driver, sould i try to restore the OS, or forget it and go back to a fresh install?

Good question. Bear in mind that I'm only theorising, but it does sound as though you have several problems there. You mentioned ext4 in an earlier post. I have no experience of ext4. Seeing some of the problems that some members have, I thought I would give it a miss for a few months at least.

Anyway, if I was in your situation, I'd try a PS2 keyboard first. If I was able to fix the GUI and there were no other problems, then fine. If not - well, that's when I would think of a reinstall. And perhaps with an ext3 filesystem for good measure. :|

One point - I'm sure you know this. Using xfix will restore the xserver but with the open-source 'nv' driver. You'd then have to reinstall the proprietary 'nvidia' driver.

---

