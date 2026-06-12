---
title: "Why don't any drivers, Flash work from Live CD?"
date: 2011-07-05
forum: General Help
---

### Post by Wiking on 2011-07-05
Why won't any drivers, for flash, mp3, and video files work in Kubntu running it off a live CD? I tried several line commands but nothing works.

---

### Post by timgood on 2011-07-05
These are all non-free software, and so can't be included on the Live CD owing to licensing restrictions and the fact that some (like mp3 codecs) may be illegal in certain countries. 

You can install these in a live session, but changes will be lost when you restart. You can make a persistent live usb key that will save changes - there is help available for that [here]("http://www.ubuntu-news.net/2010/04/16/create-a-persistent-bootable-ubuntu-usb-flash-drive/").

---

### Post by corrytonapple on 2011-07-05
Did you try
```
sudo apt-get install ubuntu-restricted-extras
```
in your Terminal?

---

### Post by dFlyer on 2011-07-05
> **Wiking said:**
> Why won't any drivers, for flash, mp3, and video files work in Kubntu running it off a live CD? I tried several line commands but nothing works.

They are not included on the cd, and need to be installed after the OS is installed. Just start synaptic and search ubuntu-restricted-extras.

---

