---
title: "installing local .deb pkg with synaptic ?"
date: 2010-04-04
forum: General Help
---

### Post by birdy62 on 2010-04-04
Hi,
Is it possible to install a local .deb package with synaptic package manager?  I managed to trash network-manager-gnome removing it by mistake instead of a package with a similar name..... oops:oops:. So now have no network connections. I downloaded the following file [network-manager-gnome_0.8~a~git.20091014t134532.4033e62-0ubuntu1_i386.deb]("file:///C:/network-manager-gnome_0.8%7Ea%7Egit.20091014t134532.4033e62-0ubuntu1_i386.deb") via a computer with a net connection. and now have it on a usb key. Can I point the synaptic package manager to the local package and install like that, or do I have to do it via the console. I also have my original Karmic 9.10 disk, which I imagine has the package on as well.  Is there a way to add it via the system installer? Which would be the best if any?

thanks

---

### Post by amite on 2010-04-04
i think  u need to do this........

open Setting>>repository in sysnaptic package manager and then add "Cdrom with ubntu 9.10 'karmic kuala'. then click reload and then apply.......it will install ur missing packages.

---

### Post by 3rdalbum on 2010-04-04
No need to tell Synaptic about this package; just double-click it and the Gdebi Packagte Installer will appear. If it tells you that you are missing some dependencies, you would have to go and download those and install them first.

---

### Post by ugm6hr on 2010-04-04
> **3rdalbum said:**
> No need to tell Synaptic about this package; just double-click it and the Gdebi Packagte Installer will appear. If it tells you that you are missing some dependencies, you would have to go and download those and install them first.

Exactly.

For non-networking related .deb files, you can copy the file to /var/cache/apt/archives/ and then just use Synaptic as normal.

This has the benefit of downloading & installing any dependencies necessary.

However, without a network connection, this wouldn't add anything over just double-clicking and opening with GDebi.

---

### Post by birdy62 on 2010-04-04
Ok thanks everybody. It's fixed. Thanks. I double clicked on the .deb package which installed ok . It gave me some trouble with the wireless connection repeatedly asking for the password for my connection. Luckily it accepted a connection with an ethernet cable and I went online an re-installed the package via synaptic. Wireless connection is now fine.

---

