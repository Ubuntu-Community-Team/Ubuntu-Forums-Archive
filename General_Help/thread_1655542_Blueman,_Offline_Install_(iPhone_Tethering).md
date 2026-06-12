---
title: "Blueman, Offline Install (iPhone Tethering)"
date: 2010-12-29
forum: General Help
---

### Post by shoot2kill on 2010-12-29
Hi, I have just installed ubuntu on my machine which doesn't have Internet.

I can access the net on my laptop and copy any files over. 

I am wanting to install blueman to tether my iPhone. 

I cannot find a .deb of it, so downloaded the tar.gz but the stock install doesnt have a compiler. I could download and copy over a compiler, but I'm guessing I'm going to be here hours copying over each dependancy that I come across (I'm guessing there may be a few)

So I was wondering how I can tether my iPhone or how I can install blueman? Does anyone know of any pre-built packages I can just copy n install?

Hope that my question is clear enough. 

Thanks!

---

### Post by shoot2kill on 2010-12-29
I managed to solve this problem by using an offline package-manager called keryx

A good tutorial for using it: [http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/)

it loads a synaptic like interface on another machine to download the required files and then installs them on the first machine. 

very good, and easy to use, although if you want to use windows as the second machine, you will need to install python and a couple of python library's: [http://keryxproject.org/forums/index.php?topic=103](http://keryxproject.org/forums/index.php?topic=103)

---

### Post by WorMzy on 2010-12-29
I'm glad you found a solution.

For future reference though, you can obtain the packages available in the repos at this address: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Here's the blueman package: [http://packages.ubuntu.com/search?keywords=blueman](http://packages.ubuntu.com/search?keywords=blueman)

---

### Post by shoot2kill on 2010-12-29
and would this method download ay needed dependancies too?
that was my main problem, as i was running stock ubuntu. 

It turned out that blueman didnt need any dependancies, but many other apps do, dont they?

---

### Post by WorMzy on 2010-12-30
No, you'd need to manually download the dependencies too (assuming you don't already have them)

---

### Post by EXCiD3 on 2010-12-30
Keryx will download the dependencies for you.

---

