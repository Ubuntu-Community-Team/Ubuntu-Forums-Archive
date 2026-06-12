---
title: "Problems with synaptic package manager"
date: 2006-02-19
forum: General Help
---

### Post by shiroma on 2006-02-19
i am trying to install wine and whenever i run synaptic package manager or apt-get upgrade i get this:

W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by metwo on 2006-02-19
That's because ftp.free.fr is down/doesn't exist. What's in your sources.lst? You might want to comment out that line.

This goes through how to install wine: [https://wiki.ubuntu.com/Wine](https://wiki.ubuntu.com/Wine)

---

### Post by Sutekh on 2006-02-19
Not really a problem, just a bummed repository.

Your repository list is stored in this file
```
/etc/apt/sources.list
```
You can simply comment out (using a #) the offending repository, and this will go away.  When the repository is back up, remove the #.  If the repository is dead, then probably remove the line altogether.

Try this code in a terminal window (from the Menu; Applications -> Accesories -> Terminal)
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```This will backup the list, so you can always change it back, and then allow you to edit the file.

Once you are in then you can comment (#) out the repository.


 - Here's a good link for up-to-date repositories
[Up-To-Date Repositories - by ]("http://www.psychocats.net/linux/sources.php")[aysiu]("http://www.ubuntuforums.org/member.php?u=21941")

 - To install wine you will need this repository too (add it to your sources.list)
```
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/
```

 - That wiki link is good too, for instructions to install wine.

---

