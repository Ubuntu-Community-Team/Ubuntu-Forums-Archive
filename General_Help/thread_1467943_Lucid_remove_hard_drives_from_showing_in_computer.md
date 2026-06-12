---
title: "Lucid remove hard drives from showing in computer ?"
date: 2010-05-01
forum: General Help
---

### Post by SlugSlug on 2010-05-01
I have a load of partitioned hard drives and even though the are refrenced in fstab I still get Bookmark Icons and they are also visable in 'Computer'

How do you remove these icon?

I would also like the ones not refrenced in fstab to only be mountable via password - lucid seems to just mount when you click, I did change this as in another post but it also made USB keys need a password

     Code:
     gksu gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla 
change the ResultActive=yes to
 
ResultActive=auth_admin_keep
[URL="http://ubuntuforums.org/report.php?p=9085746"]
[/URL]

---

### Post by dino99 on 2010-05-01
the easiest way is to install MontManager and tweaks the rights for each device as you need

---

### Post by SlugSlug on 2010-05-01
according to mountmanager nly administrator can mount drive, but there is no where to select must input password

and there is no way to stop drives showing in places & computer

---

### Post by SlugSlug on 2010-05-01
figured out why my drives always show in Computer -- I changed mount points to /media/  and anything in there shows in browser !

:lolflag:

---

