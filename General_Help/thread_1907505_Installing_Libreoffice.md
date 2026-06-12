---
title: "Installing Libreoffice?"
date: 2012-01-11
forum: General Help
---

### Post by googleye on 2012-01-11
Just downloaded ubuntu to my dhd for testing purposes, planning on writing some of my schoolwork on my phone if possible. So I enter libreoffice.org and in the download section I'm being recommended a rpm package 32-bit. Enter terminal, tar -xvfz "filename", and I get some strange error about "z" not existing or something. If I try without the "z" it works but when I cd to the folder and type ./configure there's no such folder or file. What's wrong?

---

### Post by itman on 2012-01-11
Install with apt-get this will resolve dependicies

---

### Post by cryptotheslow on 2012-01-11
rpm packages are not intended for Ubuntu systems.

I thought LibreOffice was installed by default with an Ubuntu Desktop install anyway so should already be there. If not it should be available in the repositories for you to install via Software Centre or Synaptic package manager (depending what version of Ubuntu you have installed).

---

### Post by bluexrider on 2012-01-11
> **googleye said:**
> Just downloaded ubuntu to my dhd for testing purposes, planning on writing some of my schoolwork on my phone if possible. So I enter libreoffice.org and in the download section I'm being recommended a rpm package 32-bit. Enter terminal, tar -xvfz "filename", and I get some strange error about "z" not existing or something. If I try without the "z" it works but when I cd to the folder and type ./configure there's no such folder or file. What's wrong?

Run this code in terminal

```
sudo apt-get install libreoffice
```

---

