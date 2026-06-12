---
title: "dual monitors settings?"
date: 2010-10-17
forum: General Help
---

### Post by lazylew on 2010-10-17
My 2 monitors are "cloned" in Xubuntu, but I want them separate.
I thought this could help me:
[http://ubuntuforums.org/showthread.php?t=1161731&highlight=monitors](http://ubuntuforums.org/showthread.php?t=1161731&highlight=monitors)
but there's talk of an xorg.conf file, which I don't even have.

How do I get my 2 monitors working separately?

---

### Post by lazylew on 2010-10-23
> **lazylew said:**
> My 2 monitors are "cloned" in Xubuntu, but I want them separate.
I thought this could help me:
[http://ubuntuforums.org/showthread.php?t=1161731&highlight=monitors](http://ubuntuforums.org/showthread.php?t=1161731&highlight=monitors)
but there's talk of an xorg.conf file, which I don't even have.

How do I get my 2 monitors working separately?
Could someone please tell me whether or not it is possible to get 2 monitors working (separately!)?
All I can find is talk about the xorg.conf file, which does not exist in Xubuntu.

If it's not possible, I'll have to switch to Ubuntu again.

---

### Post by QIII on 2010-10-23
xorg.conf no longer exists by default.

Could you give us some information on your graphics card, what driver you have installed, etc?

---

### Post by TroN-0074 on 2010-10-23
In the regular ubuntu (Not xubuntu) under System>preferences>Monitors you have the option checked "same image in all monitors" just uncheck that option and select apply.

---

### Post by lazylew on 2010-10-23
> **QIII said:**
> xorg.conf no longer exists by default.

Could you give us some information on your graphics card, what driver you have installed, etc?I know it's Nvidia, but that's it. About drivers I haven't got a clue.
I know one monitor (22" amw) is best at 1680x1050 and the smaller one (15" Medion) on 1024x768, but that's as far as my hardware knowledge goes.

---

### Post by lazylew on 2010-10-23
Say QIII, do you use Xubuntu? You're the first one to respond in 6 days, so I'm wondering how many people here actually use Xubuntu :confused:
If you're not sure about the possibility of 2 screens in Xubuntu because you're on Ubuntu yourself, just say so, because I'm about to change over (again).

No disrespect (email sometimes reads different than what's intended); I'm just tired of 3 weeks of OS-hopping/tweaking and setbacks :(

I do appreciate the reply you gave :popcorn: (I never post with only sad smilies ;-))

---

### Post by clhsharky on 2010-10-23
lazylew

That question came up in irc #xubuntu yesterday and the mod said that xfce4 (duel monitors working separately) will not work. And that the xfce4 dev's were not interested in changing that feature. The mod recommended Ubuntu.
I did not know that about duel monitors with xfce4 and I use Xubuntu on 5 year old box, but never tried it.

Live and learn.

Sharky

---

### Post by lazylew on 2010-10-24
> **clhsharky said:**
> lazylew

That question came up in irc #xubuntu yesterday and the mod said that xfce4 (duel monitors working separately) will not work. And that the xfce4 dev's were not interested in changing that feature. The mod recommended Ubuntu.
I did not know that about duel monitors with xfce4 and I use Xubuntu on 5 year old box, but never tried it.

Live and learn.

SharkyThank you Sharky, at last the uncertainty about this is resolved.
Back to Ubuntu it is then!

---

### Post by xurious on 2010-10-24
Edit: I'm using xubuntu 10.10

I just installed xubuntu this morning... I have my dual monitors of different resolutions(1440x900, 1024x768 ) working.

It was cloned during the xubuntu install.
Stayed cloned during first login.
Updated to nvidia drivers.
Rebooted, went into nvidia settings, enable both monitors, reboot again.

Presto, it works.

---

### Post by lazylew on 2010-10-24
> **xurious said:**
> Edit: I'm using xubuntu 10.10

I just installed xubuntu this morning... I have my dual monitors of different resolutions(1440x900, 1024x768 ) working.

It was cloned during the xubuntu install.
Stayed cloned during first login.
Updated to nvidia drivers.
Rebooted, went into nvidia settings, enable both monitors, reboot again.

Presto, it works.well, I changed to Ubuntu earlier today and I think I'll stick with it for now. 
Thanks for the tip; if ever I want to go Xubuntu again I'll try it.

---

### Post by eldiabolosk on 2010-12-12
Lazylew: Did you get your dual monitor issue solved? I just installed Xubuntu 10.04 32bit using a Matrox G450 card. The screens are clonned, but I would love to achive a fluid single view stretched over two screens. Please let me know if that worked in Ubuntu. Thanks. 

Ed.

---

### Post by lazylew on 2010-12-12
> **eldiabolosk said:**
> Lazylew: Did you get your dual monitor issue solved? I just installed Xubuntu 10.04 32bit using a Matrox G450 card. The screens are clonned, but I would love to achive a fluid single view stretched over two screens. Please let me know if that worked in Ubuntu. Thanks. 

Ed.yes, I had it sorted by switching to regular Ubuntu ;)
I know nothing about what you call "a fluid single view stretched over two screens", since I always use the two screens separately.

---

### Post by eldiabolosk on 2010-12-12
What I want to achieve is that two monitors will show one desktop. Part of the desktop will be on monitor one, and the other part will be on monitor two. Essentially I do not want them to show the same thing. I want to be able to navigate my mouse from monitor one to monitor two acting as a big screen. Is this what you achieved?

ed

---

### Post by lazylew on 2010-12-12
> **eldiabolosk said:**
> What I want to achieve is that two monitors will show one desktop. Part of the desktop will be on monitor one, and the other part will be on monitor two. Essentially I do not want them to show the same thing. I want to be able to navigate my mouse from monitor one to monitor two acting as a big screen. Is this what you achieved?

edno, what I do is have one screen with eg firefox and the other with openoffice - separation is what I aimed for. For me it's most practical.

---

### Post by eldiabolosk on 2010-12-12
I guess my goal is very similar. Thank you.

Ed.

---

