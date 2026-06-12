---
title: "Disable bluetooth at boot"
date: 2011-11-11
forum: General Help
---

### Post by pixmin on 2011-11-11
Hi,

Each time I boot my computer, bluetooth is on and I have to manually disable it. I have found ways to not have the bluetooth icon at boot but that's not what I want. I want to disable bluetooth when the computer boots, and then have the option to turn it on if needed.

Thanks

---

### Post by pr3zident on 2011-11-11
> **pixmin said:**
> Hi,

Each time I boot my computer, bluetooth is on and I have to manually disable it. I have found ways to not have the bluetooth icon at boot but that's not what I want. I want to disable bluetooth when the computer boots, and then have the option to turn it on if needed.

Thanks

try this press alt + f2 and type in gnome-session-properties and look for bluetooth - uncheck it or remove it ....

---

### Post by pixmin on 2011-11-11
Thanks, but that will just prevent the icon to show up in the topbar, bluetooth will still be on in the background, which is not what I want.

---

### Post by pr3zident on 2011-11-11
> **pixmin said:**
> Thanks, but that will just prevent the icon to show up in the topbar, bluetooth will still be on in the background, which is not what I want.

try this:
[http://http://ubuntucomputing.posterous.com/how-to-disable-bluetooth-on-startup-ubuntu-tw]("http://http://ubuntucomputing.posterous.com/how-to-disable-bluetooth-on-startup-ubuntu-tw")

---

### Post by pixmin on 2011-11-11
> **pr3zident said:**
> try this:
[http://http://ubuntucomputing.posterous.com/how-to-disable-bluetooth-on-startup-ubuntu-tw]("http://http://ubuntucomputing.posterous.com/how-to-disable-bluetooth-on-startup-ubuntu-tw")

Woa, this is perfect, thanks a lot!

---

### Post by pr3zident on 2011-11-11
> **pixmin said:**
> Woa, this is perfect, thanks a lot!

np :)

---

### Post by BillyBoa on 2011-11-11
> **pixmin said:**
> Woa, this is perfect, thanks a lot!

Please state as SOLVED the Thread from the Thread Tools

---

### Post by btindie on 2011-11-11
I've found that that method doesn’t always work, it can end up re-enabling itself.

rc.local gets run when the system is booting, as the last thing that's done, but that's usually before the desktop has finished loading and the user has logged in. When the desktop finishes loading it then enables BT. At least that's what I've found from my own experience and have ended up adding the rfkill command to a custom script that I run every time when I log in. PITA but it works. Until they fix this limitation it's always going to be a hack.

---

