---
title: "Network Tools Ubuntu 11.10"
date: 2012-03-24
forum: General Help
---

### Post by arbo0704 on 2012-03-24
I have a question about Network Tools in Ubuntu 11.10. I was wanting to know how I could resize the application so I could view IP information section in the program?

---

### Post by wildmanne39 on 2012-03-24
Hi, you should be able to put your cursor on the spot you need to make larger or in the bottom corner of the window and hold the left mouse button down and move it to make it larger.
Thanks

---

### Post by uRock on 2012-03-24
I have noticed this problem as well. No matter how big the window is I still can't see the information.

There is a bug report here, where they say a fix has been release. [s]My system is up to date, so I wonder if I am missing something.[/s] Apparently they released the fix for the next version of nettool, which does us no good. 8(

 [https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/806606](https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/806606)

---

### Post by wildmanne39 on 2012-03-24
Hi, uRock it looks like you have to install this ppa then install the packages for the fix.
[https://launchpad.net/~mfisch/+archive/gnome-nettool](https://launchpad.net/~mfisch/+archive/gnome-nettool)
Thanks

---

### Post by uRock on 2012-03-24
> **wildmanne39 said:**
> Hi, uRock it looks like you have to install this ppa then install the packages for the fix.
[https://launchpad.net/~mfisch/+archive/gnome-nettool](https://launchpad.net/~mfisch/+archive/gnome-nettool)
Thanks

Thanks, will do.

---

### Post by uRock on 2012-03-24
To add this PPA, run the following commands one by one into a terminal,```
sudo add-apt-repository ppa:mfisch/gnome-nettool
```^^^Will add the PPA to your software sources list.```
sudo apt-get update && sudo apt-get upgrade
```^^^Will upgrade the packages.

This worked for me.:p

---

