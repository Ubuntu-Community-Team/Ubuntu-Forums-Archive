---
title: "After startup, no taskbar or menus"
date: 2010-01-18
forum: General Help
---

### Post by Colonel Forbin on 2010-01-18
On my desktop, running 9.10 64 bit, when I start up, I get the error message
"cannot update ICEauthoriy /home/local" and after I hit ok to go beyond that, my taskbar and menus flash, then disappear. I get to my desktop, but have no functionality. I installed klamav yesterday, and got this on my next startup. Is there any way to save my installation, and not have to re-install the O/S. I'm pretty much a noob.

Thanks

---

### Post by Colonel Forbin on 2010-01-18
bump

---

### Post by ankspo71 on 2010-01-18
Hi,
I don't know if this will work or not, but can you try pressing Ctrl+Alt+F2, then log into the terminal screen, and type...
```
sudo apt-get remove klamav && sudo apt-get autoremove
```
It will ask you for your username and password.
The above command will uninstall klamav and other the files that got installed with it

Next you need to reboot.
```
sudo reboot
```

This might or might not help, but I think it's worth trying to remove klamav to try to get a working desktop back. Klamav is a little more suited for the Kubuntu, but clamtk is more suited for Ubuntu.
Let us know what happens.

---

### Post by Colonel Forbin on 2010-01-18
That didn't work. I also removed clamav which I had installed yesterday. The system is now back to what it was last time it worked. Don't know the next thing to try.

---

### Post by ankspo71 on 2010-01-18
Hi. Try this link...
[http://ubuntuforums.org/showthread.php?t=1382554](http://ubuntuforums.org/showthread.php?t=1382554)
Someone there found a solution.
Hope it helps.

---

### Post by Colonel Forbin on 2010-01-18
was able to use that to get to a desktop where my taskbar flashes, and I can't start any programs. any ideas?

---

### Post by Colonel Forbin on 2010-01-19
bump

---

