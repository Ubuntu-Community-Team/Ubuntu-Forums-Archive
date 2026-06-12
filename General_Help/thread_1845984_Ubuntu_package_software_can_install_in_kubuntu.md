---
title: "Ubuntu package software can install in kubuntu ?"
date: 2011-09-18
forum: General Help
---

### Post by SBMN7 on 2011-09-18
Hello frens, i creat package software using APT on CD from ubuntu. Now i remove ubuntu from my system and i install Kubuntu 10.10 on my system. Now i want to install that package software CD in kubuntu. But i try many times, but i cant besuccess. Please help me, how can i install that APT on CD package collection in kubuntu? Please help me.

---

### Post by psrdotcom on 2011-09-18
Do you know where you have downloaded the package? And I think, which extension of package you have downloaded?

---

### Post by ajgreeny on 2011-09-18
If both OSs were 10.10 version there should be no problem using the ubuntu aptoncd CD, or iso file, if you did not burn a disk, to restore the packages to your new kubuntu installation.

However, I seem to remember having a problem with the restore function of aptoncd in some versions of the *ubuntu family of OSs.  If that is the case you can use the archive manager to extract the aptoncd *.iso file (or the CD if you made one) and then manually copy all the .deb files from the packages folder it contains by navigating to the /packages folder of that extracted archive and using```
sudo cp *.deb /var/cache/apt/archives
``` and then ```
sudo apt-get update
``` to refresh the cache.

---

### Post by SBMN7 on 2011-09-18
Dear friends, file extension is .deb. I backup them from ubuntu 11.04 and i want to install them in kubuntu 10.10 . I try using that command but i cant be success. I already burn them into CD Using APTonCD & also i have their package folder. It can possible friends?

---

### Post by Elfy on 2011-09-18
Thread closed. Please do not post duplicates, it dilutes community effort.

---

