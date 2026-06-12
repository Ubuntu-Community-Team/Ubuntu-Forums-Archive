---
title: "copying files?"
date: 2011-03-28
forum: General Help
---

### Post by rahulbest on 2011-03-28
i have php files....want to copy those files in var/www fiolder but i m unable to that...as its saying permission denied...how to do that???

---

### Post by rahulbest on 2011-03-28
plz help me with this......how to get permission

---

### Post by ~Plue on 2011-03-28
```
to copy files;
sudo cp /path/to/file /var/www/

if its a directory, use the 'r' switch;
sudo cp -r /path/to/directory /var/www/
```or. to make it really easy, simply run nautilus as root and just copy-past (but dont mess with the system files!)
```
gksu nautilus
```

---

### Post by PowerBarry43 on 2011-03-28
Try typing "sudo cp (location of the file you want to copy)* /var" in the terminal then you'll have to type your password

---

### Post by rahulbest on 2011-03-28
hey thnks...now i want to log in from root user to a normal user...how to do that

---

### Post by Linux_junkie on 2011-03-28
> **rahulbest said:**
> hey thnks...now i want to log in from root user to a normal user...how to do that

You don't! sudo allows you to run certain commands as root user and when you have finished and quit terminal it terminates the root privilege.

---

### Post by rahulbest on 2011-03-28
i copied that thing in root var www but i m unable to edit it or access it....how i can set permission for that

---

### Post by ~Plue on 2011-03-28
> **rahulbest said:**
> i copied that thing in root var www but i m unable to edit it or access it....how i can set permission for that
you can edit it the way you normally do from within the root nautilus window (right-click>open with text editor)

or if you prefer not to use the root nautilus, run *gksu gedit /path/to/file*

---

### Post by rahulbest on 2011-03-28
with the help of chmod can we do that???
how i can do that????

---

### Post by ~Plue on 2011-03-28
> **rahulbest said:**
> with the help of chmod can we do that???
how i can do that????
since you're insisting on changing the permissions...
```
sudo chown -R $USER: /var/www
```chmod-ing the files to 77_6_ is the way to get you the permissions to modify the file without changing the ownership. but that would mean any user can make changes to those..so here, we change the ownership of /var/www recursively to your user

---

### Post by rahulbest on 2011-03-28
i am unable to get read write execute permission to that directory...
actually i copy v5.1 directory from mydesktop computer to laptop...now i cannt access that folder even after copying it on var/www

---

### Post by ~Plue on 2011-03-29
> **rahulbest said:**
> i am unable to get read write execute permission to that directory...
actually i copy v5.1 directory from mydesktop computer to laptop...now i cannt access that folder even after copying it on var/www
thats what the chown command in the previous post is for. **ch**ange **own**er

---

