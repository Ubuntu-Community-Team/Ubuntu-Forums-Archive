---
title: "Install kubuntu in place of ubuntu"
date: 2012-04-01
forum: General Help
---

### Post by magodiafano on 2012-04-01
Hello
now I have ubuntu 11.10 installed together with windows 7 in dual boot.
Since ubuntu is too heavy for my laptop i'd like to install kubuntu in its place.

Do you have a guide to do that? or could I simply install kubuntu in the same partition of ubuntu and the last will be erased?

---

### Post by HiImTye on 2012-04-01
[https://help.ubuntu.com/community/FromUbuntuToKubuntu](https://help.ubuntu.com/community/FromUbuntuToKubuntu)

---

### Post by mörgæs on 2012-04-01
Kubuntu is not much lighter. In order to get speed, you should try Xubuntu or (even lighter) Lubuntu.

You don't need a full install, just add the desktop:

```
sudo apt-get install xubuntu-desktop
```

---

### Post by 2F4U on 2012-04-01
If Ubuntu is too heavy for your laptop, you probably won't be much happier with Kubuntu. In my experience, KDE is at the moment the heaviest desktop environment available.

---

### Post by StephanG on 2012-04-12
I'd have to agree with the others that Kubuntu probably isn't the route you want to go if you're already struggling with performance.  But then, I have a laptop that seems to work better on Kubuntu than Ubuntu, and turning off the Desktop Effects would probably help...

But, Xubuntu and Lubuntu are definitely more lightweight than Ubuntu.

But, whatever you decide to do, you can just "sudo apt-get install (k/x/l)buntu-desktop".  But, if you want to simultaneously remove all the bits and pieces belonging to Ubuntu, it's a little trickier.  I would suggest doing a completely fresh install with new distro.

When you get to the part where it asks you how you want to install it on your Hard Drive, you simply choose "manual".  Then, you select your current Ubuntu partition and tell it that you want to mount it as "/", without formatting the partition.  Then, it should delete everything except your personal files in your /home directory.

DISCLAIMER:  I'm assuming that you did not manually split your /home directory when you installed Ubuntu the first time.

---

