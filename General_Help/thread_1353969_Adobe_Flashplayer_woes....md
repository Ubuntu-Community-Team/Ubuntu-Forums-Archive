---
title: "Adobe Flashplayer woes..."
date: 2009-12-13
forum: General Help
---

### Post by eveningsky339 on 2009-12-13
I have had some issues with Flashplayer for a while now, but after some trial and tribulation, I believe to have Flashplayer 10 installed properly.  

However, there is one particular website (which I love) that does not work.  Or should I say, nothing works when I click on it.  The site itself comes up just fine, the buttons animate when I pass the mouse over them, but clicking them does absolutely nothing at all.

[http://www.ferryhalim.com/orisinal/](http://www.ferryhalim.com/orisinal/)

Youtube, addictinggames.com, etc all work just fine, so I an uncertain as to why this single website is affected.  I have tried several web browsers and encountered the same problem.

Any help would be appreciated.  :)

---

### Post by Daveth on 2009-12-13
I really like ferryhalim's site- it works fine on opera 10.10, and the newest adobe flash download. Are you entirely up to date?

---

### Post by ankspo71 on 2009-12-13
Hi,
I can play the games on that site with my firefox. I'm using Firefox 3.5.5 with Shockwave Flash 10.0 r32  You can find out your version of flash by opening firefox, click on tools, then click on addons, then when the addons opens - click on plugins, then scroll down to see which one is installed.

I installed my flash plugin by installing ubuntu-restricted-extras.

Also, My firefox has no addons installed too, so maybe you have an addon that might be blocking the pop-up windowed games? Try disabling the 'adblock plus' addon (for example), to see if you can load the games.

Also, if you have installed other types of flash plugins (gnash, klash, etc), make sure they are disabled or uninstalled, because they can cause conflicts with the adobe/shockwave one.

Also, if this ends up being a older version firefox issue (but it shouldn't be), you can find and install  firefox-3.5 in Synatptic Package Manager. 

Edited:because I just noticed you said this concerns all browsers. (oops)

I hope something I said might help.
James

---

### Post by eveningsky339 on 2009-12-13
Thanks for the quick replies!

**Daveth,**
I installed and tried Orisinal on Opera.  I managed to bring up a game by clicking on the button approximately 736.7 times, but couldn't get past anything from there.  So, limited success... hopefully one step closer to playing the games.

**ankspo71,**
I have Shockwave Flash 10.0 r42 and my Firefox is up to date.  Disabled all other addons and no dice.

I plan on removing Flashplayer 10 in the terminal and then trying to grab a deb from Adobe's website.  I ran into problems when I tried this last time because my machine runs on 64-bit architecture, and 32-bit was the only .deb that was offered on Adobe.  I'll see what I can find, though.

---

### Post by ruario on 2009-12-19
Google for: gdk_native_windows

On Opera workaround can be [found here]("http://my.opera.com/ruario/blog/flash-problems-on-linux#first-click")

---

### Post by Grenage on 2009-12-19
The issue with buttons not being clickable is a common on; you can actually get them working by holding down right-click, then clicking the button with a normal left-click.

The only way I ever got it fixed was to manually download flash from the Adobe site (tar file), then replace the one in /usr/lib/firefox/plugins.

---

