---
title: "accidently deleted /etc/profile file"
date: 2011-10-07
forum: General Help
---

### Post by CryptKeeper777 on 2011-10-07
I must be more carful in bash... I just managed to delete the file /etc/profile (or more accurately: I overwrote it with an empty file because I though /etc/profile was a directory where I wanted to move the file).

Can someone post me the content of such a /etc/profile file (Ubuntu 11.04)?

---

### Post by Vaphell on 2011-10-07
```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

```

---

### Post by sisco311 on 2011-10-07
In Ubuntu, there should be a copy of the default profile file in /usr/share/base-files/profile

---

### Post by CryptKeeper777 on 2011-10-07
> **sisco311 said:**
> In Ubuntu, there should be a copy of the default profile file in /usr/share/base-files/profile
Yes there is, it has the same content as posted in the first reply. Is this collection of base-files for exactly this purpose, as a backup for unthoughtful users like me? ;)

Thank you both!

A little OT, but anyway: The reason I want to edit the /etc/profile file is that I want to change the root prompt. The user prompt can easily be changed in the .bashrc file. Is editing the /etc/profile file the best way to change the root prompt or is there a better way?

---

### Post by sisco311 on 2011-10-07
> **CryptKeeper777 said:**
> Yes there is, it has the same content as posted in the first reply. Is this collection of base-files for exactly this purpose, as a backup for unthoughtful users like me? ;)


Probably. 

> **CryptKeeper777 said:**
> 
Thank you both!


You are welcome!

> **CryptKeeper777 said:**
> 
A little OT, but anyway: The reason I want to edit the /etc/profile file is that I want to change the root prompt. The user prompt can easily be changed in the .bashrc file. Is editing the /etc/profile file the best way to change the root prompt or is there a better way?

You could edit root's .bashrc file: /root/.bashrc

---

