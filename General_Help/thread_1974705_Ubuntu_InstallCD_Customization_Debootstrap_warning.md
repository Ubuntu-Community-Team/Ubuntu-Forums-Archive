---
title: "Ubuntu InstallCD Customization Debootstrap warning"
date: 2012-05-06
forum: General Help
---

### Post by tyrant92 on 2012-05-06
Hello guys, I need helps here.

I was making a customized version of Ubuntu Alternate CD 11.10. I did step-by-step tutorial in this webpage ([https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)). SO, at first, I didn't do anything except added sentence "Install custom installation" and made custom preseed file. Then, I did the "build repository using apt-ftparchive" section. Then I burned the file into iso.

Then, I used virtualBox to install my custom version of ubuntu alternate cd. In the installation process "installing base system", I got a debootstrap warning.

Failing to run chroot dpkg /target --force-depends --install:
/var/cache/apt/archive/base-files.deb
/var/cache/apt/archive/base-passwd.deb

When I pressed "CTRL+F4", I got warning:
"Invalid user 'root:root`.
I have no idea what wrong with steps I did. I did what the website told precisely.

How do I overcome this warning? 

Thanks in advance.

---

### Post by Lo Phat on 2012-05-20
I don't believe you did anything wrong, I have been creating an install CD for quite sometime now, and using Precise is the first time I received this error.  I believe it's a debootstrap bug, but not quite sure how to fix it.  It seems like base-files needs base-passwd to setup up /etc/passwd, but bass-passwd needs base-files to create the /etc directory!  You can keep going, by repeating the same step in the install, but I am not sure how to remove the error.  I will repost if I figure it out.

---

