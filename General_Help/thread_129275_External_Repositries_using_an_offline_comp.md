---
title: "External Repositries using an offline comp"
date: 2006-02-13
forum: General Help
---

### Post by Mikeee on 2006-02-13
Hey all,

im trying to install sendmail on kubuntu 5.10 but the computer does not and will not have access to the internet to install it. I downloaded the sendmail source and tried to do it manually but no luck. Is there anyway that I can get sendmail on an external device and use it as a repositry that kubuntu package manaager can read from and install itself? Sendmail doesnt appear on the normal kubuntu cd to install from that.

Any ideas?

Thanks

---

### Post by gingermark on 2006-02-13
You can download the sendmail package from [here](http://packages.ubuntu.com/breezy/mail/sendmail).

Keep in mind you will have to also grab the packages sendmail depends on, if you don't already have them

Move them across to your Kubuntu box by whatever method you like.

Then, run Konsole and navigate to the folder containing the .deb files, and type ```
sudo dpkg -i packagename.deb
``` (where packagename.deb is the package file you want to install).

If only the sendmail related deb files are in the folder you can type ```
sudo dpkg -i *.deb
``` to install all of them.

[This page](https://wiki.ubuntu.com/AptMoveHowto) might also interest you, but as I have no idea what system your internet-connected computer is running, I can't really answer your question more generally.

---

