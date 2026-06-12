---
title: "help with make menuconfig"
date: 2006-02-08
forum: General Help
---

### Post by muzcuk on 2006-02-08
I've been seeing all this bluetooth support and hp printing support etc. etc. loading whenever I boot my computer with linux. I don't want them to. There are ways to specify what loads and what doesn't during your startup, I know, but I want to dig down and go to the root of the problem (well, its not a problem actually, its just aggravating). 

I tried to recomplie my kernel a couple of times, I suceeded. But all I made was small chnges in make menuconfig. Whenever I tried to do some big changes (like disabling the usb support, I don't use any usb devices) it started to give me errors during the complie process and I never got to complie it with big differences. I believe when I mess with setting, I mess with the dependencies, so whenever I take something out I have to take several things out with it because other things need it. 

What I really want to do is to disable module support and add everything I need directly into the kernel and leave everything I don't need out. 

So I need a big manual book about what these options are, which one needs which one, and most importantly, which ones I need and which ones I don't.

Who can help me with these? I'm thinking, there probably is a command that I can use to see what modules are running while I'm using my system normally, so that could be a starting point but I obviously need some help with that too..

---

### Post by zxee on 2006-02-09
To see what modules are running just do 'lsmod' in the terminal.
There are many how-tos on kernel compiling and ones that address the issue of built in modules or loadables. [http://www.faqs.org/docs/Linux-mini/Modules.html](http://www.faqs.org/docs/Linux-mini/Modules.html)
that link is old but covers the basics. Good luck

---

