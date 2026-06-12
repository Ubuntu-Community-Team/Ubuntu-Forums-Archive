---
title: "how to get sl-modem-daemon"
date: 2006-05-03
forum: General Help
---

### Post by jsmidt on 2006-05-03
I need to get sl-modem-daemon to set up my modem.  I can't just type apt-get intall sl-modem-daemon since I can't get the internet until I get my modem set up. (I am using a public computer now) How can I get this package?

---

### Post by towsonu2003 on 2006-05-03
go to packages.ubuntu.com, [search for the package, download it]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fs%2Fsl-modem%2Fsl-modem-daemon_2.9.10%2B2.9.9d-6ubuntu1_i386.deb&md5sum=8f67b8b3ce6fdef952b9ebcfada7c7c6&arch=i386&type=main"), transfer it to your ubuntu desktop. Make sure you don't have any .deb files in your desktop. after that, do:
```

cd ~/Desktop
sudo dpkg -i *.deb

```

Check out the second link in my signature for more info on sl-modem (if yours is alsa supported, there is a section for that) as well as for wvdial (tool to dial out).

---

