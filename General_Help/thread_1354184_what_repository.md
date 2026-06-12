---
title: "what repository?"
date: 2009-12-13
forum: General Help
---

### Post by tropdoug on 2009-12-13
I am trying to install ffmpeg which is required by jysmphonic. when I use synaptic I get an unmet dependancy box (see attached image) My question is, which repository do I need? 

I have attached my respository list as well

I have searched for the offending files and cannot find them, therefore I am unable to proceed. This seems to be a somewhat obtuse way of doing business. You can't do this because of this, but we won't tell you where you can get the missing bit. 

Can anyone throw some light on this problem please.

---

### Post by lyall on 2009-12-13
have you checked Synaptic Package Manager the the four files
libavcodec52
libavdevice52
libavfilter1
libavformat52

I checked mine and all four files are there
and I have checked the other software and this is what I have

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
[http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free
Medibuntu [ Ubuntu 9.10 "karmic koala" free non-free

You can install them from Synaptic by selecting them to install
then try installing the ffmpeg

it is worth a try

good luck and have fun learning

---

### Post by dcstar on 2009-12-14
> **tropdoug said:**
> I am trying to install ffmpeg which is required by jysmphonic. when I use synaptic I get an unmet dependancy box (see attached image) My question is, which repository do I need? 

I have attached my respository list as well

I have searched for the offending files and cannot find them, therefore I am unable to proceed. This seems to be a somewhat obtuse way of doing business. You can't do this because of this, but we won't tell you where you can get the missing bit. 

Can anyone throw some light on this problem please.

You have 3rd-party repositories enabled, this sort of thing can happen because you are not installing official software.

---

### Post by mc4man on 2009-12-14
While using debian-multimedia for a packaged ffmpeg and /or it's libs may work for a while, sooner than later dependencies will break. A generally poor idea.

You should think about restoring the ubuntu repo's versions of the ffmpeg libs (- extra versions in synaptic

You could then try the repo's ffmpeg, if it works, great, otherwise remove ffmpeg only and [build]("http://ubuntuforums.org/showthread.php?t=786095") a newer or current ffmpeg as static to /urs/local

If that doesn't work out ( as far as ffmpeg itself), then build as a .deb package set . ( in which case the debian-multimedia's source. diff.gz and .dsc can build you a nice set - watching out not to break any current support with U. repo apps, which becomes more likely with newer ffmpeg -r's, though it's certainly manageable

---

