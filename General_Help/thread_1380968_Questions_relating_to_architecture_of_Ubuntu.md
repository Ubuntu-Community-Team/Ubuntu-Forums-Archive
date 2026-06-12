---
title: "Questions relating to architecture of Ubuntu"
date: 2010-01-14
forum: General Help
---

### Post by aeubz on 2010-01-14
Hi, I don't know if the title is appropriate for this discussion but I am trying to figure out a command to know if my ubuntu is 64 or 32 bit.  If it is 32bit can I upgrade to 64bit without reinstalling everything(drivers, programs..)?  And which one is better?

---

### Post by sisco311 on 2010-01-14
```
uname -m
```

i386, i486, i586 or i686 => 32bit
x86_64 => 64bit

---

### Post by aeubz on 2010-01-14
> **sisco311 said:**
> ```
uname -m
```

i386, i486, i586 or i686 => 32bit
x86_64 => 64bit

Thanks, its i686 :(

---

### Post by audiomick on 2010-01-14
Going to 64 bit will mean a re-install. 64bit is apparently faster at some things, and can deal with more than 4GB RAM, if I have understood and remembered everything I have read correctly.

If your system is running and you are happy with everything, you might consider waiting until the next version update before you change.

It might be worth getting the 64bit Live CD to make sure everything really works properly. It should, but knowing is better than believing.

Here is something I haven't tried out.
This firefox add-on
[https://addons.mozilla.org/en-US/firefox/addon/13153/](https://addons.mozilla.org/en-US/firefox/addon/13153/)
might be a help. If I understand things correctly, it will generate a list of installed applications which can be saved. After the new install, the list can be used to install the applications that were installed in the old install. As I said, I haven't tried it, but have a look.

---

### Post by sisco311 on 2010-01-14
If you want to switch to the 64bit version you have to reinstall Ubuntu.

You can save a list of the currently installed packages.

Go to Synaptic -> File menu -> Save Markings As... -> check the *Save full state, not only changes* checkbox and choose a filename and a location.  

To install the packages on the new system, go to Synaptic -> File menu -> Read Markings -> point it at your saved file -> click Apply to start the download and installation of all of those packages you had installed previously.

If you don't have a separate home partition, then backup your home directory. Your home directory contains all your  personal settings (wallpaper, theme, bookmarks ...).

---

### Post by aeubz on 2010-01-14
Thank you audiomick and sisco311 for you help :P

---

### Post by audiomick on 2010-01-14
> **sisco311 said:**
> 
Go to Synaptic -> File menu -> Save Markings As... -> check the *Save full state, not only changes* checkbox and choose a filename and a location.  

To install the packages on the new system, go to Synaptic -> File menu -> Read Markings -> point it at your saved file -> click Apply to start the download and installation of all of those packages you had installed previously.

I think that is effectively what the firefox add-on does

> If you don't have a separate home partition, then backup your home directory. Your home directory contains all your  personal settings (wallpaper, theme, bookmarks ...).

If you don't have a separate /home partition, consider making one if you do re-install. Then you can just re-mount it during a possible future re-install instead of having to save it all and copy it back in.

---

