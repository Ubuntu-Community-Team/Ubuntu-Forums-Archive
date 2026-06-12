---
title: "Can't Install Bin File in 9.10"
date: 2009-11-22
forum: General Help
---

### Post by tracyandskye on 2009-11-22
I was running some OpenBravo POS in 8.10 & now I'm trying to install it in another machine running 9.10, but I'm getting an error.  As far as I can tell, I'm installing it exactly the same as before.  Here is what's in my terminal window:

voodoo@voodoo-desktop:~$ sudo chmod +X openbravopos-2.30-linux-installer.bin
chmod: cannot access `openbravopos-2.30-linux-installer.bin': No such file or directory
voodoo@voodoo-desktop:~$ cd Desktop
voodoo@voodoo-desktop:~/Desktop$ sudo chmod +X openbravopos-2.30-linux-installer.bin
voodoo@voodoo-desktop:~/Desktop$ sudo ./openbravopos-2.30-linux-installer.bin 
sudo: ./openbravopos-2.30-linux-installer.bin: command not found
voodoo@voodoo-desktop:~/Desktop$ ls
Installing bin files.odt  OpenBravo POS  openbravopos-2.30-linux-installer.bin
voodoo@voodoo-desktop:~/Desktop$

---

### Post by Prodigal Son on 2009-11-22
```
ls -l $HOME/Desktop | grep bin 
```

Can you show us the output ?

---

### Post by tracyandskye on 2009-11-22
voodoo@voodoo-desktop:~$ ls -l $HOME/Desktop | grep bin
-rw-r--r-- 1 voodoo voodoo    14790 2009-11-14 11:37 Installing bin files.odt
-rw-r--r-- 1 voodoo voodoo 20748504 2009-11-22 12:17 openbravopos-2.30-linux-installer.bin
voodoo@voodoo-desktop:~$

---

### Post by Prodigal Son on 2009-11-23
> **tracyandskye said:**
> voodoo@voodoo-desktop:~$ ls -l $HOME/Desktop | grep bin
-rw-r--r-- 1 voodoo voodoo    14790 2009-11-14 11:37 Installing bin files.odt
-rw-r--r-- 1 voodoo voodoo 20748504 2009-11-22 12:17 openbravopos-2.30-linux-installer.bin
voodoo@voodoo-desktop:~$

```
sudo chmod +x $HOME/Desktop/openbravopos-2.30-linux-installer.bin && $HOME/Desktop/openbravopos-2.30-linux-installer.bin
```

---

### Post by tracyandskye on 2009-11-23
I needed to run the 2nd command with sudo but it worked.  Thanks!  So the desktop folder has always been under home right?  Why was I able to do this in 8.10 & not 9.10?  Is there something different with my install?

---

