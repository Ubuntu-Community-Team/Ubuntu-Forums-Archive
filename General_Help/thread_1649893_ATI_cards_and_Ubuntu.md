---
title: "ATI cards and Ubuntu"
date: 2010-12-20
forum: General Help
---

### Post by jworr on 2010-12-20
I've been using Nvidia graphics cards for a number of years because they were much easier to get running in Ubuntu.  I've heard recently that ATI cards are now just as easy to use with full 3d support, is that the case?  I'm not trying to troll, I'm just curious if anyone has had good experiences getting new ATI cards to fully work with Ubuntu 10.10

thanks

---

### Post by rev elation on 2010-12-20
my ATI 9800 PRO didn't work very well. using Compiz or playing games was out of the question.

my crossfire HD4770's worked somewhat better if i recall correctly. I managed to get 3D going but the performance was slow. I think results are quite varied.

Assuming this thread was made because you're pondering the question of whether or not to get an ATI card is to google testimonials to specific cards. Finding a step-for-step on how they/he/she managed to get the card in question to work flawlessly would also be a good comforter.

---

### Post by jworr on 2010-12-20
Yes, I'm mostly looking for testimonials and I tend to trust the users of this site.  I know NVIDA cards have worked well for me in the past, I'm just wondering if I should branch out :).  Since AMD bought out ATI I've heard things have improved as far as linux driver support is concerned, though it would be nice to know some people have actually managed to get the cards to work.  Are the ATI cards detected by the Ubuntu Additional drivers manager (System->Administration->Additional Drivers)?

---

### Post by rev elation on 2010-12-20
Yes they are, but when I last used ATI cards there were about 3-5 different drivers you could choose between (including the 'additional drivers'). Some would work, some would do absolutely nothing, and everyone had the same card but used different drivers with different results. That was possibly a year back though.

Hopefully things are simpler now.

---

### Post by 4Orbs on 2010-12-20
Two months ago I built a new computer with an ati HD5770 card and it works with no problem and using the proprietary driver provided in the Ubuntu repository. Actually, I had one problem. The Catalyst Control Center would not launch from the applications menu (as root). The command to launch the control center as root is:
```
gksudo amdcccle
```

---

### Post by gradinaruvasile on 2010-12-20
> **jworr said:**
> Yes, I'm mostly looking for testimonials and I tend to trust the users of this site.  I know NVIDA cards have worked well for me in the past, I'm just wondering if I should branch out :).  Since AMD bought out ATI I've heard things have improved as far as linux driver support is concerned, though it would be nice to know some people have actually managed to get the cards to work.  Are the ATI cards detected by the Ubuntu Additional drivers manager (System->Administration->Additional Drivers)?

I use nvidia cards in my Linux boxes usually. They work stable and have no issues with them.

Recently i built a computer for someone that had an Ati onboard card in it. I put my hdd on it and gave it a test ride for 2 days. Here is what i observed:

First, the hardware:
I have a Asus M3N78-VM (+Athlon II 250 @ 3,00GHz CPU) card that has an onboard 8200 nvida card. The card runs very fast, faster than a 7300 dedicated card (tested) and runs VDPAU.
The mobo uses DDR2 memory.
The other computer had an Asus M4A78LT-M (+Athlon II x3 445 @ 3.1 GHz) mobo that has an onboard Ati/AMD 3000 card. It also has DDR3 RAM (2 GB here).

Second, my experience:
I use Debian Squeeze now and this is very close to Ubuntu 10.04 as far as kernel and other packages go. 
I booted in single-user mode, removed the nvidia driver (i use the driver provided on the nvidia site, uninstaling is very easy) and installed the latest (10.12) ati driver (also from their site with the provided install script. Run aticonfig --initial to genarate an xorg.conf.
Restarted the computer and i had working gdm. No issues here, the driver is as easy to install as the nvidia one.

I dont run compiz. The general feeling was the same as with the nvidia card. Scrolling maximized windows used less CPU than with the nvidia driver. I did not have stability issues when running normal applications.

Video/movies: 
I tested a 1080p clip and i found no VDPAU-like hardware acceleration (the card is 3 series and indeed it as no h264 accelerationin its description, the 4xxx series have that, have to get a 4xxx card to test it).
I tested vlc, totem and smplayer - the winner was smplayer with the least cpu used (max 70% and ~60% overall vs vlc's 60-90%). This was achieved with the "gl (fast -Ati cards)" output.
Totem was at 90-100% totally unusable (gstreamer-properties was set to xv output).
I could not use libva, it gave an error (it doesnt work even with my 8200 card so it is maybe a config isue Edit - it is working now, but it is not as good as vdpau).
Normal size videos had no issues.

Games/3d - Glxgears gave a score of ~3000 (with nvidia 8200 was ~2500) - this is not a reliable test though.
I normally play Smokin' Guns (ioquake3 engine), Urban Terror (ioquake3 engine), True Combat Elite (RTCW engine), Lord of the Rings Online (via wine).

All 3 native linux games from above exhibited a very annoying bug - i had a 1-2 second mouse/keyboard input lag (variable). This made them essentially unplayable.
Tried various fixes such as different dga mouse settings but none helped (though almost eliminated the issue for the menus, but in-game was the same).
The frame rate was somewhat higher than with the nvidia 8200, also i had no tearing ( with the nvidia 8200 sometimes i had a little tearing-like effect).

The Lord of the Rings Online game ran slower than with nvidia and exhibited some artifacts here and there (the nvidia 8200 runs this game flawlessly). O also managed to lock up the game (was in a window then) when i unticked a 3d-related option its menus - this never happened with the nvidia.

All in all the performance was solid and it was stable. It seems the Ati drivers have come a long way in improving stability.
Now my only real issue was that in game mouse lag thing (that does not happen with the nvidia 8200) and may appear under some circumstances even with the nvidia drivers too as far as i read about it so it may not be fglrx-specific.
All on all nvidia wins because it has better 3d support -  is more compatible with Wine-based games (and probably with more demanding Linux games too) and has better video playback (VDPAU rocks).

Im curious about the 4xxx series of Ati cards, i have to test one when i get the chance.

---

### Post by jworr on 2010-12-22
Thanks for all of your replies, they were very interesting and informative.

---

