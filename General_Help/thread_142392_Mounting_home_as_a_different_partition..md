---
title: "Mounting /home/ as a different partition."
date: 2006-03-10
forum: General Help
---

### Post by rikard_grankvist on 2006-03-10
This is probably a trivial question, but I feel I need to ask for directions before I start tinkering with this myself, to avoid data loss.

I dual boot with windows. To share files between the OS's I have a fat32 partition that currently mounts as /media/hda6/. Since I have all my documents and mp3's and stuff in this folder, I thought it might be a good idea to have it be my /home/ folder instead, so I don't have to click around so much when I want to save something I've created in a program (since the open/save dialog always starts at the home folder). How would I do this? I obviously already have some config files and stuff in my home folder (which currently mounts to the linux root partition), that I don't want to lose, so I'm wondering how I'll go about changing the home directory without any data loss.

---

### Post by kaamos on 2006-03-10
It is a bad idea to have your home folder in fat32 since it does not know how to handle permissions. I suggest you instead create a link like
```
ln -s /media/hda6 ~/Documents
```
The Documents folder will show up in all the sidebars and some (most?) open/save dialogs start there if it is present.

---

### Post by rikard_grankvist on 2006-03-10
Thanks! That worked great.

---

