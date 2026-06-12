---
title: "Can't Install RAR Archive"
date: 2011-02-17
forum: General Help
---

### Post by rf.bennett1 on 2011-02-17
I'm trying to extract an RAR file which has my stuff on it from university, they use Windows Vista Ultimate so i thought i would be safe when saving my work to my flash drive. So i saved my work with the program winzip. when i got home i put in my flash drive and asked Kubuntu to extract only to find i don't have a RAR program to extract so i asked to install one via the Kpackage Manager and everything seemed fine so i asked it to extract again and said cannot extract unknown file. so i went through the terminal to install again and to make sure they were no bits of the install missing and i got this.

robert@HP-COMPAQ-LINUX-KDE:~$ sudo apt-get install unrar-nonfree
[sudo] password for robert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'unrar-nonfree' has no installation candidate
robert@HP-COMPAQ-LINUX-KDE:~$



Is there any other way of extracting my work as i need to get my essay open and finnish it before monday. Also why is it saying that the package is missing? and what is the other source? Is there a way to decrypt this RAR file that vista has made?

Also one more thing once ive managed to decrypt and extract my work what is the reccomended format to between vista and kubuntu so i wont get anymore issues?

Thanx for reading and anyhelp would be awesome :)

---

### Post by mikewhatever on 2011-02-17
The package name is **unrar**, and there is also unrar-free.

---

### Post by Habitual on 2011-02-18
Description: Unarchiver for .rar files (non-free version)
 Unrar can extract files from .rar archives. If you want to create .rar
 archives, install package rar.

```
sudo apt-get install -y unrar
```

---

### Post by oldos2er on 2011-02-18
unrar-free is in the universe repo. If you're sure it's enabled, you may need to run **sudo apt-get update**

---

### Post by spcwingo on 2011-02-18
If you're having problems with unrar I think "p7zip-full" will also handle rar archives.  From that package's description in Synaptic:

> not only does it handle 7z but also ZIP, Zip64, CAB, [COLOR="Red"]RAR[/COLOR], ARJ, GZIP, BZIP2, TAR, CPIO, RPM, ISO and DEB archives. 7z compression is 30-50% better than ZIP compression.

---

