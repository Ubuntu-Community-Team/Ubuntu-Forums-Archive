---
title: "Flash video stops loading"
date: 2009-11-09
forum: General Help
---

### Post by Nat90 on 2009-11-09
Hello everyone, 

After I upgraded to Karmic (64-bit) I've been having troubles with youtube videos and similar sites.
The video loading bar starts loading really fast as it used to in Jaunty, at a speed that would load a 10 minute video in 5 seconds (as it should according to my internet connection), but when it reached 10%, it stops, and it starts loading really slow, slower than the video itself, sometimes to come to a complete stop by 50%; so I have to leave it loading for 20 minutes and come back, like we did in 2003.

This happens both under Compiz and Metacity, In Firefox 3.5.4 with 'flash non-free' which as I understand, is the same flash downloaded from the adobe site.


If you have a way to work this out I'd appreciate it.

---

### Post by jbrown96 on 2009-11-09
try the 64-bit version of flash. It's a pre-release version. Just google. remove 32-bit flash player ```
sudo apt-get remove flashplugin-nonfree
``` Download the file and extract it. Create a folder in .mozilla (it's hidden) called plugins and move libflashplayer.so into it.

---

### Post by efflandt on 2009-11-09
There is a sticky on the 64-bit forum.  If you have an older Athlon from years ago and 64-bit flash bogs or explodes Firefox, you may also want to see the bit about invalid instruction there.  Apparently my early Athlon64 3200+ does not have lahf, but someone came up with a plugin fix for that.

---

### Post by Nat90 on 2009-11-10
Unfortunately neither solution worked

I have to say though, that flash works "fine" (under metacity); it's just this loading problem, which I don't get, but besides that, it run alright

---

