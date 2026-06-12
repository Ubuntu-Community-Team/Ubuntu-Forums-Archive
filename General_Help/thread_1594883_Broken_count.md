---
title: "Broken count"
date: 2010-10-12
forum: General Help
---

### Post by margaret crawford on 2010-10-12
:(I upgraded ubuntu ywo days ago everything was fine untill today 
i got an error message saying error brocken count >0
usually means installed packages have unmet dependencies
ive tried to restall package but wont let me ive also tried unstalling
it keeps saying install first before trying to remove what do i doto 
fix this thank you .

---

### Post by plucky on 2010-10-13
> **margaret crawford said:**
> :(I upgraded ubuntu ywo days ago everything was fine untill today 
i got an error message saying error brocken count >0
usually means installed packages have unmet dependencies
ive tried to restall package but wont let me ive also tried unstalling
it keeps saying install first before trying to remove what do i doto 
fix this thank you .

Open a terminal (Applications > Accessories > Terminal) and use ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
```

Any errors,copy and paste to the forum.
If long output use [noparse]```

```[/noparse] blocks to display the output.

Good Luck

---

### Post by margaret crawford on 2010-10-16
Thank you but this didnt work dont know what else to do anybody help me out thanks x

---

### Post by margaret crawford on 2010-10-16
done this over and over again and it still says error flashplugin non free install or uninstall 
i have tried to do this too and it still wont let me . it says this file is too damaged .
i have used a terminal and it says 1 installed , 1 upgraded and then says error flashplugin failed to install .

---

### Post by hansdown on 2010-10-16
Welcome to the forum, margaret crawford.

Click system> administration> synaptic package manager.

Search for, and install

```
flashplugin-installer
```

It should help sort things.

Thanks go to Lovinglinux.

---

### Post by margaret crawford on 2010-10-18
> **hansdown said:**
> Welcome to the forum, margaret crawford.

Click system> administration> synaptic package manager.

Search for, and install

```
flashplugin-installer
```It should help sort things.

Thanks go to Lovinglinux.
Thanks for your help i tried package manager but still flashes up error broken package flashplugin nonfree this only happened when i upgradedtried everything nothing works .thank you x

---

### Post by Quackers on 2010-10-18
When in synaptic have a look at the very bottom of the screen on the left. It lists available packages, installed packages and broken packages. Are any broken packages listed?

---

### Post by margaret crawford on 2010-10-20
> **Quackers said:**
> When in synaptic have a look at the very bottom of the screen on the left. It lists available packages, installed packages and broken packages. Are any broken packages listed?
yes flash plugin nonfree package did not install tried everything to fix this but wont let me install or uninstall
can you help thanks x

---

