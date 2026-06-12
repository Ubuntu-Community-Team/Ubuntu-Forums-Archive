---
title: "Desktop Environment for a Slower PC"
date: 2011-06-18
forum: General Help
---

### Post by mysticxhobo on 2011-06-18
I'm new to these forums and also a new ubuntu user. I have an older IBM P3 laptop im running ubuntu on. And im wondering if there's a way to change the desktop environment to one which would use less system resources. Im currently running the default. I've used other distros way back in the day that would allow you to use KDE. Can KDE be installed and would this be a better option for an older computer?  Also any general tips on which features to disable would be great.  Thanks, james bell

---

### Post by OlyPerson on 2011-06-18
Look into Lubuntu and Xubuntu.  KDE (Kubuntu) would not run any faster than normal Ubuntu on an older computer like yours.

---

### Post by Linux_junkie on 2011-06-18
> **mysticxhobo said:**
> I'm new to these forums and also a new ubuntu user. I have an older IBM P3 laptop im running ubuntu on. And im wondering if there's a way to change the desktop environment to one which would use less system resources. Im currently running the default. I've used other distros way back in the day that would allow you to use KDE. Can KDE be installed and would this be a better option for an older computer?  Also any general tips on which features to disable would be great.  Thanks, james bell

KDE can be installed but depending on the amount of RAM your laptop has.   I believe KDE can run within 512MB of RAM but it is ideal to have 1GB+ of RAM for KDE.

For low amounts of RAM up to 512MB you would be better off with LXDE or XFCE.

---

### Post by mike555 on 2011-06-18
You can uninstall things you don't use, of course use your own judgment;

Uninstall using the package manager (mark for complete removal)

- bluez
- bluez-alsa
- bluez-cups
- bluez-gstream
- britty
- compiz
- compiz-core
- computer-janitor
- empathy
- empathy-common
- espeak
- espeak-data
- evolution
- evolution-common
 - evolution-data-server (but not data-server common)
- evolution-webcal
- f-spot
- g-brainy
- gwibber
- gwibber-service
- indicator-me
- indicator-messages
- mono-2.0-gac
- python-ubuntuone
- python-ubuntuone-client
- python-ubuntuone-storageprotocol

- shut down , wait a minute then start ... you will see much less memory usage.

 - then you can install some lighter apps, like ; gnote ,  mirage , gufw , abiword , Thunderbird , ubuntu-tweak ,etc.

---

### Post by Simian Man on 2011-06-18
> **mike555 said:**
> You can uninstall things you don't use, of course use your own judgment;

- shut down , wait a minute then start ... you will see much less memory usage.

 - then you can install some lighter apps, like ; gnote ,  mirage , gufw , abiword , Thunderbird , ubuntu-tweak ,etc.

Just uninstalling applications will free up hard drive space, but won't use less memory.  Xfce is likely the best bet.

---

### Post by mike555 on 2011-06-18
Yes it will use less memory , I went from about 250MB to around 90 at start up .......
[IMG]http://i40.tinypic.com/14c402e.jpg[/IMG]

---

### Post by mysticxhobo on 2011-06-18
thanks for the replies. i think xfce sounds like a good choice. so i have to reinstall the entire operating system using xubuntu? or can i just install xfce?

---

