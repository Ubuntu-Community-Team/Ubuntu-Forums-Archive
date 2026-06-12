---
title: "Plugin Settings Help"
date: 2009-11-09
forum: General Help
---

### Post by infinitelink on 2009-11-09
Let the fun begin! 

I am, like as are many, using FF on 9.10. The odd thing is, I cannot set the browser to use gecko-mediaplayer. After some doing I was able to purge flashplugin-nonfree (in the form of the nspluginwrapper) from the system, but then flash just wouldn't play. 

So how does one set FF to use that plug-in? Where does one point FF? So far I've tried thusly for Flash under FF's Application settings, /usr/lib/mozilla/plugins/gecko-mediaplayer.so, but that didn't work.

I was able to hack it a bit by using a script from here, [http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771), but instead the browser uses the (when I right-click the embedded player and choose 'About', 'Totem Browser Plugin 2.28.1', 'Browser Plugin using GStreamer 0.10.25'. Not that I have anything against Gstreamer, but I was just trying to get the mplayer plug-in running. : ( I do have to say I like the TBP's option to 'Open in VLC', however; anyone know whether this is the 'totem-mozilla' plugin package or else?

More that's is interesting: I copied that userscript into Midori's script folder (had to create it, but once done it works), and loaded a Youtube page, and...unlike FF the script in Midori uses the 'gecko-mediaplayer' (which I'm seeking for FF to use) plug-in instead. Again, any ideas?

---

