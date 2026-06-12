---
title: "Disk errors"
date: 2011-11-24
forum: General Help
---

### Post by Agent26 on 2011-11-24
Hi there all,
Today i'm trying to learn how to use a utility like scan disc,  is there one I can download from the software center?
 
Perhaps there is a technique using terminal or something else all together. 
Any suggestions would be greatly appreciated.
Thankyou.
 
Ive got Xubuntu 10.4.2

---

### Post by sudodus on 2011-11-24
You can test if the linux file system is good this way. ***Run a live session*** and mount ***no*** partitions, for example run from your installation CD or USB drive and from a terminal window, do
```
sudo e2fsck -f /dev/sd[COLOR=Red]xy[/COLOR]
``` where x should be changed to the letter of your system drive and y to the number of the partition, for example /dev/sd[COLOR=Red]a5[/COLOR]. Look for the device mounted to / in the output of ```
df
```

---

### Post by Agent26 on 2011-11-24
Thanks Sudodus I will give this a try now......

---

### Post by Agent26 on 2011-11-24
Hi there,
So far ive had  a few problems, bit noob at the mo.
 
Do you mean run a live session from an installation cd?
how do unmount a file system

---

### Post by sudodus on 2011-11-24
> **Agent26 said:**
> Hi there,
So far ive had  a few problems, bit noob at the mo.
 
Do you mean run a live session from an installation cd?
Yes installation CD or USB drive!
> how do unmount a file systemIt is not mounted by default when you run a live session. If you don't mount it, you must not unmount it. (But if you mount it with the file browser, you can also unmount it.)  I'm not sure about xubuntu (Thunar), but right-clicking should let you choose different actions.

Check if it is mounted with the terminal command ```
df
```

---

### Post by boast on 2011-11-24
I assume ubuntu has this, but on arch its automatically checks the file system after an X amount of boot ups.

---

### Post by philinux on 2011-11-24
> **Agent26 said:**
> Hi there all,
Today i'm trying to learn how to use a utility like scan disc,  is there one I can download from the software center?
 
Perhaps there is a technique using terminal or something else all together. 
Any suggestions would be greatly appreciated.
Thankyou.
 
Ive got Xubuntu 10.4.2

The system will run this automatically every ~ 30 boots. Unless you have a reason to run it manually?

---

### Post by Agent26 on 2011-11-24
Hi, thanks Phil, thats good to know
I'm just trying to get to know it a bit better and maintain a nice healthy system.
Mainly get used to the terminal.

---

### Post by Agent26 on 2011-11-25
Thanks guys thats problem solved now.

---

