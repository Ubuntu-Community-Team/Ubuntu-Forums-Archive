---
title: "firefox 4 takes forever to load initially?"
date: 2011-05-23
forum: General Help
---

### Post by rebeltaz on 2011-05-23
When I start Firefox 4 on my Ubuntu 10.4 laptop, it takes about a minute for Firefox to actually load and display itself. Does/has anyone else had this problem? Is there anything that I can do about it? Thanks...

---

### Post by linuxinstalledfromhdd on 2011-05-23
Have you tried to install Bleachbit and clean out all your caches with it yet?

sudo apt-get install bleachbit

sudo bleachbit

---

### Post by Andrew.Z on 2011-05-24
Vacuuming is the part of BleachBit is the most likely to speed up Firefox.  Another option is disabling Firefox extensions.  A third option is diagnostic: temporarily disable the Firefox profile with a command like (assuming Firefox is closed!)
```
mv ~/.mozilla ~/.mozilla.disabled
```

---

### Post by rebeltaz on 2011-05-24
Thank you both. I will try BleachBit, but if that doesn't work, what does disabling the profile tell me? Assuming that that speeds things up.

---

### Post by wildmanne39 on 2011-05-25
> **rebeltaz said:**
> When I start Firefox 4 on my Ubuntu 10.4 laptop, it takes about a minute for Firefox to actually load and display itself. Does/has anyone else had this problem? Is there anything that I can do about it? Thanks...
Hi, also you could add it to your start up applications it will take a little longer to boot but then it should open faster, but it sounds like it needs the cache cleared and maybe to many add ons.

---

### Post by lovinglinux on 2011-05-25
Most likely that your databases are not optimized or you have a problematic add-on. 

See [http://www.webgapps.org/tutorials/firefox/troubleshooting/startup-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/startup-issues-and-solutions)

---

### Post by rebeltaz on 2011-11-27
I actually renamed the profile and then copied it back to the original name. I guess in the process of copying the files, whatever was screwed up was fixed. Thanks...

---

