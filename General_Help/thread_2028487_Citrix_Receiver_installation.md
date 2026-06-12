---
title: "Citrix Receiver installation"
date: 2012-07-18
forum: General Help
---

### Post by yesterdayman on 2012-07-18
I want to install Citrix Receiver under Ubuntu 12.04.  There are 3 download files listed on the Citrix web site for x86 systems running Linux.  They are .tar.gz, .rpm, and .deb.  Which is the right one for Ubuntu 12.04 Desktop and how do I install it once downloaded?  All of them say that they require OpenMotif 2.3.1.  What is that and where can I get it?

Please be nice; I am a complete Linux newbie.  I have already installed Citrix Receiver under Windows and Android so I'm not a complete dummy.

---

### Post by Toz on 2012-07-18
To get the motif libraries, you'll need to install libmotif4:
```
sudo apt-get install libmotif4
```

Download the deb file and install it (32-bit):
```
sudo dpkg -i icaclient-12.1.0_i386.deb
```
OR for 64-bit:
```
sudo dpkg -i icaclient_12.1.0_amd64.deb
```

The executables will be installed to /opt/Citrix

---

### Post by yesterdayman on 2012-07-20
Thanks Toz.  All fixed now.

---

