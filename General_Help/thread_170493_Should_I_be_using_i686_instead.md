---
title: "Should I be using i686 instead?"
date: 2006-05-04
forum: General Help
---

### Post by adrenaline on 2006-05-04
Hello!  I've been running Ubuntu for a couple months now and I just noticed after going to [http://www.mozilla.com/firefox/]("http://www.mozilla.com/firefox/") that in the download box it recognizes that I should download the i686 version.  Does this mean I should be running the i686 kernel instead of the default 386?  Thanks!

---

### Post by Qrk on 2006-05-04
You certainly can run the i686 kernel, but it isn't a big deal either way. To get the 686 kernel, just install the package "linux-i686" in synaptic.

---

### Post by adrenaline on 2006-05-04
Thanks!  I actually installed k7 instead since I'm running on an AMD Athlon.  Not sure there's a difference but it's nice to think there's one.

---

### Post by Rory on 2006-05-04
I moved to the k7 kernel and I found it made an improvement.  

You may also want to look at the version of Firefox that's optimized for AMD processors.  

Here are the basics:
SWIFTFOX
Firefox optimized for Linux and AMD: [http://getswiftfox.com/](http://getswiftfox.com/)
test how fast it renders pages here: [http://scragz.com/tech/mozilla/test-rendering-time](http://scragz.com/tech/mozilla/test-rendering-time)
Ubuntuforums install tips: [http://www.ubuntuforums.org/showthread.php?t=142798](http://www.ubuntuforums.org/showthread.php?t=142798)

commands:
1) extract to folder.
2) In terminal, cd to folder where firefox.sh resides.
3) attach plugins to this version (note: you must have the original ubuntu version of Firefox installed first, so the plugins can be drawn from somewhere.
4) right-click your Firefox kicker icon and browse to the new firefox.sh

rory@ubuntu:~$ cd /home/rory/downloads/swiftfox/swiftfox152/plugins/
rory@ubuntu:sudo ln -s /usr/lib/mozilla-firefox/plugins/* .


Again, noticeable differences but not huge.  But, if you upgrade your kernel, get swiftfox, etc, combined, you'll begin to feel a difference.

R.

---

### Post by adrenaline on 2006-05-04
Wow, thanks Rory!  I'll certainly look into it! :)

---

