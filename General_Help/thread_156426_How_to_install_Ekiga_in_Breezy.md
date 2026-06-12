---
title: "How to install Ekiga in Breezy?"
date: 2006-04-07
forum: General Help
---

### Post by jazzi on 2006-04-07
[SIZE="2"]Ekiga is the next generation of GnomeMeeting,oh,it sounds great.
BUt is there a way to [COLOR="Red"]install Ekiga in Ubuntu5.10 ?[/COLOR]
Someone help me? [/SIZE]
:-k

---

### Post by waster on 2006-04-07
1. upgrade to dapper
2. install ekiga

Sorry, can't help with Ekiga in Breezy. Look in backports.

---

### Post by jazzi on 2006-04-07
[QUOTE=waster]1. upgrade to dapper
2. install ekiga

Sorry, can't help with Ekiga in Breezy. Look in backports.[/QUOTE]

Thank you all the same.but is there no way in Breezy?

---

### Post by jazzi on 2006-04-07
I have found a way to resolve the problem:the source aticle is here:[http://www.ubuntuforums.org/showthread.php?t=146453]("http://www.ubuntuforums.org/showthread.php?t=146453")
the simple steps is:
1.add the following to the sources.list
> deb [http://pkg-voip.buildserver.net/ubuntu](http://pkg-voip.buildserver.net/ubuntu) breezy main
Paste it at the end of the sources.file
2.Open System/Administration/Synaptic

 It might tell you that something like "some sontents have not been validated..." -> click OK

3.Search "Ekiga"

 Mark the box Ekiga to install

 Click Apply

4. Once synaptic has finish the job, close, and go to Applications/Internet/Ekiga

Enjoy

---

### Post by cvmostert on 2006-04-17
thank you... will install and try ekiga out...

---

