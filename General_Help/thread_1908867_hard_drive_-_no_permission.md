---
title: "hard drive - no permission"
date: 2012-01-14
forum: General Help
---

### Post by juanEcuador on 2012-01-14
I have a 1 TB samsung hard drive, when on Natty installed it and everything worked perfectly, could write on the drive and also delete. Yet since upgraded to Oneiric i cant. here attached is a picture of what the system tells me whenever i tray to change permissions of any file.
Thanks for any help you can provide. :(

---

### Post by BlouBlou on 2012-01-14
Open it with "sudo nautilus", and try changing permissions with it.

---

### Post by varunendra on 2012-01-15
Is it your home folder? It seems that perhaps you had a separate /home partition in natty, while now you have a different 'home' folder and you are trying to access the files in your previous home folder.

In any case, you can try the following to take the ownership of the folder and the subfolders/files in it:
```
sudo chown -Rc *<your user id here>* *<the folder path here>*
```
For example, if your user ID (that appears in the terminal) is "juan", and the directory you want to take ownership of is "/home/n_n-juan", then-
```
sudo chown -Rc juan /home/n_n-juan
```
will change the ownership of the n_n-juan directory and all of its subdirectories/files to be owned by you (juan). The -c switch is there only to show you the names of the subfolders/files whose ownership is changed, so it can be omitted.

Alternatively, you can also do what *BlouBlou* suggested above (not suitable for too many subfolders/files), just replace 'sudo' with 'gksu'. That is-
**Alt+F2 > gksu nautilus**

It is recommended to always use 'gksu' instead of 'sudo' for running GUI apps ([see why]("http://www.psychocats.net/ubuntu/graphicalsudo")).

---

### Post by Paqman on 2012-01-15
> **BlouBlou said:**
> Open it with "sudo nautilus", and try changing permissions with it.

Sudo is only for command-line apps, please use gksu or gksudo for graphical apps.

---

