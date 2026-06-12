---
title: "Pidgin"
date: 2010-09-27
forum: General Help
---

### Post by Rahuljaiswal on 2010-09-27
I just upgraded pidgin to 2.7.3 using this [http://pidgin.im/](http://pidgin.im/)
i want it to support video/audio chat in gmail or yahoo.. plz help
in gmail its supporting audio but video is not supporting.
i know using firefox browser i can do both. but is it possible for pidgin to do the same thing???

---

### Post by psycho5 on 2010-09-27
You can use GYachi for yahoo messenger it supports audio and video. And I use empathy for all my chat. It has audio video but I never tried it.

---

### Post by anirudhtomer on 2010-09-27
Source of the following information: [http://en.wikipedia.org/wiki/Pidgin_%28software%29](http://en.wikipedia.org/wiki/Pidgin_%28software%29)

As of version 2.6 (released on August 18, 2009) Pidgin has a voice/video framework which uses [Farsight2]("http://en.wikipedia.org/wiki/Farsight") and is based on Mike Ruprecht's Google Summer of Code project from 2008.[[7]]("http://en.wikipedia.org/wiki/Pidgin_%28software%29#cite_note-6")  That release provides the ability to have voice/video conversations  using the XMPP protocol (including Google Talk), though the  implementation is not yet fully complete. The framework will also allow  for voice/video conversations on other protocols, such as MSN and Yahoo,  in the future

---

### Post by anirudhtomer on 2010-09-27
Source of the following information: [http://en.wikipedia.org/wiki/Pidgin_%28software%29](http://en.wikipedia.org/wiki/Pidgin_%28software%29)

As of version 2.6 (released on August 18, 2009) Pidgin has a voice/video framework which uses [Farsight2]("http://en.wikipedia.org/wiki/Farsight") and is based on Mike Ruprecht's Google Summer of Code project from 2008.[[7]]("http://en.wikipedia.org/wiki/Pidgin_%28software%29#cite_note-6")  That release provides the ability to have voice/video conversations  using the XMPP protocol (including Google Talk), though the  implementation is not yet fully complete. The framework will also allow  for voice/video conversations on other protocols, such as MSN and Yahoo,  in the future

---

### Post by anirudhtomer on 2010-09-27
Source of the following information: [http://en.wikipedia.org/wiki/Pidgin_%28software%29](http://en.wikipedia.org/wiki/Pidgin_%28software%29)

As of version 2.6 (released on August 18, 2009) Pidgin has a voice/video framework which uses [Farsight2]("http://en.wikipedia.org/wiki/Farsight") and is based on Mike Ruprecht's Google Summer of Code project from 2008.[[7]]("http://en.wikipedia.org/wiki/Pidgin_%28software%29#cite_note-6")  That release provides the ability to have voice/video conversations  using the XMPP protocol (including Google Talk), though the  implementation is not yet fully complete. The framework will also allow  for voice/video conversations on other protocols, such as MSN and Yahoo,  in the future

---

### Post by anirudhtomer on 2010-09-27
I am really really sorry. There was some problem with my browser that's why multiple replies were sent.

---

### Post by Rahuljaiswal on 2010-09-27
you people are just amazing... anyway i have solved the problem of video/audio support of gmail via pidgin... but couldn't solved yahoo... seems i have to install gyachi... well i wanted to do everything on one massenger. for yahoo video/audio i will install gyachi. but if anyone knows how to get audio/video in pidgin, that will be appreciated... thanks guys for your replies... :)

---

### Post by Tibuda on 2010-09-27
> **Rahuljaiswal said:**
> you people are just amazing... anyway i have solved the problem of video/audio support of gmail via pidgin... but couldn't solved yahoo... seems i have to install gyachi... well i wanted to do everything on one massenger. for yahoo video/audio i will install gyachi. but if anyone knows how to get audio/video in pidgin, that will be appreciated... thanks guys for your replies... :)

[http://developer.pidgin.im/wiki/Using%20Pidgin#DoesPidginsupportwebcamsvideo](http://developer.pidgin.im/wiki/Using%20Pidgin#DoesPidginsupportwebcamsvideo)
> Does Pidgin support webcams (video)?
Yes, but only for XMPP/GMail.
This means no Yahoo video in Pidgin.

---

### Post by Rahuljaiswal on 2010-09-27
yes pidgin does support video chat in gmail n i am doing it.

---

### Post by Rahuljaiswal on 2010-09-27
ok... so for yahoo video/audio chat i have to rely on gayachi now. n i have read lots of forums on this  that gayachi is too good... will have to give it a try i guess... please send me the links and way how can i install it on my ubuntu... :)

---

### Post by Tibuda on 2010-09-27
> **Rahuljaiswal said:**
> yes pidgin does support video chat in gmail n i am doing it.

Yes, I was talking about Yahoo.

---

### Post by Tibuda on 2010-09-27
> **Rahuljaiswal said:**
> ok... so for yahoo video/audio chat i have to rely on gayachi now. n i have read lots of forums on this  that gayachi is too good... will have to give it a try i guess... please send me the links and way how can i install it on my ubuntu... :)

Gyachi is not on Canonical repositories, so you have to use a third party PPA.

Add this PPA to your [software sources](http://www.psychocats.net/ubuntu/sources) (in the System menu): [https://launchpad.net/~loell/+archive/ppa](https://launchpad.net/~loell/+archive/ppa)
Update your package database, and install the [gyachi](apt:gyachi) package using the software store, synaptic or other method.

Or run those commands in a terminal:
```
sudo add-apt-repository ppa:loell/ppa
sudo apt-get update
sudo apt-get install gyachi
```

---

### Post by Rahuljaiswal on 2010-09-28
thank you very much... :)

---

