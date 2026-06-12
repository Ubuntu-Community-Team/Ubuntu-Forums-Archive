---
title: "Applying folder permissions at startup?"
date: 2006-01-21
forum: General Help
---

### Post by Protex on 2006-01-21
Hey there guys, I've restricted a folder to be viewed by root only, but I have to redo the permissions through Nautilus every time I boot up, is there a way I can set these permissions to load automatically?

---

### Post by aysiu on 2006-01-21
How about changing ownership instead of permissions?
Just do a ```
sudo chown -R root:root /folder_name
sudo chmod -R 700 /folder_name
```

---

### Post by Protex on 2006-01-21
[QUOTE=aysiu]How about changing ownership instead of permissions?
Just do a ```
sudo chown -R root:root /folder_name
sudo chmod -R 700 /folder_name
```[/QUOTE]

I tried that, and it worked, but only for that session. I rebooted and the folder was open again.

---

### Post by aysiu on 2006-01-21
[QUOTE=Protex]I tried that, and it worked, but only for that session. I rebooted and the folder was open again.[/QUOTE] Is this folder on a Windows partition by chance...?

---

### Post by Protex on 2006-01-21
[QUOTE=aysiu]Is this folder on a Windows partition by chance...?[/QUOTE]

Well I don't have windows installed on my PC, but that is a FAT32 partition, yes.

---

### Post by aysiu on 2006-01-21
[QUOTE=Protex]Well I don't have windows installed on my PC, but that is a FAT32 partition, yes.[/QUOTE] FAT32 doesn't support permissions. Reformat it as something else, then, especially since you don't have Windows installed on your PC.

---

