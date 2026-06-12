---
title: "Package downloading doesn't work"
date: 2011-12-05
forum: General Help
---

### Post by geebob on 2011-12-05
I can't download packages from Software Center, Synaptic package manager nor Update manager.  I would get messages that said I should check my internet connection (its okay, I'm sending this from the computer in question) and that packages could not be verified.

I followed some advice from a previous thread that said to change my source to the "best source"  I tried that and packages dissappeared from SC and SPM.  I went back and changed the source to US source.

I tried SPM again (on ndiswrapper, wine was on a previous attempt) and here is what I got:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/html2text/html2text_1.3.2a-15_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/html2text/html2text_1.3.2a-15_i386.deb)
  Could not connect to 10.0.0.2:8080 (10.0.0.2). - connect (111: Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/po-debconf/po-debconf_1.0.16+nmu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/po-debconf/po-debconf_1.0.16+nmu1_all.deb)
  Unable to connect to 10.0.0.2:8080:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_8.1.2ubuntu4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_8.1.2ubuntu4_all.deb)
  Unable to connect to 10.0.0.2:8080:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsys-hostname-long-perl/libsys-hostname-long-perl_1.4-2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsys-hostname-long-perl/libsys-hostname-long-perl_1.4-2_all.deb)
  Unable to connect to 10.0.0.2:8080:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmail-sendmail-perl/libmail-sendmail-perl_0.79.16-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmail-sendmail-perl/libmail-sendmail-perl_0.79.16-1_all.deb)
  Unable to connect to 10.0.0.2:8080:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/m/module-assistant/module-assistant_0.11.3ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/m/module-assistant/module-assistant_0.11.3ubuntu1_all.deb)
  Unable to connect to 10.0.0.2:8080:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.56+r2729-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.56+r2729-1_all.deb)
  Unable to connect to 10.0.0.2:8080:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-dkms_1.56+r2729-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-dkms_1.56+r2729-1_all.deb)
  Unable to connect to 10.0.0.2:8080:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-source_1.56+r2729-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-source_1.56+r2729-1_all.deb)
  Unable to connect to 10.0.0.2:8080:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.56+r2729-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.56+r2729-1_i386.deb)
  Unable to connect to 10.0.0.2:8080:


I am currently running Ubuntu 11.04 on a Dell Inspiron 1501 Laptop.

---

### Post by Rubi1200 on 2011-12-05
I'm able to get there. Are you behind a proxy?

---

### Post by forsubhi on 2011-12-05
do you try downloading package by using 
sudo apt-get

---

