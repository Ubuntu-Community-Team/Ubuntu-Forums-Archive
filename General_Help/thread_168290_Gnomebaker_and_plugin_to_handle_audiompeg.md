---
title: "Gnomebaker and plugin to handle audio/mpeg"
date: 2006-04-30
forum: General Help
---

### Post by GreveFelix on 2006-04-30
Hello friends,
First I used K3B as a burning tool, but I had some problems with it ... I read somewhere, that K3B is rather for Kubuntu than for Ubuntu. So I installed via Automatix Gnomebaker. But I am still not able to create a audio cd out of compressed files like mp3. It says, that I need to install some plugins. But I can not find any in "synaptic" or elsewhere. It seems like I need a plugin to handle audio /mpeg and for some Text-things. Does somebody know where I could get those plugins? And how, because I am quite new to ubuntu and dont know much about it. Or should I use an other programm?

---

### Post by artships on 2006-04-30
Using synaptic, add gstreamer0.8-plugins

---

### Post by GreveFelix on 2006-05-01
Hey thanks!! It worked... :-D

---

### Post by dickohead on 2006-06-07
Brilliant! Thank you.

---

### Post by beameup on 2006-07-07
Will doing that screw up the Gstreamer 10 stuff with Dapper?

---

### Post by beameup on 2006-07-07
Googling, I added the 3 plug-ins from this post [http://bugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=339895](http://bugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=339895)

gstreamer0.8-(mad|vorbis|flac) 

and GnomeBaker now bakes mp3s to Audio CD's
I also had gstreamer0.8 - theora|misc|lame|gnomevfs already installed.

All the gstreamer 0.10 stuff was installed, but GnomeBaker still needs 0.8.



OK, Now realizing I'm in an old thread ](*,)

---

### Post by CGW on 2006-07-08
Is there any reason why you just wouldn't install all of the 'gstreamer' plugins?  It seems every time someone has a codec problem they're told to install a gstreamer package.  Why not just install them all and be done with it?

---

