---
title: "Cannot get full screen res after lubuntu install"
date: 2011-01-27
forum: General Help
---

### Post by cheapodonuts on 2011-01-27
Installed Lubuntu on an old VAIO notebook with 256meg RAM.
My fault I guess, as I clicked away hastily during the install just to get it done. But now my only choices for screen res are 800x600 or less!! :lolflag:  It's like looking at a greetings card! And I have myself to thank for it. :P

So how do I get into the system to see the bigger picture?


Thanx in advance folks.

---

### Post by Vaphell on 2011-01-27
what gfx do you have in that laptop?
```
lspci | grep VGA
```

---

### Post by cheapodonuts on 2011-01-27
It's just the original built in stuff.
VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)

---

### Post by Vaphell on 2011-01-27
i815 chipset then, check which driver is loaded
```
lsmod | grep -w -E 'i81.|intel|vesa'
```
paste the line above in terminal, does it return anything?
if vesa then check if you have intel driver package installed (xserver-xorg-video-intel)

either way i think you may be forced to familiarize yourself with xorg.conf, which is used to override settings generated in autodetection phase of bootup (obviously something fails)

[http://threeeighthsspacer.com/blog/2009/09/08/dell-inspiron-2500-with-intel-82815-graphics-xorgconf-for-1024x768/](http://threeeighthsspacer.com/blog/2009/09/08/dell-inspiron-2500-with-intel-82815-graphics-xorgconf-for-1024x768/)

[http://www.linux-solved.com/post/Intel-i815-video-problem-solved-28432.html](http://www.linux-solved.com/post/Intel-i815-video-problem-solved-28432.html)
different driver suggested here

not for sony vaio but maybe it will work. Most probably you don't have that xorg.conf file so you will need to create it.

---

### Post by cheapodonuts on 2011-01-29
Now I am laughing even more at what this little laptop is doing. I allowed it to upgrade Lubuntu, once again without me really looking at what was happening. And it upgraded to Ubuntu! Hahahahah So now those commands do not work! :lolflag: And still, I have 800x600

So I re-installed Lubuntu, and the 800x600 is here anyway. No option appeared to change it.

Thanks for those codes Vaphell, I will try them again, now.

I'll try and learn about xorg as you suggested, but I'm not a good learner these days. :confused:
My tinnitus can be very annoying when I try to learn new stuff. :mad:

---

### Post by cheapodonuts on 2011-01-29
Ok, I'm cancelling this install. I have no desktop on the screen now.

If I go again with Lubuntu, I will get back to this thread. Thanks for trying to help you guys! 

Have some donuts!

[IMG]http://i81.photobucket.com/albums/j226/chashugh/donuts-2.jpg[/IMG]

---

