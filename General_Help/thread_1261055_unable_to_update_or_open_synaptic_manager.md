---
title: "unable to update or open synaptic manager"
date: 2009-09-08
forum: General Help
---

### Post by seangal82 on 2009-09-08
Help i cannot update ubuntu 9.04 form desktop or open synaptic packet manager from drop down or terminal. I can update from terminal but the update manager keeps opening  with the same updates every half hour.
I have used command gksudo synaptic  witch has generated the following 
:(synaptic:4488): libglade-WARNING **: could not find glade file '/usr/share/synaptic/glade/window_main.glade'
synaptic: rggladewindow.cc:59: RGGladeWindow::RGGladeWindow(RGWindow*, std::string, std::string): Assertion `_gladeXML' failed.

any ideas

---

### Post by SoftwareExplorer on 2009-09-08
Welcome to the ubuntu forums :) Could you post the output of ```
sudo apt-get upgrade
```?

---

### Post by seangal82 on 2009-09-10
Hi thank you for the welcome and taking the time to help..

  sudo apt-get upgrade
[sudo] password for sean: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
The following packages will be upgraded:
  app-install-data-partner dnsmasq-base gnome-terminal gnome-terminal-data
  kdelibs-bin kdelibs5 kdelibs5-data language-pack-en language-pack-gnome-en
  libcurl3-gnutls libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libgnutls26
  libmjpegtools-1.9 libmono-cairo2.0-cil libmono-corlib2.0-cil
  libmono-data-tds2.0-cil libmono-data2.0-cil libmono-getoptions2.0-cil
  libmono-i18n2.0-cil libmono-posix2.0-cil libmono-security2.0-cil
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil
  libmono-system-web2.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil
  libnss3-1d libnss3-dev libpam-modules libpam-runtime libpam0g libpurple-bin
  libpurple0 libvorbis0a libvorbisenc2 libvorbisfile3 libxml2 libxml2-utils
  linux-libc-dev linux-restricted-modules-common mesa-utils mono-2.0-gac
  mono-2.0-runtime mono-common mono-gac mono-jit mono-runtime
  openprinting-ppds-postscript-konica-minolta pidgin pidgin-data
  python-gobject python-libxml2 tzdata
57 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 30.1MB of archives.
After this operation, 1659kB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by SoftwareExplorer on 2009-09-10
So, two questions:If you do update from the terminal, does the error opening synaptic go away? Also, if you update from the terminal, do the updates in the update manager change?

---

### Post by seangal82 on 2009-09-10
first question. No the error still the same.. and it's the same case for the second question the list in update manager always has the updates from when this started.

---

### Post by SoftwareExplorer on 2009-09-10
What if we try reinstalling synaptic:

```
sudo apt-get update&&sudo apt-get upgrade
sudo apt-get remove synaptic
sudo apt-get install synaptic apturl gnome-app-install gnome-codec-install jockey-gtk language-selector software-properties-gtk synaptic ubufox ubuntu-desktop update-manager update-notifier
```


Then does it work?

---

### Post by directhex on 2009-09-10
> **SoftwareExplorer said:**
> What if we try reinstalling synaptic:

```
sudo apt-get update&&sudo apt-get upgrade
sudo apt-get remove synaptic
sudo apt-get install synaptic apturl gnome-app-install gnome-codec-install jockey-gtk language-selector software-properties-gtk synaptic ubufox ubuntu-desktop update-manager update-notifier
```


Then does it work?

"aptitude reinstall synaptic" seems a bit easier

---

### Post by seangal82 on 2009-09-13
Perfect that worked a charm. Again thank you very much for the help i'll be looking you up for the next problem :-)

---

### Post by SoftwareExplorer on 2009-09-13
> **seangal82 said:**
> Perfect that worked a charm. Again thank you very much for the help i'll be looking you up for the next problem :-)
Your welcome. :) It was a lucky guess that the file it was complaining about had gotten corrupted, and that reinstalling synaptic would replace it.

---

