---
title: "Themes folder?"
date: 2012-07-10
forum: General Help
---

### Post by Divisi on 2012-07-10
I'm just trying to download a theme for Xubuntu, I did what the instructions told me, but the terminal told me there was no such directory.

Do I simply have to make the folder?

Thanks!

---

### Post by Toz on 2012-07-10
If you're talking about ~/.themes, then yes, create the folder if it doesn't exist. Note that themes placed in this directory will only be available to the user who owns the directory. If you want the theme made available for all users, you need to add it to /usr/share/themes directory (you'll need root priviledges).

---

### Post by Divisi on 2012-07-10
> **Toz said:**
> If you're talking about ~/.themes, then yes, create the folder if it doesn't exist. Note that themes placed in this directory will only be available to the user who owns the directory. If you want the theme made available for all users, you need to add it to /usr/share/themes directory (you'll need root priviledges).

Yes thats it, where exactly do I make it?  Do I have to do .themes or just themes?

---

### Post by Toz on 2012-07-10
It has to be called **.themes** and it has to be in your home directory. If you are using Thunar (the File Manager), make sure you have hidden files enabled (Ctrl+H). You can also create the folder from a terminal window using this command:
```
mkdir ~/.themes
```

---

### Post by sibin xavier on 2012-07-10
Check usr/share/themes

---

