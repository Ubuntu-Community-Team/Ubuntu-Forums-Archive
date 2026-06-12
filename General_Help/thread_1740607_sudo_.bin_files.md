---
title: "sudo .bin files"
date: 2011-04-27
forum: General Help
---

### Post by j-peg on 2011-04-27
Hey i have earlier used .bin files and not have a problem with it but now it tells me that i don't have permission, and it doesn't work when i use sudo o0

```
jpeg@masterbate:~/Desktop/untitled folder$ ./Maple14Linux32Installer.bin
bash: ./Maple14Linux32Installer.bin: Permission denied
jpeg@masterbate:~/Desktop/untitled folder$ sudo ./Maple14Linux32Installer.bin
sudo: ./Maple14Linux32Installer.bin: command not found
```
What can i do?

---

### Post by Vaphell on 2011-04-27
```
chmod +x Maple14Linux32Installer.bin
```

---

