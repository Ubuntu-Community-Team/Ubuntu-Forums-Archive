---
title: "Changing gnome master keyring password"
date: 2006-06-21
forum: General Help
---

### Post by zerohalo on 2006-06-21
Does anyone know how to change the master password for the gnome keyring? Searched the net but came up empty ](*,)  (though found some people asking the same question in other forums). gnome-keyring-manager allows changing the passwords in the keyring, but not the master password for the keyring itself. 
Thanks!

---

### Post by santo on 2006-06-23
Maybe you should take a look in this thread: [http://ubuntuforums.org/showthread.php?t=187874&page=2&highlight=keyring+password](http://ubuntuforums.org/showthread.php?t=187874&page=2&highlight=keyring+password)

One of the suggestions was to simply remove a folder called keyring* in /tmp, but for me that doesn't work :-(

Another possibility is by trying out the new pam tarballs from cvs which allow to change the master password.
I haven't tried them yet though

---

### Post by santo on 2006-06-23
In the meantime I did find another thread ([http://www.linuxquestions.org/questions/showthread.php?t=410266](http://www.linuxquestions.org/questions/showthread.php?t=410266)) but also this didn't work for me.

I did find however one way to remove the default keyring resulting in a new keyring being created the next time it's required and thus asking for a new password:

```

sudo apt-get install gnome-keyring-manager
gnome-keyring-manager

```

this will open an application where you can delete the default keyring.

I know it's a rather drastical way for changing the password, but at least it did work for me.

---

