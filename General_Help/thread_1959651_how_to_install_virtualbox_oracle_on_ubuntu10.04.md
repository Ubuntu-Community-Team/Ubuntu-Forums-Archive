---
title: "how to install virtualbox oracle on ubuntu10.04?"
date: 2012-04-16
forum: General Help
---

### Post by ubto66 on 2012-04-16
Can I install latest virtualbox using terminal?

If I have to install using this procedure
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Then what does this part mean?
**"Debian-based Linux distributions**

  **Note:** VirtualBox has been moved from *non-free* to *contrib* with 4.0, so please adjust your repository settings. 
  Add one of the following lines according to your distribution to your /etc/apt/sources.list:"


Thanks.

---

### Post by JCM_Pico on 2012-04-16
> **ubto66 said:**
> Can I install latest virtualbox using terminal?

If I have to install using this procedure
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Then what does this part mean?
**"Debian-based Linux distributions**

  **Note:** VirtualBox has been moved from *non-free* to *contrib* with 4.0, so please adjust your repository settings. 
  Add one of the following lines according to your distribution to your /etc/apt/sources.list:"


Thanks.
 
1 - You just need to download *.deb packaged (i386 for a 32bit system and AMD64 for a 64bit system)


Ubuntu 10.04 LTS ("Lucid Lynx") [ i386]("http://download.virtualbox.org/virtualbox/4.1.12/virtualbox-4.1_4.1.12-77245%7EUbuntu%7Elucid_i386.deb") | [ AMD64]("http://download.virtualbox.org/virtualbox/4.1.12/virtualbox-4.1_4.1.12-77245%7EUbuntu%7Elucid_amd64.deb")

Then is just click to install

2 - **"Debian-based Linux distributions" **... Well linux distributions that are base in debian... Ubuntu is one of them.... but for installing it would probably be easier to just download the *.deb file and click on it

---

### Post by ubto66 on 2012-04-16
Thank you for the answer.
I downloaded and installed the package the way you suggested, and the 
machines work.
During installation I got this fail message
"Trying to register the virtualbox kernel modules using DKMS
Failed trying without DKMS
Recompiling virtualbox kernel modules"

Should something be done?

---

### Post by JCM_Pico on 2012-04-16
Check this link... [https://forums.virtualbox.org/viewtopic.php?f=7&t=35248](https://forums.virtualbox.org/viewtopic.php?f=7&t=35248) and you got your question solved :p

---

### Post by ubto66 on 2012-04-16
Thanks.
I understand this
you get a kernel update
but I don't understand the sentence
you need to manually install the kernel modules again by issuing '/etc/init.d/vboxdrv setup' as root.
How do you issue etc?

---

### Post by Habitual on 2012-04-16
Terminal >
```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by ubto66 on 2012-04-16
Thank you.
I think I got it now.

---

### Post by CharlesA on 2012-04-16
By default Vbox will use DKMS - do you not have it installed?

DKMS makes kernel upgrades much less painful.

---

