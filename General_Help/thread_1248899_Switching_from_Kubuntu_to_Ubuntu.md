---
title: "Switching from Kubuntu to Ubuntu"
date: 2009-08-24
forum: General Help
---

### Post by elusivespoon on 2009-08-24
Some time ago I installed enough KDE applications that the Kubuntu start up screen is now the default. I'm also experiencing a problem with a special key on my laptop which it has been [suggested]("http://ubuntuforums.org/showthread.php?t=734788") is a result of some KDE shortcuts.

The point being I'd like to switch back to configurations default for an Ubuntu install without having to install from a CD again. I have installed 'ubuntu-desktop' but that didn't do the trick.

---

### Post by starcraft.man on 2009-08-24
> **elusivespoon said:**
> Some time ago I installed enough KDE applications that the Kubuntu start up screen is now the default. I'm also experiencing a problem with a special key on my laptop which it has been [suggested]("http://ubuntuforums.org/showthread.php?t=734788") is a result of some KDE shortcuts.

The point being I'd like to switch back to configurations default for an Ubuntu install without having to install from a CD again. I have installed 'ubuntu-desktop' but that didn't do the trick.

Can't you simply at Login manager (i.e. after GRUB) just go Options > Sessions > GNOME and then login and take ya to GNOME. After that, should default to gdm and gnome for later logins. Once set, feel free to uninstall the kde or kubuntu-desktop packages which I assume ya have to have kubuntu as an option to login. Removal shouldn't be big problem, if ya need help, see my installation sig on software management or stickies in beginners talk section.

---

### Post by rcayea on 2009-08-24
I am no expert on this issue, but I would suggest that you go to synaptic and look for any KDE apps and remove them. I had to do this. Also, look for KDE core files and KDE desktop. If you did install Gnome already then removing KDE won't cause any mishap at next boot.

---

### Post by philcamlin on 2009-08-24
remove all kde apps then login to the gnome session

---

### Post by 67GTA on 2009-08-24
To get gnome login screen back, open a terminal and run ```
sudo dpkg-reconfigure gdm
``` and select gdm as the default. Then run ```
sudo update-alternatives --config usplash-artwork.so
``` to select the default usplash. Then update the kernel image to include the changes with ```
sudo dpkg-reconfigure linux-image-$(uname -r) 			 		
``` You will have to manually remove anything else KDE related you don't want anymore.

---

### Post by elusivespoon on 2009-08-24
I guess I need to be a little more clear. I seem to actually be between states of Kubuntu and Ubuntu. The boot screen is Kubuntu. The login manager is GDM. The main problem (as I understand it from the thread I linked to) is Kubuntu changed some configurations. So I'd like to do more than remove all the KDE apps and use GDM, but reset to the Ubuntu default configurations. Though I am a little murky on what configurations exactly were messed up, so I guess that isn't much help. . .

---

### Post by 67GTA on 2009-08-24
> The boot screen is Kubuntu.

Use the usplash command I posted to choose Ubuntu's default and then update the kernel image. You will have The orange/brown boot screen again. Other than that, there shouldn't be any other messed up configurations. KDE uses separate folders for it's settings, and don't affect Gnome settings. If it is booting into KDE, then look for a button on the login screen and choose gnome as the default session.

---

### Post by snowpine on 2009-08-24
Here you go:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

