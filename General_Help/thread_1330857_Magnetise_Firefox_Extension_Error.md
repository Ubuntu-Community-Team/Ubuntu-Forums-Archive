---
title: "Magnetise Firefox Extension Error"
date: 2009-11-18
forum: General Help
---

### Post by franklovecchio on 2009-11-18
I can't get magnet links to work.  Here's the problem:

I go to a torrent page at torrentz.com (we'll say that it's a LEGAL torrent).  I click on the "Magnetise" link in the bottom of the Firefox window.  I get:

> Magnet link is magnet:?xt=urn:btih:1f7a8b5cdc0fad61321177b51ca234e02bbdba72&tr=http://tracker.openbittorrent.com/announce&tr=http://tracker.publicbt.com:80/announce&tr=http://denis.stalker.h3q.com:6969/announce

> Firefox doesn't know how to open this address, because the protocol (magnet) isn't associated with any program.

First, I tried editing the prefs.js file for the Magnetise extension before installing (I added the last two lines):

```
pref("extensions.magnetiser.boolpref", false);

pref("extensions.magnetiser.intpref", 0);

pref("extensions.magnetiser.stringpref", "A string");

pref("extensions.magnetiser.trackers", "tr=http://tracker.openbittorrent.com/announce&tr=http://tracker.publicbt.com:80/announce&tr=http://denis.stalker.h3q.com:6969/announce");



// https://developer.mozilla.org/en/Localizing_extension_descriptions

pref("extensions.magnetiser@hotsexgary.com.description", "chrome://magnetiser/locale/overlay.properties");

pref("network.protocol-handler.external.magnet", true);
pref("network.protocol-handler.app.magnet", "/usr/bin/transmission");
```


This didn't work.  Then, I tried editing the about:config of Firefox, inserting new Boolean and String fields.

network.protocol-handler.external.magnet, true
network.protocol-handler.app.magnet, /usr/bin/transmission

Why can't I get this to work?

---

### Post by danking12 on 2009-11-18
Hey, I found this thread...

[http://ubuntuforums.org/showthread.php?t=308130]("http://ubuntuforums.org/showthread.php?t=308130")

It is similar to what you had to do but you also have to make sure the preference name network.protocol-handler.expose-all is set to true

That being said this hasn't worked for me. I have the same issue as you. Any word on a fix yet?

---

### Post by danking12 on 2009-11-18
Hey, I fixed part of the problem. I have deluge queing the torrents. I did this by running the following commands?

```
gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/usr/bin/deluge %s"
gconftool-2 -s /desktop/gnome/url-handlers/magnet/needs_terminal false -t bool
gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true
```

Now my problem is that the queued torrent never gets added to the list of downloading torrents. If you look at the status bar in the bottom you can see and double click on something that will show the magnet link you are trying to add.

One for the next step...

---

### Post by franklovecchio on 2009-11-18
I had seen that thread.  My network.protocol-handler.expose-all was already set to true as well!

However, I did try putting those 3 lines into the command line:

```
gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/usr/bin/transmission %s"
gconftool-2 -s /desktop/gnome/url-handlers/magnet/needs_terminal false -t bool
gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true 
```

...and it worked!  I went to a Torrentz.com page, hit "Magnetise", and Firefox asked me to choose Transmission or another program.  Voila!

---

### Post by danking12 on 2009-11-18
Does your program actually start downloading the torrent? I am using deluge and I have the issue I describe above where it doens't appear in the list but in some window about queued torrents. Maybe I will give transmission a shot.

---

### Post by franklovecchio on 2009-11-18
Oh, no it DOESN'T appear in the list of downloading torrents...I was just excited that the error was gone.  When I hit "Magnetise", it simply makes Transmission shift places on the screen.  It's quite odd, actually.

---

### Post by danking12 on 2009-11-18
I tried using Transmission as well with no results to the torrent actually downloading. Hopefully I'll be able to figure this out soon. Let me know if you actually get something to download using a magnet uri.

---

