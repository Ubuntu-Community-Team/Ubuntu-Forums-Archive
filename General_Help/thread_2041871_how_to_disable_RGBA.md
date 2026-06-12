---
title: "how to disable RGBA"
date: 2012-08-13
forum: General Help
---

### Post by MRxSNIPES2 on 2012-08-13
how to disable RGBA I am Using Ubuntu 10.04 64-bit.
sorry if i left any thing out just ask me.

---

### Post by johnathansmith on 2012-08-13
Hi, try this:
> 3. Go to System -> Preferences -> Gnome Color Chooser. Go to the Engines tab. Check the box next to Global and choose Murrine in the drop down list next to the check box. Click Preferences. In the window that comes up find 'Configuration of Enable/Disable RGBA support', and check both boxes under that section. Click OK. Click Apply and then Close.


[Source link]("https://wiki.ubuntu.com/DesktopTeam/RgbaGtkWithPPA/")

---

### Post by MRxSNIPES2 on 2012-08-13
OK thank. if i don't want to keep it any more how will i remove it from my system.

---

### Post by johnathansmith on 2012-08-13
It's all in the link that I posted:
> Uninstallation
If you install it and then hate it - don't worry. It can easily be put right.

1. Go to System -> Administration -> Synaptic Package Manager.

2. Click the Origin button in the bottom left hand corner.

3.

If you're running Karmic:
If you're running Lucid:
Select ppa.launchpad.net/main from the sidebar on the left
Select the 'erik-b-andersen/rgba-gtk' PPA from the sidebar on the left
4. Select each of nautilus, nautilus-data, libnautilus-extension1, murrine-themes, and gtk2-engines-murrine in turn, going to Package -> Force Version and choosing the version of that package that does not have ppa in it.

5. When you've marked all that can be for downgrading click Apply and Apply (again).

6. Go to Settings -> Repositories.

7. On the Other Software Tab, select the 'http://ppa.launchpad.net/erik-b-andersen/rgba-gtk/ubuntu' source, and click Remove.

8. Click Close and Close (again).

9. In the sidebar, click the Sections button and then select All.

10. Search for gnome-color-chooser and mark it for removal, and then search for gtk2-module-rgba and mark it for complete removal.

11. Click Apply and Apply (again). Close synaptic.



---

### Post by MRxSNIPES2 on 2012-08-16
OK i am now just getting to it and i keep getting this

E: Unable to correct problems, you have held broken packages.
E: Unable to lock the download directory

OK i got it back now just with in 10min of retrying.
thanks for the help.

---

