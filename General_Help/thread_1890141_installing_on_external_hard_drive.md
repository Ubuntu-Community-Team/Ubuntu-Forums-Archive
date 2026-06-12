---
title: "installing on external hard drive"
date: 2011-12-02
forum: General Help
---

### Post by jokenkil on 2011-12-02
can i use wubi to install ubuntu on my 1 terabyte external hard drive?

---

### Post by staf0048 on 2011-12-02
You should be able to, though I've never used wubi myself, so I can't speak from experience.  Since you're installing it to an external drive anyway, why not load up the live CD/USB and just select the external drive as your target source?

If you want to be "extra" safe, you can even rip out the hard drive from your computer before you begin so you don't pick the wrong drive and mess up any data you have on there, but this certainly is not necessary.

---

### Post by fantab on 2011-12-02
> **jokenkil said:**
> can i use wubi to install ubuntu on my 1 terabyte external hard drive?

Any particular reason you want to use WUBI? IMO you don't need WUBI. You can install Ubuntu directly to your 1TB EXHDD. 

Partition your EXHDD using [GParted Live]("http://gparted.sourceforge.net/livecd.php") with 15 GB for " / " mountpoint , and " /home " what ever GBs you Need to save your Data and a SWAP partition (2-4GB). Format Partitions as ext4.

iNSTALL UBUNTU- choose Manual Install with "Something Else" option. Direct the Installation to linux formatted partitions and let the installation Completed.
Install Ubuntu BOOT LOADER TO EXHDD ONLY.

Tell your BIOS to BOOT USB DEVICES FIRST... so that when ever the EXHDD is plugged in it boots to Ubuntu and when it is not plugged in it BOOTS the OS on HDD.

also [SEE THIS]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by oldtimer7777 on 2011-12-02
> **jokenkil said:**
> can i use wubi to install ubuntu on my 1 terabyte external hard drive?

You would not want to use Wubi to install on your 1Tb HDD.  Use plain ole' Ubuntu from a disc.  Here is a nice guide to get everything just the way you want it too:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

