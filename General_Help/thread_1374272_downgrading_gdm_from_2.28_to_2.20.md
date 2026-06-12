---
title: "downgrading gdm from 2.28 to 2.20"
date: 2010-01-06
forum: General Help
---

### Post by phoenixfire900 on 2010-01-06
hi i did the tutorial on how to downgrade the gdm from 2.28 to 2.20 but when i ask it to do this command : sudo apt-get install gdm-2.20 it tells me file could not be found or error retrieving file.  what do I do?

---

### Post by cariboo on 2010-01-06
You can get the version you need from [here]("http:///packages.ubuntu.com/"). Look for the Jaunty version.

---

### Post by phoenixfire900 on 2010-01-06
which section do i look under in jaunty?

---

### Post by phoenixfire900 on 2010-01-06
it wont let me install the version cause it says i already have a newer version

---

### Post by cariboo on 2010-01-06
You have to completely remove gdm before you can downgrade. You can use a terminal and type:

```
sudo apt-get purge
``` 

but be aware that it might remove many necessary packages.

To see what it will remove before actually doing it, it might be a better idea to go to System-->Administration-->Synaptic Package Manager and mark gdm for complete removal. The program will give you a list of what else it will remove.

Just out of curiosity, why are you trying to remove gdm? Just because you don't like the looks?

---

### Post by phoenixfire900 on 2010-01-06
i like the theme options in 2.20

---

### Post by Zoot7 on 2010-01-06
> **phoenixfire900 said:**
> i like the theme options in 2.20
That's hardly a reason to downgrade to 2.20 IMO. Removing gdm is removing a pretty important core piece of your Ubuntu installation, it'll more than likely pull out the whole gnome desktop. I'd avoid it if I were you. ;)

If you're looking for themes for gnome, I'd say you can find pretty much all of them here:
[http://www.gnome-look.org/](http://www.gnome-look.org/)

---

