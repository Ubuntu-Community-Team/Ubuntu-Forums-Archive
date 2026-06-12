---
title: "Boots to terminal login, now what?"
date: 2009-12-08
forum: General Help
---

### Post by hougSTAR on 2009-12-08
I just installed Kubuntu last night, and then I updated it to the latest packages and video card.  Now, when the computer boots into Kubuntu, it goes into a terminal and it asks for my Login and then Password.  

I got the Login and Password correct, and now it says james@ubuntu: and nothing else.  How do I start the actual desktop interface from here then tell it not to use the terminal for a login?  I put in "start kbm" like a previous topic recommended, but nothing happens. :confused:

---

### Post by rahilm on 2009-12-08
try startx

---

### Post by hougSTAR on 2009-12-08
Thanks

It starts going through a lot of text then it says "unable to connect to X server."  I take it that I need the X server to boot into the desktop?

Edit: It also at the top mentions a FATAL ERROR with my video card (Nvidia GeForce 6200).  I just updated it's drivers after I updated Kubuntu.  The drivers did work fine when I had Ubuntu installed a few days ago (uninstalled it 35 hours ago)

---

### Post by rahilm on 2009-12-08
i am clueless too. That is what i used to do when my usb-persistent install always booted to the command line. You can play around or wait till an experienced user answers your question.
Hint:try Google

---

### Post by sanderj on 2009-12-08
I would go back to the basic X server config. AFAIK, you can do that with:


```
sudo dpkg-reconfigure xserver-xorg

```

Then start the X server with startx (or a reboot). If that works, you can try to configure your specific driver again.

---

