---
title: "Natty - how to install LibreOffice 3.4.6?"
date: 2012-05-22
forum: General Help
---

### Post by Sternfan on 2012-05-22
[SIZE="2"]Hi all,

I recently updated to LibreOffice 3.5.3 and absolutely hate it (in writer, which I use 90% of the time, they removed text boundaries).  It also has odd behaviour when opening old documents (bullet points messed up etc.)  

So - how do I go about installing LibreOffice 3.4.6?

Any help greatly appreciated,
Rob[/SIZE]

---

### Post by wilee-nilee on 2012-05-22
> **Sternfan said:**
> [SIZE=2]Hi all,

I recently updated to LibreOffice 3.5.3 and absolutely hate it (in writer, which I use 90% of the time, they removed text boundaries).  It also has odd behaviour when opening old documents (bullet points messed up etc.)  

So - how do I go about installing LibreOffice 3.4.6?

Any help greatly appreciated,
Rob[/SIZE]

Purge the libreoffice you have, find all associated files and delete then go to their site and download the install.

---

### Post by scouser73 on 2012-05-22
> **Sternfan said:**
> [SIZE="2"]Hi all,

I recently updated to LibreOffice 3.5.3 and absolutely hate it (in writer, which I use 90% of the time, they removed text boundaries).  It also has odd behaviour when opening old documents (bullet points messed up etc.)  

So - how do I go about installing LibreOffice 3.4.6?

Any help greatly appreciated,
Rob[/SIZE]

1 Remove Libreoffice with this command in Terminal

```
sudo apt-get remove libreoffice*.*
```

2 Click and download Libreoffice version 3.4.6.1 either the 32bit or 64bit verion

[http://www.libreoffice.org/download/?type=deb-x86&lang=en-GB&version=3.4.6]("http://www.libreoffice.org/download/?type=deb-x86&lang=en-GB&version=3.4.6")

3 Extract the file to **~/Desktop**

4 Rename the file to **libreoffice**

5 Open Terminal and enter this command:

```
sudo dpkg -i ~/Desktop/libreoffice/DEBS/*.deb
```

6 Then enter the following command into Terminal:

```
sudo dpkg -i ~/Desktop/libreoffice/DEBS/desktop-integration/libreoffice3.4-debian-menus_3.4-602_all.deb
```

***You have now installed Libreoffice 3.4.6***

---

