---
title: "No Launcher"
date: 2011-10-16
forum: General Help
---

### Post by iKeirNez on 2011-10-16
So yesterday I installed the ATI/AMD proprietary graphics driver and upon rebooting I have no launcher, just a desktop with a few items. How can I fix this? I can get into terminal by pressing **CTRL + ALT + T**. How can I remove the driver from the console?

Keir

---

### Post by Frogs Hair on 2011-10-16
Hello and Welcome

Before removing the driver try the commands below .```
unity --reset
```
```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```



To remove the driver you need to know the package name . Use the command below (insert package name) Restart after the driver is removed and use the restart button on the computer if the shutdown button isn't visible .```
sudo apt-get remove package-name
```

I use Nvidia drivers , so I can't help with the ATI driver package name .

---

### Post by iKeirNez on 2011-10-17
> **Frogs Hair said:**
> Hello and Welcome

Before removing the driver try the commands below .```
unity --reset
``````
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

To remove the driver you need to know the package name . Use the command below (insert package name) Restart after the driver is removed and use the restart button on the computer if the shutdown button isn't visible .```
sudo apt-get remove package-name
```I use Nvidia drivers , so I can't help with the ATI driver package name .

Thanks very much for helping me! I the first bit didn't work and the second bit I didn't know the package name, BUT I still had the .run file on my desktop so this is what I did in terminal.

```
cd Desktop
```

```
sudo sh ati.run --uninstall
```

Then I rebooted and it was perfect! Thanks!

Keir

---

