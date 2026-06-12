---
title: "Can we undo a dpkg action??"
date: 2006-04-07
forum: General Help
---

### Post by sands on 2006-04-07
I installed ekiga and all the dependencies given to download from its site by using 
dpkg -i *

Now all those installed ones became broken..
when I try to remove them UbuntuDesktop is also being added to the list..
How to fix the error??

Can we do that by undoing dpkg action??

---

### Post by aysiu on 2006-04-07
Have you tried this? ```
sudo apt-get -f install
```

---

### Post by sands on 2006-04-07
No whats this??
What will happen??

---

### Post by sands on 2006-04-07
Yes, I tried..
Again it says it will remove all those along with UbuntuDesktop

---

### Post by aysiu on 2006-04-07
Go ahead and remove ubuntu-desktop.
Once it's all fixed then just do a ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by nanotube on 2006-04-07
ubuntu-desktop is just a meta-package that installs all the desktop dependencies. it can be removed without any bad effects. :)

ah, i guess aysiu beat me to it. you're a quick one, as usual :)
though i would think that reinstalling ubuntu-desktop would not be necessary...

---

### Post by aysiu on 2006-04-07
[QUOTE=nanotube]though i would think that reinstalling ubuntu-desktop would not be necessary...[/QUOTE] It probably isn't really necessary, but in case some crucial packages also get uninstalled, reinstalling ubuntu-desktop will make sure those packages get put back.

---

### Post by sands on 2006-04-07
Thnx..
Now everything is fine..

---

### Post by nanotube on 2006-04-07
[QUOTE=aysiu]It probably isn't really necessary, but in case some crucial packages also get uninstalled, reinstalling ubuntu-desktop will make sure those packages get put back.[/QUOTE]

hmm, i suppose that's a good point. :)

---

