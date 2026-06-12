---
title: "Need virtualization with usb support"
date: 2010-06-20
forum: General Help
---

### Post by Belgatom on 2010-06-20
I want to use belgian tax on web and some other programs that don't seem to hack in Ubuntu (Ipod Nano 5th generation among others). Anyway, I thought that it would be time to experiment with virtualization. But I have several times that the free edition of Virtual Box does not support usb: ie I wouldn't be able to connect my cardreader (idcard reader) nor my ipod nano 5th generation. 

What should I go for?

---

### Post by James78 on 2010-06-20
Go for VirtualBox. But go for the non-ose version. It has USB support, and it works just as well as you'd expect it too.

Add this to your repository:```
deb http://download.virtualbox.org/virtualbox/debian lucid non-free
```Then run this command to install the GPG key:```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```Then update the package lists, and install virtualbox-3.2```
sudo apt-get update
sudo apt-get install virtualbox-3.2
```

To see the full list of repositories for different distributions of Ubuntu, go here.
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by John Bean on 2010-06-20
The OP indicates Feisy is in use. If that's true it's probably not a good idea to attempt to install the current Lucid port of VB.

---

### Post by James78 on 2010-06-20
That's why I added the line about the full list of repositories. Feisty isn't in there, but that isn't my doing or fault. They have what they have, and nothing more. All I can do is provide the link for as much help as possible!

P.S. Last time I checked, Feisty support ended 2 years ago!

---

### Post by Belgatom on 2010-06-20
Will this work on Karmic? (Needed to still update my profile)

---

### Post by James78 on 2010-06-20
Follow my same instructions, except, add this repository instead.```
deb http://download.virtualbox.org/virtualbox/debian karmic non-free

```

---

### Post by John Bean on 2010-06-20
The link is fine, the explicit instructions are wrong if the OP is really using Feisty. Support has nothing to do with whether an OS is still in use or not, I know several people still using Windows 98...

We should offer advice based on known fact rather than assumptions.

Edit: I see the OP has clarified the situation while I was typing. I think that rather proves the point I was tying to make.

---

### Post by James78 on 2010-06-20
The known fact is that there's no VBox repository for Feisty, so I had to do the next best thing and assume he had upgraded within the meantime. Either way, it doesn't matter, and there's no point discussing it or arguing about it. His question has been answered. ;)

---

