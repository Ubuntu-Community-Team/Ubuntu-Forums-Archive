---
title: "Lost /etc/profile configuration"
date: 2011-09-12
forum: General Help
---

### Post by paolomarco on 2011-09-12
I did a double install of AMD SDK....

The result is, since it was a known bug, but not to me, to a comple damage of that file.
I have checked and there are no backup copies left....

Can you please help me ? Posting yours ?

Is there a way to rebuild it ? 

Thanks a lot to everyone... 

This is the situation now....



```


more /etc/profile


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
AMDAPPSDKROOT="/opt/AMDAPP"
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:"/opt/AMDAPP/lib/x86_64":"/opt/AMDAPP/lib/x86"
export AMDAPPSDKROOT
export LD_LIBRARY_PATH


```


Any Help ?

Could you read and post here your /etc/profile ?

---

### Post by paolomarco on 2011-09-12
Please Help  me !  :popcorn:

---

### Post by saltmarshlamb on 2011-09-12
Not sure if it's anyhelp - but here's mine though I've not installed amd sdk so perhaps it's of no use.

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

### Post by sisco311 on 2011-09-12
There is a copy of the default file in /usr/share/base-files/

---

### Post by paolomarco on 2011-09-12
> **sisco311 said:**
> There is a copy of the default file in /usr/share/base-files/
  Great !!! 

If i knew it !!!!

Thanks a lot to all of you !!!


:KS:KS:KS:KS:KS

---

### Post by sisco311 on 2011-09-12
You are welcome!

---

