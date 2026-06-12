---
title: "bitfonts, pixelfonts, xfonts system wide, please!"
date: 2012-03-18
forum: General Help
---

### Post by ohnonot on 2012-03-18
i like the old x-fonts very much and would love to use them system wide.
this seems to be totally impossible these days.

from my semi-noob-nerd point of view, the 2 systems (xfont and the new, what is it, truetype, xft...?) seem to exist totally seperately on my machine.
some terminals use xfonts, others use... truetype? xft?, conky is able to use both - and it looks really good on my desktop without xft.

using the truetype conversions of old pixelfonts usually does not look so good, plus most apps are scaling them to their own needs and these fonts look good only in one size.
i can't seem to set up a system wide rule to NOT scale them.

also it seems my old machine would be much faster if it don't have to apply font smoothing, hinting and all that. but that's a minor issue right now.

i also started a thread [back to X]("http://ubuntuforums.org/showthread.php?p=11774932#post11774932")

---

### Post by ohnonot on 2012-03-19
nobody has anything to say to this?
does that mean that it *is* totally impossible these days?

---

### Post by ohnonot on 2012-03-24
hello admins, could this be moved to a more frequented subforum?

---

### Post by The Cog on 2012-03-24
Moved to General Help

---

### Post by gutterslob on 2012-03-24
I'm not quite sure what you're asking for, exactly.
Do you mean you have a problem with your system displaying bitmap/pixel fonts?

I'm not a Ubuntu user any longer, but I think it's to do with Ubuntu having bitmap font support disabled by default. Iirc, you need to delete your /etc/fonts/conf.d/70-no-bitmaps.conf file

Here's an example: [http://iamfuss.deviantart.com/journal/How-to-install-artwiz-pixel-fonts-in-Ubuntu-226000883](http://iamfuss.deviantart.com/journal/How-to-install-artwiz-pixel-fonts-in-Ubuntu-226000883)

Hope this helps. Let me know if I've somehow misunderstood your question.

---

### Post by ohnonot on 2012-03-26
> Here's an example: [http://iamfuss.deviantart.com/journal/How-to-install-artwiz-pixel-fonts-in-Ubuntu-226000883](http://iamfuss.deviantart.com/journal/How-to-install-artwiz-pixel-fonts-in-Ubuntu-226000883)
this absolutely hit the spot! thanx gutterslob.
i have quite a few more fonts to choose from now. bitfonts.

but still, most of the fonts i can see with xfontsel (*-*-*-*-*-*-*-*-etc.) are not available. 

the explanation is getting a bit messy now, i hope someone takes the time to understand what i'm driving at:
i'm especially interested in bitfonts that *don't *scale. which, imho, bitfonts don't do by definition, but it seems that most environments (Xfce, firefox) scale them anyway, i don't know how.
however, since applying the quoted fix (or unfix) there are *some* of those newly available bitfonts that don't get scaled (meaning, if i change fontsize in some font selection gui, nothing happens), and some that do.

one example: the font family 'fixed' (misc fixed) is rather large, lots of different bitfonts in different sizes and weights. i do have a new font showing up called 'fixed', but it's always the same font being scaled and it looks blurry. so somehow the font 'engine' does not 'see' all those different choices for 'fixed'.
and that i would like to have very much. plus all the otther fonts i can see with xfontsel (so they are obviously installed) but cannot access right now.

and thanks to admin for moving the thread.

---

### Post by gutterslob on 2012-03-26
> **ohnonot said:**
> this absolutely hit the spot! thanx gutterslob.
i have quite a few more fonts to choose from now. bitfonts.Good to know. 


[quote=ohnonot]but still, most of the fonts i can see with xfontsel (*-*-*-*-*-*-*-*-etc.) are not available. [/quote]I haven't used Ubuntu in a long while, but if you did "sudo dpkg-reconfigure fontconfig-config" like in that guide I linked, you should have gotten a dialog box that asked you 3 questions. If you answered "Native", "Automatic" and "Yes" to the 3 questions it asked you, then you should be able to use most of your bitmap/pixel fonts in GTK apps after a reboot. That's how it works in Debian, at least. If you're still having problems, it might have something to do with either Ubuntu or the desktop environment you're running.


[quote=ohnonot]i'm especially interested in bitfonts that *don't *scale.[/quote]Yes, I get that.  


[quote=ohnonot]but it seems that most environments (Xfce, firefox) scale them anyway, i don't know how.
however, since applying the quoted fix (or unfix) there are *some*  of those newly available bitfonts that don't get scaled (meaning, if i  change fontsize in some font selection gui, nothing happens), and some  that do.[/quote]Depends. Some bitmap fonts come in more than 1 variant. Like fixed (the X11 included font set), which comes in many sizes. They're technically not scaling, its just that your font picker app (not sure what you use) is selecting a different set each time you change the size, which might give you the impression that they're being scaled. Some bitmap-like fonts do get scaled, however, since they come in .ttf format. Good example of that would be [Anonymous Pro](http://www.ms-studio.com/FontSales/anonymouspro.html). If you install that (just extract and drop in ~/.fonts and restart X - log out and back in) you'll notice that the smallest size (pt 8 or 9, I think) looks like a bitmap while scaling higher makes it look like a regular truetype.


> one example: the font family 'fixed' (misc fixed) is rather large, lots of different bitfonts in different sizes and weights. i do have a new font showing up called 'fixed', but it's always the same font being scaled and it looks blurry. so somehow the font 'engine' does not 'see' all those different choices for 'fixed'.
and that i would like to have very much. plus all the otther fonts i can see with xfontsel (so they are obviously installed) but cannot access right now. Not sure about the blurriness, but set it to size 9 and "semicondensed" (-Misc-Fixed-Medium-R-Semicondensed-*-12-110-75-75-C-60-ISO10646-1) and it should look pretty decent. 

