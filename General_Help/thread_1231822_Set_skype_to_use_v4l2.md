---
title: "Set skype to use v4l2"
date: 2009-08-04
forum: General Help
---

### Post by jdp2681 on 2009-08-04
I have been beating my head into a brick wall on this.  I am still a N00b to Ubuntu and I am trying to get my web cam to work with Skype.  When I test it and start a communication my video has bars through it.  I get the same results from gstreamer-properties when I use v4l but the video is fin on v4l2.  I am thinking that I need to change Skype to use the v4l2 but I can not find a way to make this change.  Can anyone help???

---

### Post by djtechsupport on 2009-11-13
I am having the same problem.  My cam works fine for VLC, Cheese, but not for Skype.  Is there a way to trick Skype into using V4L2 or something?  Currently running 9.1 Ubuntu 32 bit on an Asus X83-VB

---

### Post by monkeyslayer56 on 2011-05-29
I know im a couple years late to the problem but seeing as how hard it seams to be to find a working solution i'll post what works for me. But when you launch skype launch it like
```
LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype
```
On 32bit it will probbaly be just lib instead of lib32 (im on 64bit)
 on arch linux the package that has that file is lib32-v4l-utils. What i did was just made a bash script ```
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

``` and named it myskype and put it into /usr/bin
Hope this helped someone

---

