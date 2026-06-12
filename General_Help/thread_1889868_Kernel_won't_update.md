---
title: "Kernel won't update"
date: 2011-12-02
forum: General Help
---

### Post by jgcsd on 2011-12-02
When I boot my computer, I get the grub menu with my OSes and their various kernel versions to select from.

But the latest option I can use on one of my Ubuntus is 2.6.32-34, despite 2.6.32-35 and 2.6.32-36 being updated.

Does anyone know why it's doing this, and how I can fix it?

I'm on Ubuntu 10.04

---

### Post by faixan on 2011-12-02
> **jgcsd said:**
> When I boot my computer, I get the grub menu with my OSes and their various kernel versions to select from.

But the latest option I can use on one of my Ubuntus is 2.6.32-34, despite 2.6.32-35 and 2.6.32-36 being updated.

Does anyone know why it's doing this, and how I can fix it?

I'm on Ubuntu 10.04

you might find help in here;

[http://ubuntuforums.org/showthread.php?t=1888866](http://ubuntuforums.org/showthread.php?t=1888866)

---

### Post by surfer on 2011-12-02
did you run your update with
```
$ sudo apt-get update
```

in order to update the kernel try:
```
$ sudo apt-get dist-upgrade
```

---

### Post by faixan on 2011-12-02
> **surfer said:**
> did you run your update with
```
$ sudo apt-get update
```

in order to update the kernel try:
```
$ sudo apt-get dist-upgrade
```

can you please look into my problem in the above given link ? :(

/*edit*/
i'm running dist-upgrade now, 
doesn't updating the OS using update manager do same thing ? :s

---

### Post by jgcsd on 2011-12-03
> **faixan said:**
> you might find help in here;

[http://ubuntuforums.org/showthread.php?t=1888866](http://ubuntuforums.org/showthread.php?t=1888866)

Thankyou! The solution was in that thread here [http://ubuntuforums.org/showpost.php?p=11507971&postcount=23](http://ubuntuforums.org/showpost.php?p=11507971&postcount=23)


```

sudo apt-get update # Update repositories and check Internet connection
# Note: Do not proceed if you don't have an Internet connection.
sudo apt-get purge grub-common # Will remove Grub legacy and Grub 2
sudo apt-get install grub-pc # Installs Grub 2
```

---

