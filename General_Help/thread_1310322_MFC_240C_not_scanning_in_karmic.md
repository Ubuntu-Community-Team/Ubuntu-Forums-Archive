---
title: "MFC 240C not scanning in karmic"
date: 2009-11-01
forum: General Help
---

### Post by Ruhani04 on 2009-11-01
I upgraded today from jaunty to karmic which was my first upgrade without a new install.
It worked well with some problems, however. Sound didn't work but got that fixed.
My brother MFC 240C prints and scans if I use sudo xsane. But I would like to use xsane without sudo. I tried to change the udev rules for usb from 0664 to 0666 and also followed the following advice [http://art.ubuntuforums.org/showthread.php?p=7924949](http://art.ubuntuforums.org/showthread.php?p=7924949).
Both did not work. So far as I understand it is a permission problem since xsane finds the scanner when started with sudo. It would be appreciated if somebody could point me in the right direction. Not sure what happened in karmic that it still blocks access to the scanner without sudo.:confused:

---

### Post by Ruhani04 on 2009-11-02
Ok, problem solved. As expected it is a permission problem which seems to reoccur with every new ubuntu version. I found the solution here:
[http://ubuntuforums.org/showpost.php?p=3830897&postcount=5](http://ubuntuforums.org/showpost.php?p=3830897&postcount=5)

sudo chmod 666 /dev/bus/usb/(bus nr)/(device nr) changes access permissions and xsane works fine. Unfortunately this benefit disappears after reboot.
So I went back to /lib/udev/rules.d/50-udev-default.rules and also changed the 660 to 666 in the last line of the printer rules. And this seemed to do the trick on a permanent basis.:D

---

