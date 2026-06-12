---
title: "ati driver"
date: 2006-04-22
forum: General Help
---

### Post by sunrex on 2006-04-22
hello, im attempting to install my ati driver, but when i try to install it this happens:

> darksoul@secure-one:~/Desktop$ sudo sh ati-driver-installer-8.24.8-x86_64.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.24.8............................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: Xorg 7.0.0

Detected version of X does not have a matching 'x700_64a' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430_64a    XFree86 4.3.x 64-bit
    x680_64a    X.Org 6.8.x 64-bit
    x690_64a    X.Org 6.9.x 64-bit
Removing temporary directory: fglrx-install


---

### Post by cwmccabe on 2006-04-22
You might try here: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by sunrex on 2006-04-22
i run dapper, and im trying to install ati...

it says what i put up there, i just dont know how to fix it..

"#

If the ATI driver installer complains about your Xorg 7.0.0 (Dapper flights) being too new, use following:

X_VERSION=x690 fakeroot ./ati-driver-installer-<version>.run

"

... that doesnt work, fakeroot doesnt work.. can anyone give me the command needed

---

### Post by Ramses de Norre on 2006-04-22
sudo apt-get install fakeroot

---

