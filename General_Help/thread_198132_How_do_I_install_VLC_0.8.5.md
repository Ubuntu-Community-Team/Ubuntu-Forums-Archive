---
title: "How do I install VLC 0.8.5?"
date: 2006-06-16
forum: General Help
---

### Post by TomSelleck on 2006-06-16
When I do an "apt-get vlc", I get the older version 0.8.4.  The latest stable is 0.8.5.  According to [their site](http://nightlies.videolan.org/), I just add "deb [http://nightlies.videolan.org/build/dapper-i386](http://nightlies.videolan.org/build/dapper-i386) /" to my sources.list.  When I tried installing then, I still got 0.8.4.  

They provide a [download link](http://nightlies.videolan.org/build/dapper-i386) to get the files, but I'm a newb and don't know which ones I need or what to do with them.  I would be happy to compile it myself if someone could point me to a HOWTO. 

I think I need to compile it anyway to get support for PVR streaming from the command line.  At least that's what it says in [VLC's documentation](http://www.videolan.org/doc/streaming-howto/en/ch10.html#id299174).

---

### Post by mlind on 2006-06-17
I installed 0.8.5 from VLC nightlies repo too. You may have to import their
their [gpg key]("http://nightlies.videolan.org/key") aswell.

```

sudo sh -c "wget -O - http://nightlies.videolan.org/key | apt-key add -"
sudo aptitude install vlc vlc-plugin-alsa wxvlc

```

If you plan to build it yourself, read about apt package building using
apt-get build-dep and dpkg-dev.

---

### Post by TomSelleck on 2006-06-18
I had to uninstall 0.8.4, import their GPG key, make sure their repo was in my sources.list, then "apt-get install vlc vlc-plugin-*".  This installed 0.8.5 and fixed a few issues I had with 0.8.4.  Thanks for the help!

---

### Post by mlind on 2006-06-18
[QUOTE=TomSelleck]I had to uninstall 0.8.4, import their GPG key, make sure their repo was in my sources.list, then "apt-get install vlc vlc-plugin-*".  This installed 0.8.5 and fixed a few issues I had with 0.8.4.  Thanks for the help![/QUOTE]

I think you only need to install vlc-plugin-alsa with Dapper.
Good you got it working.

---

### Post by nix4me on 2006-06-18
Will 0.8.5 play the current apple.com quicktime trailers?

0.8.4 will not play them.

nix4me

---

### Post by mlind on 2006-06-18
[QUOTE=nix4me]Will 0.8.5 play the current apple.com quicktime trailers?

0.8.4 will not play them.

nix4me[/QUOTE]

nope :(
well, you can see the image but it's very distorted/blurred..

---

### Post by Mark.Pilgrim on 2006-07-23
> **mlind said:**
> nope :(
well, you can see the image but it's very distorted/blurred..

Run VLC (0.8.5 or later) and go to Settings -> Preferences.  Select the "Advanced options" checkbox in the lower right corner, then open Input/Codecs -> Other codecs -> FFmpeg and set "Skip the loop filter for h.264 decoding" to "All".  Quit and relaunch VLC.

(found in the VLC forums)

---

### Post by mlind on 2006-07-23
> **Mark.Pilgrim said:**
> Run VLC (0.8.5 or later) and go to Settings -> Preferences.  Select the "Advanced options" checkbox in the lower right corner, then open Input/Codecs -> Other codecs -> FFmpeg and set "Skip the loop filter for h.264 decoding" to "All".  Quit and relaunch VLC.

(found in the VLC forums)

Thanks for the info.

Last time I tried playing NWN 2 [trailer]("http://nwvault.ign.com/View.php?view=Movies.Detail&id=462") (.mov version), the image was all blurred. I've since recompiled FFmpeg from [Debian multimedia]("http://www.debian-multimedia.org") and now the video displays okay without any changes to VLC settings.

---

