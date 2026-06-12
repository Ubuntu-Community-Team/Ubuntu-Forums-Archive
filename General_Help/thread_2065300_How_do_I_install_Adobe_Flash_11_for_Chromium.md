---
title: "How do I install Adobe Flash 11 for Chromium?"
date: 2012-10-01
forum: General Help
---

### Post by Eirreann on 2012-10-01
I was trying to watch a video on PBS.org, but it wouldn't load because apparently my Chromium web browser doesn't have Flash 11.  When I followed the link it gave me to download flash, it downloads as either a YUM file, a .tar.gz file, or a .rpm file, none of which I have any idea how to use (they don't run like an executable file or anything!)
So how do I install Adobe Flash Player 11 for Chromium?  Oh, it's not on Firefox either, and I don't know how to install it for there, either...

---

### Post by Frogs Hair on 2012-10-01
I get the same message from Opera which uses the flash player from the repository, but the flash version provided with Chrome works fine. 

This is odd because Youtube runs fine in Opera. This is one reason I installed Chrome, but didn't expect a problem so soon.

---

### Post by Frogs Hair on 2012-10-01
The flash version PBS is requesting is what is installed according to the synaptic package manger. I have disabled my script blocking extensions in Opera and restarted with the same result. :confused:

---

### Post by TheMophead on 2012-10-01
> **Eirreann said:**
> I was trying to watch a video on PBS.org, but it wouldn't load because apparently my Chromium web browser doesn't have Flash 11.  When I followed the link it gave me to download flash, it downloads as either a YUM file, a .tar.gz file, or a .rpm file, none of which I have any idea how to use (they don't run like an executable file or anything!)
So how do I install Adobe Flash Player 11 for Chromium?  Oh, it's not on Firefox either, and I don't know how to install it for there, either...
Installing Flash Player for Firefox is easy, just type
```
sudo apt-get install flashplugin-nonfree
```However installing it for Chromium is a bit more involved.

copy libflashplayer.so file into /usr/lib/chromium-browser/plugins directory
```
sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/chromium-browser/plugins
```Restart Chromium if you had it open and test it out on a site such as YouTube etc or whatever your intentional site was.

Hope this helps!

---

### Post by haresear on 2012-10-01
> **Eirreann said:**
> I was trying to watch a video on PBS.org, but it wouldn't load because apparently my Chromium web browser doesn't have Flash 11.  When I followed the link it gave me to download flash, it downloads as either a YUM file, a .tar.gz file, or a .rpm file, none of which I have any idea how to use (they don't run like an executable file or anything!)
So how do I install Adobe Flash Player 11 for Chromium?  Oh, it's not on Firefox either, and I don't know how to install it for there, either...
If you download and extract the .tar.gz file, you should find a readme text file that tells you how to install. It is just a matter of copying the flash files to the appropriate places.

---

### Post by Eirreann on 2012-10-01
> **haresear said:**
> If you download and extract the .tar.gz file, you should find a readme text file that tells you how to install. It is just a matter of copying the flash files to the appropriate places.

Ah, that explains a lot, thanks!

@TheMophead:  Thank you, too!  Your advice was incredibly successful!

---

