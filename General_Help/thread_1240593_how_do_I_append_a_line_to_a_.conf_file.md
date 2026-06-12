---
title: "how do I append a line to a .conf file?"
date: 2009-08-14
forum: General Help
---

### Post by 3pinner on 2009-08-14
I have to append a line to the dhclient.conf file. How do I do that?

---

### Post by starcraft.man on 2009-08-14
Open it with any text editor with root priveledges. For example, to edit the file with gedit, the gnome text editor do the following in a terminal (Applications > Accessories > Terminal):

```
gksudo gedit /etc/dhcp3/dhclient.conf
```

When you don't know the path to the file, use Places > Search. Usually finds it quick, just make sure to set the Look In setting to File System (root directory and below) rather than home only.

---

### Post by ad_267 on 2009-08-14
If it requires root access to edit you can press Alt+F2 and run "gksudo gedit" and then use the text editor to browse to that file and edit it, adding the line to the end of the file.

From the command line you can run:
```
echo "line to add" | sudo tee -a /path/to/file
```

---

### Post by credobyte on 2009-08-14
```
echo "this will be in a new line" >> $HOME/output.txt

```

If you can't do it as a *normal* user, switch to root by entering *sudo -i* !

---

