---
title: "file sharing"
date: 2009-09-02
forum: General Help
---

### Post by ALnot on 2009-09-02
I have a vista box and an Ubuntu 8.04 box I want to share files.
For example, I have Netbeans 6.7.1 on the vista box and want to transfer
it to the Ubuntu box and install it.

Thanks,
total fng.

---

### Post by zoogTHOMzoog on 2009-09-03
You most likely will have to download a linux version of netbeans... there is one in the repo's, just search for it in Synaptic, or from the terminal type ```
sudo apt-get install netbeans
```.

As for file-sharing with Vista / Linux, there are several howto's on this forum

---

### Post by CaesarLike on 2009-09-03
For a simple file sharing solution, install oppenssh server onto the ubuntu machine, then download WinSCP for the vista box.  You then simply use winscp to log into your Ubuntu box using SSH and move files between the 2 computers.  You can get winscp here:
[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

---

### Post by sanderj on 2009-09-03
> **ALnot said:**
> I have a vista box and an Ubuntu 8.04 box I want to share files.
For example, I have Netbeans 6.7.1 on the vista box and want to transfer
it to the Ubuntu box and install it.

Thanks,
total fng.

You can use normal Windows browsing & sharing on your LAN. On Linux, it's called Samba.

Easy method: using the file browser Nautilus on Ubuntu, right click the directory you want to share, and start sharing.

Long, long, old-skool story: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by ALnot on 2009-09-03
thanks ALnot

---

