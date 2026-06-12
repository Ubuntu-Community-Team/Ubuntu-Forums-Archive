---
title: "Issues with Nvidia proprietary drivers"
date: 2009-08-26
forum: General Help
---

### Post by Alpaca? on 2009-08-26
So, I'm attempting to enable nvidia proprietary drivers. I go to System/Administration/Hardware drivers and it comes up with two drivers:
Nvidia accelerated graphics driver (version 180) (Recommended)
Nvidia accelerated graphics driver (version 173)

So I click on 180 and hit activate. I authenticate, then it does some searching and installing. After that, it does absolutely nothing. My screen doesn't change, and the green light button beside the driver doesn't light up. If I reset my computer it tells me something along the lines of "Could not load nvidia kernel(or Module). I then have the option of putting my laptop into low graphics mode, which I do.

After that I roll a "use default configuration" setting and it takes me to my desktop with the correct resolution.

Now, is there any way I can use the nvidia graphics driver without it messing up for me?


My Laptop and Card:
Thinkpad T61
Nvidia Quadro NVS 140m

Rolling Ubuntu 9.04.

---

### Post by x33a on 2009-08-26
not sure why that method isn't working, but you can take a look here:

[http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185](http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185)

---

### Post by Gnowm on 2009-08-26
I have the same (well similar) issue. No matter how the nvidia 173 module is installed (restricted drivers way, or apt-get) always runs in low graphics mode. It was never really an issue cause this was just my server, now I wish to use same box to play Planeshift. tried uninstalling ALL nvidia related items via synaptic and still no luck. checking out that link now. Weird.

---

### Post by fanglinyong on 2009-08-26
first:goto the nvidia network download the software drive for your display card!
se:  when the console gives u four choice,you should select the last choice,quiet to console modle,in the textmoudle ,you then run the softwaredrive
third:after intall ,reboot your pc!

---

### Post by Triplejolt on 2009-09-10
Using Quadro NVS 140M myself and can't get this to work with any Ubuntu drivers at all. I've gone through the 77.x to the beta 190.x and none of them wants to play ball. The 800x600:61 is getting really annoying. I'm unable to force any other settings and are starting to believe this is going to be my permanent setting. I'm just not able to change this at all. Any other suggestions out there?

Btw, the "Hardware Drivers" feature under System -> Administration is gone. Any reason for this? How do I get it back, lol

---

