---
title: "Turn Off Google Chrome Button Sounds"
date: 2010-02-03
forum: General Help
---

### Post by zeroseven0183 on 2010-02-03
Hi! I'm trying KDE now however, I found something that annoys me a little bit. I'm using Google Chrome and noticed that there's a sound every time I click a button (whether it's the Close, or the New Tab, or the Minimize button). It's just a notification sound though. Very short.

Is there a way to, somehow, disable this?

Other browsers and applications do not have that sound.

---

### Post by zeroseven0183 on 2010-02-04
* bump *

---

### Post by zeroseven0183 on 2010-02-06
Anyone else having this same instance with Google Chrome in Kubuntu?

---

### Post by Kurogane21 on 2010-02-08
Yeah I'm having the same thing, I'm not sure how to turn it off.

---

### Post by shayguitarra on 2010-02-13
Yes, the same thing is happening to me. I've searched right through the Notification options and can find nothing.

It is more than a little annoying.

---

### Post by zeroseven0183 on 2010-02-15
3 people having the same problem now.. Any KDE experts?

---

### Post by lflindsey on 2010-02-18
I had the same problem, and I found a fix.  At least, it works for me.

In a terminal, run gnome-volume-control
In the Sound Effects tab, change sound theme to No Sounds.

That should do it.

---

### Post by shayguitarra on 2010-02-18
That works.

In my case I already had "No Sounds" selected, and I also had to tick the mute box.

As an aside, I think this effects more than Chrome. I've had the same problem with my music player, gmusicbrowser.

---

### Post by ezabi on 2010-02-25
I tried the gnome-volume-control and chose no sound but failed.
Muting the volume would affect all the system sounds.
I had to replace the sound file that is being used by the system with an empty sound file

*```
sudo mv /usr/share/sounds/ubuntu/stereo/button-pressed.ogg /usr/share/sounds/ubuntu/stereo/button-pressed.ogg.old
```*

*```
sudo touch /usr/share/sounds/ubuntu/stereo/button-pressed.ogg
```*

---

### Post by five4ty7am on 2010-04-14
i had the same problem using 9.10 and, after backing the files up somewhere safe, deleted the contents of -

/usr/share/sounds/ubuntu/stereo 

these are the origional install sound files for login, logout, question boxes, etc.

---

### Post by cyrylski on 2010-07-11
> **shayguitarra said:**
> That works.

In my case I already had "No Sounds" selected, and I also had to tick the mute box.

As an aside, I think this effects more than Chrome. I've had the same problem with my music player, gmusicbrowser.

I had exactly the same problem after installing Kubuntu desktop over my previous Gnome install. 

I reckon it's a matter of confused settings, as this affected my various non-KDE apps as well. That helped, though. 

Antother question is why are Gnome sounds playing at all in KDE environment, is there any service or anything that provides them? Just curious...

---

### Post by dramagods on 2010-09-04
Hi,
I had the same problem. I had installed Gnome on my Kubuntu and when I removed it some Gnome sounds remained in my KDE desktop. 

I solved it removing the ubuntu-sounds package.

---

### Post by Gaba_p on 2011-02-25
Same problem after installing KDE. I already had 'No sounds' selected, and muting sound effects in gnome-volume-control would mute ALL system effects, no good...

I'll try removing the ubuntu-sounds package, but I'm guessing I'll lose all system sounds.

---

### Post by Gaba_p on 2011-02-25
Of course, opening gnome-volume-control now results in several errors.

Anybody knows the KDE equivalent of gnome-volume-control??

For what I can tell there's no way of selecting a sounds 'package' (as 'No sounds' or 'KDE sounds' or 'Users sounds') like there is in gnome-volume-control...

---

### Post by russelld on 2012-09-04
> **ezabi said:**
> I tried the gnome-volume-control and chose no sound but failed.
Muting the volume would affect all the system sounds.
I had to replace the sound file that is being used by the system with an empty sound file

*```
sudo mv /usr/share/sounds/ubuntu/stereo/button-pressed.ogg /usr/share/sounds/ubuntu/stereo/button-pressed.ogg.old
```*

*```
sudo touch /usr/share/sounds/ubuntu/stereo/button-pressed.ogg
```*

awesome!!!

this worked to kill the chromium tab closing noises!! :P

thanks

---

