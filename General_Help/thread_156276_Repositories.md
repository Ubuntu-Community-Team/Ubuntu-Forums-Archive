---
title: "Repositories"
date: 2006-04-06
forum: General Help
---

### Post by WSTGangsta on 2006-04-06
I added a repository incorrectly with Adept, and now Adept doesn't load. It says that APT database could not be opened. How do I get root permissions to edit ect/apt/sources.list?

---

### Post by rado_london on 2006-04-06
Put "sudo" without the quotes before the command. So to edit sources.lst the comman should look like this:
```
sudo gedit /etc/apt/sources.list
```

It will ask you for password. You need to fill your user password.

Good luck

---

### Post by WSTGangsta on 2006-04-06
I dont have gedit, I have Kate, and thats not starting for some reason it says:
```
tony@linux:~$ sudo kate /ect/apt/sources.list
Error: "/var/tmp/kdecache-tony" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.

```

---

### Post by aysiu on 2006-04-06
KMenu > System > Konsole ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo kwrite /etc/apt/sources.list
```

---

### Post by WSTGangsta on 2006-04-06
[QUOTE=aysiu]KMenu > System > Konsole ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup sudo kwrite /etc/apt/sources.list
```[/QUOTE] Thanks so much that worked perfect!
EDIT: Crap, I "properly" did it, now when I try to use apt-get install whatever, this happens:
```
tony@linux:~$ sudo apt-get install apache
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by WSTGangsta on 2006-04-06
Sorry I have to bump this so that my new question gets answered... :oops:

---

### Post by aysiu on 2006-04-06
```
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
``` This usually means you're trying to apt-get when Adept or Synaptic Package Manager is open.

---

### Post by WSTGangsta on 2006-04-06
I looked at the running process thing, and adept is running, but once again without root privilege's I can't end it.

---

### Post by Fatstink on 2006-04-06
are you trying to run adept and us apt-get at the same time?

---

### Post by WSTGangsta on 2006-04-06
Nope, I am using other websites to find ways to get software, I cant wait till my dad cancels DSL, it complicates everything! (constantly crapping out during a download)

---

### Post by aysiu on 2006-04-06
```
sudo killall adept
```

---

### Post by WSTGangsta on 2006-04-06
Yeah thats what I did, actually. It would be nice if root access wasnt such a pain in the ***.

---

