---
title: "Zotac MAG MAG HD-ND01-U Mini PC"
date: 2010-01-06
forum: General Help
---

### Post by tcchris on 2010-01-06
Hi I just ordered this mini pc for boxee on my tv , hopefully through hdmi .
Has anyone used this or any atom/ion combos ?
I'd like to know if :
1. Is all hardware recognized correctly
2. Some people use nvidia ppa , is this necessary or is vdpau in karmic good to go ?
3. 64 or 32 bit , for streaming and hd playback 
4. does the wireless work ? don't need it but it might be useful 
5. will it play hulu flash ok?
6. I am thinking of xubuntu , restricted extras , medibuntu , and boxee .
Thank you .

---

### Post by tcchris on 2010-01-06
Anyone have a atom/ion ?

---

### Post by tcchris on 2010-01-07
Help anyone , at least , is xubuntu best or unr or minimal ?

---

### Post by chandragaajula on 2010-01-17
Hi,

I bought a MAG HD-ND01 and managed to install Ubuntu 9.10 (via [www.pendrivelinux.com](www.pendrivelinux.com) and avoided having to buy an external CD drive).

Everything works well, but for audio on HDMI and display driver.

The trick to solving the lack audio output when I connected my pc to HDTV was to use the alsamixer to enable the HDMI audio output.

However, I am still having problems with the NVIDIA X Server Settings. I tried downloading the drivers from the NVIDIA website and followed all the instructions. Everything was supposed to be done right, however the NVIDIA ION processor is not being used and that is making my PC useless when connected to the HDTV.

This link will help you with a few problems you will face:
[http://www.greenhughes.com/content/how-install-ubuntu-and-boxee-acer-aspire-revo](http://www.greenhughes.com/content/how-install-ubuntu-and-boxee-acer-aspire-revo)

If anybody has a solution please post it here.

~Chandra

---

### Post by dchall1 on 2010-04-09
I have the same system, and will be using either Boxee or XBMC.  Haven't finished setting up or testing yet.

---

### Post by archeryrob on 2010-05-11
Well, did you get it tested out by now? I am running some old P4's and want to ditch them for something small like this. I am sure this is a big step up for Ubuntu and flash with what I got, but I don't want to buy this if somethign else is better.

HTPC build from parts are looking $200 - $300 more than this right now just with a DVD drive.

---

### Post by r+9 on 2010-08-31
I'm using mine as a media center, the aslamixer thing is required to enable HDMI audio, but it's a quick fix.

I've noticed that it runs HULU just fine in anything but full-screen, for some reason there is a lot of "clipping" I'm not sure what the technical term is.  I'm running Ubuntu 10.04 and it's not a very "clean" install there may be extra stuff running or configure that is causing me issues.

The plan is to install Lubuntu and try again.  I've had a some positive performance results using Lubuntu on systems that were too sluggish with Ubuntu (Gnome vs LXDE)

edit: Another point I forgot to check out, I'm using 64bit Ubuntu 10.04, the normal release of Lubuntu is 32bit.  Not sure if that will play a part. 
Over all I like the zotac MAG, it's a great little device and I've been trying to ditch CD media for a while, so nothing lost there.
Tanget: it's not quite powerful enough to play World of Warcraft unless you just solo and farm. (what I originally wanted to try with it)

---

### Post by rseascape on 2011-05-06
I have a Zotac Mag-mini HD-ND01-U Mini PC and yes it all works...but there are some tweaks you need to do.

Ubuntu Natty Narwhal HDMI {SOLVED}....the fix is really easy!
open a terminal and type in alsamixer
un-mute the SPdif digital output

Now your HDMI will output audio....

---

