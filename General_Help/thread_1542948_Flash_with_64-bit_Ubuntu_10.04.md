---
title: "Flash with 64-bit Ubuntu 10.04"
date: 2010-07-31
forum: General Help
---

### Post by tmallory on 2010-07-31
Hey everyone, I'm trying to get flash to work in Ubuntu x64. I used Synaptic to download the flash plug-in, however when I try to go to youtube it tells me I have to update flash. When I try to, the Adobe site tells me Google Chrome already has the latest version installed.

How can I get it to work? I'm hoping there's an easy cure, since I'm new to Ubuntu.

Thanks for any help

---

### Post by howefield on 2010-07-31
Try this addon to ensure that you have the correct version for your system.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

If you then have issues with buttons, do this.

Open a terminal and type

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
``` 

And add the following before the last line

```
export GDK_NATIVE_WINDOWS=1
```

---

### Post by tmallory on 2010-07-31
> **howefield said:**
> Try this addon to ensure that you have the correct version for your system.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

If you then have issues with buttons, do this.

Open a terminal and type

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
``` 

And add the following before the last line

```
export GDK_NATIVE_WINDOWS=1
```What if I'm using Google Chrome and not Firefox?

---

### Post by howefield on 2010-07-31
> **tmallory said:**
> What if I'm using Google Chrome and not Firefox?

Sorry, missed that little gem :)

You have Firefox on your system unless you have removed it ?

You could use it with flash-aid to ensure that the correct flash has been installed, Chrome will pick it up just the same.

---

