---
title: "Web pages not displaying correctly in Firefox"
date: 2009-11-27
forum: General Help
---

### Post by AndrewGen on 2009-11-27
I just installed Ubuntu 9.10 to my hard drive, after using Fedora, and notice that certain web sites/pages in Firefox do not display correctly as they did in Fedura.  Many of the page elements are now jumbled, and are merging with text throughout the web pages.  The fonts are also different from what was displayed when using Firefox in Fedura. 

What can I do to fix this situation, as I would like to continue using Ubuntu 9.10 with Firefox.

Thanks you,
Andrew

---

### Post by coffeecat on 2009-11-27
Which version of Fedora were you using? I've installed both 9.10 and Fedora 12 to this laptop and the websites I've visited display the same in both distros - probably because they're using the same version of Firefox (iirc). I have noticed a couple of very minor display glitches with the 3.5.5 version of Firefox that comes with Ubuntu 9.10, so this might be a version difference.

Why not post a screenshot of what you get plus a link to the same site so that others can test it with different browsers?

As far as fonts are concerned, did you install the Microsoft core fonts in Fedora? That might be why you're getting a difference. Try installing the ttf-mscorefonts-installer package and see if that helps. Beware though, some people (I didn't) are being affected by a bug that prevents download of the font files from the sourceforge repo. If that happens to you there are other ways of installing MS fonts, but as an erstwhile Fedora user, you may know how to do that. If not, just post back.

By the way, in my eyes font rendering generally in Karmic is the best out of the box I've seen from any distro/release. I had to enable autohinting in Fedora to get anywhere near as good as Karmic. Karmic is stil better though. Imho.

---

### Post by audiomick on 2009-11-27
You might find something interesting here:
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by PvSinNL on 2009-11-27
You might want to check your font preferences, under System > Preferences > Appearance > Fonts (tab). Do you have "Subpixel smoothing (LCD's)" enabled? If so, you could click the Details button and try different settings for hinting, and also check the Resolution (dpi) setting.
I also had some rendering issues with Firefox, and found that I got the best results by using "slight" hinting, and setting the resolution to the actual dpi value of my monitor. (Somehow, the latter isn't adjusted automatically in Gnome, at least not on my system, although X itself seems to be aware of the proper value, see e.g. the output of xdpyinfo.)

---

### Post by AndrewGen on 2009-11-27
> **coffeecat said:**
> Which version of Fedora were you using? I've installed both 9.10 and Fedora 12 to this laptop and the websites I've visited display the same in both distros - probably because they're using the same version of Firefox (iirc). I have noticed a couple of very minor display glitches with the 3.5.5 version of Firefox that comes with Ubuntu 9.10, so this might be a version difference.

Why not post a screenshot of what you get plus a link to the same site so that others can test it with different browsers?

As far as fonts are concerned, did you install the Microsoft core fonts in Fedora? That might be why you're getting a difference. Try installing the ttf-mscorefonts-installer package and see if that helps. Beware though, some people (I didn't) are being affected by a bug that prevents download of the font files from the sourceforge repo. If that happens to you there are other ways of installing MS fonts, but as an erstwhile Fedora user, you may know how to do that. If not, just post back.

By the way, in my eyes font rendering generally in Karmic is the best out of the box I've seen from any distro/release. I had to enable autohinting in Fedora to get anywhere near as good as Karmic. Karmic is stil better though. Imho.

I was using Fedora 12 (with Firefox 3.5.4), and now switched to Ubuntu 9.10 (with Firefox 3.5.5).  I did not install any Microsoft core fonts in Fedora.  
Could the version difference in Firefox be the issue?  
I can't seem to find a download of Firefox 3.5.4.  They keep redirecting the download to ver 3.5.5.

Any suggestions.  This is quite frustrating.

Thanks, Andrew

---

### Post by AndrewGen on 2009-11-27
> **PvSinNL said:**
> You might want to check your font preferences, under System > Preferences > Appearance > Fonts (tab). Do you have "Subpixel smoothing (LCD's)" enabled? If so, you could click the Details button and try different settings for hinting, and also check the Resolution (dpi) setting.
I also had some rendering issues with Firefox, and found that I got the best results by using "slight" hinting, and setting the resolution to the actual dpi value of my monitor. (Somehow, the latter isn't adjusted automatically in Gnome, at least not on my system, although X itself seems to be aware of the proper value, see e.g. the output of xdpyinfo.)

Thanks for the suggestions.  I tried all of those, but it didn't seem to resolve the problem.  BTW - how do I check the actual dpi value of my monitor?

Thanks,
Andrew

---

### Post by coffeecat on 2009-11-27
I stand corrected on the version differences, but the difference between 3.5.4 and 3.5.5 is going to be minimal, I would have thought. But please post a screenshot and link. We need to see if this is a general problem in Firefox in Karmic, or just a local problem in your system.

---

### Post by AndrewGen on 2009-11-27
> **coffeecat said:**
> I stand corrected on the version differences, but the difference between 3.5.4 and 3.5.5 is going to be minimal, I would have thought. But please post a screenshot and link. We need to see if this is a general problem in Firefox in Karmic, or just a local problem in your system.

Attached is a screen shot of a client site. [www.ActiveCounseling.net]("http://www.ActiveCounseling.net")

As you can see, the text which should be in the outlined blue box, is wrapping and overlapping incorrectly.  (Other elements on different sites are also displaying incorrectly).

Thanks for your help,
Andrew

---

### Post by coffeecat on 2009-11-27
Yes, I see what you mean. But it's displaying just fine for me in FF 3.5.5 in Karmic. See my screenshot. I do have the MS fonts installed.

The only thing I can suggest is to close firefox, rename your ~/.mozilla folder and then restart FF so that it creates a new ~/.mozilla with default settings and see if the problem remains.

---

### Post by AndrewGen on 2009-11-27
> **coffeecat said:**
> Yes, I see what you mean. But it's displaying just fine for me in FF 3.5.5 in Karmic. See my screenshot. I do have the MS fonts installed.
 
The only thing I can suggest is to close firefox, rename your ~/.mozilla folder and then restart FF so that it creates a new ~/.mozilla with default settings and see if the problem remains.
 
 
Thanks. How do I install the MS fonts?

---

### Post by Paul41 on 2009-11-27
The page also displays correctly for me.

to install MS fonts:

```
sudo apt-get install ttf-msttcorefonts-installer
```

---

### Post by coffeecat on 2009-11-27
> **AndrewGen said:**
> Thanks. How do I install the MS fonts?

Have a look at my first post (post #2) in this thread.

Did resetting the ~/.mozilla folder help?

---

### Post by AndrewGen on 2009-11-27
> **coffeecat said:**
> Have a look at my first post (post #2) in this thread.

Did resetting the ~/.mozilla folder help?

The installation of the MS fonts did the trick. :D

Thanks everyone.

---

