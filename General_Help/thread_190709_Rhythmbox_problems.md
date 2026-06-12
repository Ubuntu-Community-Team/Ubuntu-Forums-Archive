---
title: "Rhythmbox problems"
date: 2006-06-06
forum: General Help
---

### Post by pinkythepenguin on 2006-06-06
Hopefully this is a small error as I love Rhythmbox! I have just upgraded to Dapper Drake all went smooth apart from when I try and play .mp3's it displays the error message of 

The file is not a audio steam <then displays the location> :(

I have tryed several different albums and single songs but nothing seems to work and I have  
all the correc plug in's installed

any help will be much appreciated :KS

---

### Post by ifokkema on 2006-06-06
[QUOTE=pinkythepenguin]Hopefully this is a small error as I love Rhythmbox! I have just upgraded to Dapper Drake all went smooth apart from when I try and play .mp3's it displays the error message of 

The file is not a audio steam <then displays the location> :(

I have tryed several different albums and single songs but nothing seems to work and I have  
all the correc plug in's installed

any help will be much appreciated :KS[/QUOTE]

I think this will solve your problem:
```
sudo apt-get install gstreamer0.8-plugins
```

This will install a bunch of plugins, that will also allow rhythmbox to play mp3's.

Edit: That happens, when you work on both Breezy and Dapper... sigh... sorry :)

Ivo

---

### Post by no1wantdthisname on 2006-06-06
Er, the newer rhythmbox uses gstreamer0.10.
Check [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) for how to install support for mp3.

---

### Post by kaamos on 2006-06-06
Dapper rb uses gstreamer 0.10 and breezy rb 0.8. So try this (universe & multiverse enabled):

```
sudo apt-get install gstreamer0.10-plugins-bad* gstreamer0.10-plugins-ugly*
```

---

### Post by givré on 2006-06-06
Read this to know more 
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) :wink:

EDIT : Why is every boody always faster than me :cool: 
Anyway, that's the prove that the ubuntu community is great

---

### Post by pinkythepenguin on 2006-06-06
Thank you all :-D

---

