---
title: "Wine Wont Install"
date: 2010-01-22
forum: General Help
---

### Post by richiejenkins on 2010-01-22
```
richiejenkins@desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages

```

Any Ideas?

---

### Post by Benster900 on 2010-01-22
[FONT=Arial Black]try using synaptic package manager.[/FONT]

---

### Post by richiejenkins on 2010-01-22
> **Benster900 said:**
> [FONT=Arial Black]try using synaptic package manager.[/FONT]

[IMG]http://img25.imageshack.us/img25/6424/screenshotttr.png[/IMG]

---

### Post by Saiko Berry on 2010-01-22
[I]sudo add-apt-repository ppa:ubuntu-wine/ppa
[/I]

---

### Post by richiejenkins on 2010-01-22
Did this instead and worked:

```
sudo apt-get install wine1.2
```

Thanks anyway :D

---

