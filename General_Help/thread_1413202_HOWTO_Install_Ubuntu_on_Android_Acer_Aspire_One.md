---
title: "HOWTO: Install Ubuntu on Android Acer Aspire One"
date: 2010-02-22
forum: General Help
---

### Post by 3rdalbum on 2010-02-22
Some of the new Acer Aspire One netbooks are set up for dual-boot Windows 7 and Android. Fortunately, we can turn this into dual-boot Ubuntu/Android!

First, boot up the machine into Windows 7. Follow the prompts to set up a first username and password. After the reboot, you'll be given the opportunity to set up some basic Android settings from within Windows. When you perform this step you gain the ability to boot Android. You can choose whether to have the machine boot up to Android first, or to Windows (Ubuntu) unless you hit F9. Choose carefully - once Windows is gone, you won't be able to change this setting AFAIK.

Now shut down Windows and boot up the Ubuntu CD or USB. At the partitioning screen, choose "Specify partitions manually". The main basis behind this is to preserve the 8 gigabyte partition, because this is the Android partition (it's a fat32 partition around the middle of the partition table).

So, change the partitioning however you like, as long as you keep this 8 GiB partition. Specify a partition as / and another partition as 'swap' (optional).

Continue to install Ubuntu as normal. When you next reboot, you'll either:

a. Boot straight into Ubuntu through GRUB unless you hit F9 to go to Android
b. Boot straight into Android unless you hit F9; once in Android you can use the icon at the top-left to switch to Ubuntu (through GRUB).

And that's all there is to it.

---

