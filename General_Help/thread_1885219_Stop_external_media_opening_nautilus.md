---
title: "Stop external media opening nautilus"
date: 2011-11-22
forum: General Help
---

### Post by CaptainMark on 2011-11-22
Since the change to 11.10 i cant find the option to stop nautilus opening when i plug in an external hdd, im sure it used to be in nautilus preferences, in system settings> removable media you can set it not to open any programs when media is inserted but i still want cd's to open banshee etc,

---

### Post by deonis on 2011-11-22
It's now in settings->removable media

cheers

---

### Post by CaptainMark on 2011-11-24
thats where im looking for it

---

### Post by deonis on 2011-11-24
Hi, I am not talking about nautilus preferences I am taking about System Settings

---

### Post by CaptainMark on 2011-11-24
yes this is where im looking you got the 5 options for cd, dvd, music player, photos and software, none of these stops nautilus opening when i plug in a hdd only the bottom option of "Never prompt or start programs on media insertion" but like i said this it too much and will stop all the functions working too, there must be the right option somewhere

---

### Post by deonis on 2011-11-24
my bad did not see it

---

### Post by CaptainMark on 2011-11-24
just re-read my first reply, sorry it was not meant to sound rude, probably seemed it though,

---

### Post by kleingeist on 2011-11-30
i had the same problem and couldn't find a setting anywhere.
after some scanning through the registry ewww i mean sorry forgot that they called it dconf i found 
/org/gnome/desktop/media-handling/automount-open and set it to false. 
(open dconf-editor and find the key or type "dconf write /org/gnome/desktop/media-handling/automount-open false" in a terminal)

Now Nautilus stays put when i insert an usb drive. More specialized "media" (like my telephone) are still prompting for action, but i actually like it for them.

---

