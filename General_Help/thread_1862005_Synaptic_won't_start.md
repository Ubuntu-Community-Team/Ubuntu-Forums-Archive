---
title: "Synaptic won't start"
date: 2011-10-16
forum: General Help
---

### Post by Trior27 on 2011-10-16
Hello!

I can't start the synaptic package manager I get the following error starting it from a terminal and from the system/admin menu.

```
E: ERROR: no s'ha pogut crear el directori de configuració /root/.synaptic - mkdir (2: El fitxer o directori no existeix)
```

(I translated it here)
```
E: ERROR: unable to create setup directory /root/.synaptic - mkdir (2: File or directory does not exist)
```

I've been struggling with Wine recently in order to install an old game ([[COLOR="RoyalBlue"]which I have't succeeded yet[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1861822")) Maybe I changed something I shouldn't have... but I don't know what might that be :roll:

---

### Post by MooPi on 2011-10-16
Can you access a terminal and enter this command
```
sudo apt-get update
```
if you can successfully update the underlying code stucture for synaptic is working and you probably just need to add the directory listed in the error message.
So from terminal type this command
```
sudo mkdir /root/.synaptic
```
Then reattempt to start Synaptic

---

### Post by MooPi on 2011-10-16
I can't edit the last post so here is additional info.
If during your attempt to configure wine did you give root a password ?
I found this thread describing a similar error message here:
[http://ubuntuforums.org/showthread.php?t=733932]("http://ubuntuforums.org/showthread.php?t=733932")

---

### Post by Trior27 on 2011-10-16
Yes, your first post solved the problem.
Error message came after typing the password... I wonder how did I manage to erase that directory?

Works perfectly. Much obliged :D

---

### Post by ajsoulmate on 2011-10-16
i have the same problem but with another error message :/

```
Could not launch 'Synaptic Package Manager'
Failed to execute child process "gksu" (No such file or directory)
```

---

### Post by MooPi on 2011-10-16
Try to open Synaptic through terminal
```
gksudo synaptic
``` And see if that solves your problem. But your menu item should open with the same process and isn't Hmmmm ?

---

