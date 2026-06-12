---
title: "Which version of Linux would be best for this laptop?"
date: 2009-09-15
forum: General Help
---

### Post by HybridTheorist on 2009-09-15
Hello, I've got an old laptop (Toshiba Satellite 1805, 1.1 Intel Celeron, 256mb Ram) that I would like to install Linux on (preferably a version of Ubuntu but open to try any that will work) to get a feel for it and play around with, before I purchase a new laptop. I'm doing this to see if I want to use Linux with the new laptop or stick with Windows. So what would be a good version or flavor of Linux to try?
I do have some older Ubuntu CD's (5.1 & 7.1)  Would either of those work ok?  Thanks.

---

### Post by Boondoklife on 2009-09-15
You could try those, though I would suggest a newer version. Here is a listing of the top used distro's take a look [http://iso.linuxquestions.org/](http://iso.linuxquestions.org/)

If you want a crash course and learn alot then check out gentoo.

---

### Post by Shpongle on 2009-09-15
if you have used linux before or ubuntu id recommend crunchbang linux, its based on ubuntu and light on resources, it can involve a lot of editing of text files if you want to configure certain things though , but its all part of the learning process

---

### Post by snowpine on 2009-09-16
> **HybridTheorist said:**
> Hello, I've got an old laptop (Toshiba Satellite 1805, 1.1 Intel Celeron, 256mb Ram) that I would like to install Linux on (preferably a version of Ubuntu but open to try any that will work) to get a feel for it and play around with, before I purchase a new laptop. I'm doing this to see if I want to use Linux with the new laptop or stick with Windows. So what would be a good version or flavor of Linux to try?
I do have some older Ubuntu CD's (5.1 & 7.1)  Would either of those work ok?  Thanks.

1st of all, don't use any version of ubuntu older than 8.04. That is the oldest version that is still supported. (If you go older than that, you won't be able to install new software, receive security updates, bug fixes, etc.) Your best bet is actually the current version (9.04) which many feel is the fastest yet.

I would recommend giving CrunchBang a try. It is the best lightweight "remix" of ubuntu in my opinion. If that's not fast enough for you (I think it will be okay), your best bet is to step outside the ubuntu family and give Puppy or Slitaz a try... they are very fast, but lack some of ubuntu's "bling".

---

### Post by Lars Noodén on 2009-09-16
You can make each version of Ubuntu just like any other by adding or removing packages.  Since there is little RAM, try installing as lean packages as possible.  



A netbook remix might be worth looking at:
[http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)

For the GUI, try Fluxbox or FVWM-Crystal

[http://packages.ubuntu.com/jaunty/fvwm-crystal](http://packages.ubuntu.com/jaunty/fvwm-crystal)
[http://packages.ubuntu.com/jaunty/fluxbox](http://packages.ubuntu.com/jaunty/fluxbox)

They may be a little low on eye candy but fast.

---

### Post by chessnerd on 2009-09-16
Personally, I'd go with Xubuntu before I tried Crunchbang or something else. It has the XFCE desktop environment, but it has been modified to look and work more like Gnome from Ubuntu. That way, if you end up installing Ubuntu on your new laptop, you will be more familiar with the setup of the desktop. I used Xubuntu as my first distro and really enjoyed working with it. It has lower system requirements than Ubuntu and I used it on a computer with 256MB RAM without any problems.

Whatever distro you pick, though, remember to be patient when learning. Frustrations will arise, but figuring out how to get past them will be a rewarding experience. Have fun with it and before you know it, you'll be the one posting the help and advice on the forums. :)

---

### Post by HybridTheorist on 2009-09-17
Ok I went w/ Xubuntu and it looks good. But...the highest display setting I can get is 800x600 when I have 1024x768 in XP. So i have about a 1" black border around my Linux desktop instead of full screen. How do I change to a higher resolution?

---

### Post by holycow131415 on 2009-09-18
hey, i have xubuntu and had that same problem. First, you will have to find what driver your graphics card uses. mine uses r128 for my rage mobility. well anyway, you will have to edit your xorg.conf file to something like this for it to work. and replace the driver with the correct one for you. terminal > lspci will show you i believe.

[http://ubuntuforums.org/archive/index.php/t-495256.html](http://ubuntuforums.org/archive/index.php/t-495256.html)

---

### Post by Levviathor on 2009-09-18
I think you should poke around in the settings to see if you can fix teh resolution there.  If that doesn't work, *then* you could poke around with xorg.conf.

---

