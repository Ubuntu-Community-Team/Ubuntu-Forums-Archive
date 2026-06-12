---
title: "Sony Vaio E series VPCEB1Z0E"
date: 2010-03-12
forum: General Help
---

### Post by birdmanuk on 2010-03-12
Just bought one of these - [http://www.sony.co.uk/product/vn-e-series/vpceb1z0e-b](http://www.sony.co.uk/product/vn-e-series/vpceb1z0e-b)

Installed 9.10 64bit, install went smoothly, but now having a few problems with graphics card drivers and sound.

The system has a ATI Mobility Radeon™ HD 5470 Graphics so I guess it's too new for a driver?

Anyone else tried the same laptop?

---

### Post by birdmanuk on 2010-03-15
Just changed the title on this thread.

---

### Post by Cuppa-Chino on 2010-03-15
Hi Birdman,

the laptop is very new and support is being worked on. the most active thread for sound is this one:

[http://ubuntuforums.org/showthread.php?t=1424795]("http://ubuntuforums.org/showthread.php?t=1424795") 

short answer both not working fully (sound and 3d graphics driver) at the moment, support should be up with ubuntu 10.04 lucid lynx - I am running alpha3 of that at the moment, beta is out this week (nb both issues not solved yet)

Hope this helps, fingers crossed issues will be sorted soon

---

### Post by crypto2600 on 2010-03-15
> **birdmanuk said:**
> Just bought one of these - [http://www.sony.co.uk/product/vn-e-series/vpceb1z0e-b](http://www.sony.co.uk/product/vn-e-series/vpceb1z0e-b)

Installed 9.10 64bit, install went smoothly, but now having a few problems with graphics card drivers and sound.

The system has a ATI Mobility Radeon™ HD 5470 Graphics so I guess it's too new for a driver?

Anyone else tried the same laptop?

Try the steps i outlined here: [http://ubuntuforums.org/showpost.php?p=8972359&postcount=3](http://ubuntuforums.org/showpost.php?p=8972359&postcount=3)

---

### Post by birdmanuk on 2010-03-16
Thanks for the reply, I think I will wait for Lucid, fingers crossed :-)

---

### Post by Cuppa-Chino on 2010-03-19
birdman:

as crypto has stated you can run 9.10 with the method he described -- unfortunately AMD has not yet release a driver that a full supports the card (and says so!) and support the newer xorg version to be found in lucid lynx

---

### Post by birdmanuk on 2010-05-02
Just a quick update, graphics now work in Lucid. Although still having issues with sound. I believe it's being worked on.

---

### Post by dino99 on 2010-05-02
have you paprefs and gnome-alsamixer installed ?

---

### Post by birdmanuk on 2010-05-02
Yes, just installed them.

I can see 2 sound devices, 

Realtek ALC269 
ATI R6xx HDMI

It's the ATI that I guess I need to get working.

---

### Post by linuxrulez on 2010-05-04
i got my sound working after installing the latest alsa driver.

---

### Post by birdmanuk on 2010-05-04
How did you go about upgrading alsa?

---

### Post by linuxrulez on 2010-05-06
> **birdmanuk said:**
> How did you go about upgrading alsa?

Download the latest alsa driver : <http://alsa-project.org/main/index.php/Download#Latest_Software_Source_Releases>
Direct link to the tarball that has the fix: <ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2>
Download the tarball and unzip it to a folder. From terminal navigate to the this folder
Then type
./configure
make
sudo make install 
alsamixer

:guitar:

---

### Post by Rackstar on 2010-05-07
> **birdmanuk said:**
> Just a quick update, graphics now work in Lucid. Although still having issues with sound. I believe it's being worked on.

Hi!

Not trying to hijack your thread here, but did it work out of the box with new updates, or did you do something special?

Thanks!

---

### Post by birdmanuk on 2010-05-07
Rackstar,

           I just did a fresh install of 10.04. on reboot, I had a restricted driver pop up. Installed that and all was OK.

Just no sound. I'm keen to wait for a .deb to get sound working.

---

### Post by birdmanuk on 2010-05-10
I compiled alsa, rebooted and got sound at boot, but once I logged in, no sound again :-(

---

### Post by mrphd on 2010-05-28
open a terminal, type "alsamixer" and make sure that none of the levels are at zero

---

### Post by jayachandranm on 2010-06-26
Detailed instructions for installing latest alsa can be found at,

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

Your laptop may have the ATI HD soundcard for digital out and intel 5 series 3400 or similar soundcard for analog output. It may be the intel soundcard that you will be using for your normal audio from laptop.

---

### Post by birdmanuk on 2011-10-31
Digging up this thread again to see if anyone has installed 11.10 in the E series. 

So far it feels like a step backwards :-( Although I have graphics working, it's not as crisp as it was in 10.10, also battery life has been reduced dramatically. I have also enabled scrolling on the touchpad, it doesn't seem to be working though.

Apart from that it's very fast to boot - (really slow to shutdown), still getting used to Unity. 

Anyone else upgraded (I did fresh install btw)

---

### Post by oldos2er on 2011-10-31
Closed. Please start a new thread for your question.

---

