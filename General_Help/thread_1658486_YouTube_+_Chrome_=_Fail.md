---
title: "YouTube + Chrome = Fail"
date: 2011-01-02
forum: General Help
---

### Post by MiiPianist on 2011-01-02
Ever since I installed the 10.10 edition, I can't watch videos on YouTube without the fear of my computer restarting.

Almost everytime when I open Chrome and try to watch a video, My monitor freezes and the last second of audio plays over and over. This goes on for about 20 seconds before my computer restarts on its own.

I tried downloading different versions of Chrome, like the Beta and the Unstable one (I currently have the Stable one installed). Also, I uninstalled and reinstalled the flash plugin from Ubuntu Tweak. None of the above seem to work.

I can't find any solutions. Can anyone help me on this?

---

### Post by lovinglinux on 2011-01-03
If you are on 32bit, then just installing flash via Ubuntu Tweak won't work, because Chrome has a bundled flash player that is prioritized. You need to turn it off. To do that, type about[noparse]:[/noparse]plugins in the address bar, then click "Details" in the top-right of the plugins list to expand all detected plugins. Then go to the Shockwave Flash section and disable the one that contains "/opt/google/chrome/libgcflashplayer.so" as path. Restart the browser.

I'm not sure if Chrome 64bit also has such bundled plugin, but I don't think so.

If that doesn't work, then you could try my [Flash-Aid 2.0]("http://www.webgapps.org/addons/flash-aid") extension for Firefox. Although is a Firefox extension and needs Firefox to run, any changes made by it will also affect Chrome, as long as you disable it's bundled plugin.

---

### Post by MiiPianist on 2011-01-03
I'm in 64-bit, so...

I tried doing the thing you said with the bundled pugin but I couldn't find the path.

Kind of a nooby question, but how do I use the .xpi file tou told me download? :P

---

### Post by hawthornso23 on 2011-01-03
You may also find this page of interest
[http://www.youtube.com/html5](http://www.youtube.com/html5)
The best fix for flash problems is not to use flash at all.

---

### Post by lovinglinux on 2011-01-03
> **MiiPianist said:**
> I'm in 64-bit, so...

I tried doing the thing you said with the bundled pugin but I couldn't find the path.

So it is only available in the 32bit., which makes sense, since the 64bit plugin is not even beta yet.

> **MiiPianist said:**
> Kind of a nooby question, but how do I use the .xpi file tou told me download? :P

Drag it to Firefox window to install or open it via Firefox File menu. After installing it, you need to run it. See instructions [here]("http://www.webgapps.org/addons/flash-aid").

> **hawthornso23 said:**
> You may also find this page of interest
[http://www.youtube.com/html5](http://www.youtube.com/html5)
The best fix for flash problems is not to use flash at all.

Try me extension [FlashVideoReplacer]("http://www.webgapps.org/addons/flashvideoreplacer"). It can detect if an YouTube video has html5 version and redirect to the html5 page. If the html5 video is not available, the extension can replace the flash player in order to use a different plugin, like gecko-mediaplayer, that uses much less CPU and works much better. It replaces the video on the site, but can also be configured to open it in a new tab, a new window or a standalone external player.

---

