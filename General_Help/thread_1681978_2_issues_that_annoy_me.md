---
title: "2 issues that annoy me"
date: 2011-02-05
forum: General Help
---

### Post by uvaio on 2011-02-05
Hi Guys,

There are 2 things which really annoy me on my Ubuntu I wonder someone can help me to resolve these.

1. clipboard is not permanent. It often happens that I copy something e.g. text in Thunderbird or open office and as soon as I close the window and want to paste text to other program it is not in clipboard anymore. Is it possible to make clipboard persistent what ever happens?

2. this started on upgrade to 10.10, Every time nautilus is opened from application like skype or firefox it asks for pass and opens nautilus in root session. Not very nice since I have to type pass and work with the files which I just downloaded under root is not really good anyway.

Does anyone an idea how to resolve these?

Thanks

---

### Post by Sazhen86 on 2011-02-05
Hi

I'm not sure about the second issue as I'm still on 10.04 which seems to work fine.

For the clipboard issue, take a look at glipper or gclip.

Cheers

---

### Post by coldraven on 2011-02-05
Or look at Pastie
[http://www.omgubuntu.co.uk/2010/10/pastie-handy-clipboard-manager-indicator-applet/](http://www.omgubuntu.co.uk/2010/10/pastie-handy-clipboard-manager-indicator-applet/)

---

### Post by sanderd17 on 2011-02-05
can you run firefox from terminal and show us a log from the pont where you open nautilus?

---

### Post by ugm6hr on 2011-02-05
> **uvaio said:**
> 1. clipboard is not permanent. It often happens that I copy something e.g. text in Thunderbird or open office and as soon as I close the window and want to paste text to other program it is not in clipboard anymore. Is it possible to make clipboard persistent what ever happens?

2. this started on upgrade to 10.10, Every time nautilus is opened from application like skype or firefox it asks for pass and opens nautilus in root session. Not very nice since I have to type pass and work with the files which I just downloaded under root is not really good anyway.

1. This is a reflection of the default for Ubuntu. You need a clipboard manager program to achieve persistence, and allow you to paste previously copied data.
The 2 commonly mentioned options are parcellite and glipper (amongst others mentioned above). e.g. To install parcelite:
```
sudo apt-get update
sudo apt-get install parcellite
```
Parcellite then appears in the Accessories menu, and will autostart every reboot once launched the first time. It sits in your panel, and is pretty straightforward to use. I only dabbled briefly with glipper, which I believe is a little heavier on resources, and also manages images etc (parcellite only manages text).

2. Where is the default download location in firefox? What if you launch firefox from terminal and download something?

---

