---
title: "Internal Speakers are not working"
date: 2011-01-24
forum: General Help
---

### Post by lagom on 2011-01-24
Hi there, 

I don't get any further.

I just got started with Linux a few weeks ago, and after some minor troubles everything worked fine. But now, just last week, the internal speakers stopped working, while headphones still get me all the sound. 

I've tried to fix it, but I just wasn't able to. Among other things, I was following some tipps in the Ubuntu documentation. 

Things I noticed: 

-- the soundcard doesn't appear in the BIOS
-- The Dell CD, which is supposed to detect any defects on the hardware, says that everything is fine with my sound and manages to play music over the speakers
-- and, as said, I still can listen to music over headphones. Jus nothing over the regular speakers. 
-- I've reinstalled the OS (different versions, Mint and Ubuntu, both the stable and the "experimental" version) 

I really need your help, I'm so close to moving back to windows, and that would be a shame. 

I'm working with a Dell Latitude E4300. Ubuntu 10.04 is right now installed. 

If I enter 
> sudo aplay -lthat's the result 

> 
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0Any help is so much appreciated!! 

Salome

---

### Post by gordintoronto on 2011-01-24
Did you try the current version of Mint? I have a laptop which behaves the same as yours in 10.04, but when I boot the latest Mint, the speakers and headphones work properly.

---

### Post by lagom on 2011-01-25
I can hardly believe that it could be that easy. I tried like thousand things, checked settings, etc. 

and now a simple 

apt-get update

and

apt-get upgrade

would help me and solve my speaker issues. Sound is all fine again. Crazy!

Thank you so much! 

Salome

---

