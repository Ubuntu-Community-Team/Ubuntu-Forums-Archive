---
title: "Linux Registry?"
date: 2012-02-16
forum: General Help
---

### Post by Nirav32 on 2012-02-16
Windows operating system uses registry to store application settings
Linux operating system how handle that?

---

### Post by dcstar on 2012-02-16
> **Nirav32 said:**
> Windows operating system uses registry to store application settings
Linux operating system how handle that?

Linux uses various methods instead of a central database (Windows Registry) that destroys your system if it becomes corrupted.

System wide settings are stored in /etc, User settings are stored in the /home folder for each user.

---

### Post by Nirav32 on 2012-02-16
> **dcstar said:**
> Linux uses various methods instead of a central database (Windows Registry) that destroys your system if it becomes corrupted.

System wide settings are stored in /etc, User settings are stored in the /home folder for each user.

Linux uses file format to store setting?

---

### Post by dcstar on 2012-02-16
> **Nirav32 said:**
> Linux uses file format to store setting?

Usually text, look for yourself.

---

### Post by Mark Phelps on 2012-02-16
> **Nirav32 said:**
> Linux uses file format to store setting?

YES ... Linux inheritted a lot of approaches from UNIX -- and that used files, not databases, to store configuration information.  These files usually start out with a period "." in their filename, which causes then to become "hidden" by default.

If you recall, MS Windows did the same thing in the old days -- they put the info in ".ini" files.  Then, they switched over to using the registry -- which is really a collection of something known as "hives" -- which, oddly enough, are also "files", but these are treated as if they comprised a single, integrated, database system.

---

### Post by oldos2er on 2012-02-16
Changed thread title.

---

### Post by 3Miro on 2012-02-16
The closest thing that you can see to a registry is gconf. However, gconf stores data only for Gnome specific applications (Gnome is the default environment in Ubuntu). If your version of Linus isn't using Gnome or Gnome specific applications, then you wouldn't even have gconf.

---

