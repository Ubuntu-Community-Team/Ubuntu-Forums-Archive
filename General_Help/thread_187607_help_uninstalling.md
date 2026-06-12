---
title: "help uninstalling"
date: 2006-06-03
forum: General Help
---

### Post by newhen on 2006-06-03
okay i have this whole file i want to remove and throw out of my desk but its sets to only be able to do that if ur root so how do i remove it?

---

### Post by newhen on 2006-06-03
bump

---

### Post by givré on 2006-06-03
[QUOTE=newhen]okay i have this whole file i want to remove and throw out of my desk but its sets to only be able to do that if ur root so how do i remove it?[/QUOTE]
What kind of file do you want to remove, if this is some system files, be careful with that.
Anyway, there is a powerfull command to do that kind of things : rm, but read the manual before (man rm ).
If you prefere a gui to do that, you could also run nautilus as root (gksu nautilus)

---

### Post by thasheep on 2006-06-03
If it's on your desktop, do this in a terminal and enter your password when asked.
```
sudo rm ~/Desktop/name-of-file
```

---

### Post by givré on 2006-06-03
And if you want to uninstall apps, you should try Add/remove in the main menu.
To uninstall any package, the advance thing is to run synaptic

---

### Post by newhen on 2006-06-03
grr i get a message saying it isnt there but it is i see it its called eclient
admin@admin-desktop:~$ sudo rm ~/Desktop/eclient
Password:
rm: cannot remove `/home/admin/Desktop/eclient': No such file or directory
admin@admin-desktop:~$

---

### Post by givré on 2006-06-03
let see the output of ```
ls -hal ~/Desktop
```
it will list all the file you have in your Desktop directory

---

