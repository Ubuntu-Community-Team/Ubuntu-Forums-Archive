---
title: "Run command in other language"
date: 2009-10-25
forum: General Help
---

### Post by gaiterin on 2009-10-25
Hi! I'm developing Gufw, and I have a problem. Can you help me, please? Thanks :)
(Bug in Launchpad: [https://bugs.launchpad.net/gui-ufw/+bug/459554](https://bugs.launchpad.net/gui-ufw/+bug/459554))

The question is: How can I run a command in the terminal in other language?

I explain:
By example, I enter in Ubuntu with Spanish language.
But I like run a command from my application in english, for check the result in english, I do: LANG=en sudo ufw status
but the exit is in Spanish.

I need the exit of "sudo ufw status" in english, not translate to spanish:
```
marcos@marcos-desktop:~$ LANG=en sudo ufw status
Estado: activo

A                          Acción     De
-                          -------     --
51413/tcp                  ALLOW       Anywhere

marcos@marcos-desktop:~$ 
```

Thanks!

---

### Post by gaiterin on 2009-10-25
Uhm... I don't undertand!

In Ubuntu 9.10 the setting LANG=en not works (the command returns the exit in actual language).
Ubuntu 9.10 exit:
```
marcos@marcos-laptop:~$ LANG=en sudo ufw status
Estado: activo

A                          Acción De
--                         ------  ----
51413/tcp                  ALLOW   Anywhere

marcos@marcos-laptop:~$ 
```






But in Ubuntu 9.04 works! (the command returns the exit in english language):

Ubuntu 9.04 exit:
```
marcos@marcos-laptop:~$ sudo ufw status
[sudo] password for marcos: 
Estado: activo

A                          Acción De
--                         ------  ----
51413/tcp                  ALLOW   Anywhere


marcos@marcos-laptop:~$ LANG=en sudo ufw status
Status: active

To                         Action  From
--                         ------  ----
51413/tcp                  ALLOW   Anywhere

marcos@marcos-laptop:~$ 
```

Any idea, please?
Is it a bug in some package maybe?
Thanks!

---

### Post by P4man on 2009-10-25
perhaps you need to install the languages first ? System > administation > language supprt > install/remove languages. Just guessing really.

---

### Post by gaiterin on 2009-10-25
@p4man That isn't the problem, all languages are installed.

---

### Post by sisco311 on 2009-10-25
```
sudo env LANG=en_US.UTF-8 ufw status
```

---

### Post by gaiterin on 2009-10-25
@sisco311: Not works for me :( Thanks by idea ;)

```
marcos@marcos-laptop:~$ sudo env LANG=en_US.UTF-8 ufw status
Stato: attivo

A                          Azione      Da
-                          ------      --
51413/tcp                  ALLOW       Anywhere

marcos@marcos-laptop:~$ 
```

Any more ideas, please? Thanks!

---

### Post by sisco311 on 2009-10-25
You have to install the translation packs:
```
sudo apt-get install language-pack-en
```
for GUI applications:
```
sudo apt-get install language-pack-gnome-en
```

---

### Post by geirha on 2009-10-25
Setting LANG to an empty string should disable translations, which usually means it will be in english.

```
sudo env LANG= ufw status
LANG= sudo ufw status
```

---

### Post by gaiterin on 2009-10-25
I don't understand *-)

I have 2 partitions:
- A new instalation of Ubuntu 9.10
- Ubuntu 9.10 upgraded from Ubuntu 9.04

The result of command: LANG=en sudo ufw status is:
- A new instalation of Ubuntu 9.10: WORKS
- Ubuntu 9.10 upgraded from Ubuntu 9.04: NOT WORKS

The result of command: LANGUAGE=en sudo ufw status
- A new instalation of Ubuntu 9.10: WORKS
- Ubuntu 9.10 upgraded from Ubuntu 9.04: WORKS

But I don't undertand, LANG=en must be works. Is it LANGUAGE a valid command?

Can anybody test this in an upgraded system, please? Thanks!

---

### Post by gaiterin on 2009-10-25
I don't understand...
In the upgraded Ubuntu from Ubuntu 9.04, If I run another command with LANG=en works! But ufw command not!

marcos@marcos-laptop:~$ chmod +x --verbose test
el modo de «test» cambia a 0755 (rwxr-xr-x)
marcos@marcos-laptop:~$ LANG=en chmod +x --verbose test
mode of `test' retained as 0755 (rwxr-xr-x)
marcos@marcos-laptop:~$ sudo ufw status
Estado: activo

A Acción De
- ------- --
51413/tcp ALLOW Anywhere

marcos@marcos-laptop:~$ LANG=en sudo ufw status
Estado: activo

A Acción De
- ------- --
51413/tcp ALLOW Anywhere

marcos@marcos-laptop:~$
marcos@marcos-laptop:~$ chown -v marcos:marcos test
el propietario de «test» permanece como marcos:marcos
marcos@marcos-laptop:~$ LANG=en chown -v marcos:marcos test
ownership of `test' retained as marcos:marcos
marcos@marcos-laptop:~$

Any idea about this anormal run? Thanks

---

### Post by sisco311 on 2009-10-25
If the *env_reset* option is enabled in the /etc/sudoers file, sudo resets some environment variables.

You can preserve the environment variables with sudo -E:
```
LANG=en sudo -E ufw
```

Or just the LANG variable:
```
sudo env LANG=en ufw
```

for more info please read the man page:
```
man sudo | less --pattern\="SECURITY NOTES"
```

btw, what's the output of:
```
sudo sudo -V
```
the command will print out a list of the defaults sudo was compiled.

---

