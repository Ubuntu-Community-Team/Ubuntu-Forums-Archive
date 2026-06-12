---
title: "Gdebi: Bad File Descriptor"
date: 2009-06-27
forum: General Help
---

### Post by bonkadventure2 on 2009-06-27
Ok, so I recently upgraded to Ubuntu Karmic Koala 9.10 Alpha and everytime I try to install something using Gdebi, it tells me "Bad file descriptor"
This did not happen before. The only way I have been able to unpackage and package .deb files is via the terminal by cding to the directory where the .deb file is and typing "sudo dpkg -i filename.deb"

Please help!

---

### Post by poetofzwan on 2009-10-05
This is a known Beta bug that has been appears to be fixed and is scheduled to be release soon.  The bug report can be seen here: [https://bugs.launchpad.net/ubuntu/+bug/388953](https://bugs.launchpad.net/ubuntu/+bug/388953).

For now, you can install gdebi (rather than gdebi gtk) from Ubuntu Software Store which will allow you to install .deb files correctly.  The app is also called "GDebi Package Installer". 

P.S. Make sure that you choose to open files with correct GDebi Package Installer.  GDebi GTK will obviously still be default if simple double click.

Hope that helps :)

---

### Post by michillin212 on 2009-10-08
Thanks so much.  This is the first time i doubted Ubuntu.  You really saved me.  =)

---

### Post by poetofzwan on 2009-10-08
Glad to have helped.

Never doubt Ubuntu!  However, always doubt any software with a Beta label lol.

---

