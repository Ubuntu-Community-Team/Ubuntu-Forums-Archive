---
title: "Linux Mint Gloria KDE (Jaunty 9.04) with Radeon 9500 Catalyst 9.3"
date: 2009-11-11
forum: General Help
---

### Post by DeusEx on 2009-11-11
I have got video acceleration!
I installed Mint Gloria (eg Jaunty 9.04) KDE from scratch, however no video driver worked, none of the proprietary (fglrx / ati catalyst) or open source (Mesa SGI).

Apparantly it is not possible to run 9.04, it's X server (Xorg -version = 1.6) and fglrx or ati catalyst. Plus with the open source drivers I got a freeze when starting KDM and errors regarding MTRR.

Working procedure (quite easy):
* make sure the system is updated and upgraded, i run 2.6.28-16-generic.

* Downgrade xserver to 7.4 (Xorg 1.5.2) using [Tyler's howto](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue). (for mint i had to include replacing 'gloria' with 'felicia' in apt sources.

* reboot. download Catalyst 9.3 and install. use aticonfig --initial -f. reboot

* everything should work!

---

