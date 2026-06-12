---
title: "Ubuntu &amp; Firefox fonts look horrible on a 13&quot; Laptop"
date: 2009-10-05
forum: General Help
---

### Post by cyanide on 2009-10-05
Hi,
   I have just installed Ubuntu 9.04 ( Juanty Jacklope ) on my 13.3" laptop (Resolution 1280*800). My problem is that all the fonts on Ubuntu and Firefox look thick and chunky. It really screws up the user experience for me. I have till recently been working on a 15.4" laptop running ubuntu 9.04 and it did not have any problems with the fonts.

Now I have looked up almost all the post on Ubuntu forums and on other ubuntu blogs, none have worked properly for me. I have searched the forums for the words firefox,font,smoothing,anti aliasing,ubuntu.


I have tried the following:

1. placing a font.conf file in the home directory.

2. turned on text smoothing in firefox about:config.

3. selected subpixel smoothing and full hinting in  System > Appearances > Fonts window.

4. I have tried changing the fonts in other firefox and ubuntu. 


None of what I have tried has worked. I would appreciated help from people who are familiar with these issues on a small screen. 

If anyone has successfully solved this issue. I would like a complete run down on all your settings, themes, fonts, tweaks or hacks. Screenshots will be even better. 

Any help is appreciated.

Thanks.

---

### Post by Vaphell on 2009-10-05
show some screenshot so we know what you mean by 'thick and chunky' :-)

---

### Post by cyanide on 2009-10-05
> **Vaphell said:**
> show some screenshot so we know what you mean by 'thick and chunky' :-)

The first screenshot I have attached is of firefox. Look at the tabs in firefox and also the gnome menu bar. There are no rounded edges in the tabs. They like blocks and fyi I have tried installing a grease monkey script to round the tabs but still no luck. 

The second screenshot is of my desktop.

 I would like the fonts to be smaller and smooth like the fonts from windows and it should also look good on a 13" screen.

---

### Post by anonymous_user on 2009-10-05
The tabs are controlled by the theme, so try a different theme.

As for the fonts, try this:

[http://ubuntuforums.org/showpost.php?p=7544051&postcount=3](http://ubuntuforums.org/showpost.php?p=7544051&postcount=3)

---

### Post by CatKiller on 2009-10-05
> **cyanide said:**
> 
3. selected subpixel smoothing and full hinting in  System > Appearances > Fonts window.

Was full hinting the one that looked best? There are other options available in that tool. Also, setting the pixel order appropriately is a necessary step if you're using subpixel options.

The screenshot you posted looked fine to me on a cursory glance, which suggests that it's a problem with the way the image is presented by your screen rather than a font issue *per se*.

---

### Post by cyanide on 2009-10-05
> **CatKiller said:**
> Was full hinting the one that looked best? There are other options available in that tool. Also, setting the pixel order appropriately is a necessary step if you're using subpixel options.

The screenshot you posted looked fine to me on a cursory glance, which suggests that it's a problem with the way the image is presented by your screen rather than a font issue *per se*.

Can you tell me the fonts you have choosen in Appearances???

Also any help on theme/settings/hacks that you think will look good on a 13" screen.

Thanks!!

---

### Post by cyanide on 2009-10-05
I would like my firefox to have the same fonts as those on this attached screenshot!!

---

### Post by CatKiller on 2009-10-05
> **cyanide said:**
> Can you tell me the fonts you have choosen in Appearances???

At the moment I'm using Linux Libertine for everything but the Terminal, although I have played with others in the past. It's largely a personal preference thing.

For other visual settings, 800 vertical pixels isn't very much. Dropping one of the panels would probably be a good first step, and potentially making the other one smaller would help too. You might have usability problems if you make your panel elements too small to accurately hit, though. Possibly auto-hide would be helpful.

It's probably worth pointing out that none of the text in that last screenshot is a "Firefox" font. Those are all (with the exception of the window title if you're using Emerald) controlled by the GTK theme settings, the text of which can be altered by the Appearance &#8594; Fonts tool.

If wherever you got that screenshot from is just using the default Ubuntu setup with different colours (the name implies the Dust theme) then it's just using the "Sans" font, IIRC. I did used to know which actual font that was an alias for, but I can't remember now.

---

