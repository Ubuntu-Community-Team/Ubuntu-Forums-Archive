---
title: "kubuntu 9.10 64bit with wubi"
date: 2009-11-05
forum: General Help
---

### Post by wirate on 2009-11-05
i downloaded kubuntu-9.10 desktop amd64 image. then i extracted it and ran the wubi.exe inside. when choose kubuntu, enter the required information and click install, it starts downloading a kubuntu-9.10 desktop i386. the downloaded iso is placed in the same folder as wubi.exe.

any help?

---

### Post by dcstar on 2009-11-06
> **waqar said:**
> i downloaded kubuntu-9.10 desktop amd64 image. then i extracted it and ran the wubi.exe inside. when choose kubuntu, enter the required information and click install, it starts downloading a kubuntu-9.10 desktop i386. the downloaded iso is placed in the same folder as wubi.exe.

any help?

Are you sure you have 64-bit hardware?

---

### Post by wirate on 2009-11-06
yeah. I use 64-bit Windows 7. anyway, i found a workaround for my previous problem over the internet. now wubi installs from the downloaded image but when i reboot, kubuntu behaves as a live cd with an "Install Kubuntu 9.10" icon on the desktop. when i run it, it only shows my actual partitions to choose for the installatio. i think wubi creates something like a virtual partition to install on. that was the case with ubuntu 9.04.

and if this is how its meant to be, whats the difference between wubi and booting from a burned cd?

---

### Post by pinko on 2009-11-13
Run wubi.exe

While running wubi locate the running pyrun.exe location (its an executable used by wubi) C:\Users\[user]\AppData\Local\Temp\pyl****.tmp goto the data folder and edit isolist.ini 
find [Kubuntu-amd64] heading make sure all files relating to amd64 are not uncommented including metalinks. This was the case with mine the metalink url was for i386 version and the amd64 version was uncommented.

---

