---
title: "Sound becomes fuzzy when nVidia drivers are installed."
date: 2010-06-07
forum: General Help
---

### Post by Goldfoot on 2010-06-07
Ok, let me start by saying that I did search, a lot, and couldn't find a  solution to my specific problem.  If it's somewhere in the  Comprehensive Sound Problems Solutions Guide, then I didn't find it and none of the stuff in there that seemed like it might be helpful actually was.  

I just installed 10.04 (64 bit, in case that matters) last week.   I  have onboard sound and video,  and they working fine until I installed  the proprietary drivers for my video card.  When this happened, my sound  got all fuzzy/scratchy.  I can go back into the Hardware Drivers and  remove the proprietary ones and then the sound is fine.  My problem is  that I want to use better drivers for my video, but not at the sacrifice  of sound quality.  I went to the nVidia site, and they have drivers  from April 24, 2010 on there, but those didn't help my issue, and actually caused some problems of their own.

I have an ECS GeForce7050M-M motherboard.  The nVidia site detected a GeForce GTX 480 for video. My audio is Realtek ALC662 Rev1.   I had this  same problem when I tried 8.04, 8.10, and 9.04, but I didn't narrow it down to the  nVidia drivers at the time.  This time I was able to, but I don't know  how I can fix my issue.  After about a week of not having the video drivers, I installed them because the default drivers caused some pretty substantial  slow down on my computer.   Now I have that  fuzzy I sound I mentioned, and it's very irritating.  I use my computer  for music and watching videos more than anything else and having a sound  issue like this is very upsetting.  I've tried removing/purging the  existing sound drivers and then reinstalling them but that didn't do  anything for my issue.  

I don't really know where else to start because I  have no idea what the video drivers may have done to my system that  would effect the sound.  Like I said, before I installed the proprietary  video drivers the sound worked fine, but now that the video drivers are  installed, there's a distinct fuzzy or scratchy sound whenever a sound  is played.  I would really like to use Ubuntu exclusively, but if I cannot get this working, I am going to have to go back to Windows.  I don't know what else to do, and I don't want to do that, but this is a make or break issue for me and for all the things wrong with Windows, I've never had an issue like this.  Does anyone have any ideas or has solved this specific problem?

---

### Post by kampman on 2010-06-07
How are your speakers connected? Are you just using a pair of speakers plugged into the green jack on the back of the motherboard, or something more elaborate (6-channel, SPDIF)?

---

### Post by Goldfoot on 2010-06-07
> **kampman said:**
> How are your speakers connected? Are you just using a pair of speakers plugged into the green jack on the back of the motherboard, or something more elaborate (6-channel, SPDIF)?

Yeah, just a 3.5mm stereo plug in the back of the motherboard.  It's not the plug because, like I said, I can remove the proprietary drivers and the sound is fine.

---

### Post by kampman on 2010-06-08
Have you tried messing around with the levels in Alsamixer? (open a terminal window and type alsamixer)? I don't know why activating the nvidia drivers would do it but maybe the master or PCM volume is up too high causing a distorted sound. If that fixes it, you have to run 'alsactl store' to actually save your new settings.

There are a couple of complaints about the on-board sound on this motherboard in the reviews on Newegg. You might want to consider disabling the on-board sound in your BIOS and installing an old PCI sound card.

---

