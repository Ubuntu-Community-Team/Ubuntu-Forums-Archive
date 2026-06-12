---
title: "No sound - Dapper - CMedia 8738..."
date: 2006-06-07
forum: General Help
---

### Post by Mtnear on 2006-06-07
After installing the Breezy Badger version of Ubuntu I cannot hear any sound or play any music through the system.  I'm new to Ubuntu, but I can see that this may be a common problem from the forums searches that I've done.  I just haven't located a fix yet.  Upgrading to the Dapper Drake release did not fix the issue either.

My motherboard is a Chaintech Apogee 7NJL1 which has the sound onboard via the CMedia 8738 chipset.

One thing I’ve noticed is that I get an error when starting the fm tuner program regarding /dev/radio.  I’m not sure if this is related or something else.  Any help would be appreciated on how to diagnose this problem.

---

### Post by mattkenn4545 on 2006-06-07
Double click the sound applet (by the clock) then go to preferences and your looking for ic-something output that should get you going

Are you using spdif for sound output?

Sorry for the incoherence but I'm at work

---

### Post by Mtnear on 2006-06-08
Mattkenn thanks for the response.

I didn't see any "ic-something output".  I can however find my CMedia device and driver listed in the ubuntu system when I look under system devices, so I think it has detected it okay.

I can open amarok and play a stream for example and it shows the music playing, but there is no sound at all.  I double clicked on the sound icon near the clock and checked everything to make sure nothing was muted and it all looks fine.  I'm stuck.

---

### Post by mattkenn4545 on 2006-06-08
OK try this
1. By the clock double click the sound applet to bring up the volume control
2. go to Edit->Prefs
3. Look through that list and see if there is any switches that are for IEC* (mine is (IEC958 Output)
4. Once you find that look in the switches tab and make sure that the output is selected

See if the does the trick

---

### Post by Mtnear on 2006-06-12
Okay, sorry to not follow up on this in case anyone else is having the same problem, and thanks again mattkenn for providing some help.  Here is the latest in this issue.

I now have a dual boot system of Win Xp and Ubuntu 6.06.  I ended up deleting the single Breezy Badger upgraded to Dapper Drake system that I had when I previously wrote this post.  Anyway, I'm bringing that up only because I've been unable to get the onboard cmedia sound to work in Windows as well even with all the included motherboard drivers installed.  I've built many pc's and I've never had this type of problem.  I ended up installing a Soundblaster! 24bit sound card that I wasn't using to get sound to work under Windows, but since that hardware isn't supported under linux (at least that was my experience the last time I tried to use it under Fedora Core 3) I still don't have any sound in Ubuntu.  I can still open programs like xmms for example, pick a stream off of shoutcast.com and then see it playing in the player, but there's no sound no matter what I do.  

Mattkenn, I haven't completely tried your instructions above.  I will give that a shot next.  I just wanted to ask if I can't get this onboard cmedia working, does anyone happen to know if Dapper can support my soundblaster card?  Thanks.

---

### Post by mattkenn4545 on 2006-06-12
I'd Think that it will work being that soundblasters are fairly common

---

### Post by Mtnear on 2006-06-29
I haven't messed with this issue any further, but since I don't want to let this thread end without resolve I've decided to do a fresh install with the onboard audio turned off in the bios.

This comes after reading many posts from people who are saying their soundblaster cards worked directly after install with no tweaking needed.  I'm wondering if my issue has been complicated since the original CMedia onboard audio was turned on and didn't work, and then I switched to the soundblaster pci card.  I'm hoping that a fresh install would directly find my soundcard and get it working?  Hopefully I'll be able to try this soon.

---

### Post by wingzinco on 2006-06-30
Thanks, please keep us posted.  I have a Soundblaster card that was working fine with Breezy but since the upgrade I've had no luck.  I have a dual boot (xp/ubuntu) machine and was also considering a fresh install of Dapper.  Hope it works out for you.

---

### Post by Mtnear on 2006-06-30
Well, it looks like this probably isn't going to solve my problem.  I was able to take the time last night to pop the dapper 6.06 live cd in my system, make sure the onboard audio was turned off in the bios and let the system boot up into the live cd system.  When I check the sound under preferences it still shows the cmedia8738 listed as my default sound and no sign of the soundblaster live card in the available options.  This is very disappointing, and I'm wondering if there is a way to just load the emu*** driver that I hear everyone with soundblaster cards using?  I'm dual booting, and the soundblaster card is working fine under XP, so I know it's functioning okay.

---

### Post by Mtnear on 2006-06-30
By the way, [this thread]("http://www.ubuntuforums.org/showthread.php?t=19307") seems to be the best information I've found yet on how to possibly get this working.  I'll be trying this next.

---

### Post by Mtnear on 2006-07-03
Well, this thread no doubt continues to be confusing to anyone who referenced it for sound help, but here is my latest on the issue.  I decided to turn the onboard sound back on in the bios, booted up, and now sound works fine.  Only, the wires for my speakers are plugged into my soundblaster pci card, not the onboard audio jacks.  This makes absolutely no sense.  Looking under preferences > sound shows the CMedia 8738 driver being used which is finally correct for my onboard sound, but again the speakers aren't plugged into the onboard jacks.  I'm assuming that this means the soundblaster card is working by way of the CMedia 8738 sound driver instead of it's own.  Oh well, sound works for now.  I'll still be investigating this to figure out what's going on if anyone happens to have similar problems.

---

### Post by cvmostert on 2006-10-19
i have the same problem here at a freinds house... if you get whats going on... pls PM me.

I still do not get youtube working with sound... flash sound...

---

