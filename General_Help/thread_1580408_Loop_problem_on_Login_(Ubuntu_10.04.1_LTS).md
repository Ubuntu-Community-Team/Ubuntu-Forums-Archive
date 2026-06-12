---
title: "Loop problem on Login (Ubuntu 10.04.1 LTS)"
date: 2010-09-23
forum: General Help
---

### Post by RVGL on 2010-09-23
Hello

This is my first message. I am using Kubuntu. When I came back from the  States -- where I stay for long while -- I had to update the system to Ubuntu 10.04 LTS. So I did.

I have now a loop problem for the login process.

On a terminal I can read such a message about BASH : 

0 packages can be updated
0 updates are security updates

-bash: /etc/profile: line 22: Erreur de syntaxe près du symbole inattendu " else "
-bash: /etc/profile: line 22: ' else'
-bash: setenv : commande introuvable
-bash: setenv : commande introuvable
-bash: setenv : commande introuvable
-bash-4.1$

I am sorry for the french text.

Do you have any idea what happened and above all : what to do ?

I thank you very much.:smile:

---

### Post by andrewthomas on 2010-09-23
Post the output of 

```
cat /etc/profile
```

---

### Post by RVGL on 2010-09-24
Thanks AndrewThomas

This is the result of cat /etc/profile


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



tdc500 is offline         Reply With Quote

---

### Post by andrewthomas on 2010-09-24
You may have a problem with a character that I can't see.  I attached a copy of my /etc/profile

You could 
```

sudo mv /etc/profile /etc/profile.old
sudo mv  /path/to/downloaded-file /etc/profile
```and see if there is a difference.

# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

```
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

### Post by RVGL on 2010-09-25
Dear Andrewthomas

You were right. In fact when I copy (by hand !!!!) the /etc/profile I did not see a very strange 's' after the 'then' in
if [ "`id -u`" -eq 0 ]; thens
So I did

sudo vi /etc/profile > supress of the s

every thing is under control now.

I thank you very much.

Do you have an idea of the origin of this 's' ?

Have a very nice day.

RVGL

---

