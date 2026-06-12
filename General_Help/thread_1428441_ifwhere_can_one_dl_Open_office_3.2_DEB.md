---
title: "if/where can one d/l Open office 3.2 DEB?"
date: 2010-03-12
forum: General Help
---

### Post by eltonw on 2010-03-12
I have been on the open office site, and tried several different downloads for Open Office 3.2. However, once I unpack the gzipped file, I get *several* deb packages:shock: from within the archive.

Could someone kindly point me to a link where I can d/l a **single deb package** so I may easily install / (upgrade to)version 3.2? FWIW, I am using Karmic with the latest updates and OO ver. 3.1.1 on my netbook.

TIA!):P

---

### Post by sandyd on 2010-03-12
> **eltonw said:**
> I have been on the open office site, and tried several different downloads for Open Office 3.2. However, once I unpack the gzipped file, I get *several* deb packages:shock: from within the archive.

Could someone kindly point me to a link where I can d/l a **single deb package** so I may easily install / (upgrade to)version 3.2? FWIW, I am using Karmic with the latest updates and OO ver. 3.1.1 on my netbook.

TIA!):P
```

sudo apt-get -y remove openoffice.org*
wget -c http://download.services.openoffice.org/files/stable/3.2.0/OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz

tar xvfz OOo_3*.tar.gz
cd OOO* 
cd DEBS
cd desktop*
mv * ../
cd ../
sudo dpkg -i *.deb
``` tada!

---

### Post by eltonw on 2010-03-14
unfortunately, no "tada", or even a tiny "whoopie"!:-(

While I can launch the Presenter, Spreadsheet, or Writer from the Office menu / group in Karmic's NBR, _**both Synaptic and Ubuntu Software Center show that OO is NOT installed,**_ they both show: "Canonical provides critical updates for openoffice.org until April 2011." below the software description.

I must have seriously corrupted something in the system.
I've now chosen to 're-install' via Synaptic, but no updates show in the channel. Perhaps a reboot is in order.

thank you for your reply, nevertheless...

---

### Post by rahilm on 2010-03-14
ubunty, like most linuxes, has a very bad software management.

---

### Post by Hagar Delest on 2010-03-14
No. The Sun version is incompatible with the Ubuntu version. That's why you see that the Ubuntu version is not installed. But scroll a bit and in Synaptic you'll see that there is a version installed (because Synaptic is just a frontend for dpkg, which you've used to install the debs).

---

