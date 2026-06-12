---
title: "Ubuntu and Xampp"
date: 2009-09-21
forum: General Help
---

### Post by mohabitar on 2009-09-21
I've searched numerous places but could not find an answer to this:
I've installed and started xampp on Xubuntu with no problem. Xampp is located in a folder called opt. However I can not add anything to that folder or subfolders such as htdocs because I do not have permission. How do I fix that?

---

### Post by Partyboi2 on 2009-09-21
If you want to add files to /opt using a Gui you can press Alt+F2 and type
```
gksu nautilus
```
This will give you admin rights, but remember to close the nautilus window after making you changes.
If you are using the terminal then you can use 'sudo' to gain admin rights to make your required changes. 
So if you want to create a directory under /opt/xampp called htdocs you would use
```
sudo mkdir /opt/xampp/htdocs
```

---

### Post by flameproof on 2009-09-29
> **Partyboi2 said:**
> So if you want to create a directory under /opt/xampp called htdocs you would use
```
sudo mkdir /opt/xampp/htdocs
```

But then you have your web content in the XAMPP directory?

How you make i.e. home/user/htdocs/ the default directory for all web content?

I use xampp too, but feel that user content should stay in /home/ rather then any system directories.

---

