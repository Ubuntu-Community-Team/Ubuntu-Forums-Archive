---
title: "Password problem"
date: 2011-02-12
forum: General Help
---

### Post by Ryssen on 2011-02-12
I did a new install and every thing went well,I can create mew users and install new programs with the password.Then all of a sudden when trying to install programs it wont accept the password...
I even did another new installation (Virtual box) and the same thing happend.
After a while it won accept the password.
Is there a soultion to this?   :(


Edit:The password still works to logg in to my user.

---

### Post by uRock on 2011-02-12
Which version are you using? 

What were you doing the last time it excepted your password?

---

### Post by Ryssen on 2011-02-12
It is Ubuntu 10.10
As I have Ubuntu on Virtual box I Think I was working in windows,can remember doing anything special in Ubuntu,

---

### Post by williamts99 on 2011-02-12
> **Ryssen said:**
> It is Ubuntu 10.10
As I have Ubuntu on Virtual box I Think I was working in windows,can remember doing anything special in Ubuntu,


I had an issue with this concerning a network installation of Lubuntu.  Not sure if this is the same problem, but seems like it.
The solution from the linked post was to open a terminal, and run
```
gconf-editor
```

Navigate to Apps>gksu
Ensure that 'sudo mode' is checked.


[http://ubuntuforums.org/showpost.php?p=9866562&postcount=3](http://ubuntuforums.org/showpost.php?p=9866562&postcount=3)

---

