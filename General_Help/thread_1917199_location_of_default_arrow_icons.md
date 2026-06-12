---
title: "location of default arrow icons?"
date: 2012-01-29
forum: General Help
---

### Post by scubscub on 2012-01-29
Hello, in Lubuntu 11.10, I have these left/right arrows which show up in a number of applications (firefox, Evince, File roller, the file manager).  I want to change them, but changing the theme, the icons, etc. through "customize look and feel" has no effect.

So I figured I would find where these are located and change them that way, but I can't figure out where they would be.  I've been poking around in usr/share/icons with no success.


Does anyone know where I should look?

Thanks for any help...

---

### Post by scubscub on 2012-02-01
I'm still puzzled by this.  I can change the theme on firefox, but for the rest of the programs, nothing has any effect.  How do I change these arrows when the "customize appearance" option has no effect?

Surely, there must be a location somewhere on the computer where these icons are kept.

---

### Post by scubscub on 2012-02-03
bump...

---

### Post by Rodney9 on 2012-02-03
Firefox has it's own themes - [https://addons.mozilla.org/en-US/firefox/themes/](https://addons.mozilla.org/en-US/firefox/themes/)

You can change icons in Menu - Preferences - 'Customize Look and Feel' under the 'Icon Set' Tab

For a cool Icon set see  - [http://ubuntuforums.org/showthread.php?t=1880394](http://ubuntuforums.org/showthread.php?t=1880394)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by scubscub on 2012-02-03
Hi Rodney, thanks for replying.  

The arrow icons I want to change appear in certain programs, like evince, pcmanfm, etc.  (of course I could change the theme in firefox, but that does not change the other programs).

These arrows do not change when I change the theme or the icons via the "customize look and feel" ui.

I figure that these must be part of a default look for lubuntu or lxde, so I figure they must be in some specific directory -- so even though the customize ui is not affecting them, I could go to that directory and do it myself.

Any idea where it could be?

And perhaps I am describing these wrong -- should I be calling them "buttons" instead of "icons"?

---

### Post by Rodney9 on 2012-02-03
Yes I think maybe they are buttons, but I think I know what you mean now.

There seems to be only two sets of arrows though.

You can change them in Menu - Preferences - 'Customize Look and Feel' under the 'Widget' Tab

There maybe some other way possibly in the .config files, but I don't know.

Rodney

---

### Post by scubscub on 2012-02-05
Yep, changing them in the "widget" tab of "customize look and feel" has no effect.  Even if I pick a theme that shows different arrow buttons in the preview, on my actual computer everything else changes but not the arrows.

As to .config files, I'll try to check it out.  I had thought these programs might all be targetting the same arrow buttons somewhere through symbolic links -- when I searched "arrow" in the file system I just found a bunch of symlinks, and couldn't figure out where they were pointing, or if they were involved anyway.

---

