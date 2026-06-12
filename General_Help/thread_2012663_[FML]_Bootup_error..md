---
title: "[FML] Bootup error."
date: 2012-06-29
forum: General Help
---

### Post by UAdnan on 2012-06-29
Hell:mad: (The smiley is the O ),

So this is the 3rd episode of my problems with Ubuntu just for today, that are really getting annoying today.

So after editing some files related to my track-pad trying to revive its multi-touch support which worked back in the days where I used to use Windows.

My computer wasn't really happy with the thing so it decided not to boot anymore, and to get stuck at the Ubuntu boot screen ( I use Ubuntu 12.04 ) with all the 5 dots fixed at the red color. 
As usual there was a message showing some driver that's not mounted yet or not ready (Not sure if that's the message 100%), before it wasn't an issue and the 5 red dots get fixed for about 5 seconds then I get to my login screen, but not anymore now...
If you don't know, while displaying the message I mentioned above, I have 3 options:

1- Wait, wait forever this time.
2- Press S to skip mounting (Tried it, in vain)
3- M for manual recovery.

I had no option, I pressed M, not sure of what would appear, then I got a black screen with some text, and an error that was reappearing over and over again regularly:

*import: unable to open x server `' @ error/import.c/Import/ImportImageCommand/366.*

Before that error there was a few messages which I guess aren't important to type, but there was something ( I don't remember well, sorry, if it's really necessary I will reboot and type it ) with */etc/default/saned* or something like that.

The Boot Repair utility did nothing, I also checked the repair Filesystem option in case, but nope.

I'm not really sure and I hope that what I'm saying isn't stupid - while it sounds so - I have no server stuff as the error shows... Just telling, but I guess that 90% it has nothing to do with that. x]

So may I tell again that the last thing I did is messing up with my track-pad files.

I am currently under a LiveUSB session, if there's anything I can do to repair that issue, I'll be really thankful to the person who might help me.

I apologize for ranting,
UAdnan.

*_PS: Please note that I tried my best not to create a third topic for today, but Google wasn't helpful..._*

---

### Post by UAdnan on 2012-06-29
Woo Hoo :guitar: ! Repaired it myself ! 
Sorry for that. :popcorn:

):P

---

### Post by southerngeek on 2012-06-29
> **UAdnan said:**
> Woo Hoo :guitar: ! Repaired it myself ! 
Sorry for that. :popcorn:

):P

Why don't you post your solution here for others' future reference... ;) tnx

---

### Post by UAdnan on 2012-06-30
You're right. 

So actually I had edited a file called xorg.conf as some website showed, which got to mess up with some display stuff... 

However when I boot up my computer I wait until I get the mounting message then I press M, then CTRL + ALT + F2, enter my login stuff. 

Then I write the following:

sudo apt-get remove --purge xserver-xorg

sudo apt-get install xserver-xorg

sudo dpkg-reconfigure xserver-xorg

That's it ! ^.^

---

