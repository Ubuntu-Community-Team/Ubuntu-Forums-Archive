---
title: "Add directory to PATH"
date: 2009-12-24
forum: General Help
---

### Post by werdna5225 on 2009-12-24
I am trying to install gnome shell and I keep having the message "PATH does not contain /home/andrew/bin, it is recommended that you add that."  I think I should be adding global profile at /etc/profile, but whenever I add the line, nothing happens.  I have attached a copy of /etc/profile.  ANy help would be greatly appreciated.



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

---

### Post by prshah on 2009-12-24
Hi, global paths are in /etc/environment
```
Thu Dec 24 @14:27:43:~$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_IN"
SLASHEMOPTIONS=/home/user/.slashemrc
INTEL_BATCH=1
Thu Dec 24 @14:27:44:~$ 

```

Separate multiple paths with a ":", not ";" as in the Windows world. Just FYI.

---

### Post by redmk2 on 2009-12-24
> **werdna5225 said:**
> I am trying to install gnome shell and I keep having the message "PATH does not contain /home/andrew/bin, it is recommended that you add that."  I think I should be adding global profile at /etc/profile, but whenever I add the line, nothing happens.  I have attached a copy of /etc/profile.  ANy help would be greatly appreciated.

...



Why do you feel you need a global path statement?  When you are logged in you are and using ~/andrew/bin it should be in your shell path, but not globally.

I would use the the .bashrc file.  This is the file that sets ***your ***shell environment.

I'm not near any Ubuntu hosts at the moment, so this is by memory; at the bottom of my .bashrc file I have this PATH=$PATH:/home/me/bin (or close to that).

[**_[COLOR="DarkSlateGray"]Here is the Google search[/COLOR]_**]("http://www.google.com/search?q=.bashrc+*+path&btnG=Go!") for the information.

---

