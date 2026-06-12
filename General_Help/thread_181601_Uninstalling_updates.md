---
title: "Uninstalling updates"
date: 2006-05-24
forum: General Help
---

### Post by Dr. Feelgood on 2006-05-24
I recently installed some updates for my graphics card driver and such and it has royally screwed what was once a good thing.  You can read about my fiasco here if you'd like:

[http://www.ubuntuforums.org/showthread.php?t=173636](http://www.ubuntuforums.org/showthread.php?t=173636)

No one seems to be able to fix the problem so now I just want to get rid of that damn update that broke everything in the first place.  I just don't know how.  Any one have some info?

---

### Post by an.echte.trilingue on 2006-05-24
I think I can help you, but I need you to answer a couple questions:

1.  Did you update xorg.conf with:

```
sudo dpkg-reconfigure xserver-xorg
```

?  I don't think arnieboys tutorial covers that.

2.  Did you compile the driver yourself as in arnieboy's tutorial?

3.  Did you install the driver or update through the package manager?

---

### Post by Dr. Feelgood on 2006-05-24
I honestly don't know if I updated xorg with that line.  Let me know if I should.  I did install the drivers myself as per arnie's walkthrough, and yes everything was working wonderfully.  Yes, I updated through synaptic, and that's when the trouble began.  I reinstalled the drivers the way I did before and even tried updating them, but while DRI came back my graphics were still super slow.  So what's the next step?

---

### Post by an.echte.trilingue on 2006-05-24
AFAIK, when Arnieboy wrote that howto, he had to because the drivers could not be distributed due to licensing.  That situation has now changed and Ubuntu distributes them as a .deb. 

Problem is, when you install things outside of apt, apt cannot resolve dependancies for you.  Further, Ubuntu devs make minor changes to packages so that what you install is slightly different from the source code, enough so that things will break.  If you followed arnieboys tutorial and then installed the .deb, then this probably just threw X for a loop.

The first thing we want to do is make sure that it is not just your config that is buggered:
```

sudo dpkg-reconfigure xserver-xorg
```

This will attempt to reconfigure xorg to use your driver.  Be aware that this is going to ask you some questions; know your screen resolution.  Restart X with ctrl+alt+backspace or reboot and see if it is working now.  You might have to do this a couple times before you find the config that is right for you.


If that does not work, you probably just broke the binaries and this is a little harder (but not much):

```
sudo dpkg -r xserver-xorg-driver-savage
sudo apt-get install xserver-xorg-driver-savage
sudo dpkg-reconfigure xserver-xorg
```

Restart X or reboot and let me know how it works!

---

### Post by Dr. Feelgood on 2006-05-24
Well, I tried the reconfiguring xorg and something actually worked.  My FPS are not up to where they used to be but they are alot better than before.  It's up to around 370 or so.  It's good enough to run what little stuff I use.  I don't think I'm going to bother with the binaries.  You, my good man, are a lifesaver.  Thanks a million.

---

