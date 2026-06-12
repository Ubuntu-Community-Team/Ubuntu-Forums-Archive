---
title: "Youtube videos randomly stop loading"
date: 2011-06-05
forum: General Help
---

### Post by stinkinrich88 on 2011-06-05
Hello,

Youtube works fine until the buffer decides to stop loading. When the video gets to that point, it just hangs. I have to click slightly to the right of the marker on the play bar to start it loading again, and keep doing this every time it stops loading. Very annoying!

Any ideas how I can solve this? I can't find flash anywhere in synaptic to re-install it. The problem happens on firefox and Chrome. And I'm using 32 bit Natty 11.04.

Thanks!

---

### Post by mgmiller on 2011-06-05
Search synaptic for flashplugin-installer.  I have not experienced the problem you mention in either 32 or 64 bit installs of Natty.

You can also try the flash-aid extension for firefox.  It will make sure you have the latest version of flash and correct incompatibilities if you have multiple versions, such as flash and gnash, etc installed and tweak a bunch of its settings as well.

---

### Post by stinkinrich88 on 2011-06-05
ah, I uninstalled flashplugin-installer, but it made no difference (Flash still works at previously). Unfortunately Chrome is my main browser, so I can't use flashaid. I do not have any other versions of flash installed. Any ideas how I can re-install flash? The Adobe website didn't offer, just said I already have flash and Chrome will update me automatically.

Thanks!

---

### Post by pqwoerituytrueiwoq on 2011-06-05
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)
will take care of everything from firefox (effects will be visible on other browsers also)

---

### Post by stinkinrich88 on 2011-06-05
> **pqwoerituytrueiwoq said:**
> [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)
will take care of everything from firefox (effects will be visible on other browsers also)

Ah ok!

Well, I just installed flash aid, then followed the setup wizard (using all recommended settings - flash beta), restarted firefox |(and chrome) and unfortunately the problem still exists on both browsers... hmmmm

---

### Post by pqwoerituytrueiwoq on 2011-06-05
64bit flash beta is version 10,3,162,29

[http://www.adobe.com/swf/software/flash/about/flashAbout_info_small.swf](http://www.adobe.com/swf/software/flash/about/flashAbout_info_small.swf)

---

### Post by stinkinrich88 on 2011-06-05
> **pqwoerituytrueiwoq said:**
> 64bit flash beta is version 10,3,162,29

[http://www.adobe.com/swf/software/flash/about/flashAbout_info_small.swf](http://www.adobe.com/swf/software/flash/about/flashAbout_info_small.swf)

Hmm, I have 10,3,181,14 installed... Reckon I need to re-do the wizard and choose "stable" this time?

---

### Post by mgmiller on 2011-06-05
i suspect you may have the 32 bit flash installed with the wrapper to make it work in 64 bit.  Try to make sure flash aid is switching you to the 64 bit version.  (Assuming you are running 64 bit).

Edit: Never mind, I just noticed you're running 32 bit.  10.3.181.14 is the current 32 bit flash.

---

### Post by pqwoerituytrueiwoq on 2011-06-05
sudo apt-get purge flashplugin-nonfree flashplugin-installer && rm ~/.mozilla/plugins/*flash*.so

---

