---
title: "file manager as root"
date: 2009-08-20
forum: General Help
---

### Post by AmerNewbieInDE on 2009-08-20
is there a way to open nautilus as root? i have tried gksu nautilus / and gksu nautilus ~ but neither give me access

---

### Post by oldos2er on 2009-08-20
**gksu nautilus** should work. If it doesn't, could you post the output?

---

### Post by AmerNewbieInDE on 2009-08-20
laptop:~$ gksu nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directoryPlease ask your system administrator to enable user sharing.

led: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
** (nautilus:5988): WARNING **: Unable to add monitor: Operation not supported

and when i try to copy folders off my external onto the hard drive, it tell me i dont have the permission

---

### Post by credobyte on 2009-08-20
```
gksudo nautilus

```

---

### Post by AmerNewbieInDE on 2009-08-20
well, thanks for the try... same thing,anyone else?

funny, now i cant even run <su>, it is telling me authentication failed. wtf, i just got done a new install...

---

### Post by -=hazard=- on 2009-08-20
$su -i
$nautilus

?

---

### Post by credobyte on 2009-08-20
> **AmerNewbieInDE said:**
> well, thanks for the try... same thing,anyone else?

funny, now i cant even run <su>, it is telling me authentication failed. wtf, i just got done a new install...

su refers to a root account ( which by default is disabled ). Use sudo ( relies on sudoer's file ) ;)

---

### Post by AmerNewbieInDE on 2009-08-20
got it, gotta run sudo nautilus from alt+f2

when i tried su, i was trying to get root from terminal

oh, what does it mean, cant copy special file... what i am doing, i was running ubuntu off my external sata drive, it is giving me many bad errors, so i reloaded new on my notebook, now i am trying to get everything off the external.  

actually, do you know what folders i need to get, in order for me to have everything back how it was? including kububtu and kernel updates..i had i think the numbers were 2.6.31 rc5

---

### Post by ajgreeny on 2009-08-20
get the nautilus plugin from the repos called gksu-nautilus with ```
sudo apt-get install gksu-nautilus
```You will then be able to right click on a file or folder in the right-hand pane of nautilus and chose "Open as administrator", give your password and a new nautilus window will open with root privileges.

---

### Post by AmerNewbieInDE on 2009-08-20
> **ajgreeny said:**
> get the nautilus plugin from the repos called gksu-nautilus with ```
sudo apt-get install gksu-nautilus
```You will then be able to right click on a file or folder in the right-hand pane of nautilus and chose "Open as administrator", give your password and a new nautilus window will open with root privileges.

thanks, i will get that

---

### Post by fooman on 2009-08-20
> **ajgreeny said:**
> get the nautilus plugin from the repos called gksu-nautilus with ```
sudo apt-get install gksu-nautilus
```You will then be able to right click on a file or folder in the right-hand pane of nautilus and chose "Open as administrator", give your password and a new nautilus window will open with root privileges.

+1 for gksu-nautilus !

that and "nautilus-open-terminal" (allows you to right-click in nautilus or on desktop and choose "open in terminal")... are 2 of the first things i add to a fresh ubuntu installation.  :)

invaluable imho.

---

### Post by oldos2er on 2009-08-21
Just FYI, the package is actually named **nautilus-gksu**.

---

### Post by treehouse on 2009-08-21
You can also stick a launcher on your panel or desktop that executes the command 'gksudo "gnome-open %u"' and then drag any files, programs, or folders onto the launcher to open them as superuser.

---

### Post by ajgreeny on 2009-08-21
Whoops!  Sorry about the wrong name.  The memory starts to play tricks when you get to my age.

---

