---
title: "Installing gnome from livecd"
date: 2010-04-15
forum: General Help
---

### Post by Jforce93 on 2010-04-15
Hi everyone,

I managed to mess up GNOME on my ubuntu laptop. Now, I can't connect to the internet because the network manager applet is removed. Is there anyway to reinstall gnome from the livecd of ubuntu? Also, I want to uninstall GNOME and install LXDE, is there anyway to do this without uninstalling any of the applications that are installed by default with gnome, such as openoffice.org or firefox?

Thanks,

Jordan

---

### Post by ttshivers on 2010-04-15
I have an answer for your question about installing LXDE:

You can install LXDE very easliy.  Even if you install LXDE, you should still keep gnome installed just in case.  To install LXDE, open the ubuntu software center and type LXDE in the search box.  An item should come up that says LXDE.  Install that package and reboot your computer.  When the login screen appears, click on your username and then change the season box (which is at the bottom of the screen) to LXDE.  When you install LXDE, it will not remove any programs or files.

---

### Post by ajgreeny on 2010-04-15
The *network manager applet* alone is not needed to connect to the internet, but *network-manager* is.  Is that what you mean?  What exactly did you do to get into this pickle?

If so you will need to download *network-manager* and *network-manager-gnome* using a live CD onto a USB drive, and then install them to your hard disk installation using ```
sudo dpkg -i network-manager-gnome network-manager
```, as I don't think you can use a live CD as a repository, unless things have changed from previous ubuntu versions.

---

### Post by Jforce93 on 2010-04-15
> **ajgreeny said:**
> The *network manager applet* alone is not needed to connect to the internet, but *network-manager* is.  Is that what you mean?  What exactly did you do to get into this pickle?

If so you will need to download *network-manager* and *network-manager-gnome* using a live CD onto a USB drive, and then install them to your hard disk installation using ```
sudo dpkg -i network-manager-gnome network-manager
```, as I don't think you can use a live CD as a repository, unless things have changed from previous ubuntu versions.

Would i have to cd into the directory with the file in it before i install it. I just download it, no apt-on CD, right?

---

### Post by zvacet on 2010-04-15
> Would i have to cd into the directory with the file in it before i install it.

Yes and easier way is to download it to your home directory.For installing LXDE (after you establish network connection) find in synaptic **lubuntu-desktop** and install it.

---

### Post by Jforce93 on 2010-04-15
> **zvacet said:**
> Yes and easier way is to download it to your home directory.For installing LXDE (after you establish network connection) find in synaptic **lubuntu-desktop** and install it.

Where can i download it from?

---

### Post by Jforce93 on 2010-04-15
I'm gonna try to connect to the internet using ifconfig and install lxde!

---

### Post by zvacet on 2010-04-16
You can try to connect with 

```
sudo pppoeconf
```

That should work and after that you can install network manager with 

```
sudo apt-get install network-manager-gnome network-manager
```

for LXDE

```
sudo apt-get install lubuntu-desktop
```

---

### Post by ajgreeny on 2010-04-16
You will not be able to download lubuntu-desktop to a third party machine and then copy it over to yours and useit, I'm afraid.  That package is just a meta-package and does not actually contain all the package requirements of LXDE; it simply tells the system which to download from the repos, so web access is needed for that.

---

