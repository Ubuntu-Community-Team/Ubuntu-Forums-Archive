---
title: "How do I upgrade from 5.04 to 5.10?"
date: 2006-03-12
forum: General Help
---

### Post by plavi on 2006-03-12
I would like to upgrade from 5.04 to 5.10. But I don't want to do a clean installation!
Did somebody know how?

---

### Post by kittycatsexycat on 2006-03-12
i think there's a command to upgrade from hoary to breezy...

try
apt-get upgrade hoary

i'm not sure but i'm certain there's a command....

just not from breezy to dapper yet...

---

### Post by localzuk on 2006-03-12
You need to edit the file /etc/apt/sources.list

Run ```
sudo gedit /etc/apt/sources.list
``` from a terminal.

Replace all references to 'hoary' with 'breezy'.

Now run 
```
sudo apt-get update
sudo apt-get dist-upgrade
```

This will take a while - then all you should need to do is restart your computer.

---

### Post by gdcondor on 2006-03-12
You have to change "hoary" to "breezy" in the repositories of synaptics and then update all the packages.

It's a good idea to check that ubuntu-base and ubuntu-desktop are installed or selected to be installed.

---

### Post by plavi on 2006-03-12
Thanks I will try

---

### Post by dcstar on 2006-03-12
[QUOTE=plavi]I would like to upgrade from 5.04 to 5.10. But I don't want to do a clean installation!
Did somebody know how?[/QUOTE]
You go to the clearly marked "Installation and Upgrade Help" forum, you then look at the top thread called "Breezy Upgrade Notes":

[http://ubuntuforums.org/showthread.php?t=74990](http://ubuntuforums.org/showthread.php?t=74990)

---

### Post by localzuk on 2006-03-12
That isn't a very nice message for a new member of the forum...

---

