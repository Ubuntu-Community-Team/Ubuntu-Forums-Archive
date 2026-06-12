---
title: "32-bit VLC in 11.04 64-bit Ubuntu"
date: 2011-06-28
forum: General Help
---

### Post by steevven1 on 2011-06-28
How can I uninstall the 64-bit version and install the 32-bit version of VLC Media Player in Ubuntu 11.04 64-bit edition? I would prefer to use apt-get or aptitude commands to do this, Synaptic would be fine too I suppose. Last resort would be installing from a .deb file or compiling source.

I've had a lot of trouble with the 64-bit version of VLC that I never had with the 32-bit version.

Thanks!

---

### Post by FormatSeize on 2011-06-28
```
sudo apt-get remove --purge [whatever VLC's package name is]
```
Then you can go to the repositories and get the 32-bit version. You can get it through the Software Center if you like. 
 
I'm not sure whether or not it will work under Linux, but I don't see why it wouldn't. I have a 32-bit machine, so there's no way for me to try it. But if it doesn't work, you can always just remove it.

---

### Post by steevven1 on 2011-06-28
Thanks for the reply. You say "go to the repositories and get the 32-bit version." What does that mean? I'm not sure how to do this. I opened Synaptic and searched for VLC, but there isn't specifically a 32-bit version there...Thanks.

---

### Post by oldos2er on 2011-06-28
[http://packages.ubuntu.com/natty/vlc](http://packages.ubuntu.com/natty/vlc)

Scroll down to the bottom of the page, select i386. I imagine you'll need to get i386 versions of vlc's dependencies too.

---

