---
title: "I have an Ubuntu Laptop I cannot get access to"
date: 2012-08-27
forum: General Help
---

### Post by bleutyler on 2012-08-27
So, a laptop had Ubuntu 10.X and Win 7.  It belongs to my wife who wanted it to boot from windows instead of Linux.  

So I booted into Windows, had it repair the master boot record though the Control Panel.  So now the laptop boots instantly to windows.  

However, I need to undo that operation, and boot into the Ubuntu 10.X partition.  There are SSH keys on it that are installed on the remote server, so if I boot in there, I can ssh right away and be fine.

So while I am googling, if anyone has a suggestion, I will appreciate it.

---

### Post by spiky001 on 2012-08-27
Hi  You can boot into it using a live cd, To repair grub you would have to reinstall grub from ubuntu live cd. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)  Also to change boot order look at this post [http://ubuntuforums.org/showpost.php?p=11678390&postcount=12](http://ubuntuforums.org/showpost.php?p=11678390&postcount=12)

---

### Post by bleutyler on 2012-08-27
Due to issues with grub, I was unable to install it from the Live CD.  

The boot-repair tool did not work, it would not install because it could not find the apt-get repository.

attempting to use 'grub install' did not work either, as I was getting errors with that.  

I needed it done as soon as possible, so I just installed 9.04 from a LiveCD into the smallest partition, then when it loaded grub, the original 10.04 installation was an option in Grub.

Not ideal, but it was fixed.

---

