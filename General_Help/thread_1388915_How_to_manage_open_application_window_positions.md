---
title: "How to manage open application window positions"
date: 2010-01-23
forum: General Help
---

### Post by dale8458 on 2010-01-23
I want to find a utility that will allow me to manage the size, position of open application windows.  Like tile, cascade of that other OS.  So if I have my FTP, Editor, Terminal, Browser I can organize the screen ...

---

### Post by BraedonVickers on 2010-01-23
If your machine can run compiz, have a look into some of the advanced options in that. If i remember correctly, there are some window management features in there that may help.

---

### Post by dale8458 on 2010-01-23
I have Ubuntu 9.10 64 bit  Is compiz load with a stock install?  I am a bit confused over compiz, gnome, and there is some other name as well.  Do you have a moment to set me straight?

Thanks

---

### Post by BraedonVickers on 2010-01-23
Gnome is basically your entire graphical interface. It is a project that  provides your desktop environment, and a lot of the standard  applications that come with Ubuntu, and other gnome based distributions.

Compiz is basically a flash window manager(draws/manipulates the windows  on the screen), that replaces the standard one from gnome. It gives  you assorted cool effects. It should come with ubuntu by default. You  can attempt to enable it via  System->Preferences->Appearance->Visual Effects->Extra. If  this works, you are then running compiz. If it doesn't, then your  graphics drivers are not up to the task.

To get into the custom settings, you will need to install the setting  manager gui.
```
sudo aptitude install compizconfig-settings-manager
```That should install the manager, with a menu item under  System->Preferences(i believe). There is a WHOLE lot of things you  can do with compiz, so have fun :)

Hope that helps,

   Braedon

---

