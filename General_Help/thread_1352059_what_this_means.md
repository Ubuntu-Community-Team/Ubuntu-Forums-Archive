---
title: "what this means?"
date: 2009-12-11
forum: General Help
---

### Post by anakonda007 on 2009-12-11
E: /var/cache/apt/archives/kdelibs5-data_4%3a4.3.2-0ubuntu7.2_all.deb: unable to create `/usr/share/kde4/apps/ksgmltools2/customization/cs/entities/install-intro.docbook.dpkg-new' (while processing `./usr/share/kde4/apps/ksgmltools2/customization/cs/entities/install-intro.docbook')
E: /var/cache/apt/archives/kdebase-runtime-data-common_4%3a4.3.2-0ubuntu4.1_all.deb: unable to create `/usr/share/locale/l10n/sg/flag.png.dpkg-new' (while processing `./usr/share/locale/l10n/sg/flag.png')
E: /var/cache/apt/archives/kdebase-runtime-data_4%3a4.3.2-0ubuntu4.1_all.deb: unable to create `/usr/share/kde4/services/searchproviders/en2de.desktop.dpkg-new' (while processing `./usr/share/kde4/services/searchproviders/en2de.desktop')
E: /var/cache/apt/archives/kdelibs-data_4%3a3.5.10.dfsg.1-2ubuntu7.2_all.deb: unable to create `/usr/share/apps/ksgmltools2/customization/cs/entities/underGPL.docbook.dpkg-new' (while processing `./usr/share/apps/ksgmltools2/customization/cs/entities/underGPL.docbook')
E: /var/cache/apt/archives/linux-libc-dev_2.6.31-17.54_i386.deb: unable to create `/usr/include/linux/mempolicy.h.dpkg-new' (while processing `./usr/include/linux/mempolicy.h')

this message appears when upgrading ubuntu 9.10
what can i do for this?

---

### Post by SuperSonic4 on 2009-12-11
Could be anything from not using sudo to no room in / (or /var) to a lack of updated source. Try ```
sudo apt-get update && sudo apt-get upgrade
```

Should that fail what is the output of ```
df -h
```

---

### Post by anakonda007 on 2009-12-11
E: /var/cache/apt/archives/linux-headers-2.6.31-17_2.6.31-17.54_all.deb: unable to create `/usr/src/linux-headers-2.6.31-17/arch/arm/mach-s3c2410/include/mach/regs-sdi.h.dpkg-new' (while processing `./usr/src/linux-headers-2.6.31-17/arch/arm/mach-s3c2410/include/mach/regs-sdi.h')
E: /var/cache/apt/archives/linux-headers-2.6.31-17-generic_2.6.31-17.54_i386.deb: unable to create `/usr/src/linux-headers-2.6.31-17-generic/include/config/fb/ddc.h.dpkg-new' (while processing `./usr/src/linux-headers-2.6.31-17-generic/include/config/fb/ddc.h')
E: /var/cache/apt/archives/kdelibs5-data_4%3a4.3.2-0ubuntu7.2_all.deb: unable to create `/usr/share/kde4/apps/ksgmltools2/docbook/xsl/common/tr.xml.dpkg-new' (while processing `./usr/share/kde4/apps/ksgmltools2/docbook/xsl/common/tr.xml')
E: /var/cache/apt/archives/kdelibs-data_4%3a3.5.10.dfsg.1-2ubuntu7.2_all.deb: unable to create `/usr/share/apps/ksgmltools2/docbook/xsl/html/manifest.xsl.dpkg-new' (while processing `./usr/share/apps/ksgmltools2/docbook/xsl/html/manifest.xsl')

what this mean?

---

### Post by cavh on 2009-12-11
SuperSonic4 asked you to post the output of 

```
df -h
```

Please do this so we can help you.

---

### Post by anakonda007 on 2009-12-11
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda10             10G  553M  8.9G   6% /
udev                  498M  308K  497M   1% /dev
none                  498M  596K  497M   1% /dev/shm
none                  498M  288K  497M   1% /var/run
none                  498M     0  498M   0% /var/lock
none                  498M     0  498M   0% /lib/init/rw
/dev/sda1              12G  9.4G  1.2G  90% /home
/dev/sda6             7.4G  469M  6.6G   7% /var
/dev/sda7             2.8G  121M  2.5G   5% /boot
/dev/sda9             3.7G  3.2G  289M  92% /usr
/dev/sdb1             3.9G  4.0K  3.9G   1% /media/MEZO


that's what appeared

---

### Post by Leppie on 2009-12-11
looks like during the upgrade your /usr partition (/dev/sda9) gets clogged up. who did your partition if I may ask? assigning >7 gigs to /var and less than 4 gigs to /usr doesn't seem logical to me.

---

### Post by anakonda007 on 2009-12-12
my administrator who assigned my partitions but why?

---

### Post by Leppie on 2009-12-12
maybe you're not supposed to install systema wide applications.

---

