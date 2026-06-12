---
title: "Problems rendering fonts"
date: 2010-11-07
forum: General Help
---

### Post by carlosgs91 on 2010-11-07
.

---

### Post by rattskjelke on 2010-11-10
I have the same problem. I have only seen it in the Firefox main window, not in the menus or side bar and I haven't seen it happen with any other applications. It doesn't take 4 hours on mine it can happen within a few minutes. It can be any character or group of up to 3 characters.

Sometimes if I minimize and restore Firefox it will cure the problem for a while then it will come back later with a different letter or letters appearing as solid blocks.

I have used 9.04, 9.10, 10.04 and 10.10 and it did it on all versions and all versions of Firefox since then.

I don't know how to tell if this is a problem with Ubuntu, Firefox or my video card or video driver.

Setting visual effects to none, normal or extra has no effect.

I don't think it is a hardware problem because I have no video or font problems running Windows XP on the same computer. It doesn't seem to happen when running Ubuntu from the live CD. I tried Fedora 11 last year and did not have the problem.

---

### Post by cyberCMDR on 2010-11-13
Have a similar problem, using Ubuntu 10.10 on a Dell Inspiron 1501.  I found that if you go to System->Preferences->Appearance->Fonts and switch between subpixel smoothing and best shapes, the letters will appear normally.  The problem is it keeps recurring, and I have to toggle between the two modes.

Just tried entering:
sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/
to enable auto hinting as per [http://www.webupd8.org/2010/08/new-ubuntu-1010-font-available-for.html](http://www.webupd8.org/2010/08/new-ubuntu-1010-font-available-for.html), to see if that helps.  Too soon to tell; I'll see if the problem still pops up.

---

### Post by cyberCMDR on 2010-11-13
Found an article on this at [http://www.webupd8.org/2009/07/fix-fonts-in-firefox-35-and-ubuntu.html](http://www.webupd8.org/2009/07/fix-fonts-in-firefox-35-and-ubuntu.html)

---

