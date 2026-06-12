---
title: "Setting default file manager in Xubuntu"
date: 2010-05-13
forum: General Help
---

### Post by rmcellig on 2010-05-13
Is there a GUI that will allow me to set a default file manager for Xubuntu? I would like to use the Nautilus File manager. Right now I access Nautilus from a launcher I have on my Panel. I would like to have the ability to switch file managers, set defaults etc... and hope that there is something out there that would allow me to do this.

---

### Post by mr_pouit on 2010-05-13
> **rmcellig said:**
> Is there a GUI that will allow me to set a default file manager for Xubuntu? I would like to use the Nautilus File manager. Right now I access Nautilus from a launcher I have on my Panel. I would like to have the ability to switch file managers, set defaults etc... and hope that there is something out there that would allow me to do this.

I don't know any GUI, but you can do that by setting Nautilus instead of Thunar as the default application for the following mimetypes:
* x-directory/gnome-default-handler
* x-directory/normal
* inode/directory

---

