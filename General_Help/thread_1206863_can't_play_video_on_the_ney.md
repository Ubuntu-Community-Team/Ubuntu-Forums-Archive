---
title: "can't play video on the ney"
date: 2009-07-07
forum: General Help
---

### Post by findit on 2009-07-07
Ok I think i have every thing up and running(thanks), but when i go on the net and i click on a video it tells me it can not play it because my OS does not meet the requirments or I need macroflash player. I did notice different types of flash player for linux for ex. YUM, .rpm, .deb. What do I need to do to get streaming videos to play. Thanks

---

### Post by abhi_69 on 2009-07-07
install flashplugins-nonfree from medibuntu repo.
*********
# apt-get install flashplugins-nonfree
********
hope this can play online flash videos. use mplayer or vlc to play flash videos from local disk.

---

### Post by philinux on 2009-07-07
> **findit said:**
> Ok I think i have every thing up and running(thanks), but when i go on the net and i click on a video it tells me it can not play it because my OS does not meet the requirments or I need macroflash player. I did notice different types of flash player for linux for ex. YUM, .rpm, .deb. What do I need to do to get streaming videos to play. Thanks

If this is a fresh install and you want flash and to be able to play DVD's then click the Medibuntu and Restricted Formats links below. Make sure you follow the instructions to the letter.

---

### Post by findit on 2009-07-07
I'm sorry is that non-free as in you have to pay for them? Will the macromedia ones not work?

---

### Post by philinux on 2009-07-07
> **abhi_69 said:**
> install flashplugins-nonfree from medibuntu repo.
*********
# apt-get install flashplugin[COLOR="Red"]**s**[/COLOR]-nonfree
********
hope this can play online flash videos. use mplayer or vlc to play flash videos from local disk.

flashplugin-nonfree is in the ubuntu multiverse repo. Does not come from medibuntu.

To install it on ubuntu from a terminal you would need:-
```
**sudo** apt-get install flashplugin-nonfree
```

Cheers

---

### Post by findit on 2009-07-07
Yes Phil it is a fresh install. I though some of the media players are in the install

---

### Post by philinux on 2009-07-07
> **findit said:**
> Yes Phil it is a fresh install. I though some of the media players are in the install

If you follow the links it is not media players but codecs etc.

---

### Post by philinux on 2009-07-07
> **findit said:**
> I'm sorry is that non-free as in you have to pay for them? Will the macromedia ones not work?

Non free means means it is proprietary software but not open source. You dont have to pay.

A good rule is to install software from add/remove or synaptic. Only occasionally direct from websites.

Make sure you take time to read the stickies in the absolute beginners forum

---

### Post by findit on 2009-07-07
Ok thanks, so the mediabuntu should have everything I would need?

---

### Post by philinux on 2009-07-07
> **findit said:**
> Ok thanks, so the mediabuntu should have everything I would need?

And restricted formats. Take your time to read the info on both sites.

---

