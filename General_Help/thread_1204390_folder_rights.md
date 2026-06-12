---
title: "folder rights"
date: 2009-07-04
forum: General Help
---

### Post by PowerSource on 2009-07-04
i was going to install a theme, and the website said that i had to place som folders into /usr/share/themes but when i try to paste there it won't let me do it!
what do i have to change/do to paste the folders there?:???:

---

### Post by michy99 on 2009-07-04
You need to give yourself temporary root permissions. To do it with the file manager, press alt-F2 and enter```
gksudo nautilus
```Do what you need to do and then close the window.

---

### Post by wojox on 2009-07-04
Try

System -> Administration ->Login Window

Then local tab and add button

---

### Post by PowerSource on 2009-07-04
> **michy99 said:**
> You need to give yourself temporary root permissions. To do it with the file manager, press alt-F2 and enter```
gksudo nautilus
```Do what you need to do and then close the window.

so when i quit the terminal, the permissions disappear again?

---

### Post by michy99 on 2009-07-04
You do not need to have root permissions all the time. This is an important part of Ubuntu's security model.

---

### Post by doas777 on 2009-07-04
> **PowerSource said:**
> so when i quit the terminal, the permissions disappear again?

yep, but that is a good thing, overall, as you shouldn't need to write to a /usr directory regularly. if you find yourself doing it often, just create a launcher for your desktop or panels or menus.

to be precise, you are not really temporarily changing the permissions on the resource itself, but rather, running a shell with all the privileges and rights of a root user.  most actions don't require root privileges, so it's safer to just not have them.

---

