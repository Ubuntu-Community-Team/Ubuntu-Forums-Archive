---
title: "MP3 with LIVE CD"
date: 2005-02-05
forum: General Help
---

### Post by Borg on 2005-02-05
why can't I play any of my MP3s while booted into the Live CD ? Also where is WINE ?

Also the onely way to get it to boot is to load it into RAM first.

Using a SN41G2 v2 Shuttle with Ati 9800 Pro GFX Card

Thanks  :?:

---

### Post by menu on 2005-02-05
Hi Borg, from the FAQ:
[http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)
 Support for some popular formats is not included in the Ubuntu distribution because there are legal restrictions on their distribution or usage. While we make no effort to restrict the choice of users to use such formats, we prefer to support Free software and Free formats. 

MP3, and WMA are patent-encumbered, for both encoding and decoding, these patents are being actively enforced. Ogg Vorbis is a flexible and Free lossy audio codec with a proven track record.


However, you can still play your MP3s with rhythmbox if you install gstreamer0.8-mad (you need to add the universe repository). LAME can be used to encode MP3s if you install gstreamer0.8-lame.

---

### Post by blitze on 2005-02-05
You could always try Ogg Vorbis as a music compression codec.  Live CD loves that one  :D

---

