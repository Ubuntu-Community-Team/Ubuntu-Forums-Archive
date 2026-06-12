---
title: "Migrating from Linux Mint 10 to Xubuntu 11.04."
date: 2011-09-05
forum: General Help
---

### Post by casbahdk on 2011-09-05
I am fed up with Linux Mint's move to Debian Testing. I just want a stable system that works, so I would like to migrate to Xubuntu 11.04 on my home built AMD Phenom II 64 X6-1100T/ 3.3GHz powered box. Any suggestions on what software to use to backup all of my .txt, .doc, .awb, .odt, .bmp, .jpg, .mp3, .flac, .pdf, .mp4, .ogv, mpeg, .flv, etc. file formats to a second internal hard disk and restore them to the correct directories after I have wiped the hard disk with the Linux Mint 10 install?

---

### Post by dino99 on 2011-09-05
if your installation have a /home partition, then no need to worry about your data/settings.
Otherwise:
Déjà Dup is a simple backup tool. It hides the complexity of backing up the
Right Way (encrypted, off-site, and regular) and uses duplicity as the
backend.

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by casbahdk on 2011-09-05
> **dino99 said:**
> if your installation have a /home partition, then no need to worry about your data/settings.
Otherwise:
Déjà Dup is a simple backup tool. It hides the complexity of backing up the
Right Way (encrypted, off-site, and regular) and uses duplicity as the
backend.

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

Thanks for the quick reply. Yes, I have a seperate /home partition, but I have sometimes experienced problems when not doing a clean install. I am now using the GNOME version of Linux Mint 10, and will be installing Xubuntu. So, what do I need to do to clean up the /home partition, if I am to avoid problems?

---

### Post by philinux on 2011-09-05
> **casbahdk said:**
> I am fed up with Linux Mint's move to Debian Testing. I just want a stable system that works, so I would like to migrate to Xubuntu 11.04 on my home built AMD Phenom II 64 X6-1100T/ 3.3GHz powered box. Any suggestions on what software to use to backup all of my .txt, .doc, .awb, .odt, .bmp, .jpg, .mp3, .flac, .pdf, .mp4, .ogv, mpeg, .flv, etc. file formats to a second internal hard disk and restore them to the correct directories after I have wiped the hard disk with the Linux Mint 10 install? 
 
Debian testing is not unstable. You might want to read this. For normal releases ubuntu uses Debian unstable. [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by casbahdk on 2011-09-06
Cheers philinux. I wasn't referring to the stage of development, but rather to the user experience when installing, upgrading and using the OS. There seem to be some inherent issues with using a rolling release cycle, like the one that Linux Mint has adopted.

---

