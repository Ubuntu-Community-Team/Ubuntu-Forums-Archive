---
title: "Xubuntu 12.04.1 has 3rd party codecs OOB?"
date: 2012-09-06
forum: General Help
---

### Post by FrogDemon on 2012-09-06
Ok, so I dl'd and am running Xubuntu 12.04.1 live right now and lo and behold, it plays my mp3s OOB! I mean I usually install them myself, but to have them OOB is a little concerning. I didn't think Canonical's ToS allowed for that. Unless things have changed since I last read them. 

Anyways, just thought I would post about it.

---

### Post by pqwoerituytrueiwoq on 2012-09-06
they are downloaded and installed while you were installing xubuntu
there is a checkbox for this that is checked by default during the installation that you did not see

---

### Post by FrogDemon on 2012-09-06
Umm, No. I was still running LiveCD. Had not installed it yet. So, if you want to find out for yourself, dl the x64 ISO from here: 

[URL="http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/12.04/release/xubuntu-12.04.1-desktop-amd64.iso"]http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/12.04/release/xubuntu-12.04.1-desktop-amd64.iso 
[/URL] 

As for not seeing the check boxes, well, I have not installed it yet. But when I do install a *buntu distro, I do see them. One is for installing updates, the other is for the codecs. 


Edit: 
By the way, that box isn't checked by default. I am installing Xubuntu right now and still playing my mp3s.

---

### Post by mips on 2012-09-06
I could be wrong but I think it works because of the gstreamer0.10-fluendo package which is included and Fluendo has paid the license for it.

[http://en.wikipedia.org/wiki/GStreamer#Plug-ins](http://en.wikipedia.org/wiki/GStreamer#Plug-ins)
[http://www.fluendo.com/shop/product/fluendo-mp3-decoder/](http://www.fluendo.com/shop/product/fluendo-mp3-decoder/)

---

### Post by FrogDemon on 2012-09-06
If that's true, why doesn't Ubuntu come OOB with it? Anyways, thanx for posting pertinent info that I can actually dig into.

---

### Post by mips on 2012-09-06
> **FrogDemon said:**
> If that's true, why doesn't Ubuntu come OOB with it? Anyways, thanx for posting pertinent info that I can actually dig into.

I don't know but at the same time this screen confuses me,

[IMG]http://www.dedoimedo.com/images/computers_years/2012_1/xubuntu-pangolin-begin-install.jpg[/IMG]

Does that mean fluendo is downloaded from the net or is it already included on the cd and installed as a option?

---

### Post by vasilbelarus on 2012-09-06
Fluendo can be installed only from internet, when you install without internet connection this chekbox inactive.

---

### Post by FrogDemon on 2012-09-06
> **mips said:**
> I don't know but at the same time this screen confuses me,

[IMG]http://www.dedoimedo.com/images/computers_years/2012_1/xubuntu-pangolin-begin-install.jpg[/IMG]

Does that mean fluendo is downloaded from the net or is it already included on the cd and installed as a option?
On LiveCD, will it play your mp3s?

---

### Post by mips on 2012-09-06
> **FrogDemon said:**
> On LiveCD, will it play your mp3s?

I don't have a Xubuntu livecd to test but I do have a 12.04 Lubuntu livecd which I tested with.

Before booting the livecd I disconnected my network cable just in case things got downloaded from the net.

From the livecd I could play FLAC, mp3 & ogg audio content.

If it works on Lubuntu livecd I can't see why it would not work on xubuntu livecd. Video content however would not play (avi, mkv, flv, mpeg4)

---

### Post by FrogDemon on 2012-09-06
> **mips said:**
> I don't have a Xubuntu livecd to test but I do have a 12.04 Lubuntu livecd which I tested with.

Before booting the livecd I disconnected my network cable just in case things got downloaded from the net.

From the livecd I could play FLAC, mp3 & ogg audio content.

If it works on Lubuntu livecd I can't see why it would not work on xubuntu livecd. Video content however would not play (avi, mkv, flv, mpeg4)
The Ubuntu LiveCD will not play mp3s at all.

---

### Post by mips on 2012-09-06
> **FrogDemon said:**
> The Ubuntu LiveCD will not play mp3s at all.

Well that's their loss :tongue: :biggrin:

---

