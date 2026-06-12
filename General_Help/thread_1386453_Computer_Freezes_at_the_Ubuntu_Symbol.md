---
title: "Computer Freezes at the Ubuntu Symbol"
date: 2010-01-20
forum: General Help
---

### Post by DrWolfen on 2010-01-20
Lately I've been having an issue with my netbook using ubuntu 9.10.  
After downloading and installing an update, I shut down my computer.  
When I restarted it, my computer would load up past grub, show the ubuntu symbol
 for a couple seconds and then would show a blank screen with a cursor 
I could move around but would not continue loading anything.  I tried running fsck
(which I think made the problem worse :X).  After I ran it and started up my computer again,
it froze up at the ubuntu symbol rather than showing me a blank screen.  After experiencing this, I
 tried running ubuntu in recovery mode, but I would get an error saying 

/sbin/init:error while loading shared libraries: /lib/libdus-1.so.3: only ET_DYN 
and ET_EXEC can be loaded

 a lot of other text and then 

"*ERROR* panic occurred, switching back to text console
 
and then the computer is frozen again.  I've tried going into the grub menu and booting from older kernels,
 but the same thing happens.  I've also tried reinstalling ubuntu through a live CD image in a USB 
stick and that has also been unsuccessful (usually the ubuntu symbol will flash twice, and
then disappears and then I'm stuck with a blank screen.  Does anyone have any idea of what's 
wrong and what I should do?  I've scoured the depths of google and I'm completely 
stumped.

---

### Post by mikewhatever on 2010-01-20
It could very well be a hardware problem. Have you tried running fsck from a live cd or from the existing installation?
By reinstalling Ubuntu, do you mean loading live session, or did the live session loaded ok, but the installation failed?
Have you tried running memtest?

---

### Post by DrWolfen on 2010-01-20
Whenever I try to load a Live Session through my USB drive, it fails.  I always get to the screen titled "Unetbootin" and then select "Default".  After that the Ubuntu symbol blinks twice then disappears and then I'm left with a blank screen (so I haven't been able to run fsck from the original installation or a live cd).

I've also tried memtest, but only for about 5 minutes (and nothing significant really happened when I did).  Should I leave it on overnight and see what happens I guess?

Thanks for replying btw :]

---

### Post by mr clark25 on 2010-01-20
memtest should start running tests. near the top left of the screen, it tells you the progress. does it make any progress, or does it just stay in one place?


sounds like you got a bad image. i would try downloading it again and re-installing with the new image.

if that doesnt fix it, i would guess that it is a hardware problem like mikewhatever suggested.

---

### Post by DrWolfen on 2010-01-20
I'm running memtest right now.  It's been running for about 40 minutes and it's still making progress.  Also, there haven't been any errors according to the memtest screen.

I also don't think it's a bad CD image problem because I also tried loading a live CD session with Ubuntu 9.10 Netbook Remix, Ubuntu 9.04 and Ubuntu 8.10 and they all failed.  I'm downloading Ubuntu 9.10 right now just to make sure though, maybe it'll work this time.

I guess it's probably a hardware problem?

thanks for replying btw :]

---

### Post by rogue_0111 on 2010-01-20
*I also don't think it's a bad CD image problem because I also tried loading a live CD session with Ubuntu 9.10 Netbook Remix, Ubuntu 9.04 and Ubuntu 8.10 and they all failed.  I'm downloading Ubuntu 9.10 right now just to make sure though, maybe it'll work this time.*

I'm assuming you are using the same flash drive for all these cd images. Try another Flash drive or possible a different H/D (if you have one on hand)!

---

### Post by mikewhatever on 2010-01-21
Downloading again wouldn't make sure the image isn't bad in any way. Save time and bandwidth and md5sum it.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by DrWolfen on 2010-01-21
Well, rogue_0111 you were right, it was the USB.  I was able to get the live CD image to work when I used another USB drive.  After I did this, I installed Ubuntu 9.10 which deleted anything which was on my hard drive before (fortunately, I didn't have any important files one it).  However, when I start up my computer, it gives me an error which says

 "error you need to load the kernel first"

It does this when I try to go into recovery mode too.  I tried doing something online where I used "sudo update-grub", but that didn't really help.  Any ideas of what to do?

btw thanks for the help so far everyone :]

---

### Post by FreezWay on 2010-01-21
what does uname -a spit out?

---

### Post by DrWolfen on 2010-01-21
It says "Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux"

---

### Post by DrWolfen on 2010-01-21
Well I reinstalled Ubuntu 9.10 again and for some reason it worked!  I was able to actually get past the boot screen!  Everything seems to be working fine now.  Thanks for the help everyone :]

---

### Post by rogue_0111 on 2010-01-23
> **DrWolfen said:**
> Well, rogue_0111 you were right, it was the USB.  I was able to get the live CD image to work when I used another USB drive.  After I did this, I installed Ubuntu 9.10 which deleted anything which was on my hard drive before (fortunately, I didn't have any important files one it).  However, when I start up my computer, it gives me an error which says

 "error you need to load the kernel first"

It does this when I try to go into recovery mode too.  I tried doing something online where I used "sudo update-grub", but that didn't really help.  Any ideas of what to do?

btw thanks for the help so far everyone :]


Glad to help a fellow geek.

check out this thread for your current issue:

[http://ubuntuforums.org/showthread.php?t=830795](http://ubuntuforums.org/showthread.php?t=830795)

---

