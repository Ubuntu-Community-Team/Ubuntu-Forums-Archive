---
title: "keeping windows drive mounted"
date: 2006-05-21
forum: General Help
---

### Post by LORD_PoLvO on 2006-05-21
hello i am able to get my winodws drive mounted buit it unmounts when it shuts down and i have to mount again manually this is what i have done.

```
sudo mkdir /media/windows
```

then

```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o iocharset=utf8,umask=000
```


does anyone know the code to add next to keep th dirve permanently mounted so i dont have to keep doing it manually?

---

### Post by Ramses de Norre on 2006-05-21
sudo gedit /etc/fstab

add a line ```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

```
Then do sudo mount -a.

Everything in fstab is mounted at start up.

---

### Post by LORD_PoLvO on 2006-05-21
ok kool ty

---

