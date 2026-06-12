---
title: "home folder not working in ubuntu 11.04"
date: 2011-11-19
forum: General Help
---

### Post by shubham1 on 2011-11-19
home folder not working in ubuntu 11.04 i click on the launcher or open by saerching it it does not opens same with ubuntu one how evere i have no hope of opening ubuntu one so only home folder.

---

### Post by CaptainMark on 2011-11-19
what happens when you type nautilus into a terminal?

---

### Post by shubham1 on 2011-11-19
> **CaptainMark said:**
> what happens when you type nautilus into a terminal?
```
Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported
Trace/breakpoint trap

```

---

### Post by CaptainMark on 2011-11-19
nice, what version of nautilus do you have installed, this is what i get ```
mark@desktop:~$ sudo dpkg -s nautilus | grep Version
Version: 1:2.32.2.1-0ubuntu13
```

---

### Post by shubham1 on 2011-11-19
> **CaptainMark said:**
> nice, what version of nautilus do you have installed, this is what i get ```
mark@desktop:~$ sudo dpkg -s nautilus | grep Version
  
```
```
Version: 1:2.32.2.1-0ubuntu13
```

---

### Post by LinuxFan999 on 2011-11-19
Try this:

```
sudo apt-get reinstall nautilus
```

---

### Post by shubham1 on 2011-11-19
E: Invalid operation reinstall

---

### Post by CaptainMark on 2011-11-19
do you have any additional ppa's active? a vanilla install of 11.04 shouldnt give an error like this, have you tried purging nautilus and reinstalling, its worth a shot, other than that i cant help with this one im afraid, someone else may be along to help though

EDIT: too slow on the typing there, try a purge, its more thorough```
sudo apt-get purge nautilus
sudo apt-get install nautilus
```

---

### Post by shubham1 on 2011-11-19
> **CaptainMark said:**
> do you have any additional ppa's active? a vanilla install of 11.04 shouldnt give an error like this, have you tried purging nautilus and reinstalling, its worth a shot, other than that i cant help with this one im afraid, someone else may be along to help though

EDIT: too slow on the typing there, try a purge, its more thorough```
sudo apt-get purge nautilus
sudo apt-get install nautilus
```
sorry i could not get what you are trying to say

---

### Post by CaptainMark on 2011-11-19
i mean i would not have expected to see this error on a standard ubuntu system, 
trying those commands in a terminal is about all i can think to do here,

---

### Post by shubham1 on 2011-11-19
> **CaptainMark said:**
> i mean i would not have expected to see this error on a standard ubuntu system, 
trying those commands in a terminal is about all i can think to do here,
yes you are right my ubuntu is not normal its a problem ubuntu

---

### Post by LinuxFan999 on 2011-11-19
It looks like the only thing you can do is back up and reinstall Ubuntu, since Your installation is broken.

---

### Post by shubham1 on 2011-11-19
> **LinuxFan999 said:**
> It looks like the only thing you can do is back up and reinstall Ubuntu, since Your installation is broken.
Dont joke I have alreadt reinstalled I have tried to install ubun
Tu I did vut failed pleasw see my threads and see what I have not done

---

