---
title: "How to change owner of files you're not the owner of?"
date: 2012-10-01
forum: General Help
---

### Post by alexferreirag on 2012-10-01
Before erasing my hard drive to install Ubuntu I copied some files I wanted to save into an external drive. Some of those files were pictures. Now that I am running Ubuntu as my main and only OS I want to copy these pictures to Ubuntu, but apparently I do not have permission to them and I am not allowed to change the owner of the files since with Ubuntu I am no longer the owner. Any ideas on how to re-gain access to these pictures?

---

### Post by Vaphell on 2012-10-01
are your files still located on external drive or did you manage to copy them but can't claim ownership?

---

### Post by 3Miro on 2012-10-01
You can use the terminal and change ownership with sudo command.
```
sudo chown me:me *
```
will change the ownership of all files in the current folder and make them belong to user "me". Replace "me" with your user name.

You can also use nautilus in super-user mode:
```
gksudo nautilus
```
which will let you copy and move files that don't belong to you.

Both sudo and gksudo will require your password.

Note that changing ownership of the wrong file or moving/deleting the wrong file with nautilus can destroy your Ubuntu. Be careful of what you are doing. Normally system files are protected, but sudo bypasses those protections.

---

