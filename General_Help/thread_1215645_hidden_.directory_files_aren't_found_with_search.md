---
title: "hidden .directory files aren't found with search"
date: 2009-07-17
forum: General Help
---

### Post by rsmseys on 2009-07-17
I have a whole bunch of folders that used to be filled with music... but now the music has been moved and all that is left is these .directory files in the folders. When I view hidden files in nautilus I can see the file, and it's contents is something to do with amarok.

```

[Desktop Entry]
Icon=/home/ryan/.kde/share/apps/amarok/albumcovers/cache/130@e55f9553b8c87249c9eb1a0b9d559261

```But when I go to search for them all by searching for ".directory" (without quotes) it returns 0 items. Also when I run the command ls in the folder that obviously has it, nothing is returned.

ls -a returns . .. .directory (in green text)

How can I search for these .directory files and delete them all from these empty folders?

---

### Post by kidders on 2009-07-18
Hi there,

So you want to keep the folders, but delete the .directory files?

```
find /path/to/start/at -name .directory -exec rm {} \;
```

---

