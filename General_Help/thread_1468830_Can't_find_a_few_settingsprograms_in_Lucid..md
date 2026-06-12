---
title: "Can't find a few settings/programs in Lucid."
date: 2010-05-01
forum: General Help
---

### Post by arsenic23 on 2010-05-01
I'm having a great transition from Hardy to Lucid.  It has to be the most painless setup I've had since Breezy.  There is only a few things I haven't found or figured out yet:

[LIST][*]
[COLOR="Gray"]No xsane support in GIMP?  Is there a way to scan directly into the GIMP?
(xsane works correctly, but I don't see an import option like GIMP used to sport.)[/COLOR]
[COLOR="DarkRed"]**Solved!** Durr: File > Create > Xsane -- I'm blind.[/COLOR]
[*]
[COLOR="Gray"]Where is the setting to rotate the cube with the mouse wheel when the mouse is over unoccupied desktop?
(I've gotten the scroll on edges to work correctly, which was a real relief since that had been a headache in some of the other releases.)[/COLOR]
[COLOR="DarkRed"]**Solved!** Viewport Switcher > Desktop-based Viewport Switcher -- I expected it to be in the cube settings.  I think that's where it used to be.  Oh well, I don't know why it took me so long to see. [/COLOR]
[*]
[COLOR="Gray"]Where is gmplayer?  All I see is mplayer without the GUI controls.[/COLOR]
[COLOR="DarkRed"]**Solved!**  gmplayer is called mplayer-gui now.  It's still *gmplayer* to start it, but mplayer-gui to install.  That's dumb.[/COLOR]
[*]
[COLOR="Gray"]Where is the repeat button on this new Amarok?[/COLOR]
[COLOR="DarkRed"]**Solved!** It's right there at the bottom in plain site.  Uhh.[/COLOR]
[*]
[COLOR="Gray"]Is there a list of all the blogger, social networking crap, and IM packages?  I'd love to get these off my system, especially whatever causes that mail icon in the notification area.[/COLOR]
[COLOR="DarkRed"]**Solved!** Thanks ankspo71.  Removing everything from the list provided minus *indicator-applet* and including *indicator-messages* worked perfect.[/COLOR][/LIST]


If anyone could point point me in the correct direction regarding even one of these things I would really appreciate it.

---

### Post by cariboo on 2010-05-01
You can purge indicator-me, to get of the me menu.

---

### Post by arsenic23 on 2010-05-01
> **cariboo907 said:**
> You can purge indicator-me, to get of the me menu.

Are you sure? * sudo apt-get purge indicator-me* did nothing.  Logged off and back on, rebooted.  It's still there.

---

### Post by ankspo71 on 2010-05-01
Here's one way to remove some of the newest features:

[http://sticky-bones.blogspot.com/2010/04/removing-some-new-features-from-lucid.html](http://sticky-bones.blogspot.com/2010/04/removing-some-new-features-from-lucid.html)

---

### Post by arsenic23 on 2010-05-01
> **ankspo71 said:**
> Here's one way to remove some of the newest features:

[http://sticky-bones.blogspot.com/2010/04/removing-some-new-features-from-lucid.html](http://sticky-bones.blogspot.com/2010/04/removing-some-new-features-from-lucid.html)

Thanks, but if you remove indicator-applet then you'd loose the volume control slider.  It's the only one that seems to work correctly too.  Other then that the list is very helpful.  Other then that envelope icon in the indicator applet I'm feeling pretty cleaned up.

-----
Addition:  It seems clicking on the envelope does not bring up a menu anymore as I've removed everything it addresses.  Stupid stupid social icon.

---

### Post by ankspo71 on 2010-05-01
Hmm, try pressing Alt+F2 then running gnome-volume-control-applet and see if that works as good. If it does, I think you could make an autostart entry for it. It uses the old style icon though.

---

### Post by arsenic23 on 2010-05-01
> **ankspo71 said:**
> Hmm, try pressing Alt+F2 then running gnome-volume-control-applet and see if that works as good. If it does, I think you could make an autostart entry for it. It uses the old style icon though.

Brilliant!  I'd just stupidly assumed that gnome-volume-control-applet was no longer present/available/even an option.  I've had to move my panel around to keep it from appearing in odd places, but that works just fine.

-----------------
Addition:

Oh, even better, *indicator-messages*, is the package responsible for that envelope icon. Removing it fixes the problem and allows me to continue to use the indicator-applet.

---

