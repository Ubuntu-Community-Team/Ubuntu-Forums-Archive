---
title: "Aircrack-ng Help/RTL8187B Wireless Card"
date: 2010-03-07
forum: General Help
---

### Post by Skyxz on 2010-03-07
Hello, So i'm trying to install Aircrack-NG on an Ubuntu 9.10 Virtual Server, Using Sun Virutalbox.

```
Computer Stats:

Model: Toshiba Satellite Pro L300
Model No. PSLB1A-02D008
Wireless Card: Realtek RTL8187B
Ubuntu 9.10
```

Issue:

I have installed Aircrack-NG using the following terminal code:

```
sudo apt-get install aircrack-ng
```

And i had also downloaded Aircrack-NG from the "aircrack-ng.org" website.
So i did the following in terminal in hopes to patch my driver:

```
tar xfz aircrack-ng-1.0.tar.gz
cd Desktop
cd aircrack-ng-1.0
cd patches
sudo modprobe rtl8187 < It's missing the B for RTL8187B
```

It went to a new line, and didn't say it couldn't find the module. So i think it's patched.

Where do i go from here? To crack a wireless network? I'm stuck lol.
If you need any info like lspci, just tell me so. I'll get it.

Thanks so much!

---

