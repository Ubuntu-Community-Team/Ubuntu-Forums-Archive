---
title: "Serious problem with installing Kubuntu 9.10"
date: 2009-11-26
forum: General Help
---

### Post by kajman on 2009-11-26
Hi all!

I've decided to switch to newer version of Kubuntu because of some serius problems with my 9.04. 

I've downloaded the 9.10 image from kubuntu site, checked the md5 sum before burning it, and then I've verified the burn (all done in K3b, and ofcourse the checksum and verification was ok). Then, before the installation I tried to test the integrity of my CD, just to be sure from the menu after booting the CD. 

This is the point where I've encountered the first problem. When the integrity check starts, my laptop reboots every time. It's very wierd I think. But ignoring this issue (checksum and verification was ok, so...) I tried to install it anyway.

I've chosen partitions at my own (/boot, /, swap and /home, the same as I did in the previous 9.04 install, not formatting the /home and formatting the rest). I've typed all the data needed (name, pass, etc) and confirmed that everything is ok. The installer tried to format partitions chosen earlier, but a wierd error ocurred: that my /cdrom is still mounted and the installer is unable to unmount it, so the installer is unable to create a partition table or something similar. I pressed a button that supposed to make him recheck that issue, but instead it took me to the point where I have to choose partitions for my install.

And another issue here: the installer works so slow! I've checked 'top' on tty1 and as it came up a process called ubiquity is taking about 65-70% and Xorg the rest of my CPU time. EVEN if I just leave the installer without making it to do anything. Wierd. So choosing the partitions to install is very annoying as it takes much longer then it supposed to. I tried again and again (with my cdrom lid open) but the installer still is unable to unmount the /cdrom and still takes me back to partition choosing.

Why is it happening? I have to reinstall my system as quick as possible, and really don't know whats happening.

Thank you all for any advice.

PS. tried to use liveusb to install it from my pendrive, but it was taking very long time to put every file on it (about 10-15minutes! and its only 700mb of data!), and also it didn't boot properly (i've booted many distros from it already so it formated as it should be).

cheers,
kajman

---

### Post by audiomick on 2009-11-26
Hallo.
What I would do first, is simple exclusion of possible faults.
Try booting from another live CD, Knoppix maybe. This should show that the CD drive is ok or not.
Re-make the CD, even if it did test OK.

---

### Post by kajman on 2009-11-26
I've checked the CD on other PC and it passed the integrity test.
Also I've booted the install from my pendrive, and tried to install the system. It gave me the same error as before - unable to unmount /cdrom. Why is that?

I had serious problems before (almost returned my laptop to service) under 9.04. It crashed so badly, that I didn't see anything apart of some vertical lines when I started the pc (no massages like "Press <F1> to enter setup" and so on). But apparently it was loading the system, because when I've waited enough and pressed Ctrl+Alt+F1 it went to console (which I assume, because I didn't see anything) and then when I've pressed Ctrl+Alt+Delete it rebooted my machine after a long while in a "nice way". The problem with screen was solved this way, but I've got some problems with Xserver (which didn't start at first). I've got rid of them running fsck from recovery mode (had an error: NFS stale file or something). But even after that my system crashes randomly like it did earlier but comes back on feet after a simple reset. It is impossible to work on such a machine. A pity is that, the other OS I have - Windows Vista is working without any problems, just as it used before, so I assume it is not a harware problem.

The saddest thing is that I cannot reinstall my much more liked OS. What should I do? Maybe I should format the '/boot' and '/' partitions from GParted for e.g. and then try to use installer?

I'll try to reinstall Kubuntu 9.04, then maybe Ubuntu 9.04 or debian 5.01 which are the distros I have on my drive at the time. Maybe they won't have problem with unmounting my /cdrom. 

In the meantime I'd appreciate any other suggestions,
cheers,
kajman

---

