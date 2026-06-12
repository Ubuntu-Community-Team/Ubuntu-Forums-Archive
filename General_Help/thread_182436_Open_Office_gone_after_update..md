---
title: "Open Office gone after update."
date: 2006-05-26
forum: General Help
---

### Post by Kakason on 2006-05-26
Hello.

I just updated to Dapper from Breezy and everything was fine. I notice that the desktop was much faster then Breezy. Anyways, I was trying to find OpenOffice Writer, but its gone. Is this normal? Do I have to install it by Synaptic?

Murakami Kakason

---

### Post by Sef on 2006-05-26
I was missing a few things too after an upgrade, this is what I had to do to get them all back.  

Open the Terminal:

sudo apt-get update

sudo apt-get install ubuntu-base ubuntu-desktop

sudo apt-get dist-upgrade

---

### Post by silentb on 2006-05-26
OO2 has been removed from the repository, whatever the reason. Anyway you might want to use the newest version:

[ftp://ftp.rz.tu-bs.de/pub/mirror/OpenOffice.org/localized/en-GB/2.0.2/OOo_OOB680_m5_LinuxIntel_install_en-GB_deb.tar.gz](ftp://ftp.rz.tu-bs.de/pub/mirror/OpenOffice.org/localized/en-GB/2.0.2/OOo_OOB680_m5_LinuxIntel_install_en-GB_deb.tar.gz)

Install via sudo dpgk -i OOo....

---

### Post by Kakason on 2006-05-26
Thanks Sef and  silentb, i finally got it back.

Murakami Kakason

---

### Post by Sef on 2006-05-26
You're welcome.

> OO2 has been removed from the repository, ....

Likely they were updating it then.

---

