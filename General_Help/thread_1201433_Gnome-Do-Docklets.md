---
title: "Gnome-Do-Docklets"
date: 2009-07-01
forum: General Help
---

### Post by Shady3D on 2009-07-01
any one here knows how to get Gnome-Do-Docklet to work

---

### Post by smorar on 2009-07-01
The docklets don't seem to be in their repository PPA yet. So I downloaded the source, compiled it and created a deb package using checkinstall. I have attached my package here.

The docklets can be enabled in the Gnome-Do preferences under the Appearance tab with the Docky theme selected. You can configure the docklets in the Plugins tab after selecting Docklets in the drop down menu.

Enjoy :)

---

### Post by El_Tate on 2009-08-15
Hey, i've installed it on the 0.8.1 release under Intrepid and i don't see any docklets :S. Any clue?

Thanks

---

### Post by Shady3D on 2009-08-16
> **El_Tate said:**
> Hey, i've installed it on the 0.8.1 release under Intrepid and i don't see any docklets :S. Any clue?

Thanks

you should add the [gnome-do ppa]("https://launchpad.net/~do-core/+archive/ppa") in the software sources, and add the key

Update the software sources, then go check for updates in the Update Manager, you should be able to find the latest package

---

### Post by El_Tate on 2009-08-16
Hey, i've it already, but the version is the 0.8.1 instead of the 0.8.2 that the docklets have.

So... i think that we'll have to wait to get the 0.8.2 proper released for intrepid. The thing is, i won't update my whole OS for that..., i just wait to the end of the year, i think, and luckly i'll update. I've a lot of info and i'm lazy to backup my entire home folder :p

Thanks

---

