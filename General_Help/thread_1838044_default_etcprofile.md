---
title: "default /etc/profile"
date: 2011-09-02
forum: General Help
---

### Post by coweatyou on 2011-09-02
Can someone post the default /etc/profile file?  An installer lopped off the first few lines of mine.

---

### Post by sum1nil on 2011-09-02
Here you go: :popcorn:

> # /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
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

---

### Post by coweatyou on 2011-09-02
Thank you.

---

