---
title: "Change boot/xsplash screen?"
date: 2012-08-09
forum: General Help
---

### Post by ChaosChris2009 on 2012-08-09
[How To Change XSplash Themes in Ubuntu 9.10]("http://www.howtogeek.com/howto/7939/how-to-change-xsplash-themes-in-ubuntu-9.10/")

I'm digging around through this, but it only appears to work for 9.10

Run Natilus as root and after carefully digging around in /usr/share/ I wasn't able to find to find/locate images/xplash in that directory.

Any other approaches on how I can about go about this?

12.04

---

### Post by heminder on 2012-09-10
I'd like to know too. The Xubuntu boot screen is dreary and I'd like to change it to something else. Even just black with the Xubuntu logo would be better.

---

### Post by coldcritter64 on 2012-09-10
OP, I would suggest you look into the ppa for [[COLOR=Blue]super-boot-manager[/COLOR]]("https://launchpad.net/~ingalex/+archive/super-boot-manager"),

A video demonstrating it [[COLOR=Blue]--here--[/COLOR]]("http://www.youtube.com/watch?v=Vn-2hqD_tSg")

For the splash screen focus on the Plymouth instructions, it also allows for grub/burg configuration. I haven't tested this yet, but am just about to start now I've found it :)

Edit: take special note of the comments/warnings near the end of the video, good luck.

---

### Post by heminder on 2012-09-11
Interesting. I added the PPA, but it's a 100+ Mb download for a gui front-end? Isn't there a simpler way to do it, like editing a text file?

---

### Post by coldcritter64 on 2012-09-11
@ heminder, The  bare necessities to run this program add up to about 20 MB here installed. Without any of the themes I've only got super-boot-manager_4752**K**B, plowshare_64.3**K**B and buc_4625**K**B of downloading. Total download size about 9.5 **M**B and total install size for them is about 20**M**B.

I think you might be looking at the whole ppa, not just what you need to install. There are a lot of themes in that ppa as well as burg related stuff. Info taken from synaptic, one of the screenshots below has a heap of themes highlighted, you only need to download and install them as you choose them in the interface. Otherwise the three packages mentioned above will do the job plus maybe one or two actual themes (that suit your needs).

Altering grub bootloader and plymouth splash screens is not a simple task to do manually. I gave up on manually changing the splash screen just after jaunty. You will need to wait for others to help if you wish to go that route :).

@ OP and heminder, Even super boot manager can cause problems, the warnings given in the video should be heeded. I ran into a couple of hitches here today and had to manually recover the setup, not nice but I managed to bludgeon my way through somehow, _*take care with this, only adjust the bare minimum with this tool and read the tutorials included.*_ (if you do use it)

---

### Post by heminder on 2012-09-11
Nope, it's just for the gui. It needs lots of Java stuff and the dependencies get bloated with the libraries. *apt-get install super-boot-manager* yields a hefty:

```
The following NEW packages will be installed
[SIZE="1"]  aview buc ca-certificates-java curl default-jre-headless icedtea-6-jre-cacao
  icedtea-6-jre-jamvm imagemagick imagemagick-common java-common libcdt4
  libcurl3 libgraph4 libgvc5 libjline-java liblqr-1-0 libmagickcore4
  libmagickcore4-extra libmagickwand4 libnetpbm10 libpathplan4 librhino-java
  netpbm openjdk-6-jre-headless openjdk-6-jre-lib perlmagick plowshare
  plymouth-x11 rhino super-boot-manager tesseract-ocr-eng tzdata-java
0 upgraded, 32 newly installed, 0 to remove and 0 not upgraded.
Need to get 71.7 MB/71.9 MB of archives.[/SIZE]
After this operation, 196 MB of additional disk space will be used.

```

---

### Post by critin on 2012-09-11
> **heminder said:**
> I'd like to know too. The Xubuntu boot screen is dreary and I'd like to change it to something else. Even just black with the Xubuntu logo would be better.

That's funny, my 12.04 xubuntu boot screen is a nice bright blue, with colorful cubes at the bottom,  but it's a fairly new install.

How long is anyone on the boot screen anyway?  4 seconds?    :confused:

edit:  oops, didn't mean the boot screen, meant the login screen.  sorry.
still, how long does it take?

---

### Post by coldcritter64 on 2012-09-11
> **heminder said:**
> Nope, it's just for the gui. It needs lots of Java stuff and the dependencies get bloated with the libraries. *apt-get install super-boot-manager* yields a hefty:

```
The following NEW packages will be installed
[SIZE=1]  aview buc ca-certificates-java curl default-jre-headless icedtea-6-jre-cacao
  icedtea-6-jre-jamvm imagemagick imagemagick-common java-common libcdt4
  libcurl3 libgraph4 libgvc5 libjline-java liblqr-1-0 libmagickcore4
  libmagickcore4-extra libmagickwand4 libnetpbm10 libpathplan4 librhino-java
  netpbm openjdk-6-jre-headless openjdk-6-jre-lib perlmagick plowshare
  plymouth-x11 rhino super-boot-manager tesseract-ocr-eng tzdata-java
0 upgraded, 32 newly installed, 0 to remove and 0 not upgraded.
Need to get 71.7 MB/71.9 MB of archives.[/SIZE]
After this operation, 196 MB of additional disk space will be used.

```
Oh, I see what you mean, I must have already had a lot of that installed before trying, you're correct from your installs state. I already had imagemagick and the openjdk and icedtea stuff installed, sorry.

---

### Post by heminder on 2012-09-11
Okay. For anyone wanting away with the background image, I tricked my way around it: Go to the folder where the image is stored (if I recall it was in */lib/plymouth/themes/*) and change permissions of the PNG image file so it can be edited (*sudo chmod a+rw filename*). Now open the image in GIMP and make it a flat black or whatever you prefer. Save and it and done.

---

