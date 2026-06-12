---
title: "Menu Problems"
date: 2009-07-19
forum: General Help
---

### Post by wrwarwick on 2009-07-19
I am having a problem with my default menu in Ubuntu 9.04. When I right click and select edit menu, nothing happens. If I open a terminal and type "sudo alacarte" the menu editor opens. 

One other issue to add to this is I added a program launcher for ies4linux to the internet menu when using the sudo alacarte command. Now when I open it the launcher is not listed in the menu and I would like to remove it from there.

---

### Post by drs305 on 2009-07-19
One of the possible reasons for this is your menu folder is not owned by you or you don't have the correct permissions for some reason. Open nautilus with root privileges and check the ownership of the "~/.config/menus" folder and its applications.menu file (and possibly the rest in the folder). (Right click the folder or file, Properties, Permissions). You should own the folder/file and have read/write privileges. You can select yourself as the owner and set permissions by right clicking, Properties, Permissions. Or just reset the ownership to yourself with the second command and ensure you have the correct permissions.

```

gksudo nautilus $HOME/.config/  # Check ownership/permissions
sudo chown -R *yourusername*: $HOME/.config/menus

```

The individual files within the menus folder should allow you to read/write to them (mine are set to 644).

---

### Post by wrwarwick on 2009-07-19
Thanks for the info. For some reason my home folder's permissions were off so I did some searching and reset them. Everything seems to be working fine now.

Thanks again!

---