Here's a tip. Install Terminus. It's included in Ubuntu/Debian repos. Package name is xfonts-terminus, if I remember correctly. Install and restart X, and then select it via whatever app you use to select system-wide fonts and for your terminals as well (size 9). Be warned, once you start using Terminus, you'll probably never want to use anything else. Heck, you'll even start writing .css stylesheets to override websites with terminus.

Another decent font family:
[http://proggyfonts.com/index.php?menu=download](http://proggyfonts.com/index.php?menu=download)
[http://proggyfonts.com/XWindowsFontInstall.txt](http://proggyfonts.com/XWindowsFontInstall.txt)

Hope this helps clear the fog a bit.

Cheers.

---

### Post by ohnonot on 2012-03-30
> **gutterslob said:**
> Good to know. 

I haven't used Ubuntu in a long while, but if you did "sudo dpkg-reconfigure fontconfig-config" like in that guide I linked, you should have gotten a dialog box that asked you 3 questions. If you answered "Native", "Automatic" and "Yes" to the 3 questions it asked you, then you should be able to use most of your bitmap/pixel fonts in GTK apps after a reboot. That's how it works in Debian, at least. If you're still having problems, it might have something to do with either Ubuntu or the desktop environment you're running.

Yes, I get that.  

Depends. Some bitmap fonts come in more than 1 variant. Like fixed (the X11 included font set), which comes in many sizes. They're technically not scaling, its just that your font picker app (not sure what you use) is selecting a different set each time you change the size, which might give you the impression that they're being scaled. Some bitmap-like fonts do get scaled, however, since they come in .ttf format. Good example of that would be [Anonymous Pro]("http://www.ms-studio.com/FontSales/anonymouspro.html"). If you install that (just extract and drop in ~/.fonts and restart X - log out and back in) you'll notice that the smallest size (pt 8 or 9, I think) looks like a bitmap while scaling higher makes it look like a regular truetype.

 Not sure about the blurriness, but set it to size 9 and "semicondensed" (-Misc-Fixed-Medium-R-Semicondensed-*-12-110-75-75-C-60-ISO10646-1) and it should look pretty decent. 

Here's a tip. Install Terminus. It's included in Ubuntu/Debian repos. Package name is xfonts-terminus, if I remember correctly. Install and restart X, and then select it via whatever app you use to select system-wide fonts and for your terminals as well (size 9). Be warned, once you start using Terminus, you'll probably never want to use anything else. Heck, you'll even start writing .css stylesheets to override websites with terminus.

Another decent font family:
[http://proggyfonts.com/index.php?menu=download](http://proggyfonts.com/index.php?menu=download)
[http://proggyfonts.com/XWindowsFontInstall.txt](http://proggyfonts.com/XWindowsFontInstall.txt)

Hope this helps clear the fog a bit.

Cheers.thanks again.
"sudo dpkg-reconfigure fontconfig-config" did not ask me anything.
no output, no error.

however, i found this about the "fixed" font family: i had a ttf-version of that installed which somehow prevented access to the actual "fixed" font. removied that, now it integrates perfectly into any font choosing dialog, meaning changing the font size gives me the appropriate sharp bitfont, not the scaled (blurry) ttf version.

---

### Post by ohnonot on 2012-03-31
unsolved again.
what works for 'fixed' does not work for most xfonts (always refering to what i see with xfontsel).
i'm working on it but any input is appreciated.

@gutterslob:
the fonts from the proggyfont page work only partly, i.e. all proggy* fonts show up as entries in a font choosing dialog, but not as fonts (some default font is displayed instead). any suggestions?

---

### Post by gutterslob on 2012-03-31
Did you follow the install guide for Proggy that I linked to?
Note: you have to run"xset fp+ ~/.fonts &" and "xset fp rehash &" at startup everytime, or add them to your startup script/file. Another way is to add the ~/.fonts folder to to the FontPath section of your /etc/X11/xorg.conf. I don't think Ubuntu comes with a xorg.conf these days, so you'll probably need to create one first. 

You could just use terminus like I stated before, you know. Just install the package (apt-get install xfonts-terminus). Pisses all over the proggy family in terms of clarity and sharpness (looks way better too, imho) and you don't have to do anything. Just install, restart X, and you'll be able to select it for GTK apps or via xfontsel.

---

### Post by ohnonot on 2012-03-31
> **gutterslob said:**
> Did you follow the install guide for Proggy that I linked to?
Note: you have to run"xset fp+ ~/.fonts &" and "xset fp rehash &" at startup everytime, or add them to your startup script/file. Another way is to add the ~/.fonts folder to to the FontPath section of your /etc/X11/xorg.conf. I don't think Ubuntu comes with a xorg.conf these days, so you'll probably need to create one first. 

You could just use terminus like I stated before, you know. Just install the package (apt-get install xfonts-terminus). Pisses all over the proggy family in terms of clarity and sharpness (looks way better too, imho) and you don't have to do anything. Just install, restart X, and you'll be able to select it for GTK apps or via xfontsel.no, i didn't get them to work. not that i was particular interested in that font.
but i did a major cleanup in my font directory, removing some more ttf 'covering' the good stuff. and mayb these commands in my startup script did some magic...
though i have a feeling that they're not doing anything.
main thing is, i have more and more bitfonts to choose from.

thanks a bunch to gutterslob.
[-o<\\:D/\\:D/[-o<
::: groovy! :::

---

### Post by ohnonot on 2012-04-01
this is for igeking. all others may ignore it.

---

