---
title: "Can I delete ~/Music, ~/Pictures, ~/Public,... folders?"
date: 2009-12-31
forum: General Help
---

### Post by pstein on 2009-12-31
I hate these auto-created (MS adopted) sub folders in my home directory.
The inventors believe that users cannot categorize their files independently.
 
Can I delete these folders without causing any harm?
 
What happens if a program refers to one of these folders and cannot find them (e.g. Firefox to ~/Download directory)?
 
Which directory is used as global default in such a case?
 
Peter

---

### Post by MelDJ on 2009-12-31
you can delete and change the output download directory for firefox. 
the others are safe to delete

---

### Post by danastasio on 2009-12-31
You can safley delete all of those folders on your system. It depends on how the program was coded, either it will default to the ~/ for what it needs to do, or it will just make the folder on its own

---

### Post by pstein on 2009-12-31
> **danastasio said:**
> You can safley delete all of those folders on your system. It depends on how the program was coded, either it will default to the ~/ for what it needs to do, or it will just make the folder on its own
 
Ok. What about teh "Desktop" directory?
 
Where are the icons and their positions stored if I delete this folder?
 
Is it possible to make "Desktop" invisible (=pre-pend it with a dot .")
or move it to another location?
 
How do I tell Ubuntu: "ILook for icons in the Desktop folder in directory
/etc/users/user/Desktop/" ?
 
Peter

---

### Post by VCoolio on 2009-12-31
You can edit the file ~/.config/user-dirs.dirs to point to other folders.
Edit: check [this thread]("http://ubuntuforums.org/archive/index.php/t-670751.html"), it seems you need to start paths with $HOME.

---

