---
title: "Ubuntu 12.04 Sound Popping"
date: 2012-09-12
forum: General Help
---

### Post by Guerrilla Jesus on 2012-09-12
I understand that this is an often cited issue, and have looked through many different websites and threads on here giving a solution to the "sound popping" issue. The only solution I've seen is to go into alsa-base.conf and take out the last two lines, which specify some power-saving methods. However, when I access this file, no such lines exist! I've viewed a [YouTube video]("http://www.youtube.com/watch?v=RSbw42MkPvE") of the solution in action, and my file looks completely identical aside from those final two lines. The fact that this popping sound occurs ONLY when I am off of A/C power proves that it is almost without a doubt a power saving issue, however, I see no options in the system settings nor anywhere in the alsa-base.conf file. 

Specs:
Ubuntu 12.04
Intel Processor: 2.3 GHZ
Intel HD Graphics

EDIT: Fixed. Apologies.

---

### Post by SmallWorld on 2012-09-15
Don't forget to flag this thread as SOLVED.

For anyone still dealing with this problem:

I had the same problem on a HP dv6.  After booting or unsuspending my computer while on battery power, the speakers would make a regular clicking / popping / cracking sound.  I noticed after reading other postings that this only occured when I was running Chrome and left certain websites such as GMail running.

Rather than mess Ubuntu's speaker settings, I followed the solution at [http://ubuntu-with-wubi.blogspot.com/2012/07/weird-clicking-noise-in-chrome.html]("http://ubuntu-with-wubi.blogspot.com/2012/07/weird-clicking-noise-in-chrome.html") which is to disable the PepperFlash plugin in Chrome.

Disabling the PepperFlash plugin has to my surprise not had any noticable effect on Chrome's ability to view Flash-powered pages.

---

### Post by Jeyaprakash on 2012-10-05
I was getting very annoyed by that sound. Never thought chrome could be the reason. Just closed the chrome browser and opened it again. It stopped the sound. Immediately disabled the flash plugin also to be on the safer side. A great relief! Thanks!:)

---

