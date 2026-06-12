---
title: "permanent bind fstab?"
date: 2010-02-17
forum: General Help
---

### Post by berryboy on 2010-02-17
hello there :)

i currently manually add to terminal 

sudo mount --bind /home/projects /home/jamie
sudo mount --bind /home/projects /home/lee 

as i understand it u can do this @ start up in fstab?
but i must say im still new and a little lost in here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

please help.

---

### Post by geirha on 2010-02-17
This fstab-line is equivalent to the first mount-command you listed.
```
/home/projects /home/jamie none bind 0 0
```

A little tip btw. Once you've mounted a filesystem, it will be listed in /etc/mtab, with the same format as /etc/fstab.

---

### Post by berryboy on 2010-02-17
thank you for that :)

bind was what i was missing i was using default

thanks again

---

### Post by gotjazz on 2010-08-03
hrm I've used the search for quite some time and didn't find anything about this - i have several directories from  my windows drive mounted in my home dir by way of bind. Now I'd really like to know if there's a way to use the trashcan from there. as far as i can see when deleting something from such a dir, a .Trash-uid directory is created in the dir itself instead of the partitions main dir. Is there a way I can make the gnome-trash use those?

---

### Post by cowbud on 2010-08-14
did anyone file a bug for this?

---

