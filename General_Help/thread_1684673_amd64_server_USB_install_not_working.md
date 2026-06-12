---
title: "amd64 server USB install not working"
date: 2011-02-09
forum: General Help
---

### Post by Perka on 2011-02-09
Hi,

I tried to install Ubuntu server amd64 using the Universal-USB-installer that is linked to at the download page.

Once I got the the boot screen and chose to install Ubuntu it didn't work.
I had a look at the boot options given for the install and I found:
install/netboot/ubuntu-installer/i386

I had a look at my new boot-USB-stick and found that this didn't exist.
I had ../ubuntu-installer/amd64 (as expected)

So I copied the amd64 files into a i386 folder and then I was able to start the installer.

Is this a issue with the Ubuntu Server amd64 10.4 LTS install ISO or is it the Universal-USB-Installer that mess up things?

/P

---

