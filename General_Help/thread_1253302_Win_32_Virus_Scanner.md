---
title: "Win 32 Virus Scanner?"
date: 2009-08-29
forum: General Help
---

### Post by Tanner2007 on 2009-08-29
Any virus scanner for ubutnu? I wish to download *blank* and most of which usually contains a virus (I mainly use vista) so if i download off of ubuntu I wish to make sure there is no virus before moving it to my vista partition

---

### Post by lisati on 2009-08-29
Stand by for the people who might want to ask "why do you want antivirus on Linux?"

There are a number which run on Ubuntu. My favourite is AVG but the latest Linux version is command-line only.

---

### Post by tgeer43 on 2009-08-29
The following links should get you headed in the right direction:

[ClamAV Antivirus]("https://help.ubuntu.com/community/ClamAV")
[AVG Antivirus]("https://help.ubuntu.com/community/Antivirus/Avg")
[Panda Antivirus]("https://help.ubuntu.com/community/PandaAntivirus")
[F-Prot Antivirus]("https://help.ubuntu.com/community/XFProt")
[BitDefender Antivirus]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html")
[avast! Linux Home Edition]("http://www.avast.com/eng/avast-for-linux-workstation.html")
[Avira Antivirus]("http://www.free-av.de/en/download/download_servers.php")

...and they are all free.

tgeer

---

### Post by hansdown on 2009-08-29
Hi Tanner2007.

Click system> administration> synaptic package manager.

Search for clamtk.

Install it.

You will be able to scan any downloads by clicking applications> system tools> virus scanner.

---

### Post by theozzlives on 2009-08-29
Since you said *blank* it's probably not legal. And as far as Ubuntu, it would not be affected by a Windows virus. Here's a way you can scan Windows for viruses from Ubuntu:
Mount your Windows partition
```
sudo apt-get install clamav
sudo mkdir /tmp/virus
clamscan -ri --move=/tmp/virus /media/disk
```
Most of the *blank* sites contain malware that MSIE downloads and installs in the background, another good reason not to visit those.

---

### Post by Wiebelhaus on 2009-08-29
[The best hands down]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html")

---

### Post by balaknair on 2009-08-30
I agree with Wiebelhaus
Go for BitDefender

[http://tombuntu.com/index.php/2009/07/07/download-and-install-bitdefender-antivirus-on-ubuntu-with-1-year-free-license/](http://tombuntu.com/index.php/2009/07/07/download-and-install-bitdefender-antivirus-on-ubuntu-with-1-year-free-license/)

---

