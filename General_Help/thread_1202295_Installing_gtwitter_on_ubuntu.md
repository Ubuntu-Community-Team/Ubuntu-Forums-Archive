---
title: "Installing gtwitter on ubuntu"
date: 2009-07-02
forum: General Help
---

### Post by jestinjoy on 2009-07-02
Hi,
  I am using Ubuntu 9.04. I got the binary from their site. When i tried to execute the file, I got the following error message. Please help.

```
** (./gtwitter.exe:5669): WARNING **: The following assembly referenced from /home/jestinjoy/Desktop/gtwitter/gtwitter.exe could not be loaded:
     Assembly:   gconf-sharp    (assemblyref_index=4)
     Version:    2.16.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/jestinjoy/Desktop/gtwitter/).


** (./gtwitter.exe:5669): WARNING **: Could not load file or assembly 'gconf-sharp, Version=2.16.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'gconf-sharp, Version=2.16.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
File name: "gconf-sharp, Version=2.16.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f"
```

---

### Post by moster on 2009-07-02
You have to install monodevelop to get that working. Go to add/remove and find it. After that you can call it by "mono gtwitter.exe"

You should read before instructions on their home page.

---

### Post by directhex on 2009-07-02
Um... what's wrong with [apt:gtwitter](apt:gtwitter) ?

The problem here is Jaunty shipped with a broken version of GNOME# where ALL components were marked as ABI-broken (i.e. incompatible with earlier versions), rather than the one or two libraries which genuinely broke the ABI.

---

### Post by jestinjoy on 2009-07-02
I cant find anything callled monodevelop in synaptic. Please help

---

### Post by directhex on 2009-07-03
> **jestinjoy said:**
> I cant find anything callled monodevelop in synaptic. Please help

Wait... what? Now I'm UTTERLY confused. If you want MonoDevelop, then you want to click [apt:monodevelop](apt:monodevelop)

But you DON'T want that. gTwitter is already packaged and working in Ubuntu - and the problem with using your download is specifically as I stated - GConf# in Jaunty is version 2.24 and has no compatibility data (policy files) marking it as 2.16-compatible due to a packaging error.

---

