---
title: "No username/working directory in terminal"
date: 2010-10-01
forum: General Help
---

### Post by clemons32 on 2010-10-01
Hi, I'm new to the forum, but I'm having a very simple (i hope) problem with the terminal. I'm using Ubuntu 9.10, and after creating a new user, the username and working directory does not appear in the terminal. I can still access other directories in the terminal, and typing 'pwd' does in fact show the correct directory I'm working in. But all that appears where I type commands is '$' instead of 'username@host:~$' Any suggestions?

---

### Post by andrewthomas on 2010-10-01
There may be a problem with the ~/.bashrc file

Do lines 59-66 look like this?

```
# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac
```

---

### Post by sisco311 on 2010-10-01
> **clemons32 said:**
> Hi, I'm new to the forum, but I'm having a very simple (i hope) problem with the terminal. I'm using Ubuntu 9.10, and after creating a new user, the username and working directory does not appear in the terminal. I can still access other directories in the terminal, and typing 'pwd' does in fact show the correct directory I'm working in. But all that appears where I type commands is '$' instead of 'username@host:~$' Any suggestions?

Make sure that the user's login shell is /bin/bash:
```
chsh -s /bin/bash
```

---

### Post by clemons32 on 2010-10-01
Thanks guys. Yep that was it, sisco311. It was set to /bin/sh. Thanks again!

---

### Post by sisco311 on 2010-10-01
No problem.

Oh, and welcome to the forums!

---

