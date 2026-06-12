---
title: "Quick Questions for a total Linux newbi"
date: 2010-09-29
forum: General Help
---

### Post by Jack-T.Ripped on 2010-09-29
First I just installed it on a laptop, an old Dell D400. 
First is, I can't get the wireless card recognized. I have tried bFWcutter, installing the wireless packages, etc, nothing shows up in proprietary drivers. This isn't too important, I'll figure something out for it. Yes i know I sound like a real windows user, but I  don't have time to learn Linux all the way through or the money to pay for a new OS. I just need wireless working.

Second, this is stupid, but it would be useful for the person I'm installing it for. These are really quick questions. A) does farmville work on ubuntu, and if so, B) what needs done to get it working, besides just installing flash, cause that isn't fixing the issue. This will be on the desktop 32-bit version. 

Any help is so greatly appreciated, I've been scowering google for three days now with no luck.

---

### Post by Jack-T.Ripped on 2010-09-29
Also I'd like to add none of this should be taken as me complaining, besides these honestly minor issues, I love the look and feel of Linux and the speed in which it runs on these old machines I'm replacing XP on. Thanks a lot again.

---

### Post by efflandt on 2010-09-29
I am not specifically familiar with the Dell D400, but many Dell laptops use some sort of Broadcom wireless.  However, finding and activating the proper driver is a bit trickier if you do not have a wired internet connection you can use temporarily.  If you have a working wired connection, you would go to System > Administration > Hardware Drivers and see what that comes up with if anything.  Sometimes it would come up with Broadcom B43 and Broadcom STA, but each of those is mutually exclusive (only one or the other can be activated at the same time).  In earlier Ubuntu versions Dells I worked with used Broadcom STA, but not sure which works better in 10.04.

If you do not have a network connection you would need to insert the Ubuntu install CD and add that to the repositories by checking a box in Synaptic before trying to use Hardware Drivers.

But first you might run **sudo lspci -v** in a terminal and post the output of that related to your wireless here in case someone familiar with that specific chip has suggestions about what would work best for it.

I have no idea what farmville is, but the easiest way to install flash is either **flashplugin-installer** package, or better yet **ubuntu-restricted-extras** which includes that and other audio/video things and a java substitute (also see [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) to get DVD's working).

---

### Post by Megaptera on 2010-09-29
You could try this for Dell/broadcom. Says Karmic & Dell Mini but works on Dell Inspiron in Lucid too:

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Don't forget the re-boot step.

---

### Post by Jack-T.Ripped on 2010-09-29
> **Megaptera said:**
> You could try this for Dell/broadcom. Says Karmic & Dell Mini but works on Dell Inspiron in Lucid too:

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Don't forget the re-boot step.
Alright thanks a lot. It's an old Latitude. It's... Old. Very Old. ~nods~ 

Oh farmvile is a stupid flash game on facebook. The girl I'm installing it for is totally obsessed with it and wont live without it. ...  That's sad. Any who thanks so much for the help peoples.

EDIT: Ok I tried that, and reinstalled the packaging, but no luck, nothing appears in proprietary drivers. Any other suggestions?

---

### Post by spiky001 on 2010-09-29
Hi It sayes in farmville that it works on Firefox 3.6 I afraid i didn,t install not my thing but I dont see why not why not just try installing,

---

### Post by bbqsandwich on 2010-09-29
Farmville is a Web-based game that runs in your browser so it should work fine on Ubuntu if you install the Adobe Flash plugin.

---

### Post by Jack-T.Ripped on 2010-09-29
Ok I was using a different package for flash the new one works (If i can find it again for desktop and not netbook) (I'm working on two computers), so it works for her now. The wifi doesn't work still I had that package installed and rebooted. I'm about to go to work but I'll post the results of the PCI tests tomorrow. thanks everyone.

---

### Post by JedMeister on 2010-09-30
It may not be particularly relevant but I have 32 bit Karmic running on an old Dell Inspirion - can't remember the model (obviously not using right now!) It has 512MB RAM and ~1GB processor. I recall wifi was problematic to setup. But I got it working in the end. From memory it was the Broadcom B43-cutter driver (or something like that) that did the trick. Its still a little flakey at times and won't connect after waking from standby (have to reboot) but all in all it works better than some wifi I've used under Ubuntu (I have a horrible USB stick that sometimes will just not work, no matter what. works fine under Win - grrr).

Not sure if its relevant or even an option, but AFAIK often wifi in older laptops are actually a little card inside (rather than being an integral part of the mobo) and if you can get hold of an intel based one that fits (to replace whatever is there) they are apparently much better. (SO I've been told anyway).

Good luck sorting it out.

---

### Post by Jack-T.Ripped on 2010-10-02
Ok sorry for long absences and bad grammar peoples. Seems my sister, who is the laptop owner took the wireless card OUT forwhat ever reason, didn't tell me, and I never bothered to check, cause, hey, why would it be OUT?! Oh well so it should work easy as pie, no problems with the cutter package, which is already installed. 

Farmville is in fact working on the desktop, the lady plays it constantly, and i accidentally screwed her windows partition up in the process of making the linux one. ... Ooops. Oh well I'll fix that i know what i did wrong, I wasn't paying attention and removed the 8MB buffer zone and "Process_1" was uh... welll....  in my own little world I said it was too close to edge. Oh well fix it with Gpart in ubuntu. I think that's what it was called. Anywho thanks everyone for helping me out all things said and done I love using linux. Very happy. :popcorn:

---

### Post by HermanAB on 2010-10-02
Howdy,

If the little wifi wizards don't work for you, then you got to go to the ndiswrapper web site and read the howto guide and do it manually.  It is explained in much detail and is not complicated at all.

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)
[http://wiki.debian.org/NdisWrapper](http://wiki.debian.org/NdisWrapper)
[http://easylinuxwifi.org/](http://easylinuxwifi.org/)

---

