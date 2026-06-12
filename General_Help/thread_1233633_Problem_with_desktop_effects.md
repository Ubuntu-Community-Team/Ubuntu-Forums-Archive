---
title: "Problem with desktop effects"
date: 2009-08-06
forum: General Help
---

### Post by cjmabry25 on 2009-08-06
Hi all.

So I installed Ubuntu 9.04 the other day, got my sound working and installed the ATI Open-Source Edge drivers. Everything seems to be working, but I cannot enable desktop effects. I get the message "Desktop Effects could not be enabled". Any idea why this could be happening or any idea on how to fix it? 

Thanks for all the help so far :D

Oh ya, and does anyone know the link to that thread that told you how to fix your sound by typing snd hda intel model= dell or something like that? I found one that works for the Dell Dimension C521 and would like to list it so others could use it. Thanks again.

---

### Post by cjmabry25 on 2009-08-07
Bump.

Are there any commands or something I could run from the terminal to figure this out? I'll be doing some research in the meantime.

Thanks:D

---

### Post by madnessjack on 2009-08-07
Hi,

Basically, you need to setup compiz before it will work. Not sure about the sound though.

Try these commands one at a time
```
sudo apt-get install compiz compizconfig-settings-manager[FONT=monospace]
[/FONT]compiz --replace
```(source: [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion))

Then restart Xorg and try again
```
sudo /etc/init.d/gdm restart
```

---

### Post by cjmabry25 on 2009-08-08
I did the commands yoiu suggested, but it said that I already had the newest versions installed, so I did the second command to restart Xorg and my screen went to a full screen command line and Would not restart, so I turned my computer off and here I am again.

Also, here's what happens when I try to enable desktop effects. First, I get this screen.
See attachment 1.

Then this screen.
See attachment 2.

And another thing, Ubuntu didnt detect my video card like it usually does on other installs. When I go to Hardware Drivers in System > Administration, I get this screen.
See attachment 3.

Also I installed WoW via Wine, and when it boots the screen goes black with the WoW glove cursor and random orange dots in on of the corners.

Thanks:D

---

### Post by cjmabry25 on 2009-08-08
Well, since I'm no seeing an answer insight, I've decided to downgrade to Ubuntu 8.10 because of my video card (Ati Radeon X1300) not being supported by ATI in Jaunty. I might just go back to Windows...

Thanks anyways.

---

### Post by Soley on 2009-08-08
Sorry man, I did some quick googling & couldn't find anything that looked like a fix for the X1300. :(

---

### Post by cjmabry25 on 2009-08-09
Thanks anyways. I went back to Windows XP and.... AHHHH!!! This is sooooo slow compared to Ubuntu. If I go back to Intrepid or whatever befores jaunty, will it be as fast as Jaunty? I'm doin it lol. I can't believe how slow Windows is on a fresh install. Oh I need linux lol.

**EDIT: I'm downloading Hardy right now. Hopefully I'll get my drivers working. Thanks**

---

### Post by madnessjack on 2009-08-10
If you do want to give Jaunty one last try, this utility solved my problem pretty quick.

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

It told me what was wrong and proceeded to fix the problem by switching my window manager (or something :-P)

Sorry that it's not working out for you mate

---

### Post by P4man on 2009-08-10
ATI indeed stopped supporting their old cards. The opensource drivers are enough for basic stuff, but if you need anything more.. i'd suggest picking up a newer card on ebay for like €10-20.

As for WoW on wine. Have a look here:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

Seems to work okay with nvidia cards.

---

