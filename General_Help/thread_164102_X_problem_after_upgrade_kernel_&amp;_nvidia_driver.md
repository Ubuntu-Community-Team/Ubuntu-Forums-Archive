---
title: "X problem after upgrade kernel &amp; nvidia driver"
date: 2006-04-22
forum: General Help
---

### Post by vinboy on 2006-04-22
I just upgraded my kernel to 2.6.16.7 and nvidia driver from nvidia website.
After installation, reboot and I was not able to see any GUI.
when i use the console to startx, i see the screen brighten alittle but showing no image at all.

- my Xorg.0.log end with the following:
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
---------------------------------------------------

I suppose there is no error as far as the log shows, but it just stop loading when it reach the GLX part, usually it will continue to load keyboard etc.

I was able to normally startx to KDE after commenting out the GLX extension.
](*,)

---

### Post by PriceChild on 2006-04-22
Ok... i think that when it crashes to console, you need to log in, then navigate to the nvidia driver install script. Run it, then restart GDM or KDM.

That should work... took me a while to sort it out for myself too :)

Pricey

---

### Post by reign on 2006-05-15
I'm having the same problem with my nvidia drivers. If I comment out GLX in xorg.conf it works fine. Once I install the drivers and restart KDM it works fine. It only goes bad once I restart the computer, then X will only load with glx commented out until I reinstall the drivers from nvidia's website. I've been pulling my hair out about this problem for  quite some time.

---

### Post by KillrBuckeye on 2006-05-15
Try running one of tseliot's scripts.  I was having the same reboot problem where I had to reinstall the drivers every time to start X.  The script fixed the problem, but I'm not sure why.  :)

[http://ubuntuforums.org/showthread.php?t=75074]("http://ubuntuforums.org/showthread.php?t=75074")

---

