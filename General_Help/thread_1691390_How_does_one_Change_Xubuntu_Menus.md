---
title: "How does one Change Xubuntu Menus?"
date: 2011-02-19
forum: General Help
---

### Post by oaxacamatt1 on 2011-02-19
Hi All,
I was noodling around the forums one time and found an awesome '*article*,' '*wiki*,' '*post*' (you get the idea) on how to change the Xubuntu Main Menus for 10.04 LTS. I saw/found it **once** on the Ubuntu website but can't find it now.

Anybody now to find the best info for my question??
Cheers,
M

---

### Post by mr_luksom on 2011-02-19
You edit the menus manually in xubuntu. Forgive me if this is wrong, it has been a few months since I have used xubuntu.

The menu for your user is stored here:
~/.config/menus/xfce-applications.menu

To edit it, you can navigate there with Thunar by unhiding hidden files (Ctrl+H), and edit with mousepad.

The shared menu between all users is stored here:
/etc/xdg/menus/xfce-applications.menu
You will need su permission to edit this. Enter the terminal and type:

```

sudo mousepad /etc/xdg/menus/xfce-applications.menu

```

---

### Post by oaxacamatt1 on 2011-02-19
Although I do appreciate your ideas, the help you gave did not work on either account.  There is no folder '~/.config/menus/xfce-applications.menu' nor is '/etc/xdg/menus/xfce-applications.menu' correct either.
Sorry Luksom

Some one else. ;}

---

