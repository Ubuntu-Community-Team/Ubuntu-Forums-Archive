---
title: "How to tell if your system is SDA or HDA"
date: 2011-09-01
forum: General Help
---

### Post by Da_Bomb_Digity on 2011-09-01
Hey guys, I need to know if my system is SDA or HDA...I don't know how to tell and I need to know. Thanks in advance!

---

### Post by pastalavista on 2011-09-01
Open a terminal (Ctrl+Alt+T) and enter ```
sudo fdisk -l
``` That's a lowercase L ...or just copy/paste this text into terminal then enter your password (it won't show on the screen) then 'enter'

---

### Post by elliotn on 2011-09-01
you can use Disk Utility also its a GUI that list all your drives etc

---

### Post by oldfred on 2011-09-02
With Ubuntu all drives for at least a couple of years are sdX. They combined the drivers into one so all devices IDE/PATA or SATA are sdX devices.

Some other distributions still use hda as the drive designation.

---

