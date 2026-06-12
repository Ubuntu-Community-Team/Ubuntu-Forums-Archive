---
title: "Karmic: How would I change or remove startup sound and event sounds?"
date: 2010-01-05
forum: General Help
---

### Post by madmax.santana on 2010-01-05
Before karmic while I was using Jaunty, I used to do it all the time, play my favorite sounds wherever I was them, startup, error, login, logout, etc etc... I found it in System>Preferences>Sound...

But when I do the same in Karmic, the opening dialogue box doesn't give me an option to change every sound specifically, instead, although it gives me option to choose a sound theme of my own. But for that I must first compile a theme and then install it / place it in sound themes directory etc etc.

How would I change sounds for particular events without having to compile a whole new theme (customizing the current Ubuntu sound theme)...

Also, could someone direct me please,how do I create sound themes for Ubuntu and them install them in my Ubuntu?

Thanks all.

---

### Post by dcstar on 2010-01-06
> **madmax.santana said:**
> Before karmic while I was using Jaunty, I used to do it all the time, play my favorite sounds wherever I was them, startup, error, login, logout, etc etc... I found it in System>Preferences>Sound...

But when I do the same in Karmic, the opening dialogue box doesn't give me an option to change every sound specifically, instead, although it gives me option to choose a sound theme of my own. But for that I must first compile a theme and then install it / place it in sound themes directory etc etc.

How would I change sounds for particular events without having to compile a whole new theme (customizing the current Ubuntu sound theme)...

Also, could someone direct me please,how do I create sound themes for Ubuntu and them install them in my Ubuntu?

Thanks all.

9.10 changed all this stuff and there are (currently) no tools to make changes, you have to do things manually. Do a web search as there are instructions around.

---

### Post by joeyadams on 2010-01-15
This might not be the best solution, but here's what I did:

```
cd /usr/share/sounds/ubuntu/stereo
sudo mkdir shutup
sudo mv -i desktop-login.ogg shutup/
```

The sound themes are stored in /usr/share/sounds/ .  This simply moves the login theme sound into a folder where Ubuntu won't find it and will (hopefully) not play it nor complain.

The correct solution probably involves editing the GConf registry in either /desktop/gnome/sound or /schemas/desktop/gnome/sound so the login sound is specifically disabled for the current user rather than for all users.  Nevertheless, the solution I posted above will probably make other users happy too :P

---

### Post by rading on 2010-01-25
That was a quick way to make it shut up!! Hehe...

Cheers man!!!

---

### Post by madmax.santana on 2010-01-25
Yeah nice bud!
But what if I want to change them??? Hehe

---

### Post by Omeil on 2010-01-30
> **madmax.santana said:**
> Yeah nice bud!
But what if I want to change them??? Hehe

I presume you would rename the startup SFX file you want to desktop-login.ogg and move it into the stereo directory? Please correct me if im wrong.

Regards,

Omeil

---

