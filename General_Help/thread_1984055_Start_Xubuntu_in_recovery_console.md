---
title: "Start Xubuntu in recovery console"
date: 2012-05-21
forum: General Help
---

### Post by FormatSeize on 2012-05-21
It's not the fact that GNU/Linux is *obvious* to people. It's not even the fact that they may have to Google to find what they are looking for. It's the ***sheer amount*** of Googling that can lead to nowhere.
 
Simple question: How do I start Xubuntu 12.04 in the recovery console instead of my normal login screen? I tried pressing ESC, and Shift. Neither of them worked. Searching around only lead to things about people wanting to recover a busted system, and further down the list were irrelevant things.
 
 
Thanks,
FS

---

### Post by bryncoles on 2012-05-21
As far as I know, it's because of a stupid decision to hide grub during boot.  The only way I know is to edit the file ```
/etc/default/grub.
```

Find the line which reads ```
GRUB_HIDDEN_TIMEOUT=0
```and perhaps the line ```
GRUB_TIMEOUT=
``` and change them to 

```
#GRUB_HIDDEN_TIMEOUT=0
GRUB_TIMEOUT=5
```

Then run ```
 sudo update-grub
``` in a terminal.  It should now show grub when you boot your system, thus allowing you to select recovery mode.

---

### Post by black veils on 2012-05-21
pressing and *holding* shift will bring up the grub screen, with recovery option, or that is the case of 11.10.

---

### Post by FormatSeize on 2012-05-21
Thanks,  bryncoles. That worked.

---

### Post by bryncoles on 2012-05-22
happy to be of service!

---

