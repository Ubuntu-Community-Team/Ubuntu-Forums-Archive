---
title: "Cannot uninstall google-chrome-unstable"
date: 2010-03-02
forum: General Help
---

### Post by Guitardude182 on 2010-03-02
Hey all,

So yeah something done gone and got screwed up on my Ubuntu install. I got package updates one day and gdm wouldn't boot up, I fixed that, but then come to find that google chrome went missing, the icon was on my menu but it was dead, firefox icon was missing also.

I've tried the command line way of uninstalling it and doing so from within synaptic and both yield ill results. It simple responds 
```
"E: google-chrome-unstable: cannot remove file "/opt/google/chrome/product_logo_48.png".
```
I can't even find this directory or file upon searching for it. This wouldn't be a problem if I just could mark the package for re-installation, but will only allow me to mark it for complete removal or unmark it, which actually doesn't unmark it at all, still tries to remove it and thus I can't install firefox because it won't uninstall chrome, so I'm stuck without a web browser on my ubuntu :frown:

Any help is greatly appreciated.

---

### Post by bobcollard on 2010-03-02
> **Guitardude182 said:**
> 

I've tried the command line way of uninstalling it and doing so from within synaptic and both yield ill results. It simple responds 
```
"E: google-chrome-unstable: cannot remove file "/opt/google/chrome/product_logo_48.png".
```I can't even find this directory or file upon searching for it. This wouldn't be a problem if I just could mark the package for re-installation, but will only allow me to mark it for complete removal or unmark it, which actually doesn't unmark it at all, still tries to remove it and thus I can't install firefox because it won't uninstall chrome, so I'm stuck without a web browser on my ubuntu :frown:

Any help is greatly appreciated.
Use Synaptic Package Manager and "completely remove"  Then install Firefox there.  Sounds like Terminal cannot find the icon you want uninstalled at the address you are looking for it.

---

### Post by Guitardude182 on 2010-03-02
Both terminal and synaptic package manager give me the same error. And because of this I can't completely remove it. I'd actually like to reinstall chrome, but can't since it only lets me choose complete removal or unmark, which it won't remove and it won't unmark.

---

### Post by RMZindorf on 2010-03-02
This is how Google will take over the world, don't you know? However, I would either make sure you still have firefox installed before you remove Chrome. I know its fairly new to the linux platform, but I haven't had any issues with it.

---

### Post by wojox on 2010-03-02
If it's in /opt why don't you just delete the /google directory?

---

### Post by Guitardude182 on 2010-03-02
Because it's not there. There is no trace of google on my linux partition. And Firefox disappeared too. So I have no browser. Good thing I dual boot with Windows 7.



[EDIT]
Just wanted to say I solved my problem. Since it was looking for the /opt/google/chrome directory to uninstall "product_logo_48.png" but it didn't exist. I just made a /opt/google/chrome directory and then added some fony files that should have been installed with chrome including the png file that was showing up in the error. This finally allowed for a successful removal of chrome. However, I find it odd that "product_logo_48.png" caused it to keep from uninstall, all for a logo icon, but it didn't raise a hair for all the other files I didn't feel like adding to my fake directory.

---

