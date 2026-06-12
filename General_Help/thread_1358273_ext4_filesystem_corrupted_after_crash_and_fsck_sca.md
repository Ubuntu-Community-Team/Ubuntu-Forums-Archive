---
title: "ext4 filesystem corrupted after crash and fsck scan. ubuntu server 9.10"
date: 2009-12-18
forum: General Help
---

### Post by wodzu12 on 2009-12-18
hi
ok so, ive encountered page fault (probably due to ram errors) and had to hard reset my server.
once rebooted, it couldnt find grub files. ive run live cd and it turned out filesystem got corrupted so bad i couldn't even mount it, so ive run fsck, it asked something about wrong inodes (yes, you guessed it, im not an expert xD) and i let it "fix" everyhing.
after reboot the problem with grub persisted, so once again live cd, fsck - no errors this time, so i mounted it and...
..and now i have only one directory where was my whole filesystem, lost+found, and inside only directories named #number (#43532 #2354 etc)
ok, i'm guessing those are inodes numbers right? files inside are ok, free space is same as before crash, so i think eberything is there
problem is file structure is broken only, but how do i revert it to normal state? any chance?

if i won't fix it i'm pretty much screwed, so any help, tips or guesses are very much appreciated, thanks

---

### Post by wodzu12 on 2009-12-19
really hate to do this, but.. bump

---

### Post by dcstar on 2009-12-19
> **wodzu12 said:**
> hi
ok so, ive encountered page fault (probably due to ram errors) and had to hard reset my server.
once rebooted, it couldnt find grub files. ive run live cd and it turned out filesystem got corrupted so bad i couldn't even mount it, so ive run fsck, it asked something about wrong inodes (yes, you guessed it, im not an expert xD) and i let it "fix" everyhing.
after reboot the problem with grub persisted, so once again live cd, fsck - no errors this time, so i mounted it and...
..and now i have only one directory where was my whole filesystem, lost+found, and inside only directories named #number (#43532 #2354 etc)
ok, i'm guessing those are inodes numbers right? files inside are ok, free space is same as before crash, so i think eberything is there
problem is file structure is broken only, but how do i revert it to normal state? any chance?

if i won't fix it i'm pretty much screwed, so any help, tips or guesses are very much appreciated, thanks

The fsck did its best, but the corruption was obviously too much.

It is up to you to try and recover the system, the easiest way would be to save all of that recovered data, do a fresh reinstall and then selectively restore any important files back to where you think they should be.

---

### Post by go2dell on 2010-03-01
Hope you got this solved already.  Having suffered a similar fate years ago, I can give one helpful piece of advice if you ever suffer this problem again:  use FileLight.

Just boot from a LiveCD, mount your drives, then use FileLight to see where the biggest slice is.  That's probably all your data, conveniently stored together.  Just mouseover it to find out the exact name of the directory it's now in.

Once you have your system back up and running, just move the data under that directory back where you want it.

---

### Post by m_pav on 2010-04-16
Filelight, fantastic app, best suggestion ever if you run Desktop Linux, but this is a server, not a desktop and servers DO NOT HAVE A GUI.

Nevertheless, if the OP runs a desktop version of the Live-CD, then they might just be able to do as go2dell has suggested, provided the Live-CD has filelight installed. dcstar gave the correct advice, data reconstruction after a catastrophic failure is not fun, but it's the only way and this incident shows the lack of proper backups.

Concerning grub, I do not trust grub2 yet, so when I build a server, I always install an earlier version first with a legacy grub to handle booting, then re-install a later version over the top and elect not to install grub2, then I configure the server.

Sometimes I think Ubnutu tries too hard to use the "latest and the greatest", but when servers are concerned, ALWAYS GO STABLE and keep away from the bleeding edge stuff.

Mike P

---

