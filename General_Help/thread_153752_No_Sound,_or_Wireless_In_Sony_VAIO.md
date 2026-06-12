---
title: "No Sound, or Wireless In Sony VAIO"
date: 2006-04-01
forum: General Help
---

### Post by Keymaster on 2006-04-01
My Sony VAIO laptop Model VGN FE550G does not get any sound in Unbuntu, or any wirelss.  It doesn't even detect a wireless card, and the sound control only has PGM, but nothing else.  Also there is no sound output, and after just dealing with a graphics problem I'm starting to hate these VAIOs.  Any help for sound, and/or wireless is greatly appreciated.

---

### Post by JoshHendo on 2006-04-01
A friend told me once that XP is hevily modified to work with Vaios when it comes with it. Do a search of the forum, someone may have made a package that could fix this, who knows :/

---

### Post by Newbify2 on 2006-04-01
For the NIC try ndiswrapper: [http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A//ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page&ei=wv8uRNmGLqHQoAL--sTiCg&sig2=BhE2-M-QyjBQyFbbiQ21Og](http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A//ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page&ei=wv8uRNmGLqHQoAL--sTiCg&sig2=BhE2-M-QyjBQyFbbiQ21Og)

For the soundcard, I have an emachines m2350 and I went into alsamixer and I muted the External Amplifier. I have everything but the Master and PCM muted, not sure if that will help you.

Pretty sure ndiswrapper will be what you need for you wireless.

---

### Post by Keymaster on 2006-04-01
Thanks.  I hope ndiswrapper works, and as for sound I have no clue what you mean, but i'll try something.  The problem is that only PCM appears.

---

### Post by Keymaster on 2006-04-01
I heard that Fedora Core works with VAIOs easily.  Anyone know if that's true?

---

### Post by JurB on 2006-04-02
Try this for your sound problem:
- Right-click on the mixer icon
- "open mixer"
- "edit" ---> "preferences"
- enable everything and close
- go to the "Switches" tab in the mixer
- disable "external amplifier"
- test your sound

This did the trick for my Vaio, as for wireless: my card is detected... but i haven't used it yet...
I have Dapper installed on my vaio now and i must say it runs pretty smooth on it.. no real problems  yet... i can even scroll with my touchpad, something i couldn't do in Breezy

---

### Post by Petarded on 2006-04-02
I just installed Dapper Flight5 and everything works for me, give it a shot.

---

### Post by Keymaster on 2006-04-02
Dapper is an Ubuntu distro?

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=Keymaster]Dapper is **a** Ubuntu distro?[/QUOTE]
First off it is not "an" ubuntu distro. It is the next version of Ubuntu but it is still in testing. At this moment, it is still very unstable. It is currenly in alpha stage but it will soon enter beta and on June 1st it will be finally released.

---

### Post by Keymaster on 2006-04-03
Oh.  I hope it works with Sony VAIOs

---

### Post by Peacepunk on 2006-04-08
Confirmed on Vaio vgn-t16 and vgn-t17 : in Breezy (5.10), open Volume Control under Application > sound & video, click Edit Tab > Preferences, look for last item at the bottom "external amplifier", activate it, it will add a new tabb to the Volume Control Window called "switch": from this tab, un-tick the external amplifier - Hosannah, your sound is unlocked !

Yeah, it look silly to have to lock then unlock something for it to work, but who has never repeatedly swithed on & off a light bulb to try to "wake' it?

Never buy a vaio: they nice looking, with shitty sound, extraordinarly fragile, without any after sales policy, and expensive. At these cost, buy a mac.

I posted a "hard but easy way wifi howto" in beginners section, that doesn't adress the issue of unrecognized card, only guide you to the proper setup while installing.


Cheers.

---

### Post by Keymaster on 2006-04-09
Your sound trick didn't work, since nothing was available to disable.  The only thing on the list is PCM.  This is really pissing me off now, since it's the only thing keeping me from getting rid of Winblows.

---

### Post by ExMachina on 2006-07-30
I run it ubuntu on my Vaio laptop PCG-K13

try installing the the audio via easy ubuntu?
[]("http://easyubuntu.freecontrib.org/")
Ive nto had any trouble. The sound is good on my lappy
althought eh case is a tad fragiel had it 2 years has a few hair line form picking up out of backpack daily. ive been VERY hapy with it.

song vaio pcg-k13
proc- 2.8
ram- 512 
HDD- 100gb

---

### Post by Keymaster on 2006-07-31
What is easy ubuntu?  Is it part of Ubuntu 6.06?

---

### Post by ExMachina on 2006-08-03
I installed dapper drake from a live CD. Then used Easy ubuntu[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/) ( later Automatix has more stuff [http://www.getautomatix.com/](http://www.getautomatix.com/) to install random packets. Although ive not tried wifi i found [http://www.ubuntuforums.org/forumdisplay.php?f=74](http://www.ubuntuforums.org/forumdisplay.php?f=74) 

Im installing that as soon as my new HDD gets here. 
Not see anyone do this on a Sony Vaio ( i ahve PCG-K13 myself)
Well see!

---

### Post by SendDerek on 2006-08-23
I hope nobody minds that I jump into this thread, but I have the exact same problem:  No sound and no wireless card on my VGN-FE550G.  

I must say though, that I was trying and wanting to run Suse 10.1 on this Vaio, but if it will be easier to get it to work through Ubuntu, I'm all good with that. I'm pretty much brand new to linux most of this stuff is over my head.

Something that I found on google though for the sound is a patch of some kind.  Keymaster, maybe this will help you with the sound.  

[https://lists.ubuntu.com/archives/kernel-team/2006-March/000731.html](https://lists.ubuntu.com/archives/kernel-team/2006-March/000731.html)

I would love to see this topic continue until we can get those two things (sound, wireless) working.  I'm bookmarkin' this one.

PS.  I'm glad I'm not the only one. :)

Edit:  I just wanted to post this link that I found that might be of interest about the Suse 10.1 b9 Changelog.

[http://www.tuxmachines.org/node/5945/print](http://www.tuxmachines.org/node/5945/print)

> - patches.drivers/alsa-stac7661-vaio-model: Add support for VAIO
FE550G and SZ110 (156494).

What's this supposed to mean?

---

### Post by Keymaster on 2006-10-03
The issue has been resolved with the release of Ubuntu 6.06  Version 6.06 works right after install with all of the hardware that I had problems with (other than the camera, but I don't use that anyway)  It even works off the Live CD, so when it installs no changes are necessary to get sound, video, and wireless.  Horray for updates!!!

---

### Post by SendDerek on 2006-10-03
That's great news!  Thank you for sharing!

---

### Post by di0rz` on 2006-11-29
[COLOR="Black"]muted the External Amplifier and it worked thx[/COLOR]

---

### Post by mskadu on 2007-04-24
Did you manage to solve this problem? I have been using Ubuntu on a Vaio for more than a year and a half. I started with 6.0x, 6.10 and finally to 7.04 a couple of weeks ago. Have you tried upgrading?

---

### Post by SendDerek on 2007-04-24
All of my issues have been resolved since 6.10.  7.04 is awesome on a vaio!  The only things I havn't been able to fix are the motioneye webcam and microphone.  Everything else seems pretty good though.

I used to have brightness control, but now I don't...  I don't think I've done everything I can to get it working yet (ie: installing sonypi).

---

### Post by mskadu on 2007-04-25
Thats excellent. :popcorn:

---

