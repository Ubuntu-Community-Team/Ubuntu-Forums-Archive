---
title: "How to install 64-bit flashplayer"
date: 2011-01-12
forum: General Help
---

### Post by Bowserdog on 2011-01-12
After considerable effort, I decided to try and prove how ignorant I REALLY am.  I run 64-bit Ubuntu 10.10, and  this time  when I wiped & reinstalled the system, I cannot figure how to install the Adobe Beta 10.2 flashplayer for 64-bit systems.  I spent a long time poking around on the Adobe web site and finally managed to download flashplayer10_2_p3_64bit_linux_111710.tar.gz, which is what I need, as far as I can tell.  So of course I must have left my mind laying down SOMEWHERE, because I cannot figure out how to install it.  I don't know how to make Synaptic find it or even look for it.  Trying to open it and extract with Archive Manager seems to accomplish nothing I can recognize.  So how DOES one install a programXYZ.tar.gz under Ubuntu 10.10?  If anyone could help me become even a little bit less ignorant here, I will gladly promise my **eternal** gratitude for at least *the rest of this whole month*!

-Rich B.

---

### Post by lovinglinux on 2011-01-12
Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it. It will detect installed flash plugins, remove them and install the 64bit by default. The extension also checks for flash 64bit beta updates once a day, so you can keep your plugin updated.

---

### Post by veggen on 2011-01-12
> **lovinglinux said:**
> Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it. It will detect installed flash plugins, remove them and install the 64bit by default. The extension also checks for flash 64bit beta updates once a day, so you can keep your plugin updated.
Wow! I didn't know Firefox plugins can do that! :o

@OP
For the record, [this](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html) is how you install from sources.

---

### Post by lovinglinux on 2011-01-12
> **veggen said:**
> Wow! I didn't know Firefox plugins can do that! :o

Is not a plugin, is an extension that basically generates a shell script according to your system info. The script is what actually removes and install the flash plugin.

---

### Post by dwaindibbley on 2011-02-11
10.3 Wow!     

File: libflashplayer.so
Version: 
Shockwave Flash 10.3 d162

---

