---
title: "Weird bug with su/sudo root"
date: 2010-01-14
forum: General Help
---

### Post by ThePhilosopher57 on 2010-01-14
Hi all
 
su root is not working, it always say the password is not good but I am sure it has been correctly typed.
 
So I am using sudo -s for logging in and it worked for a while. But than, it start saying ''cannot find command'' or ''commande introuvable'' in french
 
Any other way to log in root? To fix this problem I can restart the computer tought...
thanks 
 
 
[SIZE=2]pol@pol-desktop:~$ sudo -s root[/SIZE]
[SIZE=2][sudo] password for mat: [/SIZE]
[SIZE=2]/bin/bash: root : commande introuvable[/SIZE]
[SIZE=2]pol@pol-desktop:~$ sudo -s root[/SIZE]
[SIZE=2]/bin/bash: root : commande introuvable[/SIZE]
[SIZE=2]pol@pol-desktop:~$ sudo -s root[/SIZE]
[SIZE=2]/bin/bash: root : commande introuvable[/SIZE]
[SIZE=2]pol@pol-desktop:~$ sudo -s root[/SIZE]
[SIZE=2]/bin/bash: root : commande introuvable[/SIZE]
[SIZE=2]pol@pol-desktop:~$ su root[/SIZE]
[SIZE=2]Mot de passeÂ : [/SIZE]
[SIZE=2]suÂ : Ã‰chec d'authentification[/SIZE]
[SIZE=2]pol@pol-desktop:~$ sudo -s root[/SIZE]
[SIZE=2]/bin/bash: root : commande introuvable[/SIZE]

---

### Post by tom4everitt on 2010-01-14
Personally I use:

sudo su

Does that work?

---

### Post by snowpine on 2010-01-14
Logging in as root is not recommended on these forums.

'sudo -i' is the Ubuntu equivalent of 'su' in other distros.

Hope that helps. :)

---

### Post by sisco311 on 2010-01-14
By default, the root account password is locked. su prompts you for the target user's password (by default root).
 
use:
```
sudo command
```
to run a command as root.

For more information, please read:
[uhelp]community/RootSudo[/uhelp]
and
```
man sudo_root
man sudo
```

---

### Post by DestructionsRightHand on 2010-01-14
try, sudo bash

---

### Post by sisco311 on 2010-01-14
> **tom4everitt said:**
> Personally I use:

sudo su

Does that work?

> **DestructionsRightHand said:**
> try, sudo bash

I wouldn't recommend this commands. They both start a root shell, but they keep some of the user's environment variables. 

sudo is a well designed setuid root command and it already has this functionality: sudo -s. Using some obscure combination of commands to gain the same functionality may circumvent sudo's security mechanism.

For a brief overview of some of the differences between su, su -, and sudo -{i,s} see : [Difference between sudo su and sudo -s]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4")

I do not want to offend anyone, but I can't understand why is *sudo su* so popular? What's next? *pkexec sudo su -c "ping localhost"*? :P

@ThePhilosopher57
Once again, please read the community documentation and the man pages carefully.  
 

@snowpine
*sudo -i* is sort of like an equivalent of *su -* ;)

---

### Post by tom4everitt on 2010-01-15
> **sisco311 said:**
> I wouldn't recommend this commands. They both start a root shell, but they keep some of the user's environment variables. 

sudo is a well designed setuid root command and it already has this functionality: sudo -s. Using some obscure combination of commands to gain the same functionality may circumvent sudo's security mechanism.



Sure, but admit its convenient to not have to type sudo every time at some occasions :) 

It should be used with care of course, and not as the standard way of doing things in the terminal.

---

### Post by ThePhilosopher57 on 2010-01-15
> **sisco311 said:**
> I wouldn't recommend this commands. They both start a root shell, but they keep some of the user's environment variables. 
 
sudo is a well designed setuid root command and it already has this functionality: sudo -s. Using some obscure combination of commands to gain the same functionality may circumvent sudo's security mechanism.
 
For a brief overview of some of the differences between su, su -, and sudo -{i,s} see : [Difference between sudo su and sudo -s]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4")
 
I do not want to offend anyone, but I can't understand why is *sudo su* so popular? What's next? *pkexec sudo su -c "ping localhost"*? :P
 
@ThePhilosopher57
Once again, please read the community documentation and the man pages carefully. 
 
 
@snowpine
*sudo -i* is sort of like an equivalent of *su -* ;)
 
 
sudo su work but I'll use sudo command.
 
I was in a hurry yesterday, I was unable to read the docs. Thanks for the help all.

---

