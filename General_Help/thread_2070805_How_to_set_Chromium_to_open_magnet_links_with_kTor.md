---
title: "How to set Chromium to open magnet links with kTorrent?"
date: 2012-10-13
forum: General Help
---

### Post by BigMoses on 2012-10-13
I tried to set kTorrent as the default app for magnet links and now in gconf the command for magnets is  /usr/bin/ktorrent. However Chromium still opens magnets using Transmission.

Any ideas how I could get it to use kTorrent?

---

### Post by dniMretsaM on 2012-10-13
Did you set all the things listed [here](http://ktorrent.org/wiki/index.php/FAQ#How_do_I_register_the_magnet_protocol_with_Ubuntu.3F)? Also, what version of KTorrent are you using?

---

### Post by BigMoses on 2012-10-14
> **dniMretsaM said:**
> Did you set all the things listed [here](http://ktorrent.org/wiki/index.php/FAQ#How_do_I_register_the_magnet_protocol_with_Ubuntu.3F)? Also, what version of KTorrent are you using?

I set all those things, but it doesn't work. kTorrent 4.1.3.

---

### Post by whatthefunk on 2012-10-14
I dont use Chromium, but you probably have to set the option in Chromium, not Ktorrent.   There should be some sort of file association setting.

---

### Post by BigMoses on 2012-10-16
> **whatthefunk said:**
> I dont use Chromium, but you probably have to set the option in Chromium, not Ktorrent.   There should be some sort of file association setting.

I agree that there should be a file association setting, but I haven't been able to find it.

---

### Post by whatthefunk on 2012-10-16
It might get its setting from the main system settings.  Have you set your system to use ktorrent as the default program to open magnet lnks with?
(Note that it tends to take a minute or so for ktorrent to open a magnet link)

---

