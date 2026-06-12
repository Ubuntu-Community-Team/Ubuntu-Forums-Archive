---
title: "Installing gnome-ppp and wvdial in 12.04"
date: 2012-06-16
forum: General Help
---

### Post by Ziton on 2012-06-16
I've been trying to get ubuntu 12.04 to connect using pppconfig. It will dial up and shake hands but not log on. I've given up and downloaded gnome-ppp and wvdial on my windows box.
One is "gnome-ppp-0.3.23.tar.bz2" the other is " wvdial_1.61-4build1.debian.tar.gz"
Never had any luck with these kinds. How do I install them?
Thanks 
Eddie

---

### Post by mbuell on 2012-06-25
For those tar files - I think you have to use "make" and "configure" - and my advice is "don't do it". I've been using linux for 4 years now, and have never had a "make" "configure" installation work correctly. Mostly I don't try. Additionally - you have to uninstall them using the reverse command line techniques - you can't use Synaptic  or apt or any of the package managers to uninstall them. 

Can you stop off at a Starbucks and use their wifi to do the update and grab the packages from the repository? If not research how to get those packages as .deb files. You can plop a .deb file on your desktop and install it from there using gdebi or synaptic or apt-get.

---

