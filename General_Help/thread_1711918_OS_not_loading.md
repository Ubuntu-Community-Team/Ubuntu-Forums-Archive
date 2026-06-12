---
title: "OS not loading"
date: 2011-03-21
forum: General Help
---

### Post by stormedwolf on 2011-03-21
I installed Ubuntu 10.10 on one of my PC's (over the old Os, because it had been corrupted). This was about 3 months ago, and I haven't had too many problems that a quick google search couldn't fix.

Until now.

Today, when I got home from work, I started up my computer and left the room for a moment. When I came back in, I looked at the monitor, and the screen was black, with a white outlined box with a list.

The contents of the list is:
Ubuntu, with Linux 2.6.35-28-generic
Ubuntu, with Linux 2.6.35-28-generic (recovery mode)
Ubuntu, with Linux 2.6.35-27-generic
Ubuntu, with Linux 2.6.35-27-generic (recovery mode)
Ubuntu, with Linux 2.6.35-25-generic
Ubuntu, with Linux 2.6.35-25-generic (recovery mode)
Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

I also have the option to press 'e' to edit the commands, and press 'c' for a command-line.

The first time I saw this, I left the list on the first option, and hit enter, the screen went black, and the only thing visible was a blinking cursor in the top left hand corner of the screen. I can type on the screen, but nothing happens.

**Edit:** After a few minutes on this screen, it goes to the normal Ubuntu loading screen (like when I'm normally starting the computer). I've waited for another 10 minutes, but there hasn't been any change.

**Edit:** After another 5 minutes some text appears, most of it has something to do with an error in one of the logical blocks. some of the text says Failed Command: READ DMA. I'm starting to think this could be a problem with my computer, not Ubuntu.

So, I found my old install disk for 10.10, thinking it was my last resort, and put it in my disk drive. I restarted the computer, and opened the boot menu. When I selected the CDROM option in the list, the screen went through some loading processes, and went to the same black screen, then went completely black, like the monitor had been turned off, but then went to another black screen, this time with a smaller cursor in the same corner. After about 5 minutes of that, the Ubuntu loading screen (the purple one with the dots under the logo) came up. I waited at least 5 minutes, but with no results.

I'm really not sure what to do. I hadn't had any warnings for this, and didn't even know anything was wrong until I tried to boot the computer up. I'm not sure if this has happened to anyone else, but I would really appreciate some help, thanks.

---

### Post by oldfred on 2011-03-21
Have you tried recovery mode, the second line? That will show the boot process and may give a clue to where it fails or what does not load. 

Also have you run memory test. OFten best to run overnight.

---

### Post by stormedwolf on 2011-03-22
Yes, I ran the memory test for a few hours, a handful of errors occurred on test 5. I didn't try the recovery mode option. Eventually, the computer did start up (in non-recovery mode), and I was able to log in. I didn't have any issues once i was able to log in, but I still hadn't solved any problems. I had to restart my computer today to finish the installation of a program, and this time, no menu showed up, but it's still taking incredibly long (20-30+ minutes)

If this happens again, I'll leave the memory test overnight and see what happens in the morning.

If it still takes as long the next time I have to restart the computer, I may just back up all my files onto my other computer, and re-install Ubuntu, so that I can overwrite the current system files, which will hopefully fix my problem.

---

