---
title: "sudo: gedit: command not found"
date: 2006-04-28
forum: General Help
---

### Post by Flowing_air on 2006-04-28
When i try to change the source list. I used the commands 
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

But it shows that "sudo: gedit: command not found"
what's wrong with my Kubuntu, is there anything i need to install?

---

### Post by monomaniacpat on 2006-04-28
Kubuntu uses Kate (I believe it's called) instead of gedit. If you want to use gedit, download it with synaptic.

---

### Post by cgjones on 2006-04-28
If you are trying to start a graphical program, such as gedit (or kate in Kubuntu), you need to use kdesu, I think.
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
**kdesu** kate /etc/apt/sources.list

```

---

### Post by Sef on 2006-04-28
> If you are trying to start a graphical program, such as gedit (or kate in Kubuntu), you need to use kdesu, I think.

That is not correct.  Just sudo gedit (or kate) file_name

e.g., sudo gedit /etc/apt/sources.list  will do the trick.  No getting into root needed.

---

### Post by ajgreeny on 2006-04-28
Sorry, sef, but *sudo kate filename* will give you an error message
"kate: ERROR: Communication problem with kate, it probably crashed."
You do need *kdesu kate filename*.
*sudo gedit filename* is OK.  Something to do with KDE, obviously.

---

### Post by cgjones on 2006-04-28
This is from the wiki, unless this way of doing it has changed.
> 
To run a program using sudo that normally is run as the user, such as gedit, go to Applications --> Accessories --> Terminal and enter gksudo gedit.

For users of Kubuntu, use kdesu in replacement for gksudo.


---

### Post by Flowing_air on 2006-04-28
Thanks everyone...:)
I am really not familiar with linux, it take me weeks time to set up my Kubuntn..:P
I have checked this command.

brant@CMGY:~$ sudo kate /etc/apt/sources.list
Error: "/var/tmp/kdecache-brant" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.

but when i used kdesu kate /etc/apt/sources.list.
It works...

And is there any other command made different from ubuntu?

---

### Post by aysiu on 2006-04-28
```
sudo kate
``` is a **really** bad idea that will

a) probably not work
b) probably mess up your user permissions and/or ~/.ICEauthority file.

If you must use Kate, do ```
kdesu kate
```

---

### Post by mjm115 on 2006-04-28
sudo cannot access the GUI for Kubuntu.  You'll get all kinds of errors.  you can either:

> 
sudo vi /etc/apt/sources.list


or

> 
kdesu kate


---

### Post by aysiu on 2006-04-28
You can also ```
sudo nano
```

I know that ```
sudo kwrite
``` works without any obviously adverse effects, but ```
kdesu kwrite
``` is the proper way to use KWrite with root privileges.

---

