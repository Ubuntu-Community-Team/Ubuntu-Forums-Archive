---
title: "shut down window repeatedly appears - not user invoked"
date: 2011-01-15
forum: General Help
---

### Post by labcede on 2011-01-15
I have a problem with my 10.10 32bit installation.  The shut down window repeated appears within a few seconds of use, and this is not user-invoked.  The shut down screen just pops up within a few seconds after logging in.  It even occurs at the login screen.  Once it appears, it'll repeatedly close & reopen.  I tried using 10.04 bit (which I normally use on my other computers), and have the same results.  This is a new computer that I just bought
Intel Atom 330 (1.6GHz, dual-core), full specs in the link
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856119016](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119016)
with a 4GB stick of RAM
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820145600](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145600)

I've already ran a memory test, and it's totally ok.

Here's a video clip of what I am experiencing on my screen.

[http://s363.photobucket.com/albums/oo77/labcede/Mobile%20Uploads/?action=view&current=VID_20110115_202211.mp4](http://s363.photobucket.com/albums/oo77/labcede/Mobile%20Uploads/?action=view&current=VID_20110115_202211.mp4)

HELP!  I've been using Ubuntu since 8.04, and this is the first time that I've ever ran into issues.

---

### Post by labcede on 2011-01-15
here's another video .... this time it's at the login screen
[http://s363.photobucket.com/albums/oo77/labcede/Mobile%20Uploads/?action=view&current=VID_20110115_214837.mp4](http://s363.photobucket.com/albums/oo77/labcede/Mobile%20Uploads/?action=view&current=VID_20110115_214837.mp4)

---

### Post by akand074 on 2011-01-15
:O your system really wants to turn off. That's kind of got some comedic value.. though I can see the frustration. I can't imagine what would cause such a thing.. just thought it's interesting.

---

### Post by labcede on 2011-01-16
I even tried looking for the process that invokes this window (with hopes of deleting it).  No such luck at identifying the process.

---

### Post by coldraven on 2011-01-16
I had a similar problem after closing the laptop lid.
Even though the Power management was set to "Blank Screen".
The shutdown window would appear and all the keyboard was disabled.
All I could do was watch the 60 second countdown until the machine switched itself off.
It seems to have been fixed when the latest kernel update happened (2.6.35-24-generic 64bit)
Your problem with the flashing reminds me of a sticky keyboard, try using another keyboard and see what happens.
Good luck :p

---

### Post by gas, meet foot on 2011-01-16
Does this happen with the Live Disk you booted from USB, or only the actual drive install?

---

### Post by labcede on 2011-01-16
either way ... live cd & usb drive install.  same results.  i've already tried my corded keyboard/mouse (typically use a logitech dinovo keyboard)  - no dice.

---

### Post by piquat on 2011-01-17
Don't take this as an answer, more fishing for an expert opinion:

I wonder if it's just getting a hardware shutdown command and if noapic would help?  (I have no idea if this would work, wait for another opinion)

Something to check on your own, is something wrong with the switch on the case?

---

### Post by labcede on 2011-01-18
case is fine. I played around with the ACPI settings in the BIOS.  still no help. argh.  I don't want to install wind*ws

---

### Post by Hatsune Miku on 2011-01-18
> **labcede said:**
> case is fine. I played around with the ACPI settings in the BIOS.  still no help. argh.  I don't want to install wind*ws

init is the process that handles start up and shut down of processes, the CPU knows to shutdown when the Kernel is unloaded. What im getting to is init is detecting something to request a reboot, did you install any new drivers or software?

---

### Post by labcede on 2011-01-19
the only new driver was activating the nvidia driver.  although, it still behaved the same way pre- & post-installation.

---

### Post by labcede on 2011-01-19
found the process that was acting up ... gnome-power-manager.  after i terminated the process & disabled it from startup, the problem never returned.  it's a little annoying, but at least the comp is usable now.  :D

---

### Post by Hatsune Miku on 2011-01-20
> **labcede said:**
> found the process that was acting up ... gnome-power-manager.  after i terminated the process & disabled it from startup, the problem never returned.  it's a little annoying, but at least the comp is usable now.  :D

Now that i recall a lot of people have trouble with the GNOME power manager. Well anyway, Glad you got it fixed :). Mark your thread as solved please :D

---

### Post by Vigh on 2011-01-20
do you have a card-reader? if so blacklist the hardware, been awhile since I did that, could be causing the problem, had a similar issue with the card reader playing up and blacklisting it solved the problem, on how to do that, I would have to refresh my memory, but it may not even be the problem

---

