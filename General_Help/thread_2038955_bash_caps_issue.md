---
title: "bash caps issue"
date: 2012-08-07
forum: General Help
---

### Post by icegood on 2012-08-07
After executing cd .. 
In my terminal i get new command with first letter capsed. What could it be?

---

### Post by papibe on 2012-08-07
Hi icegood.

Could you paste the text, or post a  screenshot? 

Regards.

---

### Post by icegood on 2012-08-08
What you don't understand? 
Just press 7 keys: "cd .. <enter> rm"
You will see
```

ice@ubuntu:~/science/main/monte_carlo_offlattice_moldyn/src$ cd ..
ice@ubuntu:~/science/main/monte_carlo_offlattice_moldyn$ Rm

```
Valid for both 'ice' and root account

---

### Post by papibe on 2012-08-08
:confused: That's very odd indeed!

Have you customized your ~/.bashrc in any way?

Could you post the result of this command?
```
diff  /etc/skel/.bashrc   ~/.bashrc

```
Regards.

---

### Post by icegood on 2012-08-08
if it valid for root account too, don't see any reasons to diff my own bashrc. But OK,
```

ice@ubuntu:~/science/main/monte_carlo_offlattice_moldyn/src$ diff  /etc/skel/.bashrc   ~/.bashrc
ice@ubuntu:~/science/main/monte_carlo_offlattice_moldyn/src$ cat ~/.profile 
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
        . "$HOME/.bashrc"
    fi
fi

export SVN_EDITOR=gedit

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
ice@ubuntu:~/science/main/monte_carlo_offlattice_moldyn/src$ 


```
and yes
```

ice@ubuntu:~/science/main/monte_carlo_offlattice_moldyn/src$ cat /etc/profile
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "$PS1" ]; then
  if [ "$BASH" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
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

# The default umask is now handled by pam_umask.
# See pam_umask(8) and /etc/login.defs.

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi
ice@ubuntu:~/science/main/monte_carlo_offlattice_moldyn/src$

```

---

### Post by papibe on 2012-08-08
May be it is your prompt?

Could you post the result of this command?
```
echo "$PS1"
```
Regards.

---

### Post by icegood on 2012-08-09
```

ice@ubuntu:~/science/main/monte_carlo_offlattice_moldyn$ echo "$PS1"
\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$ 

```

---

### Post by Habitual on 2012-08-13
You may have  a sticky Shift key on the keyboard...?
 
short test...
terminal >
```
cd \
cd /home/ice/science/main/monte_carlo_offlattice_moldyn 
cd - 
```See the symptom?

terminal >
```
type -t cd
``` should say "builtin" and 
```
grep source .bashrc
```Please let us know...

Edit: I realized after I posted that "grep source .bashrc" may not produce any results, so I have to ask, after you cp'd the /etc/skel/.bashrc  to ~, did you (re)source the .bashrc or logout and back in to see if the problem still existed?

Also, do the problem exist outside of the GUI, say at the console...?

Please let us know...

---

