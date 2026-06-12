---
title: "PATH Variable no longer includes /usr/games/"
date: 2010-05-31
forum: General Help
---

### Post by goldfish2 on 2010-05-31
This is my environment file (I've made no changes to it, this is the system default):

$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
but when I examine my PATH variable:

$ echo $PATH
/home/dan/bin:/home/dan/bin:/bin:/usr/bin:/usr/local/bin:/usr/bin/X11
You'll notice /usr/games is missing (it was there up until a few days ago). My /etc/profile makes no mention of PATH. My ~/.profile is the default and only has:

if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
This only happens in gnome, not in tty1-6. This is missing from both gnome terminal and when I try to call applications from the applications dropdown. Anyone know what could be causing this?

This is a system wide problem and I would like to fix it at the source so don't tell me to just add it to /etc/profile or ~/profile because that isn't where the problem is.  I want to know how Ubuntu is currently deriving PATH so I can fix this in the right spot.

Thanks.

---

### Post by gmargo on 2010-05-31
Do you set $PATH in your $HOME/.bashrc file?

---

### Post by goldfish2 on 2010-06-01
> **gmargo said:**
> Do you set $PATH in your $HOME/.bashrc file?

The only thing in ~/.bashrc that refers to PATH is:
```
PATH=$HOME/bin:$PATH
export PATH
```

My system is pretty default, I have no idea what could cause this.

---

