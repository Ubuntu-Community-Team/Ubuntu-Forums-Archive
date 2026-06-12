---
title: "Chromium Browser: the following plug-in has crashed - Shockwave Flash"
date: 2011-09-06
forum: General Help
---

### Post by meowsus on 2011-09-06
Hey guys.

I switched back to Chromium from Google Chrome as my main browser. Google Chrome comes with Adobe Flash pre-packaged with it, Chromium Browser does not. 

I get the error:
The following plug-in has crashed - Shockwave Flash

All the searching I've done says to install **flashplugin-nonfree** and to copy **/usr/lib/flashplugin-nonfree/libflashplayer.so** to **/usr/lib/chromium-browser/plugins/** and to start Chromium like so: **chromium-browser --enable-plugins**

(even though I don't see the **--enable-plugins** option in man chromium-browser)

Needless to say, it's not working and I have no idea how to make it start working. I've tried downloading libflashplayer.so from Adobe's site directly and from the repos. It's sitting in the plugins directory all by itself, going unused.

Little help here? :)

---

### Post by meowsus on 2011-09-07
Here's a workaround I found, finally. You see, I use Chromium to test new versions of Webkit and what-have-you, since I'm a web developer. Having an OUTDATED VERSION of flash for Chromium is fine by me, so if this is like you too, and you have Google Chrome installed as well, like I do, you can follow these steps to getting it to work.

```
cd /usr/lib/chromium-browser/plugins/
sudo ln -s /usr/lib/google-chrome/libgsflashplugin.so libgsflashplugin.so
sudo chmod a+x libgsflashplugin.so
```

If Chromium complains that the plugin has been disabled because it's outdated, tell it to shut up by doing this:

```
chromium-browser --allow-outdated-plugins
```

What this will do is run flash from Google Chrome's installation. When Chrome updates it's flash, your flash will update in tandem.

---

