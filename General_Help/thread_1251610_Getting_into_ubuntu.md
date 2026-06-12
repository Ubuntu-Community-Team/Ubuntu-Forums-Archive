---
title: "Getting into ubuntu"
date: 2009-08-27
forum: General Help
---

### Post by robbypaul on 2009-08-27
I have recently installed windows 7 onto my computer, and now it does not give me the option to either boot into ubuntu or windows when i start up. There is a file that i really need in ubuntu. I either need to find out how to access files from ubuntu on windows or how to boot back into ubuntu.

---

### Post by lisati on 2009-08-27
How was Ubuntu instaleld - with Wubi or into its own partition?

---

### Post by robbypaul on 2009-08-27
> **lisati said:**
> How was Ubuntu instaleld - with Wubi or into its own partition?
Um what is the difference between the two? :/

sorry im a bit new to this

---

### Post by themusicalduck on 2009-08-27
Difference is that a wubi installed is installed from within windows using the installer on the Ubuntu CD. If it was installed to it's own partition, then you either booted up the computer using the CD and installed it from there, or it came pre-installed on your computer.

---

### Post by blueridgedog on 2009-08-27
Can you clarify if you just want the file or if you want to get your system dual booting?

---

### Post by robbypaul on 2009-08-27
Wubi is what i used, i would like to get the file it is a text document.

---

### Post by robbypaul on 2009-08-27
Can anyone help please

---

### Post by Vince N on 2009-08-27
When you installed Windows 7,The windows 7 installer overwrote your Linux boot loader.  (I love how Microsoft doesn't care what else you have on your machine) Thats why you cannot boot into Linux.  The good news is that your files are still all intact and all you need to do is reinstall Grub.  There are several utilities that can assist you with this (My favorite is super grub disk) I don't remember the specifics it's been almost a year since I had to reinstall windows.  This article should help.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by robbypaul on 2009-08-27
> **Vince N said:**
> When you installed Windows 7,The windows 7 installer overwrote your Linux boot loader.  (I love how Microsoft doesn't care what else you have on your machine) Thats why you cannot boot into Linux.  The good news is that your files are still all intact and all you need to do is reinstall Grub.  There are several utilities that can assist you with this (My favorite is super grub disk) I don't remember the specifics it's been almost a year since I had to reinstall windows.  This article should help.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

ok i will do this thanks

---

### Post by Vince N on 2009-08-27
Let us know how it goes.

To prevent this in the future just keep in mind you want to install Windows FIRST and then Ubuntu if at all possible.  This way Windows won't overwrite your boot loader.

---

### Post by blueridgedog on 2009-08-28
> **Vince N said:**
> When you installed Windows 7,The windows 7 installer overwrote your Linux boot loader.  (I love how Microsoft doesn't care what else you have on your machine) Thats why you cannot boot into Linux.  The good news is that your files are still all intact and all you need to do is reinstall Grub.  There are several utilities that can assist you with this (My favorite is super grub disk) I don't remember the specifics it's been almost a year since I had to reinstall windows.  This article should help.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I do not think this is how a Wubi install works and I suspect that if the poster installs grub, it will not change things.  Sadly, I don't know enough about wubi to help.

---

### Post by muteXe on 2009-08-28
Nor me, but if you;ve installed your new windows over your old windows then you may have lost your ubuntu stuff.

---

### Post by linux_tech on 2009-08-28
> **robbypaul said:**
> I have recently installed windows 7 onto my computer, and now it does not give me the option to either boot into ubuntu or windows when i start up. There is a file that i really need in ubuntu. I either need to find out how to access files from ubuntu on windows or how to boot back into ubuntu.
You may try Ext2 IFS - [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

