---
title: "Ubuntu 10.04 makes little girls cry!"
date: 2011-01-06
forum: General Help
---

### Post by misterbiskits on 2011-01-06
I have an upset youngster here who cannot play poptropica.com on her ubuntu machine.
It works ok on my box, I am not sure what the problem is.  I have flash plugin installed...Once I get past the create character stage, and begin playing the screen flickers like crazy and it's unplayable.
Anyone have any advice?

---

### Post by jsriz on 2011-01-06
Hey install chrome it works like charm

---

### Post by misterbiskits on 2011-01-06
thank you i'll try it out =)
edit: no good same thing in chrome.
It works on my other ubuntu box.  I notice on the map screen (of the game), that the flickering only happens when the desktop mouse pointer rests ontop of the in-game mouse pointer.  Beyond that screen, any movement at all creates crazy flickering.
I wonder if it could be an unsupported video card?

---

### Post by jsriz on 2011-01-06
Thanq for the site its fun !!!:D

---

### Post by ronnielsen1 on 2011-01-06
Works with Iceape on AntiX. It should work on Ubuntu. You need to install flash or something. Have you installed ubuntu-restricted-extras?

---

### Post by Krytarik on 2011-01-06
> **misterbiskits said:**
> 
I wonder if it could be an unsupported video card?
What card is installed?

Did you install the appropriate driver, e.g. via "System -> Administration -> Hardware Drivers"?

Are desktop effects working?

---

### Post by mlamorey on 2011-01-06
Strange, but similar problems here. Some facebook games my kids play (ok me too) it gets a little strange. If I try to go to full screen mode it crashes - Chrome at least is upfront and says "blah blah blah crashed /opt/google/chrome/libgcflashplayer.so"

Same thing happens in both Mozilla and Chrome.

On the find update site for plugins in mozilla it does think my flash is out of date but not on through synaptic. 
Guess I am going to have to do a manual update, although on the flash site they only recognize 8.04 and 9.04 - any thoughts on which to choose?

Oh, and yesterday it just got wierd when in full screen, so today I installed the proprietary AMD driver. Now it crashes. Either way, hopefully latest flash update fixes.

---

### Post by misterbiskits on 2011-01-06
> **ronnielsen1 said:**
> Have you installed ubuntu-restricted-extras?

I just finished installing the restricted extras, and am getting the same problem in bothe firefox and chrome.

 > **Krytarik said:**
> What card is installed?

Did you install the appropriate driver, e.g. via "System -> Administration -> Hardware Drivers"?
Are desktop effects working?

Radeon 9550 256 mb AGP card.

System -> Administration -> Hardware Drivers gives me no options and says no special drivers are installed.
EDIT: Forgot to say that desktop effects...the wobbly windows(is that what you mean?) are working.

> **mlamorey said:**
> 
Same thing happens in both Mozilla and Chrome.

let me know if you figure it out =)

---

### Post by MaxIBoy on 2011-01-06
If the proprietary driver didn't help, I'm not sure what will.

---

### Post by Krytarik on 2011-01-06
@mlamorey: What version of the flash-player do you have installed then?
When manually installing from the adobe website, you can choose ".deb for Ubuntu 8.04+".

@misterbiskits: Your card isn't covered by the proprietary drivers anymore. Try "upgrading" to the Open Source Edge drivers:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by misterbiskits on 2011-01-06
Appreciate you checking that card for me, Krytarik, and for the code.  One day I'll know how to do these things for myself.
Unfortunately it didn't help =P
I have a geforce 7300 LE sitting here ... think it's worthwhile to take out the radeon and try the geforce?
Do I need to do anything special, or can I just shutdown and change cards, and boot up?
Thanks again.

---

### Post by Krytarik on 2011-01-06
> **misterbiskits said:**
> Appreciate you checking that card for me, Krytarik, and for the code.  One day I'll know how to do these things for myself.
Unfortunately it didn't help =P
I have a geforce 7300 LE sitting here ... think it's worthwhile to take out the radeon and try the geforce?
Do I need to do anything special, or can I just shutdown and change cards, and boot up?
Thanks again.
Yeah, it's worth a try, sadly it turned out that driver support (at least from the vendors) is better for Nvidia cards, the Open Source Edge drivers are still in development, so they get hopefully near the performance of the proprietary drivers over time, but at the moment the latter offer significant higher performance. And the Geforce 7300 LE is supported by the proprietary drivers.

Just shut down, switch the cards, boot up and install the driver via "System -> Administration -> Hardware Drivers". Then log out and in again.

EDIT: Thinking of it, did you reboot or logout/login after upgrading to the OSE driver?

---

### Post by misterbiskits on 2011-01-06
Yup, i did a reboot after the driver install.
OK I'm going to switch out these cards and will get back.  thanks for all the tips =)

---

### Post by misterbiskits on 2011-01-06
Ah well. the geforce turned out to be a dead card.  Too much time spent as a paperweight.  I tried a Radeon 7500 I had kicking around, but no driver support for it.
Guess I'm off to the dump tomorrow to find a card haha.
Yes I am a junk collector. 
Thanks for the help anyways =)

---

### Post by Krytarik on 2011-01-06
> **misterbiskits said:**
> I tried a Radeon 7500 I had kicking around, but no driver support for it.
The same situation as for your Radeon 9550.

You're welcome. Good luck at the dump. :-D

---

### Post by lidex on 2011-01-07
FWIW, you would do well to install the flash-aid extension to firefox:
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)
> Remove conflicting flash plugins from Ubuntu Linux systems, install the appropriate version according to system architecture and apply some tweaks to improve performance and fix common issues.

Also have a look here for further tweaks:
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

