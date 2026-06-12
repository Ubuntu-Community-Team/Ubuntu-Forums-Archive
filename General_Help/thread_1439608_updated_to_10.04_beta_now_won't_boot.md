---
title: "updated to 10.04 beta now won't boot"
date: 2010-03-26
forum: General Help
---

### Post by Dragon42 on 2010-03-26
Very new to Ubuntu, but I was able to upgrade from 9.04 to 9.10 with no problems.  New to forum and couldnt find any help in other posts.  Like everyone, I was itching to try the newest and greatest.  Tried updating last week but had the "openoffice..." bug and wouldn't install.  Tried last night and everything went fine, until I restarted the system.  Now it won't complete the boot.  It show the GRUB, and some other startups, but them blank screen.  10 min later nothing. Tried it 3 more times.  I think I am stuck, right?  New install?  This is what I am thinking of doing- 1. boot from old cd to get my files out.  2.  fresh install of 9.10 and be patient for the offical release.  Is there anything else I could do?  Has this happened to anyone else?

---

### Post by prodigy_ on 2010-03-26
Blank screen indicates a possible problem with video driver. Does "recovery mode" option work if you select it in the Grub menu?

---

### Post by Calash on 2010-03-26
10.04 is not the latest, rather it is the testing of the latest.  Until it is released you should stick with the current release versions.


That being said there is a forum deticated to the testing of this version.  You may get better information there.

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

It does sound like a video driver issue.  Did you install custom drivers when you had 9.10?

---

### Post by 2hot6ft2 on 2010-03-26
This is a good place to start
[http://ubuntuforums.org/showthread.php?t=1433791](http://ubuntuforums.org/showthread.php?t=1433791)

---

### Post by Dragon42 on 2010-03-26
Thanks for suggestions.  I found someone else had almost same issue and they posted it a few minutes ago.  To respond, no i didnt do anything for the video.  I knew the 10.04 is in beta, but I wanted to try it out and suffer if I had issues.  Now I am worried this issue wont allow me to fix anything when the final release comes.  I will also try the GRUB options, but which one?  That was one of the first things I looked for when I restarted for the 3rd time.  I had maybe 8 choices and they where all the same except 4 had (recovery "something") at the end.  The computer is at home and dont have exact verbiage.

---

### Post by prodigy_ on 2010-03-26
If you have many items in your Grub menu, that's usually because you didn't remove older kernels (those aren't removed automatically). The most recent kernel should be the topmost. And every kernel version should be listed twice - once for normal boot and once for the so-called "recovery mode". Try to boot in recovery mode.

---

### Post by Dragon42 on 2010-03-26
That is great info!  I didn't know that about the kernel, and it makes sense.  I think I already tried the oldest one (the one on the bottom of list?).  I will try the up most option tonight, and the rest until it works or does't.   Off topic, should I clean up and remove the older kernels?  If yes, how?   If its info heavy, then I will just search the forum or send me the link.  Thanks for the knowledge Prodigy, Calash and 2hot6ft2.  The other thread suggested update GRUB2 from command line...if I can get that booted.

---

### Post by drs305 on 2010-03-26
> **Dragon42 said:**
> Off topic, should I clean up and remove the older kernels?  If yes, how?  
Many users keep two kernels, the current one and one earlier kernel which they know works. That way, if the current kernel fails, you have a backup.

There is a section in the following post that discusses various ways to remove older kernels. If you like GUI apps, I highly recommend Ubuntu-Tweak. There is a paragraph on how to install and run it.

Start at the section "Removing Older Kernels" unless you want to read some of the background prior to that section. A lot of the earlier parts deal with StartUp-Manager, which was great with Grub Legacy but isn't fully developed yet for Grub 2.

[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Dragon42 on 2010-03-27
Got it running.  Didnt use a recovery but an older kernel.  Still doesnt boot right, but I am on 10.04.  Maybe it was too soon for me to try ubuntu beta's.  Thanks for all the help and directions to more info.

Now I know, and knowing is half the battle

---

