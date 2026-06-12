---
title: "Remove desktop folder from home folder."
date: 2012-05-17
forum: General Help
---

### Post by spiritech on 2012-05-17
hi,

how can i remove, disable or hide the desktop folder (link) from the home folder? i dont need it and it just gets in the way.

spiritech

---

### Post by spiritech on 2012-05-17
better still how can i change its path. so it mounts to my other hard drive.

---

### Post by prshah on 2012-05-17
> **spiritech said:**
> better still how can i change its path. so it mounts to my other hard drive.

You can set any path/directory as your home folder by changing the relevant entry in ~/.config/user-dirs.dirs 

for example, [for Ubuntu 12.04], press Alt+F2 and give the command ```
gedit ~/.config/user-dirs.dirs
```

After changing and saving, you need to logout and back in for changes to take effect.

However, changing in to a non-linux filesystem (Eg, without linux type permissions, such as FAT or NTFS) may cause breakage.

---

### Post by stinkeye on 2012-05-17
If you just want to hide it, create a file called
```
.hidden
```
in your home and folder add **Desktop** to it.

eg my ~/.hidden file.
```
bin
operatransfers
Templates
tmp
Desktop
```

When in nautilus ctrl+h to show hidden.

---

