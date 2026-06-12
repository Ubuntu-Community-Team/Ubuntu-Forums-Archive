---
title: "DLNA Client for 10.04"
date: 2010-07-18
forum: General Help
---

### Post by J_E_F_F on 2010-07-18
I have 10.04 installed on a SD card, and it works well.
I would like to use Ubuntu as a DLNA client receiver (not server)
 
I have my MP3 collection stored on a Windows 7 PC. Using Media Players "Play to" function I can play those MP3s to another Windows 7 PC on my network with a simple click.
 
I'd like to set up a small headless low power Ubuntu PC with the audio out hooked to my stereo and use the same Windows 7 Play To option to pass the mp3 file to the Ubunutu DLNA client. Is there a way to make Rythmbox be seen as a DLNA client, or another opensource app I can install to do that?

---

### Post by dino99 on 2010-07-18
some help there:

[http://manpages.ubuntu.com/manpages/lucid/man1/ushare.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/ushare.1.html)

---

### Post by benklaasen on 2010-12-28
> **dino99 said:**
> some help there:

[http://manpages.ubuntu.com/manpages/lucid/man1/ushare.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/ushare.1.html)

Nope, those are usage instructions for a Ubuntu DLNA server, not client.

J_E_F_F, there is a DLNA plugin for Rythmbox - I've just given it a spin, and while it connects to my UPnP server running minidlna and can play whatever tracks it finds, it only finds a fraction of the files. You might have better luck.

You can install the Rythmbox DLNA client plugin with this command:

sudo apt-get install rhythmbox-plugin-coherence

Next, start up Rythmbox, open Edit > Plugins and enable the plugin named "DLNA/UPnP sharing and control support". Give the plugin a few seconds to find and scan your DLNA media server.

regards
Ben

---

### Post by frogotronic on 2011-01-22
Hi,

  Just a quick question:  What do I enter for 'Port' and for 'Interface'?  on the DLNA Plugin?

see attached screenshot

Thanks,
CH

---

