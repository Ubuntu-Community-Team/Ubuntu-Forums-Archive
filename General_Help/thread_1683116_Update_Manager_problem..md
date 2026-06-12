---
title: "Update Manager problem."
date: 2011-02-07
forum: General Help
---

### Post by Santaji on 2011-02-07
It says "Software updates are available for this computer", But when i click "Install Updates" i get this error:
[IMG]http://img812.imageshack.us/img812/1143/screenshotfn.png[/IMG]

Here's the whole text that appears in the white text area under details:
```
apparmor apparmor-utils computer-janitor computer-janitor-gtk empathy empathy-common evolution evolution-common evolution-data-server evolution-data-server-common evolution-plugins google-chrome-stable hpijs hplip hplip-cups hplip-data icedtea-6-jre-cacao icedtea6-plugin indicator-appmenu indicator-sound jockey-common jockey-gtk libapparmor-perl libapparmor1 libc-bin libc-dev-bin libc6 libc6-dev libcamel1.2-14 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13 libedataserverui1.2-8 libegroupwise1.2-13 libevolution libgdata-google1.2-1 libgdata1.2-1 libhpmud0 libnautilus-extension1 libsane-hpaio linux-firmware linux-generic linux-headers-2.6.35-25 linux-headers-2.6.35-25-generic linux-headers-generic linux-image-2.6.35-25-generic linux-image-generic linux-libc-dev media-player-info nautilus nautilus-data nautilus-sendto-empathy nvidia-96-modaliases openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human openoffice.org-writer openssh-client opera python-apt python-uno ssh-askpass-gnome tar ttf-opensymbol ubuntu-docs uno-libs3 update-manager update-manager-core upstart ure xserver-common xserver-xorg-core xserver-xorg-input-evdev
```

What does all this mean? and What should i do?

---

### Post by mörgæs on 2011-02-07
Try to reboot the machine and run the following commands:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

