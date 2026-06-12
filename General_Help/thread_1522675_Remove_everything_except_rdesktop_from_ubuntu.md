---
title: "Remove everything except rdesktop from ubuntu"
date: 2010-07-02
forum: General Help
---

### Post by rbhkamal on 2010-07-02
Hi,
I'm trying to slim down the ubuntu liveCD using the instructions from the following link:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)


My objective is to trim ubuntu down and leave nothing but the ability to do remote desktop and use network-manager to manage the network. Everything else is not important... so no clipboard no sound no 3D no USB... nothing except network and rdesktop with the regular gnome desktop with a panel for the network-manager applet

I managed to trim the final ISO down to 290MB but I need it around 100MB and if possible 50MB.

I do want to keep the ability to do "sudo apt-get install openoffice" in the future though....


Can you think of any more packages that I can remove other than the following:
openoffice.org-core ubuntu-docs evolution-common hplip-data firefox openoffice.org-calc openoffice.org-common smbclient language-pack-gnome-fr-base language-pack-gnome-es-base language-pack-gnome-pt-base language-pack-gnome-de-base openoffice.org-writer rhythmbox iso-codes brasero-common tomboy empathy-common totem-common f-spot gcalctool gnome-orca seahorse evolution-data-server-common openoffice.org-draw cups example-content gnome-disk-utility evolution cups-common file-roller gnome-media-common evince synaptic openoffice.org-style-human update-manager-core yelp gnupg gnome-keyring  aisleriot libpurple0  ubuntu-mono libsmbclient ure gnome-doc-utils gstreamer0.10-plugins-good gnome-sudoku ubuntu-wallpapers gparted gnome-user-guide tcl8.4 manpages-dev ubiquity-slideshow-ubuntu gbrainy transmission-gtk man-db vino pitivi gnome-bluetooth gnome-nettool libgstreamer0.10-0 tk8.4 openoffice.org-impress apparmor empathy apport gedit gstreamer0.10-plugins-base rhythmbox-plugins nano  espeak-data totem jockey-common evolution-data-server  gnome-accessibility-themes bluez xterm evolution-webcal simple-scan aspell nautilus-sendto-empathy manpages ppp brasero openoffice.org-math screen dictionaries-common libgweather-common linux-image-2.6.32-21-generic xulrunner-1.9.2 perl-modules ubiquity perl gnome-power-manager language-pack-gnome-bn-base libsane erlang-base libgutenprint2 python2.6-minimal libgphoto2-2 gnomine mono-runtime groff-base gwibber libgtk2.0-cil mono-runtime perl-base libpython2.6 software-center hpijs iptables language-pack-gnome-xh-base geoip-database speech-dispatcher system-config-printer-gnome libgstreamer-plugins-base0.10-0 python-ubuntuone-client wamerican myspell-en-gb hunspell-en-ca hunspell-en-us ufw ubiquity-ubuntu-artwork pnm2ppa pppconfig tcpdump hplip cups-driver-gutenprint samba-common dnsmasq-base system-config-printer-common sane-utils ttf-khmeros-core libthai-data transmission-common



Thanks,
RK

---

### Post by cariboo on 2010-07-02
Why not use the [mini iso]("https://help.ubuntu.com/community/Installation/MinimalCD") and just install what you need, then use [remastersys]("http:///www.geekconnection.org/remastersys/") to create a live cd?

---

### Post by nothingspecial on 2010-07-02
I would use wicd-curses to manage the network.

It`s like a kind of ncurses gui to manage the network from the cli without having to do all that eth0 up, ifconfig, /ect/interfaces business

Then you wont need gnome atall

Or use Puppy

---

### Post by rbhkamal on 2010-07-02
Thanks, both suggestions are exactly what I'm looking for!

I just tried mini.iso but it failed to install the base-system.

Question, my iso will only run in a virtualbox virtual machine. Do you think it would be a good idea to install the kernel-virtual kernel with the generic drivers?

---

### Post by prodigy_ on 2010-07-02
Maybe you should consider Xfce instead of Gnome? It's lighter and has less unnecessary components.

---

### Post by rbhkamal on 2010-07-02
xfce might slow me down. When I have time, I will create two versions -- one with gnome and the other with xfce. And then compare the two;however, I have a feeling that the difference will only be a few mbs

---

### Post by benjaminjuel on 2010-12-13
I'm looking for something right along these lines.  Is there any way you could provide a step-by-step tutorial to build what you built?  I would ask you to share your .iso file, but drivers don't always transfer that way.

Thanks.

---

### Post by rbhkamal on 2010-12-13
Remind me in a week after my Finals are over but for I recommed u try tinycore linux. I enedup using the mini.iso and a bunsh of scripts to strip it down to 52MiBs!!!! Suck on that DSL! But tinycore linux is 11MiB.... u can't beat that

---

