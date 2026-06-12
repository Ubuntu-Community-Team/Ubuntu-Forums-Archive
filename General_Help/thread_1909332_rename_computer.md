---
title: "rename computer"
date: 2012-01-15
forum: General Help
---

### Post by Vinger on 2012-01-15
Hello,

I reinstalled Kubuntu to go from 32bit to 64bit;

Now i see that i made a typo in the name i gave to my computer.
can i rename it?

tx.

---

### Post by IanW on 2012-01-15
You need to alter the file /etc/hostname

---

### Post by claracc on 2012-01-15
Google is your friend.

From this thread: [http://ubuntuforums.org/showthread.php?p=11483864](http://ubuntuforums.org/showthread.php?p=11483864), as fdrake indicates:

to change hostname (+1 @quadproc)
Code:

sudo gedit /etc/hostname
sudo gedit /etc/hosts

also suggest to  edit you DNS hosts file , the line that has your old hostnam

---

### Post by haqking on 2012-01-15
> **claracc said:**
> Google is your friend.

From this thread: [http://ubuntuforums.org/showthread.php?p=11483864](http://ubuntuforums.org/showthread.php?p=11483864), as fdrake indicates:

to change hostname (+1 @quadproc)
Code:

**sudo gedit** /etc/hostname
**sudo gedit** /etc/hosts

also suggest to  edit you DNS hosts file , the line that has your old hostnam

When using gedit you should use gksudo and not sudo.

```
gksudo gedit /etc/hostname
```
```
gksudo gedit /etc/hosts
```

Also if it is temproary thing you can just type

```
hostname <name you want>
```

This resets after a reboot however.

Also if you want the name to stay the same but want it to appear differently in your prompt then:

```
PS1="what you want displayed here : "
```

Cheers

---

### Post by Vinger on 2012-01-16
tx!

---

