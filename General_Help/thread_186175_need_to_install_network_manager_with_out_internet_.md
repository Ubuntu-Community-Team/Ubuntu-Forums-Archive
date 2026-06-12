---
title: "need to install network manager with out internet connection"
date: 2006-06-01
forum: General Help
---

### Post by onesojourner on 2006-06-01
I need to install network manager with out internet connection. is there some where I can download the deb from?

---

### Post by patrickfromspain on 2006-06-01
packages.ubuntu.com

---

### Post by imagine on 2006-06-01
Or you can directly dive into the archive: [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/)

---

### Post by NeoChaosX on 2006-06-01
Put the Ubuntu CD in your CD drive and do this:
```
sudo apt-cdrom add
sudo apt-get install network-manager-gnome
```

---

### Post by onesojourner on 2006-06-01
[QUOTE=NeoChaosX]Put the Ubuntu CD in your CD drive and do this:
```
sudo apt-cdrom add
sudo apt-get install network-manager-gnome
```[/QUOTE]


it failed. it is still trying to download from http repos

---

### Post by blackjack6.21.91 on 2006-06-01
remove your internet sources from your sources.list (**settings --> repositories**) and remove/disable your internet sources.  It shouldn't try to use them anymore.  Why do you need the network manager if you can't get online.

---

### Post by onesojourner on 2006-06-01
well here is my complete problem
[http://www.ubuntuforums.org/showthread.php?t=185851](http://www.ubuntuforums.org/showthread.php?t=185851)

I was hoping network manager would get me going. the card is detected and its active and it is even getting a signal it just wont connect.

---

### Post by blackjack6.21.91 on 2006-06-02
EDIT
I read your original problem and my comment was pretty useless..
Maybe make sure and see your router is supported.  You may need to download a driver.  The other thing you could do is download the network manager .deb file and burn it to a CD.

---

### Post by onesojourner on 2006-06-02
I have downloaded the debs from the site above. there were 4 and I tried most of them and I could not get it installed.

---

