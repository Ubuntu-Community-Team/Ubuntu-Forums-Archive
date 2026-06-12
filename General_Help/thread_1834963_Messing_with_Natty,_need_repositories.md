---
title: "Messing with Natty, need repositories"
date: 2011-08-28
forum: General Help
---

### Post by chkneater on 2011-08-28
Hi, I have just installed UbuntuStudio 11.04 and I cannot seem to get all the repositories I need to get everything working.

Can anybody suggest some of the better repositories for Natty with a PPA link?

---

### Post by dino99 on 2011-08-28
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) natty main >> /etc/apt/sources.list'

wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

sudo apt-get install ubuntustudio-desktop

---

### Post by chkneater on 2011-08-28
Thanks dino, that helped me get the most of the repositories I want enabled, however when I run that third line I get "gpg: no valid OpenPGP data found." Other than that everything went smooth and I'm about to reboot and find out what happens!!?!?

---

