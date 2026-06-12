---
title: "not root ?"
date: 2010-04-30
forum: General Help
---

### Post by Nisal on 2010-04-30
can any one tell me y this error getting ?

i was trying this command 

sudo apt-get install sinhala-gnu-linux

and i got this :S


E:```
 Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```
nisal@nisal-desktop:~$


Edit

Now im getting 
[B]E: Couldn't find package sinhala-gnu-linux
[/B]

---

### Post by Smart Viking on 2010-04-30
Looks like you come from another linux distro and is not familiar with the sudo command.

sudo apt-get install sinhala-gnu-linux

That will do, write your login password when it ask you.

---

### Post by Nisal on 2010-04-30
> **Smart Viking said:**
> Looks like you come from another linux distro and is not familiar with the sudo command.

sudo apt-get install sinhala-gnu-linux

That will do, write your login password when it ask you.

no man i use carmic cola :S

---

### Post by Serpher on 2010-04-30
He's right though, you need to put sudo in front of the command. You can't preform administrator actions without either using the sudo command, or logging  in as root which is a stupid thing to do.

---

### Post by dino99 on 2010-04-30
are you the main user or hacking ?

---

### Post by Nisal on 2010-04-30
> **dino99 said:**
> are you the main user or hacking ?

im the main user and this is the regular account i use

> He's right though, you need to put sudo in front of the command. You can't preform administrator actions without either using the sudo command, or logging in as root which is a stupid thing to do.and sorry i use with sudo it was a mistake when posting anyway still same results

---

### Post by Serpher on 2010-04-30
That package does not exist. This is how you install it: 

[quote=http://sinhala.sourceforge.net/]Ubuntu 9.10 (Karmic) and Above (may work on older versions)

The Universe repository should already be enabled (wiki.ubuntu.com/AlwaysEnableUniverseMultiverse). If not, first enable the Universe repository.

As root/superuser, run:

apt-get install ttf-sinhala-lklug ibus im-switch ibus-m17n m17n-db m17n-contrib language-pack-si-base
From your user account (i.e. not root) run:

rm -f ~/.xinput.d/* ; im-switch -z all_ALL -s ibus
Logout and login again. Environment variables need to be set/updated (NO NEED TO REBOOT)

From your user account (i.e. not root) select your keyboard layouts by running:

ibus-setup[/quote]

---

### Post by Nisal on 2010-04-30
> **Serpher said:**
> That package does not exist. This is how you install it:

ok thanks its done :)

---

