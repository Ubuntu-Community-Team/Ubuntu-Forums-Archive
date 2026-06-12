---
title: "How to access &quot;users and groups&quot; in Ubuntu 11.10?"
date: 2011-11-06
forum: General Help
---

### Post by ausairman on 2011-11-06
Hi everyone,
I'm following a tutorial on settings up some sshfs settings, and it says the following:

"GNOME users can go to System -> Administration ->  Users and Groups -> (your user) -> Properties -> User  Privileges"

As an unwitting participant in the latest Ubuntu release I guess I am not a GNOME user anymore, but surely it's possible to access this menu somehow form within the new Ubuntu interface?

---

### Post by haqking on 2011-11-06
> **ausairman said:**
> Hi everyone,
I'm following a tutorial on settings up some sshfs settings, and it says the following:

"GNOME users can go to System -> Administration ->  Users and Groups -> (your user) -> Properties -> User  Privileges"

As an unwitting participant in the latest Ubuntu release I guess I am not a GNOME user anymore, but surely it's possible to access this menu somehow form within the new Ubuntu interface?

from terminal

 ```
sudo apt-get install gnome-system-tools
```

or do it from synaptic or software centre (synaptic is not installed by default)

then type users into the dash to bring users and groups up

---

### Post by searchfgold6789 on 2011-11-06
Actually on my friend's computer Users and Groups is installed by default. You shouldn't have to install the gnome-system-tools package. Just search "user" from the dash and it'll show up <;)
 - search

---

### Post by haqking on 2011-11-06
> **searchfgold6789 said:**
> Actually on my friend's computer Users and Groups is installed by default. You shouldn't have to install the gnome-system-tools package. Just search "user" from the dash and it'll show up <;)
 - search

depends on the system.

If its not already there then you need gnome-system-tools installed

I suspect it is to do with a upgrade vs a fresh install

---

### Post by Nipper007 on 2011-11-06
> **haqking said:**
> I suspect it is to do with a upgrade vs a fresh install

The Users and Groups is not available when I installed 11.10 32-bit version as a new install.

---

### Post by hwttdz on 2011-11-06
And the actual command line name is "users-admin".

---

### Post by haqking on 2011-11-06
> **Nipper007 said:**
> The Users and Groups is not available when I installed 11.10 32-bit version as a new install.

I know, thats why i posted in my first post how to install it ;)

---

### Post by searchfgold6789 on 2011-11-06
> **hwttdz said:**
> And the actual command line name is "users-admin".
Cool, I didn't know that.

---

### Post by frozen chosen on 2011-11-11
Go to terminal type in sudo apt-get install-gnome-system-tools
 once installed you will have to access it (users-admin) in terminal

                                                   Hope this helps
                                                    Thank you

---

### Post by haqking on 2011-11-11
> **frozen chosen said:**
> Go to terminal type in sudo apt-get install-gnome-system-tools
 once installed you will have to access it (users-admin) in terminal

                                                   Hope this helps
                                                    Thank you

like in post number [2]("http://ubuntuforums.org/showpost.php?p=11432841&postcount=2")  ;-)

---

### Post by frozen chosen on 2011-11-13
Sorry about that I should have read the whole thread I will be more careful in the future.
                                           Thank You

---

