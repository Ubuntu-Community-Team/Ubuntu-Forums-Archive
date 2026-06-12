---
title: "Firefox font is too blurry"
date: 2009-10-26
forum: General Help
---

### Post by Mackan2 on 2009-10-26
Hi.
I have been trying to solve this problem for quite some time now, hopefully some of you have already solved this and can guide me in the right direction.

Firefox fonts are too blurry for me, I don't know where to change the font-blur-settings. It is not affected by the system wide settings in ubuntu.

Check out my screen shot and you'll see what I mean, ubuntu to the left and windows to the right. I prefer the windows way, how can I set that up??

Better screenshot: [http://dl.getdropbox.com/u/599715/screen.png](http://dl.getdropbox.com/u/599715/screen.png)

---

### Post by Scunizi on 2009-10-26
Check out System>Preferences>Appearance>Fonts and change to the one you like the most.. I have mine set at Subpixel Smoothing for LCD's.. you might also change the default font used by Firefox from inside FF's preferences dialogue.

---

### Post by Mackan2 on 2009-10-26
System>Preferences>Appearance>Fonts do not change the fonts in firefox for me, is this strange?

Firefox's preferences won't let me change font anti-aliasing, just default fonts. I guess default fonts is not used in my screenshot?

Better screenshot: [http://dl.getdropbox.com/u/599715/screen.png](http://dl.getdropbox.com/u/599715/screen.png)

---

### Post by fooman on 2009-10-26
do you have the microsoft true type fonts installed?

i think the package is called "ttf-mscorefonts-installer" (available in synaptic)...or just install the "ubuntu-restricted-extras" package and it will install them along with a few other, much needed things like flash.  :)

---

### Post by winotree on 2009-10-26
See if this helps [http://ubuntuforums.org/showthread.php?p=7094387](http://ubuntuforums.org/showthread.php?p=7094387)  ;)

---

### Post by coffeecat on 2009-10-26
> **Mackan2 said:**
> System>Preferences>Appearance>Fonts do not change the fonts in firefox for me, is this strange?

You need to restart Firefox after changing the font setting. Go to System > Preferences > Appearance > Fonts (or right-click on the desktop, choose "Change Desktop Background" and click on the Fonts tab - it's quicker) and then under "Rendering", choose Monochrome. Now restart Firefox. That will give you a non-aliased font rendering somewhat like the old Windows default. Or try "Best Contrast" and restart Firefox. That looks more or less like the Vista/Win7 default.

Personally, I think that (and the Windows default) looks **ghastly**. It reminds me of the output of a particularly cheap and nasty dot-matrix printer. (You're probably too young to remember them. :wink: ) And I prefer the Ubuntu default and the Ubuntu rendering in your screenshots. But don't mind me - go for what you like. :)

---

### Post by Mackan2 on 2009-10-26
OK guys.

The MS fonts are installed.

I followed the guide winotree linked.

I restarted Firefox, several times.

No luck! Check out this screen shot:
[http://dl.getdropbox.com/u/599715/screen2.png](http://dl.getdropbox.com/u/599715/screen2.png)
As you can see; the system font uses no smoothing whatsoever in terminal but Firefox still use a smooth font, even in the menus.

From what I can remember, this has always been an issue for me when using Ubuntu (sporadically since around 6.10, now full time!). I'm on 9.10 beta BTW.

---

### Post by Mackan2 on 2009-10-26
OK, I'm playing around a bit with the settings in /etc/fonts/conf.d/ and I finally see some changes...

rm 10-hinting-slight.conf
ln -s ../conf.avail/10-hinting-medium.conf .

That one helped a bit... Now I guess I have to try them all :-)

Thanks guys!

UPDATE:
I just matched the symlinks in the folder /etc/fonts/conf.d/ with the settings from the Gnome-font-setting-GUI. 
i.e.
10-hinting-full.conf
10-sub-pixel-rgb.conf
and removed all other 10-* symlinks...

Not as edgy as the Windows example in my first screenie - I think I prefer correct anti-aliasing before none... and none anti-aliasing before incorrect...


PS. How do I change the status of this thread to [SOLVED]??

---

