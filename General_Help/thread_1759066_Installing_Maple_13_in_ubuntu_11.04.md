---
title: "Installing Maple 13 in ubuntu 11.04"
date: 2011-05-15
forum: General Help
---

### Post by samMD on 2011-05-15
Hi So I finally migrated to ubuntu because I was fed up with windows and felt whatever I needed ubuntu provided..I even got ms office running so I have stable foundation to stay with ubuntu.

Now I guess I need to know how to install Maple 13 if it is possible..I know I need to have Wine..thats about it

Thanks Ubuntu Community !

---

### Post by samMD on 2011-05-15
I have a bin file for x86 and a rar file there is a picture attached in this post..how would I install this?

---

### Post by iFargle on 2011-05-27
The general command is
$ chmod +x file.bin
./file.bin

If you're on 32-bit

cd ~/Downloads
chmod +x Maple13Linux32Installer.bin
./Maple13Linux32Installer.bin

If you're on 64-bit

cd ~/Downloads
chmod +x Maple13LinuxX86_64Installer.bin
./Maple13LinuxX86_64Installer.bin

The .rar archives contain information on what to do with the files inside the .rar archive.

---

