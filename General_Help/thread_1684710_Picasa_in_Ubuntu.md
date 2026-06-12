---
title: "Picasa in Ubuntu"
date: 2011-02-09
forum: General Help
---

### Post by JCM_Pico on 2011-02-09
Hello all.
Is there any way of running picasa in ubuntu without using wineserv?
I have a old laptop and this process (winserv) consumes 1/3 of my memory... and I need memory...

---

### Post by BHEJU on 2011-02-09
There is native support by Google for Picasa.
Here is the link. Download the deb file and install.

[http://picasa.google.com/linux/thanks-deb.html](http://picasa.google.com/linux/thanks-deb.html)

Cheers :>

---

### Post by JCM_Pico on 2011-02-10
> **BHEJU said:**
> There is native support by Google for Picasa.
Here is the link. Download the deb file and install.

[http://picasa.google.com/linux/thanks-deb.html](http://picasa.google.com/linux/thanks-deb.html)

Cheers :>


Hello there,
I uninstall picasa 3.0 running sudo apt-get remove picasa

then I installed following the given instructions the file you have gave me... but picasa wont start....
In the command line it displays
/usr/bin/picasa: line 139: 12589 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: line 175: 12692 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\

any suggestion?

---

### Post by BHEJU on 2011-02-21
I assume you tried to download from win machine. I think google's site is smart enough to identify the os you are running. So, ig gave you win installer. Just google the picasa for ubuntu and it will take you to a page where you will see a .deb file which will run in software center.

Cheers

---

### Post by JuanC on 2011-02-24
> **BHEJU said:**
> There is native support by Google for Picasa.
Here is the link. Download the deb file and install.

[http://picasa.google.com/linux/thanks-deb.html](http://picasa.google.com/linux/thanks-deb.html)

Cheers :>

Is **not a native** version of Picasa for Linux, is a Picasa for Windows + Wine package.

Also this package is unmaintained for years...

There is a native version of Picasa for MacOSX : [http://picasa.google.com/mac](http://picasa.google.com/mac) 

Why not a native version of Picasa for Linux?

---

