---
title: "Tomoe in repository?"
date: 2009-09-27
forum: General Help
---

### Post by ToshibaLaptoplinux on 2009-09-27
Does anyone know of a repository that has Tomoe in it for Jaunty? Or must I compile from source? I thought it use to be there but...

Also looking for ipamonafont.

Thanks

---

### Post by Napu5 on 2009-12-19
According to this: [http://ubuntuforums.org/showthread.php?t=812552](http://ubuntuforums.org/showthread.php?t=812552)
```
gksudo gedit /etc/apt/sources.list
```Add this at the bottom:
```
deb http://archive.ubuntulinux.jp/ubuntu-ja intrepid/
```Newer than Intrepid is not available, but the Intrepid version seems to work for later Ubuntu versions too.
do
```
sudo apt-get update
```Ignore the warning about signatures couldn't be verified
```
sudo apt-get install ubuntu-ja-keyring
``````
sudo apt-get install scim-tomoe
```
Also check out kanjipad.

---

