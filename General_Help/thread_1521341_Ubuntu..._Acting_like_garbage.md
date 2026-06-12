---
title: "Ubuntu... Acting like garbage"
date: 2010-06-30
forum: General Help
---

### Post by zerojett on 2010-06-30
Alright. Lucid Lynx is my current. 3.6.6 firefox. I've had this problem since 3.5
I did not have this problem in jaunty. Something is telling me this has to do with Java.
It only occurs when I'm on a very java-like page...

Symptoms?
Random colour lines. Random garbled text. Sometimes text can be fixed by highlighting.

Here's a picture.
I want to fix it, I enjoy Ubuntu. But I haven't found a fix yet. Considering XP... Save me!

[IMG]http://i838.photobucket.com/albums/zz301/canadian_ef/Ubuntu/Screenshot.png

---

### Post by davidmohammed on 2010-06-30
what graphics card do you have?

type 

lspci | grep VGA

in a terminal session.

---

### Post by uRock on 2010-06-30
How much RAM and SWAP do you have? I run NoScript to block most of the Java which is a big help when I start to get about 40-50 tabs going. 

Install htop and next time your system starts doing this open a terminal and enter "htop" Running htop will show you how much RAM you are using as well as showing which programs are using how much CPU and such.

---

### Post by warfacegod on 2010-06-30
Don't know if this will help or not but I wouldn't be surprised if the guy that wrote it is along shortly. Check the troubleshooting section: [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by uRock on 2010-06-30
> **warfacegod said:**
> Don't know if this will help or not but I wouldn't be surprised if the guy that wrote it is along shortly: [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

[sarcasm]I thought he switched to Chromium last week?[/sarcasm]

---

### Post by steveneddy on 2010-06-30
Looks like a video driver issue to me also.

Run the terminal commands a few posts up and post back here.

---

### Post by warfacegod on 2010-06-30
> **uRock said:**
> [sarcasm]I thought he switched to Chromium last week?[/sarcasm]

Sarcasm? It says Firefox in the window border in the screenshot.

---

### Post by lovinglinux on 2010-06-30
> **uRock said:**
> [sarcasm]I thought he switched to Chromium last week?[/sarcasm]

Funny. I didn't and I won't :)

> **steveneddy said:**
> Looks like a video driver issue to me also.

Run the terminal commands a few posts up and post back here.

Looks like a video driver issue too me also. Sometimes I have a similar issue in Firefox, although mine is confined to tooltips or content being dragged and it is not persistent. 

Last time I had this was this week, when a nVida update came through the repositories. It went away by itself.

---

### Post by uRock on 2010-06-30
> **warfacegod said:**
> Sarcasm? It says Firefox in the window border in the screenshot.

Nooooo, sarcasm that lovinglinux changed to Chromium, lol.


> **lovinglinux said:**
> Since the World Cup won't be back until Friday, I have uploaded a new avatar :):lolflag:

---

### Post by lovinglinux on 2010-06-30
> **uRock said:**
> Nooooo, sarcasm that lovinglinux changed to Chromium, lol.

Since the World Cup won't be back until Friday, I have uploaded a new avatar :)

---

### Post by zerojett on 2010-06-30
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

ATI graphics is my issue I guess. I've read about it. Can you give me direction to install the proper driver?

---

### Post by warfacegod on 2010-06-30
> **zerojett said:**
> 01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

ATI graphics is my issue I guess. I've read about it. Can you give me direction to install the proper driver?

System> Admin.> Hardware Drivers> Activate the "Recommended" driver. There is some debate about whether or not using the ATi proprietary drivers from their site is better or not. I've read about too many problems with the proprietary drivers to suggest using them. I'd stick with the ones available in Jockey (Hardware Drivers).

---

### Post by zerojett on 2010-06-30
> **warfacegod said:**
> System> Admin.> Hardware Drivers> Activate the "Recommended" driver. There is some debate about whether or not using the ATi proprietary drivers from their site is better or not. I've read about too many problems with the proprietary drivers to suggest using them. I'd stick with the ones available in Jockey (Hardware Drivers).

No proprietary drivers...

---

### Post by zerojett on 2010-06-30
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

code seems to help. i lost the page i got it from, but thanks. it's someone on this site.

still no proprietary drivers though.

---

### Post by Vaphell on 2010-06-30
i think your gfx is too old to be supported officially by amd/ati, it's like 4 generations behind. You don't have much choice.

---

### Post by zerojett on 2010-07-04
So because I have an old card, that was supported in the past 2 releases, I can't use it now...
That seems really really stupid.
Sorry, but there isn't much other word for it.
It'd be great if maybe there was a warning...
...
So now I'm stuck, my computer gets over-loaded when there is THREE images on a webpage, something that NEVER happened on ANY previous version of Linux I had used.
It's been getting so bad, that I haven't even been able to use my computer properly.
If forums were vocal, I'm sure you could hear my voice screaming profanity at this OS.
I read that Lucid was supposed to be superior. 
Now I'm rating it at a Vista level...
Buggy, and crap.

Honestly. Pathetic.

---

### Post by QIII on 2010-07-04
I understand completely that you are frustrated.  It *IS* frustrating.  I don't blame anyone for getting frustrated.

But if you chose to yell at the OS, you will be directing your ire in the  wrong direction.

I need to dispel a common misconception:  Neither Linux distros nor Windows supports hardware.  OEMs write drivers  that work with OSs.

In this case, AMD/ATI has chosen to "legacy" your card rather than  keeping up with the driver changes needed to work with the latest X  Server used in Ubuntu (and other distros).

It is not the OS that is buggy.  It is the OEM that has chosen not to support the card in a new world.

How much can you blame them?  How much effort and what resources do you expect them to expend to maintain the driver on a card that is used only on some very small fraction of machines any longer?  For cards that, if still functioning, have long outlived their expected mechanical lifetimes?  If you owned a business, how much effort would you expend?

And remember:  The Linux community has provided an open source driver that will work, albiet imperfectly, with your card.

---

### Post by zerojett on 2010-07-04
"NOTE: If you enter your card information on AMD/ATI's driver page, it will offer you the Catalyst 9-3 driver to download. However, the Catalyst 9-3 driver doesn't support X servers past 1.5, and it will not work with Lucid! !!!SO BE CAREFUL!!! If you tried to install Catalyst on a system with one of these cards, see the 'Removing the Driver' section to restore the default/pre-installed driver"

Took some trouble to find, but I found the warning.
So, x.org doesn't support old versions of Catalyst.
I know it says it the other way around, but it is true in this sense as well.
And it probably isn't possible to downgrade x server or whatever...
I read somewhere that Linux only has 1-2% of the market, now I see why.
Good day.

---

### Post by warfacegod on 2010-07-04
Those are almost certainly Microsoft figures and they are a lie. Those numbers don't take into account people that buy computers and simply wipe Windows off of it and install some form of Linux. And they are totally ignoring servers. Roughly 50% of the servers on the internet are Linux based. Hell, even your DVR is most likely Linux.

---

### Post by jwbrase on 2010-07-04
> **zerojett said:**
> "NOTE: If you enter your card information on AMD/ATI's driver page, it will offer you the Catalyst 9-3 driver to download. However, the Catalyst 9-3 driver doesn't support X servers past 1.5, and it will not work with Lucid! !!!SO BE CAREFUL!!! If you tried to install Catalyst on a system with one of these cards, see the 'Removing the Driver' section to restore the default/pre-installed driver"

Took some trouble to find, but I found the warning.
So, x.org doesn't support old versions of Catalyst.
I know it says it the other way around, but it is true in this sense as well.
And it probably isn't possible to downgrade x server or whatever...
I read somewhere that Linux only has 1-2% of the market, now I see why.
Good day.

Well, you don't have to use Lucid, first of all. In the Windows world, computers generally only get upgraded between versions once in their service life, if that. In the Linux world, it's possible to upgrade every 6 months, but not necessarily a good idea. I'm still using Jaunty. I'll probably upgrade (cautiously) to Lucid in a few months, but after that, I plan on staying with it till the end of its LTS life at the very least, if not for the rest of the life of the machine.

Secondly, if you're having video card problems, it may be good to turn of Compiz, if you're running it (I think Ubuntu defaults to it, which, even though I'd probably be using it anyways, isn't the best). You don't really need 3D effects on your desktop, and it can be buggy even with  a working 3D card.

Thirdly, I've had similar experiences with support for ATI cards (or lack thereof, whoever you want to blame for it). My first Ubuntu install was on another machine with an ATI card. An upgrade to Jaunty and the consequent switch of Xorgs and drivers left GNOME (or at least GNOME + Compiz) totally broken. I actually didn't try switching off Compiz, but rather using LXDE instead of GNOME, and LXDE gave me no such troubles.

> **warfacegod said:**
> Those are almost certainly Microsoft figures and they are a lie.

Actually, they're estimates from Web statistics sites.

The only Microsoft figures I've seen are considerably higher (around 5%).

> Those numbers don't take into account people that buy computers and simply wipe Windows off of it and install some form of Linux. And they are totally ignoring servers. Roughly 50% of the servers on the internet are Linux based. Hell, even your DVR is most likely Linux.

Server market share is totally irrelevant to the OP's hardware problems or his frustration therewith, and trying to contradict things that people say out of frustration seldom gets you anywhere, regardless of the truth or falseness of what they have said.

---

