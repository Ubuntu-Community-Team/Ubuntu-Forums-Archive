---
title: "An Error Occured While Mounting / (Along with the by-uuid... error"
date: 2011-02-18
forum: General Help
---

### Post by brandonman on 2011-02-18
Hey guys, my Dad's computer was running quite slow here lately (Running Hardy Heron). I decided to go ahead and run all the software updates, and had it go ahead and update the OS as well. Well, the install went fine, but upon booting, it crashes to busy-box with the dreaded "ALERT! /dev/disk/by-uuid/########## not found error". I found that if I waited for a while, then cd'd to the by-uuid folder, this file eventually showed up. So I figured maybe if I 'exit' from there, it would boot up and find the file. Au Contrair, things get stranger! I end up with a purple screen telling "An Error Occured While Mounting /". Here's what it looks like:

[IMG]http://img13.imageshack.us/img13/308/20110218153727.jpg[/IMG]

Any and all help is appreciated! This is quite frustrating, I'd like to get it fixed and hopefully save the data he has on there! I remember having the by-uuid error once before after running an update I think, but can't remember how I fixed it! Feels like I just used the 'exit' trick a couple of boots and it was fine??

---

### Post by jerrrys on 2011-02-19
never had this screen before, so what happens when you go to manual recovery

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=an+error+occurred+while+mounting&as_qdr=all&sa=Google+Search&lang=en#840](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=an+error+occurred+while+mounting&as_qdr=all&sa=Google+Search&lang=en#840)

---

### Post by brandonman on 2011-02-19
Bloody weird. Manual Recovery takes you to a root shell. And guess what, I can see / with the root shell. Gah, thought it couldn't mount! Grrr!!! Hopefully having this shell there makes fixing this stupid issue much easier! 

[IMG]http://img718.imageshack.us/img718/5873/20110219193305.jpg[/IMG]

---

### Post by brandonman on 2011-02-20
Bumping to the top since it's been nearly 24 hours. Hoping to get this fixed!

---

### Post by jerrrys on 2011-02-21
there's a chance that 'testdisk' can come to the rescue

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

sounds like you could use the live cd.  testdisk comes bundled with 'gparted' live cd, this would be a good route to go provided you can burn a cd...

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by brandonman on 2011-02-21
Alright, thanks for all the help so far Jerrys. I'm downloading gparted-live right now. I'll report back with how it goes!

---

### Post by brandonman on 2011-02-21
Ok, well gParted started coming up (I got the menu with boot live, memtest, etc). Well past that, it goes to all the white-text on black (Sorry, forgot what you call this, haven't had my coffee! lol) as it does it loading. Well, in the end, I get a crash to... busybox. It has a debian logo at the top, says debian has crashed, contact debian support, etc, and that it couldn't find a bootable thing in the live folder. Gah, this is frustrating! What could be wrong with this??

---

