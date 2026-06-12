---
title: "sudoers i nopasswd, running few scripts without typing password"
date: 2009-11-25
forum: General Help
---

### Post by mateusz16 on 2009-11-25
Hi everyone! i have got a big problem;/ i`ve got some troubles with my laptop after few weeks i can turn on every device in my acer but i always have to  set the commands manualy. i want to do this autmaticly but it needs password and sudo command before.
all in all i have tried few time befeore to edit /etc/sudoers file but nothing has changed.
i want i can use command /etc/init.d/alsa-utils with sudo but without typing a password my /etc/sudoers looks like that
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```
i try to use command cp and /etc/init.d/alsa-utils but when i dont use sudo it tells me that i don have premission (in "cp" case for example during copying files from /bin folder and when i use sudo it ask me for password anyway. Have you any advice for me? meybe someone could paste how my file should look? i would be very greatfull ;]

P.S
sorry for my english i`m still lerning ;]

---

### Post by SuperSonic4 on 2009-11-25
This: ```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

Should read: ```
# Members of the admin group may gain root privileges
%admin NOPASSWD: ALL=(ALL) ALL
```

---

### Post by mateusz16 on 2009-11-25
no, i want to not type password only to few commands not for all...

---

### Post by Mr. Devil on 2009-11-25
```
%admin ALL=NOPASSWD: /sbin/shutdown

```Just an example - /sbin/shutdown can be replaced with whatever you want.

---

### Post by sisco311 on 2009-11-25
[thread=1132821]HowTO: Sudoers Configuration[/thread]
> This guide is aimed at giving a beginners transition into configuring sudo, and builds up the knowledge enough to tailor permissions for a basic multi-user system (ie: Family Computer).

NOTE:
You **MUST** edit the suders file with the **visudo** command as root!

---

