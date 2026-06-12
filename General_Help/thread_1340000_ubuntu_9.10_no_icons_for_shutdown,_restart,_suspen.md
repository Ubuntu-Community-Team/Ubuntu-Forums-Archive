---
title: "ubuntu 9.10 no icons for shutdown, restart, suspend etc"
date: 2009-11-28
forum: General Help
---

### Post by manuleka on 2009-11-28
i've just realised my newly installed Ubuntu 9.10 doesn't have any icons for the shutdown, restart, suspend etc menu... 

can i get these on? cheers

---

### Post by Elfy on 2009-11-28
I believe it is the indicator-applet-session - right click panel - Add to Panel

---

### Post by Aearenda on 2009-11-28
I suspect the OP is referring to the by-design lack of icons on the indicator-applet-session menu- see [bug 458929]("https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/458929")

---

### Post by manuleka on 2009-11-29
so is there a way of fixing this? i did notice that the icons were there when i first installed ubuntu.... but have done some updates (kernel updated also)

---

### Post by manny43 on 2009-11-29
it should be top right corner on your monitor

---

### Post by Aearenda on 2009-11-29
> **manuleka said:**
> so is there a way of fixing this? i did notice that the icons were there when i first installed ubuntu.... but have done some updates (kernel updated also)

I'm still not sure which icons you are referring to. Do you mean:
1. A power icon that used to appear at the right-hand end of the panel, which started the shutdown/hibernate/etc dialog?
2. The user-name-and-online-status icon (a.k.a. indicator-applet-session) that should appear by default on a recent fresh Ubuntu installation, and which reveals options for shutdown etc when you click on it?
3. The icons that you would expect to see alongside the text entries in the menu that appears when you click on the panel icon mentioned in (2)?
4. Icons and entries for shutdown and logout in the system menu?
5. Something else?

---

### Post by manuleka on 2009-11-29
yes Aearenda @ number 1... the power icon on the right corner of top panel... i'm referring to the icons on that drop down menu... the power icon is there next to my username, but when i click it the menu list only has the texts of shutdown, restart, suspend etc but no icons :( 

i know the icons are missing because there's blank space where the icons usually sits (next to the texts) 

anyone have any idea how to bring those icons back? maybe there's an option somewhere i'm missing? cheers

---

### Post by Aearenda on 2009-11-29
Actually what you just wrote sounds like what I meant with number 3 - the 'old' icon I was referring to in option 1 had no username next to it. But anyway, I think you're out of luck - it's on purpose, though there are many who would agree with you that there should be an option to put icons in. See [bug 458929]("https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/458929").

EDIT: By the way, if you have no need for the other 'presence' features offered by the indicator-session applet, you can remove it from the panel altogether, and then you will get proper icons for shutdown, logout and lock on the main 'system' menu. This isn't an option AFAIK if you use empathy, since you will lose your online status management and indication - but if you only use pidgin, you can set the preference to put its icon back in the notification area always and manage its online status directly from there. This is what I do, and I also remove the indicator applet (the one looking like an envelope) since it doesn't do anything useful for me.

---

### Post by manuleka on 2009-11-29
> **Aearenda said:**
> Actually what you just wrote sounds like what I meant with number 3 - the 'old' icon I was referring to in option 1 had no username next to it. But anyway, I think you're out of luck - it's on purpose, though there are many who would agree with you that there should be an option to put icons in. See [bug 458929]("https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/458929").

EDIT: By the way, if you have no need for the other 'presence' features offered by the indicator-session applet, you can remove it from the panel altogether, and then you will get proper icons for shutdown, logout and lock on the main 'system' menu. This isn't an option AFAIK if you use empathy, since you will lose your online status management and indication - but if you only use pidgin, you can set the preference to put its icon back in the notification area always and manage its online status directly from there. This is what I do, and I also remove the indicator applet (the one looking like an envelope) since it doesn't do anything useful for me.

cheers... i removed it... so am getting shutdown icon on system menu... thanks :)

---

