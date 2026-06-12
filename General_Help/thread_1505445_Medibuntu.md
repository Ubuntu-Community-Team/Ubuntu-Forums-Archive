---
title: "Medibuntu"
date: 2010-06-09
forum: General Help
---

### Post by deep_purple on 2010-06-09
Hi everyone.
I just had Ubuntu 10.04 64 bit installed on my laptop and I'm trying to make mp3, avi and other file extensions work.

I downloaded all the 64 bit packages and installed:

libdvdcss2

```

wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb

```

w64codecs

```
wget -c http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu2_amd64.deb
sudo dpkg -i w64codecs_20071007-0medibuntu2_amd64.deb

```

non-free-codecs

```

wget -c http://packages.medibuntu.org/pool/non-free/n/non-free-codecs/non-free-codecs_5medibuntu1_amd64.deb
sudo dpkg -i non-free-codecs_5medibuntu1_amd64.deb

```

From all that I found on the net, this will install codecs to view media files, java, flash player and libraries that make the system compatible with 32 bit softwares.
Please correct me if I'm doing wrong.

Also,  I'm wondering which version (32 or 64 bit) of Java and flash player have been installed on my laptop.

Any help would be appreciated.

Best regards.

---

### Post by philinux on 2010-06-09
Click the restricted formats link below.

It install 64 bit java but 32 bit flash.

You can then uninstall flashplugin-nonfree and get the 64 bit flash from adobe. [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Extract and put the file libflashplayer.so here ~/.mozilla/plugins

Create the plugins folder first.

---

