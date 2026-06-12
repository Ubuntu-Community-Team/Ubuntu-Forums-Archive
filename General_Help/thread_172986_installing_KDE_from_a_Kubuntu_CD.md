---
title: "installing KDE from a Kubuntu CD"
date: 2006-05-09
forum: General Help
---

### Post by thiagoms on 2006-05-09
I'm using Ubuntu 5.10 and I'd like to test the KDE interface. Since I use dial-up connection ](*,) , dowloading kubuntu-desktop is out of question. A friend of mine gave me a Kubuntu 5.10 installation CD. How do I do to install KDE from this CD without removing Gnome or messing up with my packages?

---

### Post by aysiu on 2006-05-09
Put in the CD. Wait for it to mount.

Go to System > Administration > Synaptic Package Manager

Then go to Edit > Add CD-ROM
Add the CD-ROM as a source.

Then, just to be safe, go to Settings > Repositories and uncheck all the boxes next to the online sources. Leave only the CD-ROM source checked.

Do **not** then install Kubuntu through Synaptic. Close Synaptic.

Go to a terminal and copy and paste these commands: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` Then, go back to Synaptic and add the online sources and uncheck the CD-ROM source.

It's important you install KDE through *aptitude* as Synaptic and apt-get will not keep track of dependencies, so if you later decide, "Eh, I could do without KDE. I think I was to uninstall it," ```
sudo aptitude remove kubuntu-desktop
``` will actually remove not only *kubuntu-desktop* but also all the dependencies that came along with it.

Removing *kubuntu-desktop* with apt-get or Synaptic will remove only the pointer (which won't effectively remove anything).

---

### Post by Thirsteh on 2006-05-09
what he said above :)

---

