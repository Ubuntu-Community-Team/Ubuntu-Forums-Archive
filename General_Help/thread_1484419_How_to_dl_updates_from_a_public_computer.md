---
title: "How to d/l updates from a public computer?"
date: 2010-05-15
forum: General Help
---

### Post by komensky on 2010-05-15
Is there a direct link to Lucid updates?

How can I download the linux-headers* updates from a public computer?  This terminal runs only ms s/w.

tia

---

### Post by jerome1232 on 2010-05-15
Does keryx look like an option?

[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by komensky on 2010-05-15
Unfortunately I can't run/install any software in this machine.

---

### Post by jerome1232 on 2010-05-15
I'm pretty sure it's a mobile binary, meaning you can stick on a cd or usb disk and just run it, it should run as a regular user on a windows machine so I don't believe restrictions on the computer would stop the program from running.

Unless these things are in some sort of kiosk mode.

---

### Post by 2hot6ft2 on 2010-05-15
Keryx being the better choice you could do something like going to Synaptic on the one needing the packages and marking all the packages you want to install then clicking on File > Generate package download script

Then moving or saving the script to a usb flash drive which you can take to a windows machine and open it in wordpad then copy and paste each url into the browsers address bar and hit Enter to download them one at a time and save them to the usb drive.

Then you take the usb to the machine that created the script and open Synaptic and click on File > Add downloaded packages and point it to where the script and packages are to install them.
:popcorn:

---

### Post by EXCiD3 on 2010-05-17
No installation needed for Keryx and it is built so that you don't need any sort of internet connection on the machine you want to install things on. The synaptic download scripts require you to at least be able to update the repository list aka some sort of internet connection.

---

