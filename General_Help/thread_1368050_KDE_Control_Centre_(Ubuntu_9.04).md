---
title: "KDE Control Centre? (Ubuntu 9.04)"
date: 2009-12-30
forum: General Help
---

### Post by zcacogp on 2009-12-30
Chaps, 

A question that may betray how little I know of what I am talking about, but here goes. 

I have been playing around with the sound on my system, more specifically removing and pulseaudio to try and make Skype work, but re-installing it when I found that various other things didn't work as well without it. 

Both after removal and after re-installation, I have had a warning message when starting Amarok, telling me that various audio settings have been changed, and allowing me access to a screen I haven't seen before, which allowed me to set volume levels independently for different bits of software. The screen was called "KDE Control Centre", and looked very useful, but having closed it I don't know how to access it again. 

So, I am using Ubuntu 9.10 (Karmic); where do I find KDE Control Centre? A search on here has suggested running kcontrol from the terminal, but that tells me "kcontrol: command not found". 

Sorry for such a dense question ... all help appreciated (the sound level in Amarok is quite low, and I want to turn it up!)


Oli.

---

### Post by kellemes on 2009-12-30
> **zcacogp said:**
> So, I am using Ubuntu 9.10 (Karmic); where do I find KDE Control Centre? A search on here has suggested running kcontrol from the terminal, but that tells me "kcontrol: command not found". 

I believe "kcontrol" is replaced with "systemsettings".

---

### Post by zcacogp on 2009-12-30
Kellemes, 

Thanks. That's helpful. 

When I type "systemsettings" into the terminal, it tells me it isn't installed. However I know that KDE Control Centre *is* installed, as I have seen it ... I guess the answer is to install systemsettings and see how we get on. 


Oli.

---

### Post by kellemes on 2009-12-30
> **zcacogp said:**
> Kellemes, 

Thanks. That's helpful. 

When I type "systemsettings" into the terminal, it tells me it isn't installed. However I know that KDE Control Centre *is* installed, as I have seen it ... I guess the answer is to install systemsettings and see how we get on. 


Oli.

Don't know to be honest. I'm not using KDE currently, I'm on XFCE.

So, you're working from Gnome I understand?
Isn't there some volume-manager available in the Gnome-menu's? Or is this not working?

---

### Post by zcacogp on 2009-12-30
Thanks again kellemes - systemsettings has indeed produced something very similar to that which I saw before - it seems to have the different device preferences for the different applications, and a load of other settings as well (fonts, colours etc.) 

It doesn't have the individual volume controls for different applications as well. Yes, I'm on Gnome ... I'll have another hunt through other bits of the menus. 

Thanks for your help. 


Oli.

---

### Post by zcacogp on 2009-12-30
Gottit. Pulse Audio Volume Control. "pavucontrol" or under "Applications > Sound and Video > PulseAudio Volume Control". 


Thanks again. I think I need to know more about the way that sound is handled in Ubuntu as I don't understand all that is going on, but that is a different question for a different time. 


Oli.

---

### Post by kellemes on 2009-12-30
> **zcacogp said:**
> I think I need to know more about the way that sound is handled in Ubuntu as I don't understand all that is going on, but that is a different question for a different time. 

I know.. especially when using KDE apps withing a Gnome environment things tend to become messy, well, that's my experience anyway.

Glad you fixed it for now..

---

