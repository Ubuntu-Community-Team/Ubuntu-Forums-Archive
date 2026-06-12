---
title: "Trouble opening files."
date: 2009-08-01
forum: General Help
---

### Post by jjgall on 2009-08-01
Hi. I`m new to Ubuntu and am asking if anyone knows how to open a .bin file in 9.04. Thanks.

---

### Post by MelDJ on 2009-08-01
i dont't think you can open a bin file

---

### Post by fraser_m on 2009-08-01
What's the name of the file, and what's it for?

---

### Post by jjgall on 2009-08-01
The file is emusiclim-linux-installer.bin and it is a download manager for e-music.

---

### Post by credobyte on 2009-08-01
Try:
```
sudo chmod 755 /path/file.bin
sudo /path/file.bin

```

---

### Post by wojox on 2009-08-01
```
chmod +x file.bin 
```

```
./file.bin
```

---

### Post by jjgall on 2009-08-01
I am being told no such file exists.

---

### Post by lisati on 2009-08-01
> **jjgall said:**
> I am being told no such file exists.

Make sure you're in the correct directory. If you downloaded it to your desktop, type this in first:
```
cd ~/Desktop
```

---

### Post by jjgall on 2009-08-01
Thanks guys. I downloaded a .tar file from the same site and have  managed to open this. Will see how I get on. Ta.

---

