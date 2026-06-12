---
title: "LibreOffice on lucid 10.04"
date: 2011-01-27
forum: General Help
---

### Post by gnagnibu on 2011-01-27
Does anyone know if libreoffice.org will be insert on official repo for Ubuntu 10.04?
I know for Ubuntu 11.04, but I have no idea for 10.04...

---

### Post by NikoC on 2011-01-27
Since the release data of Natty is scheduled for the 28th of April, I think it will be too soon to include libreoffice (it's also still in beta).

But you can always install it via ppa as explained in [this]("http://ubuntuguide.net/install-libreoffice-in-ubuntu-10-0410-1011-04-using-the-ppa") guide.

---

### Post by gnagnibu on 2011-01-27
Thanks NikoC, but I know I can install it from ppa or debs.
I only want to know if someones heard if Canonical think to insert LibreOffice in the 10.04 official repo.

---

### Post by Mystro256 on 2011-04-20
It's apparently been in development since January 18th ([so says Ubuntu brainstorm]("http://brainstorm.ubuntu.com/idea/26959/")) and will probably be implemented for one of the next point releases.

---

### Post by cottfcfan on 2011-04-20
If you want to use it in 10.04 its simple.
```
sudo apt-get remove --purge openoffice*.*
```
Then add the libreoffice repo:
```
sudo add-apt-repository ppa:libreoffice/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install libreoffice libreoffice-gtk myspell-en-gb aspell
```
Remember to change myspell to your own language, and your done.

---

