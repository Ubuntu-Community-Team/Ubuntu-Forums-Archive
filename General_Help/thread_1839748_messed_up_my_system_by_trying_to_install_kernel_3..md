---
title: "messed up my system by trying to install kernel 3.0"
date: 2011-09-06
forum: General Help
---

### Post by gyyug78fg87ogguiioioioioi on 2011-09-06
please help me i messed up my system by following this guide: [http://news.softpedia.com/news/How-to-Install-Linux-Kernel-3-0-on-Ubuntu-11-04-217409.shtml](http://news.softpedia.com/news/How-to-Install-Linux-Kernel-3-0-on-Ubuntu-11-04-217409.shtml) and i got errors so i tried to reboot and now it doesent come to the login screen just that Ubuntu loader screen and then it freezes, and then to some text with no gUI if i go crazy on the keyboard while the ubuntu startup screen is loading that tells me to login and password, what should i do now and how can i enter gRUB, like it sais on the guide?

---

### Post by gyyug78fg87ogguiioioioioi on 2011-09-06
ok i found grub and tried with all the 3 older kernels that was on the list but it doesent go any longer than the ubuntu startup loader then it says on my screen "no signal" and my screen turns of, its because i uinstalled NVIDIA drivers like it said in the guide i think right?

---

### Post by nothingspecial on 2011-09-06
> **gyyug78fg87ogguiioioioioi said:**
> its because i uinstalled NVIDIA drivers like it said in the guide i think right?

Probably, can you get to a console and install them?

---

### Post by gyyug78fg87ogguiioioioioi on 2011-09-06
> **nothingspecial said:**
> Probably, can you get to a console and install them?
explaine me how please

---

### Post by nothingspecial on 2011-09-06
Press Ctrl-Alt-F1

log in (you won't see your password as you type it)

Then ```
sudo apt-get install <packages>
```

If you don't know the name of the packages, then type ```
less /var/log/apt/history.log
```

scroll or page down to the end and they should be in the last section.

You may need a wired connection for this if the packages are not in you archives.

---

### Post by realzippy on 2011-09-06
Easiest might be to choose a recovery mode at grub,then starting failsafe graphics,then install nvidia with Additional/Hardwaredrivers tool.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-09-06
thanks realzippy it worked and i came inside my desktop now i am downloading the drivers again hopefully it will fix thanks

---

### Post by gyyug78fg87ogguiioioioioi on 2011-09-06
it works now thanks, at first reboot after installed the driver, the GRUB came on automaticly and i tried the 3.0 kernel again to see if it was working now but it dident, so how can i delete the 3.0 kernel now, and do so the GRUB will not automaticly came on startup?

---

### Post by realzippy on 2011-09-06
Open Synaptic package manager..

Type the kernel number you want to remove in the search window,eg  
2.6.38-11
then mark "linux-image" **and** "linux-headers" files for that kernel
for complete remove (right-click),then hit "apply"
to remove kernels from your system and from the Grub menu.

Honestly I don't know how to hide grub,never wanted this because I keep
a bunch of kernels and ubuntu versions for testing and need the choice.
Guess google will tell...
There was a tool "startup-manager" (or similar) which may provide that option without manually editing grub related files.

---

