---
title: "Lost Ubuntu from Bootloader"
date: 2012-04-05
forum: General Help
---

### Post by balkrish999 on 2012-04-05
Hello, i installed Ubuntu using Wubi and it was there on the boot loader the option 

I had to re install windows and now the option for ubuntu is gone, 

How do i get it back Please Help ASAP 

Thank You

---

### Post by hughr2005 on 2012-04-05
This may help: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Cheesemill on 2012-04-05
When you use Wubi to install Ubuntu, it installs like any other Windows application with Ubuntu stored in a file on your Windows partition.

By reinstalling Windows you have almost definitely wiped your Ubuntu installation.

---

### Post by bcbc on 2012-04-05
So, from a previous thread you have Ubuntu on a separate 'drive', right? e.g. D:\ubuntu

And you reinstalled Windows on C: ?

So you could do this:
1. copy the wubildr from D:\ubuntu\winboot\wubildr to C:\wubildr
2. add an entry in the BCD store to boot D:\ubuntu\winboot\wubildr.mbr

But it's better and easier to do this:
1. rename D:\ubuntu to D:\origubuntu
2. Install Wubi again with the same Ubuntu release, to the D:\ drive (choose the smallest install size e.g 5GB)
3. Before rebooting, delete the new D:\ubuntu and rename D:\origubuntu back to D:\ubuntu

The second solution seems a lot of work to get a BCD entry to boot ubuntu, but it also enables the 'uninstall' option for the future.

---

