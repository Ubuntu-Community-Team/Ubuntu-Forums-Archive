---
title: "md5sum question"
date: 2006-06-24
forum: General Help
---

### Post by Ramses de Norre on 2006-06-24
Ok this may be a stupid question but I just can't find the answer.. how do you check md5sums??
I read the manual and thought it was something like this: ```
ramses@icarus:~$ md5sum --status -c torrents/KNOPPIX_V5.0.1CD-2006-06-01-EN/KNOPPIX_V5.0.1CD-2006-06-01-EN.iso torrents/KNOPPIX_V5.0.1CD-2006-06-01-EN/KNOPPIX_V5.0.1CD-2006-06-01-EN.iso.md5
md5sum: autorun.inf: No such file or directory
md5sum: autorun.pif: No such file or directory
md5sum: boot/isolinux/boot.msg: No such file or directory
md5sum: boot/isolinux/f2: No such file or directory
md5sum: boot/isolinux/f3: No such file or directory
md5sum: boot/isolinux/german.kbd: No such file or directory
md5sum: boot/isolinux/isolinux.bin: No such file or directory
md5sum: boot/isolinux/isolinux.cfg: No such file or directory
md5sum: boot/isolinux/linux: No such file or directory
md5sum: boot/isolinux/logo.16: No such file or directory
md5sum: boot/isolinux/memtest: No such file or directory
md5sum: boot/isolinux/minirt.gz: No such file or directory
md5sum: cdrom.ico: No such file or directory
md5sum: index.html: No such file or directory
md5sum: KNOPPIX/avm-license.txt: No such file or directory
md5sum: KNOPPIX/background.jpg: No such file or directory
md5sum: KNOPPIX/images/knoppix-24-1.jpg: No such file or directory
md5sum: KNOPPIX/images/knoppix-header.png: No such file or directory
md5sum: KNOPPIX/index_dk.html: No such file or directory
md5sum: KNOPPIX/index_en.html: No such file or directory
md5sum: KNOPPIX/index_es.html: No such file or directory
md5sum: KNOPPIX/index_fr.html: No such file or directory
md5sum: KNOPPIX/index.html: No such file or directory
md5sum: KNOPPIX/index_it.html: No such file or directory
md5sum: KNOPPIX/index_jp.html: No such file or directory
md5sum: KNOPPIX/index_nl.html: No such file or directory
md5sum: KNOPPIX/index_ru.html: No such file or directory
md5sum: KNOPPIX/KNOPPIX: No such file or directory
md5sum: KNOPPIX/knoppix-cheatcodes.txt: No such file or directory
md5sum: KNOPPIX/KNOPPIX-FAQ-EN.txt: No such file or directory
md5sum: KNOPPIX/KNOPPIX-FAQ-ES.txt: No such file or directory
md5sum: KNOPPIX/KNOPPIX-FAQ-FR.txt: No such file or directory
md5sum: KNOPPIX/KNOPPIX-FAQ-IT.txt: No such file or directory
md5sum: KNOPPIX/KNOPPIX-FAQ-NL.txt: No such file or directory
md5sum: KNOPPIX/KNOPPIX-FAQ.txt: No such file or directory
md5sum: KNOPPIX/knoppix-version: No such file or directory
md5sum: KNOPPIX/LICENSE.txt: No such file or directory
md5sum: KNOPPIX/modules/cloop.ko: No such file or directory
md5sum: KNOPPIX/modules/insmod: No such file or directory
md5sum: KNOPPIX/modules/rmmod: No such file or directory
md5sum: KNOPPIX/modules/unionfs.ko: No such file or directory
md5sum: KNOPPIX/README_Security.txt: No such file or directory
md5sum: KNOPPIX_V5.0.1CD-2006-06-01-EN.iso: No such file or directory
ramses@icarus:~$
```
But as you see I get a lot of errors.. is the iso corrupted or am I using an incorrect command?

---

### Post by aysiu on 2006-06-24
```
cd torrents/KNOPPIX_V5.0.1CD-2006-06-01-EN/ 
md5sum -c KNOPPIX_V5.0.1CD-2006-06-01-EN.iso.md5
```

---

### Post by Ramses de Norre on 2006-06-24
Thanks a lot, I finally know how to do that now ;)

---

