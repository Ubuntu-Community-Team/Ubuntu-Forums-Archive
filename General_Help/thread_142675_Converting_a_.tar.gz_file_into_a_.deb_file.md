---
title: "Converting a *.tar.gz file into a *.deb file"
date: 2006-03-10
forum: General Help
---

### Post by harisund on 2006-03-10
Hello

There are a couple of software that I need to install, and as usual I downloaded the source file from the web. 

I remember reading somewhere in the forums that in order for the system to maintain track of everything installed, it would be better to convert it to a *.deb file and allow dpkg to take care of it. 

Could someone please walk me through it? I really didn't know what search term to use, and consequently even if you could point me to a link that would be great !

Thanks !

---

### Post by bluevoodoo1 on 2006-03-10
If you download the source and compile it yourself use checkinstall instead of make install. checkinstall will make a .deb file so Synaptic can handle it (for easy removal later etc. etc.).

sudo apt-get install checkinstall

so when you compile from source, use checkinstall...
./configure
make
sudo checkinstall

This [link]("https://wiki.ubuntu.com/CheckInstall?highlight=%28checkinstall%29") talks more about checkinstall.

I hope that helped.

---

### Post by harisund on 2006-03-11
Thank you very much ! 

checkinstall was exactly what I was looking for .. a million thanks again !

hari.

---

### Post by bluevoodoo1 on 2006-03-11
No problem!

---

