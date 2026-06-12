---
title: "scanning?"
date: 2010-04-09
forum: General Help
---

### Post by Cityscape on 2010-04-09
I have an HP Officejet J6400 printer/scanner. All the drivers are installed, and I can scan with the default program. But it is far too complicated for anyone here to use. Can someone recommend me a good, easy-to-use scanning program (preferably being able to save as PDF easily)?

---

### Post by akakingess on 2010-04-09
I haven't tried or looked into myself, but have you tried a graphics program, such as GIMP, as it should/may have an option to scan into, and then output as PDF (possibly, just a suggestion).

---

### Post by Bucky Ball on 2010-04-09
Xsane Image Scanner. It's in the repos. Should allow you to scan through Gimp also (Gimp doesn't scan natively).

---

### Post by Cityscape on 2010-04-09
> **Bucky Ball said:**
> Xsane Image Scanner
That's one I have that is too hard to figure out how to use.
Any easier apps?

---

### Post by akakingess on 2010-04-09
> **Cityscape said:**
> That's one I have that is too hard to figure out how to use.
Any easier apps?

I think that what the other option was should work, if you already have it installed than GIMP should be able to use it (maybe as a plugin or such, not sure) in order to do your scans.

---

### Post by Bucky Ball on 2010-04-11
Like akakingness said, If you have Xsane installed, Cityscape, you might be able to scan through Gimp using it. File->Acquire and Xsane should be there as a selection. Still, if you find that software confusing then this might not be a solution for you. You really don't need to use anything in that program apart from setting your dpi, hitting the preview button, sizing up your scan area then hitting scan and choosing where to save it. It does have a lot of other potential though.

Also, when you say you have installed the drivers for the printer, are you talking the Linux drivers? Specifically HPLip. You should go here:

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

Select your printer (there is no Officejet J6400 but there is the J6405 and others) and follow your nose.

---

### Post by lidex on 2010-04-11
> **Cityscape said:**
> That's one I have that is too hard to figure out how to use.
Any easier apps?

Try simple-scan, it's in the repos:
```
sudo apt-get install simple-scan
```

---

