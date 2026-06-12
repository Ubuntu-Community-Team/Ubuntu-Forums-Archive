---
title: "Choppy desktop performance on netbook. (Sony Vaio)"
date: 2010-05-04
forum: General Help
---

### Post by ShakyJake on 2010-05-04
I just installed the new ubuntu Netbook edition on my Sony Vaio VGN-P31ZK. I almost want to take it off because of the choppy slow display. 
 
I like the interface but I just cant seem to get the rendering up to par. I checked the drivers and it isnt using a vesa driver or whatever. It is using an actual intel driver. 
 
I understand that these netbooks are limited on capability due to their size. However, this netbook came pre-loaded with Microsoft Windows 7 Full Premium. It worked very well with Windows after I disabled the areo theme. 
 
But I believe if windows 7 can run choppy-free then ubuntu Netbook should be able to do the same.
 
I am a littlebit familar with linux but far from guru. Was hoping maybe someone knew a trick or something to get it running at its peak performance. If not, I will have to restore windows 7 back on it which I really dont want to do.

---

### Post by snowpine on 2010-05-04
Your netbook has Intel GMA500 "poulsbo" graphics. This chip is not well-supported by Linux due to a bad decision on Intel's part, and this is why your desktop looks "choppy."

Use the Search feature at the top right of your screen to learn more about GMA500. Here is one thread to get you started: [http://ubuntuforums.org/showthread.php?t=1229345&highlight=gma500](http://ubuntuforums.org/showthread.php?t=1229345&highlight=gma500)

---

### Post by ShakyJake on 2010-05-04
Thanks. Going to check it out now.

---

### Post by ShakyJake on 2010-05-05
Well I can't use that thread. :-( Complying with the instructions will result in the destruction of my operating system. In order to solve the dependencies and conflicts, 3 essential programs most be removed as well as several other programs that are important. Total programs to be removed to solve conflicts is 1GB worth. 
 
:-/ Not sure this is going to help me. 
 
I think I might just wait for the DVD to arrive and just install ubuntu full on my netbook rather than just use netbook edition. Netbook edition lacks a lot of features.

---

### Post by snowpine on 2010-05-05
The desktop version does not support GMA500 out-of-the-box either, sorry. :(

You can switch to the desktop version without reinstalling by:

```
sudo apt-get install ubuntu-desktop
```

Then log out and choose Gnome Session from the login screen.

Like I said, it will not solve your graphics situation, but you might prefer the interface. Good luck!

---

