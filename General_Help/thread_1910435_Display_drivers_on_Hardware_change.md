---
title: "Display drivers on Hardware change"
date: 2012-01-17
forum: General Help
---

### Post by Anakist on 2012-01-17
I had an AMD Fusion e-350 that I couldn't get to play HD video. Had no end of problems with drivers! It just would not use FGLRX instead of vesa.

I have given up for the moment and swapped back to my q6600 / HD4350.

I did have the display working until I tried to remove the FGLRX packages and go back to FOSS drivers as per the Linux Catalyst instructions. Now I get no display at all. Boots through the BIOS, through GRUB, into the Ubuntu loading screen, then blacks out. I can ssh into the machine but not VNC. 

I have reinstalled the catalyst package with no result, then uninstalled it and reinstalled FOSS again with no result.

How do I get the display working?

Thanks.

James

---

### Post by Wayne_V on 2012-01-17
which version of ubuntu are you using?

[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by Anakist on 2012-01-17
Sorry. Oneiric.

James

---

### Post by Wayne_V on 2012-01-17
Try creating a new xorg.conf as described here:

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

If that doesn't work, take a look in /var/log/Xorg.0.log for errors.

If you did apt-get remove instead of purge it might have left old files laying around ....

---

