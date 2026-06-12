---
title: "Google Chrome Default Font Size Too Small"
date: 2010-08-30
forum: General Help
---

### Post by jdorenbush on 2010-08-30
The default (and standard for most browsers) 16 pixel font setting in Chrome is displaying fonts too small. They look similar to a 10 or 11 point font size. A 16 pixel font setting in a browser should show web fonts styled at 100 percent as a 12 point font.

So I tried switching to 17 pixel and that displays fonts at a 13 or 14 point size. So there is no middle ground to display fonts at 12 point, unless the website specifically programmed it's fonts not using percents. 

A complete system reinstall fixed the problem, until today I noticed the problem was back. I'm not sure what happened that caused it to screw up again. I tried reinstalling the software, but that doesn't fix. The problem occurs in both Chromium and Google Chrome.

Here is an example from Digg.com, one shot is from correctly displayed fonts in Firefox and the other from Chrome:
[[IMG]http://img834.imageshack.us/img834/491/fontsize.png[/IMG]](http://img834.imageshack.us/i/fontsize.png/)

---

### Post by fragos on 2010-08-30
If I'm not mistaken, Firefox has a setting for minimum font size which will override the font size specified by the site. Chrome doesn't have this setting. Setting minimum font size in Firefox could be the cause of what you see.

---

### Post by jdorenbush on 2010-08-30
My min. font size on Firefox is set to 'None'. The font size is set to 16. I've never adjusted font settings in Chrome or Firefox before. I always leave them at default. So Chrome and Firefox should be displaying fonts the same. And I've tried Chrome on other computers and the fonts look correct.

The fonts looked correct on my computer after a fresh system install, but something happened over the past three or four days that corrupted the font setting and I'm not sure what it was or how to fix it.

I'm not sure if this will help, but here are some things I've uninstalled since the date of my fresh install. This isn't everything as there are associated library files and stuff. I'm not sure if any of these would have conflicted, but maybe someone can spot something.
- byobu
- f-spot
- openoffice (and associated pkgs)
- empathy (and associated pkgs)
- geoclue (and associated pkgs)
- rhythmbox (and associated pkgs)
- gnome-games-common (and associated games)
- accessibility software (gnome-accessibility-themes, gnome-orca, brltty, brltty-x11, libbrlapi0.5, liblouis-data, liblouis0, python-louis, python-brlapi)
- unused fonts (ttf-indic-fonts-core, ttf-kacst-one, ttf-khmeros-core, ttf-lao, ttf-punjabi-fonts, ttf-takao-pgothic, ttf-thai-tlwg, ttf-unfonts-core, ttf-wqy-microhei, ttf-lyx)

---

### Post by fragos on 2010-08-30
I've been using Chrome for a long time and have never experienced your problem. Font size is usually specified in the CSS of sites you browse.

---

### Post by abelta on 2010-08-30
Same thing happens to me. The only way I've found to override default font size is doing a CTRL + on each website where I find text too small but I know it's not the smartest solution.

---

### Post by jdorenbush on 2010-08-30
> **abelta said:**
> Same thing happens to me. The only way I've found to override default font size is doing a CTRL + on each website where I find text too small but I know it's not the smartest solution.

Yeah, I saw that as being a temporary solution, but the whole thing was starting to really frustrate me.

I've also been receiving the "Aw snap." error page frequently -- on sites that work fine in other browsers. My libflashplayer.so always crashes on Flickr.com too. So until some fixes are made I'm back on Firefox.

---

### Post by nathan726 on 2010-09-03
Edit: nevermind - just tested my solution and it erased my chromium preferences #-o

---

### Post by fragos on 2010-09-03
> **nathan726 said:**
> based on discussions at the [Chrome help forum](http://www.google.com/support/forum/p/Chrome/thread?tid=389f306a52817110), I think something like this should probably work...

Ensure that Chrome is not running, otherwise this won't work
Open ~/.config/chromium/Default/Preferences in a text editor
Find the section that has "webkit": {  "webprefs": {

Then add desired font settings, for example:
```

   "webkit": {
      "webprefs": {
         "default_fixed_font_size": 11,
         "default_font_size": 12,
         "fixed_font_family": "Courier",
         "minimum_font_size": 12,
         "minimum_logical_font_siz": 12,
         "sansserif_font_family": "Times New Roman",
         "serif_font_family": "Arial",
         "standard_font_is_serif": false,
         "text_areas_are_resizable": true
      }
   }

```
The minimum_font_size and minimum_logical_font_size control the smallest font-size chrome is allowed to use.

These are the values set in the GUI Options for Fonts

---

### Post by jdorenbush on 2010-09-05
Now it's happening in Firefox too. I don't see all those settings mentioned above either, especially not in Firefox config files.

---

### Post by Deuced on 2011-04-16
sorry for bumping a so old topic,but i got the same issue and this was the only result that i got by googling.

I don't know if it's useful,but i solved by setting to "serif" the default font in chrome.After hours of tweaking i noticed that it's the default font in firefox,so now they render the pages in the same way and the small font issue went away :)

---

