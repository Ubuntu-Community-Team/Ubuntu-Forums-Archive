---
title: "Problem with dual booting Ubuntu and XP on two harddrives"
date: 2009-10-05
forum: General Help
---

### Post by Lingonet on 2009-10-05
Hello!

I have a problem with dual booting Ubuntu and Windows XP on two different hard drives. At first I couldn't even install windows, I followed a guide which told me to set the **"SATA Configuration"** to **"Combined"** instead of **"RAID Autodetect"** and now I have both the operating system on two drives. The first thing I did was to unplug the Ubuntu drive and install Windows on **"SATA 0"** on the motherboard. This went very well, and when it had been installed I shut down and switched that drives cable to **"SATA 1"** and plugged in the Ubuntu drive in **"SATA 0"**. Then I started up, went into the BIOS and enabled both of the drives. This went well, I came to grub, logged in to Ubuntu and followed a guide how to set up Windows for grub. I shut down again, came to grub and there was **"Windows XP Professional"** at the bottom line in grub. Now when I click my way down to it and try to boot it, although the Windows logo comes up, the computer strangely restarts. I tried to boot it again but this time a window came up saying that Windows had not been properly shut down and asking me if I'd like to start it in **"Safe mode"**, **"Command Prompt"**, **"Last known working state"** and so on. This is as far as I have come, and I don't know why this isn't working. I think I have installed XP at least three times now and it's starting to get a little boring since I get the same problem over and over again.

Please give me some help!

Thank you in advance!

-Lingonet

---

### Post by Giblet5 on 2009-10-05
Why?

The correct procedure would be to put the drives in the PC correctly, then:

Install Windows, selecting drive 0.
Install Ubuntu, selecting drive 1.

From your post, **I** can't figure out which drive is which any more. If a human can't figure out this digital shell game, then how is GRUB supposed to?

If Windows is on drive 0 (for pete's sake don't start juggling drives or cables):
Reinstall Linux on the second drive.

If Windows is on drive 1:
Reinstall Linux on drive 0.

Grub will figure it out if you stop it with the drive shuffling.

---

### Post by oldfred on 2009-10-05
It sounds like you have dual boot working, but have windows issues. If windows is shut down abnormally it will when restarted give you a chance to go into safe mode or command line to do repairs. 

Since it is a fresh install without having to worry about saving data you should run the normal windows file utilites to check you system. If those do not work you may have a hard disk issue.  I would run fsck, scandisk, and/or chkdsk.

If possibly a hard disk issue and it is new enough, download from synaptic:
smartmontools - lists harddrive detail info
smartctl and smartd

---

### Post by Lingonet on 2009-10-05
> **Giblet5 said:**
> Why?

The correct procedure would be to put the drives in the PC correctly, then:

Install Windows, selecting drive 0.
Install Ubuntu, selecting drive 1.

From your post, **I** can't figure out which drive is which any more. If a human can't figure out this digital shell game, then how is GRUB supposed to?

If Windows is on drive 0 (for pete's sake don't start juggling drives or cables):
Reinstall Linux on the second drive.

If Windows is on drive 1:
Reinstall Linux on drive 0.

Grub will figure it out if you stop it with the drive shuffling.

Heh. The thing is that I already had Ubuntu installed and that's why I unplugged it and installed Windows on SATA0. So you're saying that Windows will take affect if I switch this now? Then the way of solving this would be to:

Setting Windows drive to SATA1, install, then plug in Ubuntu drive into SATA0? So that it wont be any switching for Windows.

Thank you!

---

### Post by Giblet5 on 2009-10-05
> **Lingonet said:**
> Heh. The thing is that I already had Ubuntu installed and that's why I unplugged it and installed Windows on SATA0. So you're saying that Windows will take affect if I switch this now? Then the way of solving this would be to:

Setting Windows drive to SATA1, install, then plug in Ubuntu drive into SATA0? So that it wont be any switching for Windows.

Thank you!


No, I'm saying "Stop shuffling the drives around, wait for the dust to settle, and figure out what you have". Then edit your menu.lst to match the reality of the drive config.

You can't set GRUB up, then shuffle the drives all around, and expect GRUB to work well.

What is the drive config at this point?

Is Windows on SATA-0 and Linux on SATA-1?

Then your Windows entry in menu.lst should look like:
```
title Windows Vista x64
root (hd0,0)
chainloader +1
savedefault
makeactive
```

You can verify that at the GRUB menu. Just hit 'e' to edit it. If it works, then fix your menu.lst to match and reinstall the MBR on /dev/sda.

---

