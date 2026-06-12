---
title: "ati opensource already installed?"
date: 2010-12-30
forum: General Help
---

### Post by deadpool15 on 2010-12-30
hi im new to linux. say you have an ati radeon 9200 graphic card and when you installed ubuntu 10.10 onto your computer, is it already using the ati open source drivers? 

and if you go to system > administration> additional drivers ----- and said " no proprietary drivers are use on this system" ------ does that mean my ati radeon 9200  card wont be able be installed with the fglrx drivers?

i just wanted to ask this because it seem like i could never install the proprietary ati driver and i dont want to waste more time looking over 2 weeks for an answer. thanks in regard

---

### Post by jocko on 2010-12-30
The answer to both of your questions: Yes.

---

### Post by tech-hero on 2010-12-30
> **deadpool15 said:**
> hi im new to linux. say you have an ati radeon 9200 graphic card and when you installed ubuntu 10.10 onto your computer, is it already using the ati open source drivers? 
 
and if you go to system > administration> additional drivers ----- and said " no proprietary drivers are use on this system" ------ does that mean my ati radeon 9200 card wont be able be installed with the fglrx drivers?
 
i just wanted to ask this because it seem like i could never install the proprietary ati driver and i dont want to waste more time looking over 2 weeks for an answer. thanks in regard
 
 
hmmm.. i kinda confused with this thing. .but based on my experience, i have this ATI RADEON graphic card in my laptop,,, you can survive without installing its proprietary driver, but you can't maximize its full potential. you wont be able to apply effects on your desktop because the system will say that you don't have hardware to support it. so i guess, if you really want to, you can install it if you really want to...

---

### Post by trinitydan on 2010-12-30
I was mistaken previously and the open source driver is really not all that bad.  It seems that when I first Install 10.10 I mistakenly thought that the correct driver was not installed and tried to install the ATI driver that doesn't work.  In the process I messed up my open source driver.  I have it configured correctly now and I am in fact able to enable desktop effects and 3d screensavers.  The open source driver is not as bad as I was making it out to be at all.

---

### Post by dcstar on 2010-12-30
> **deadpool15 said:**
> hi im new to linux. say you have an ati radeon 9200 graphic card and when you installed ubuntu 10.10 onto your computer, is it already using the ati open source drivers? 
........

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by mcduck on 2010-12-30
> **trinitydan said:**
> I agree, the ATI driver did work better for my card.  I was able to enable desktop effects, although they didn't work all that great.  With the open source driver I can't enable desktop effects or 3D screensavers.

That won't help the OP of this thread, as the fglrx driver doesn't support Radeon 9200 any longer.

The opensource radeon driver is the best one can have for that card at this moment, and it's already installed & used by default.

---

### Post by clhsharky on 2010-12-30
deadpool15

jocko is correct.
The open source drivers are correct for your legacy chip(ATI Radeon 9200) in ubuntu 10.10.
fglrx drivers does not support legacy chips.
ATI suports legacy chips with radeon driver in the open source stack.

> you wont be able to apply effects on your desktop

With the open source driver I can't enable desktop effects or 3D screensavers. 
Why not?
3D is supported on radeon legacy chips now days.
[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

deadpool15 ati radeon 9200 graphic chip is a r200 card.


Sharky

---

### Post by deadpool15 on 2010-12-30
thanks for the inputs EVERYONE. I didn't know I was using Ati open source drivers until now. 

another quick question: any other distro version would you recommend for my card that would fit best performance wise? my friend recommend me ubuntu 10.10 for beginning linux user but I heard there are other distros that also suits for newbies like me. 

AGAIN, THANKS FOR ANSWERING.

---

### Post by cottfcfan on 2010-12-30
Linux Mint 10 is probably the best if your new to linux.
all the audio & video codecs are installed by default as well as extra software.

---

### Post by trinitydan on 2010-12-31
> **clhsharky said:**
> 
Why not?
3D is supported on radeon legacy chips now days.
[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

You are correct, it was a configuration error on my part and I now have 3D graphic acceleration on my ATI Radeon Xpress as it would have by default if I wouln't have tampered with it.  I removed the false information from my prior post.  Thank you for setting me straight on that!  It actually works pretty well.

---

