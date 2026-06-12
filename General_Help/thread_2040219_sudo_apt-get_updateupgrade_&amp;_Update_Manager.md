---
title: "sudo apt-get update/upgrade &amp; Update Manager"
date: 2012-08-10
forum: General Help
---

### Post by andox on 2012-08-10
Hi,

I'm fairly new to Xubuntu and Ubuntu, and so far I'm loving it.

When I update my machine I prefer to update via terminal; however, even after running update through the terminal I get notifications that I still have packages that need to be updated, at which point running sudo apt-get update & sudo apt-get upgrade again does not resolve. I have to go into the update manager and update there a second time.

I would like to update everything through the terminal, and not touch update manager if I can.

Is there something I am doing wrong or is the terminal limited to which packages are updated?

I've tried googling and searching through the forum, but the keywords I used: sudo apt-get update upgrade does not update all, ubuntu terminal update upgrade does not update everything, doesn't seem to return anything useful.

---

### Post by simonmoon42 on 2012-08-10
If an update needs to add or remove a dependency apt-get upgrade won't update it. I would guess that is the issue you're seeing. Though without seeing the output from the upgrade command I can't be sure. To resolve dependency issues run: 

```
sudo apt-get dist-upgrade
```

---

### Post by kc1di on 2012-08-10
Hi and welcome to ubunt/xubuntu,

try the following command ```
sudo dpkg --configure -a
sudo apt-get clean && apt-get autoclean
```

see if that will clear the problem. 

if not try this ```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```

then run upgrade again.
cheers!
Again welcome to the forums

---

### Post by andox on 2012-08-15
sudo apt-get dist-upgrade did the trick! Thanks!! :)

---

