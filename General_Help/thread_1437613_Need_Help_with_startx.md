---
title: "Need Help with startx"
date: 2010-03-24
forum: General Help
---

### Post by sqa on 2010-03-24
hi all, im new to this ubuntu yet i try to make server in VMware environment on my campus , but i have problem with BASE testing , so i need startx to run first before i can do further

the problem is that when i put the command startx it shows these errors:

[IMG]http://img.photobucket.com/albums/v603/zero-zidane/IDSBASE.jpg[/IMG]

im using vSphere Client v.4 and OS ubuntu-9.10-server-amd64

any suggestion??

---

### Post by l4zy on 2010-03-24
try /etc/init.d/gdm start if u have gnome :)


also make shure that you have installed proper packages for x

---

### Post by sqa on 2010-03-24
i start the gdm with start gdm , and it says that 

gdm start/running, process 2901

--EDIT-- problem solved my bad

---

