---
title: "Ubuntu won't start after update"
date: 2011-07-28
forum: General Help
---

### Post by eggmanneo on 2011-07-28
Today I downloaded an update (can't remember which ones they were exactly) and afterwards I was told I needed to restart my computer.  But once this happened I couldn't even get to the GRUB menu.  before the grub menu was supposed to appear I got this error message 
"error: no such device: /ubuntu/disks/root.disk" and 
"error: no such device: /ubuntu/install/boot/grub/grub.cfg"  
afterwards I get to some command line version of grub where I can type in commands like "reboot" but i don't have my old menu where I just selected the kernel I wanted.  I have a dual boot with Wubi if that makes any difference.  Does anybody have a way I can recover my copy of Ubuntu, or will I need to reinstall?

---

### Post by Frogs Hair on 2011-07-28
See this thread . [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)  (WubiMega)

---

### Post by bcbc on 2011-07-28
Boot windows, go to the \ubuntu folder and check there is a \disks subfolder that contains the root.disk and swap.disk files.

If one or all of these is missing, you need to look for a hidden folder \found.000 on the drive you installed Ubuntu to.

e.g. if it's C:\ look for C:\found.000. To do this, go to a command prompt (on XP click START, Run: CMD) (on Vista/7 click START, type CMD, and on CMD.exe above, right-click and choose Run as Administrator).
Then
```
CD \found.000
```

If the whole \ubuntu\disks directory is missing you might find a folder dir0000.chk. You'll need to move the contents back to \ubuntu\disks

If just the root.disk is missing, you might find it as root.disk or chk0000.chk. Move back and rename to root.disk

---

### Post by eggmanneo on 2011-07-28
I see the ubuntu folder in windows but I can't open it.  In the Wubi meagethread, I see instructions for fixing Wubi if you have Ubuntu 10.04 and other 10. versions but I have the latest 11.04 on my computer.  Is there any special instructions for 11.04 or should I just follow the instructions for fixing Wubi with the 10.04 version?

---

### Post by bcbc on 2011-07-28
> **eggmanneo said:**
> I see the ubuntu folder in windows but I can't open it.  In the Wubi meagethread, I see instructions for fixing Wubi if you have Ubuntu 10.04 and other 10. versions but I have the latest 11.04 on my computer.  Is there any special instructions for 11.04 or should I just follow the instructions for fixing Wubi with the 10.04 version?

If you're referring to problem #1 and #2 in the megathread, then they don't apply. You have some ntfs corruption - most likely this is caused by doing a hard shutdown, but if this isn't the case let me know.

In any case, you should run chkdsk. Open My computer (xp) or Computer (vista/7). Right click on the C: drive, Properties, Tools, Check disk for errors. Check: Fix errors automatically. Then it will tell you it can't run it while the drive is in use. Agree to let it run next time you boot. Reboot to complete and let it finish. Then repeat to look again for the files I mentioned before.

PS if you didn't install on C:, then replace that with whatever drive you installed on. In that case, you won't have to reboot.

---

### Post by eggmanneo on 2011-07-28
Ubuntu's working now, thanks for your help.  I found the folder C:\found.000\dir0000.chk. I then copied the entire folder into C:\ubuntu and then renames it \disks.  I didn't do a hard reboot initially, so I don't know what initially caused the corruption.  Now I have 16G (the size of my wubi installation) less space on the C drive.  I still have enough space, but should I have deleted something, is there a problem that I have two root.disk files in two different places?

---

### Post by bcbc on 2011-07-28
> **eggmanneo said:**
> Ubuntu's working now, thanks for your help.  I found the folder C:\found.000\dir0000.chk. I then copied the entire folder into C:\ubuntu and then renames it \disks.  I didn't do a hard reboot initially, so I don't know what initially caused the corruption.  Now I have 16G (the size of my wubi installation) less space on the C drive.  I still have enough space, but should I have deleted something, is there a problem that I have two root.disk files in two different places?

You can clear out the c:\found.000 if everything is back to normal. It's sitting there as a backup which is okay if you want it... with Wubi there are two backup strategies: 
1. copy the entire root.disk (easy but inefficient)
2. copy data/settings/programs (same as for a normal install)

Personally I back up the root.disk if I'm about to do a major update (or something experimental). Otherwise I just keep data backed up.

Since you've experienced corruption like this - I'd take a cautious approach and backup frequently if there's important data on the root.disk. And maybe consider [migrating]("http://ubuntuforums.org/showthread.php?t=1519354") to a partition install if you're intending to use Ubuntu longterm.

---

