---
title: "Always open .php files in gedit on mounted drive"
date: 2010-06-16
forum: General Help
---

### Post by sokekoke on 2010-06-16
Hi!

I have a mounted drive using NTFS with all of my websites on. When i dobbelt click a .php file it asks me if i want to run the file in terminal etc.

Can i somehow make a standard so all .php files on my mounted drive are just opened with gedit?

Thanks!!!

---

### Post by wojox on 2010-06-16
It asks you that because they are executable. You would need to make them non executable to open straight to gedit.

---

### Post by sokekoke on 2010-06-16
> **wojox said:**
> It asks you that because they are executable. You would need to make them non executable to open straight to gedit.

Could you elaborate/explain how? When opening php files on linux partition they are opened in gedit straight away, problem with executable is only on my NTFS partition

---

### Post by wojox on 2010-06-16
> **sokekoke said:**
> Could you elaborate/explain how? When opening php files on linux partition they are opened in gedit straight away, problem with executable is only on my NTFS partition

Don't really know sokekoke, I don't have a NTFS partition to experiment with. 

If I save a .php file of my machine onto a usb stick and then try to open it again on the same machine it asks me the same thing until I copy the file and change it's permissions. 

I guess that's the wonderful thing about Linux security.

---

