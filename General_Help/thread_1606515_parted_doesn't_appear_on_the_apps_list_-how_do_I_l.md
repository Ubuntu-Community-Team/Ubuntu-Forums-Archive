---
title: "parted doesn't appear on the apps list -how do I launch it?"
date: 2010-10-26
forum: General Help
---

### Post by jeremybentham on 2010-10-26
Just changed to maverick.
I don't know how to launch programs with terminal
:oops:

---

### Post by Hippytaff on 2010-10-26
Just type parted in the terminal (CTRL+ALT+T)

The same for all apps you know the name of :-)

BTW one which had me looking around for days was the one that appears in the applications menu as movie player - it is infact called totem, but the kind people here din't laugh at me when  I asked here:-)

---

### Post by Quackers on 2010-10-26
GParted (if that's what you want) is not installed by default iirc.
You can install it via the Synaptic Package Manager. It will then be available in System > Admin > Gparted

---

### Post by trikster_x on 2010-10-26
Gparted isn't included in the install, just on the live program.  You'll have to install using the software center, or type in a terminal:
```
sudo apt-get install gparted
```

---

### Post by sebikul on 2010-10-26
Hi, if you are sure you have it installed just run from a terminal
```
sudo gparted
```

if you are not sure if it's installed run from a terminal
```
sudo apt-get install gparted
```
and then the command I posted above

Hope it helps!!

---

### Post by Hippytaff on 2010-10-26
parted is an app available which comes with maverick though :-s

---

### Post by jeremybentham on 2010-10-26
Thanks everyone
It appears as already installed in synaptic

I'll try your suggestions

---

### Post by jeremybentham on 2010-10-26
sudo apt-get install gparted
worked 
it's now on system admin list


thanks

---

### Post by Hippytaff on 2010-10-26
> **jeremybentham said:**
> sudo apt-get install gparted
worked 
it's now on system admin list


thanks
Sorry, I thought you wanted parted not Gparted :-s :-)

---

### Post by Quackers on 2010-10-26
Yes, I think he did, Hippytaff. I didn't know about parted, only GParted :-)

---

### Post by Hippytaff on 2010-10-26
> **Quackers said:**
> Yes, I think he did, Hippytaff. I didn't know about parted, only GParted :-)
I get terribly confused :-)

---

