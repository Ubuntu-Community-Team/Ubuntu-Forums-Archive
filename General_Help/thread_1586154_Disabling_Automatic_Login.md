---
title: "Disabling Automatic Login"
date: 2010-10-01
forum: General Help
---

### Post by Paul A C on 2010-10-01
I have enabled automatic login in Lubuntu, and have now added a second user,  I want to DISABLE the automatic login, or perhaps change the default login.

The usual Ubuntu admin window for this does not appear to be available.

Does anyone know where in the conf files this setting is, and or whether there is a GUI that controls this.

---

### Post by MindCalamity on 2010-10-01
Did you try manually running the command gdmsetup ?

Try ALT + F2 or run it in the terminal.

---

### Post by kDDs on 2010-10-01
cvs

---

### Post by hrickh on 2010-10-01
System > Administration > Login Screen.

R.
==

---

### Post by sisco311 on 2010-10-01
> **Paul A C said:**
> 
Does anyone know where in the conf files this setting is, and or whether there is a GUI that controls this.

If you are using 10.04 (with lxdm), then /etc/lxdm/lxdm.conf. If 9.10 (with gdm), then run gdmsetup.

---

### Post by Paul A C on 2010-10-01
gdmsetup does not appear to be avaiable in Lubuntu

---

### Post by Paul A C on 2010-10-01
> **sisco311 said:**
> If you are using 10.04 (with lxdm), then /etc/lxdm/lxdm.conf. If 9.10 (with gdm), then run gdmsetup.
This looked hopeful and I editied lxdm.conf.

The autologin did say paul, I changed this to the other user, but after a reboot I was still logged in as paul.  How is that possible?

I cannot remember how I set up autologin in the first place, but I am pretty certain it was a GUI.

---

### Post by Paul A C on 2010-10-01
> **hrickh said:**
> System > Administration > Login Screen.

R.
==
This option is not available in Lubuntu, (It is what I first looked for).

---

### Post by Paul A C on 2010-10-01
> **MindCalamity said:**
> Did you try manually running the command gdmsetup ?

Try ALT + F2 or run it in the terminal.
Yes I did try this, the command is not available

---

### Post by Paul A C on 2010-10-01
> **kDDs said:**
> cvs
What do you mean cvs?

---

### Post by Paul A C on 2010-10-01
> **Paul A C said:**
> This looked hopeful and I editied lxdm.conf.

The autologin did say paul, I changed this to the other user, but after a reboot I was still logged in as paul.  How is that possible?

I cannot remember how I set up autologin in the first place, but I am pretty certain it was a GUI.
Gottcha.  thanks sisco311 you put me on the right track.  The file that needs editing is /etc/lxdm/**default.conf**
No idea what lxdm.conf is used for!

---

### Post by sisco311 on 2010-10-01
Oh, cool... glad you figured it out!

According to lxdm's man page,  /etc/lxdm/default.conf is a symbolic link to the real configuration file, /etc/lxdm/lxdm.conf in case of lxdm or /etc/xdg/lubuntu/lxdm/lxdm.conf in case of Lubuntu.

---

### Post by hrickh on 2010-10-01
> **Paul A C said:**
> This option is not available in Lubuntu, (It is what I first looked for).
Sorry about that... I missed that you were using Lubuntu.

R.
==

---

### Post by sisco311 on 2010-10-01
> **Paul A C said:**
> This option is not available in Lubuntu **10.04**, (It is what I first looked for).

Fixed. :evil: 

> **hrickh said:**
> Sorry about that... I missed that you were using Lubuntu.

R.
==

Don't be... Lubuntu 9.10 uses gdm, they switched to lxdm in 10.04. [noparse]:)[/noparse]

---

### Post by kDDs on 2010-10-02
> **Paul A C said:**
> What do you mean cvs?

I think my phone was left unlocked in my pocket ;)

---

