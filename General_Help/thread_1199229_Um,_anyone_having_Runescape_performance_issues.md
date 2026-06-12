---
title: "Um, anyone having Runescape performance issues?"
date: 2009-06-28
forum: General Help
---

### Post by hooless on 2009-06-28
Hey all,
       I'm experiencing a performance issue with the MMORPG RUNESCAPE. When I play it on Vista, my other OS on my system, it runs smoothly, no staggers. But when I run it on Ubuntu, I can't even run it well on bare minimum. anyone have an idea as to why that happens?

---

### Post by Blood//Stain//Child on 2009-06-28
> **hooless said:**
> Hey all,
I'm experiencing a performance issue with the MMORPG RUNESCAPE. When I play it on Vista, my other OS on my system, it runs smoothly, no staggers. But when I run it on Ubuntu, I can't even run it well on bare minimum. anyone have an idea as to why that happens?
 
Are you using Firefox?

---

### Post by hooless on 2009-06-29
> **Blood//Stain//Child said:**
> Are you using Firefox?

Yup, so is that the problem?

---

### Post by itsjareds on 2009-06-29
It is most likely because your graphics drivers are not installed or your driver doesn't perform as well as in Windows. For me, RSHD messes up and never deletes a movement, so a person walking around will have a giant trail of them :D

Try to see if you can install graphics drivers.

---

### Post by The Cog on 2009-06-29
Have you installed the sun java jre and plugin? I would not expect good performance from the open-source java that gets installed by dfault.

BTW, there is an issue that several people are seeing where Runescape crashes when trying to switch to HD full-screen mode on Ubuntu

---

### Post by brydonhunter on 2009-06-29
My son uses Firefox, Ubuntu 7.10 and Runescape runs like a charm. Like previously stated, check your video driver (huge issues with Firefox), check flash and java

Good luck

---

### Post by hooless on 2009-06-29
> **brydonhunter said:**
> My son uses Firefox, Ubuntu 7.10 and Runescape runs like a charm. Like previously stated, check your video driver (huge issues with Firefox), check flash and java

Good luck

hey, thanks! so, how do I check my vid driver on Ubuntu? I'm not all that good yet with ubuntu so ya...

---

### Post by hooless on 2009-06-29
Um, I'm using an integrated Mobile Intel Graphics media accelerator 4500m I think, so where could I get a driver for that??

---

### Post by Blood//Stain//Child on 2009-06-29
> **hooless said:**
> Um, I'm using an integrated Mobile Intel Graphics media accelerator 4500m I think, so where could I get a driver for that??

Intel graphics drivers are built into Ubuntu, you don't need to download and install anything. 

Back to the performance issue. That Intel IGP is actually pretty powerful for it's kind, so I highly doubt that's causing the problem.

I suggest trying Opera, and seeing if that is any better.

Here's the Opera download page.

[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

---

### Post by hooless on 2009-06-29
Sweet! thanks, but just to clarify some things... 1. I just realized that the card that I specified may not be the one that's my computer, but a card similar though. And, yes, Runescape does work with Opera, but only low detail; RSHD creates "tails" that screw up the visuals. Could that just be with Ubuntu 9.*whatever the new one is...*?

---

### Post by philcamlin on 2009-06-29
try installing the other java client from synaptic 

its not installed by default

---

### Post by hooless on 2009-06-29
> **philcamlin said:**
> try installing the other java client from synaptic 

its not installed by default

kk. do you know what it's called in synaptic?

---

### Post by Blood//Stain//Child on 2009-06-30
There does appear to be a problem. I have just tried RSHD on Firefox & Opera and it doesn't seem to work on either!

---

### Post by brydonhunter on 2009-06-30
It's not so much the actual Intel video driver but the new version of X server has some issues with some Intel video drivers. When I upgraded, I had terrible performance in Firefox. I deleted all of my old video settings from xorg.conf and restarted my X session. Performance has been perfect from Firefox since then.

WHat version of Ubuntu are you using? Was it an upgrade or a fresh install? If you are having the same problem with Opera, then it is not the browser and more likely pointing to X server and video driver.

Good luck.

---

### Post by hooless on 2009-06-30
> **brydonhunter said:**
> It's not so much the actual Intel video driver but the new version of X server has some issues with some Intel video drivers. When I upgraded, I had terrible performance in Firefox. I deleted all of my old video settings from xorg.conf and restarted my X session. Performance has been perfect from Firefox since then.

WHat version of Ubuntu are you using? Was it an upgrade or a fresh install? If you are having the same problem with Opera, then it is not the browser and more likely pointing to X server and video driver.

Good luck.

um im using the latest (9.04 i think) and I upgraded it. so how do you delete the vid settings from xorg.conf and restart the x session?

---

### Post by hooless on 2009-07-01
...bump

---

### Post by brydonhunter on 2009-07-02
Actually I made a backup copy of my xorg.conf file and then deleted the original from my /etc/X11 directory. Restarted X and everything work well for me. Didn't really look into why but it seems the new version of X operated differently concerning it's configuration files.

If your X crashes, log into a terminal session and copy your backup file back to your /etc/X11 directory.

Scott

---

### Post by hooless on 2009-07-03
> **brydonhunter said:**
> Actually I made a backup copy of my xorg.conf file and then deleted the original from my /etc/X11 directory. Restarted X and everything work well for me. Didn't really look into why but it seems the new version of X operated differently concerning it's configuration files.

If your X crashes, log into a terminal session and copy your backup file back to your /etc/X11 directory.

Scott

Ok, so I backed it up and I deleted it; now how do I restart the X session in ubuntu 9.04?

---

### Post by hooless on 2009-07-04
Ok, so I restarted the X Session, but it still didn't solve it; I can play on Standard detail just fine, but when I turn HD on, it starts out pretty well, but then it starts "tailing" then crashes. Now I'm just going to assume that it's RS itself, so I guess I'm just going to wait for an update from them.

---

