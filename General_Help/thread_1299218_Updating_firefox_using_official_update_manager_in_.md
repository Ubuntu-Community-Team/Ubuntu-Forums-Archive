---
title: "Updating firefox using official update manager in ubuntu?"
date: 2009-10-23
forum: General Help
---

### Post by errormessage on 2009-10-23
Hi, is it possible to update firefox to 3.0 to 3.5 in the update manager? Ive done "Search for updates" but it never finds firefox 3.5. Firefox 3.5 is much better and faster than 3.0 and I would like to use it instead of 3.0.
Thanks!

---

### Post by mikewhatever on 2009-10-23
No, FF3.5 is not offered as an automatic update. You can install it manually from Synaptic or with the command below.

```
sudo apt-get install firefox-3.5.
```

---

### Post by P4man on 2009-10-23
enable backports (and find out why you need to):
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by jbrown96 on 2009-10-23
Since firefox-3.5 isn't fully supported, launching it is kind of weird. In apps-->internet-->shiretoko is firefox-3.5 You can fix the quick launch button on your top bar (or desktop if you made one). Right click on the icon and go to properties. In the command section it should say ```
firefox %u
``` change that to ```
firefox-3.5 %u
```

---

### Post by lovinglinux on 2009-10-23
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm.

---

