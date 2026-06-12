---
title: "Sudoer set permission for penggy"
date: 2006-06-27
forum: General Help
---

### Post by Jeff59 on 2006-06-27
Hi all i'm trying to set up [COLOR="Blue"]"penggy" [/COLOR]for access to AOL for may 84yr old father.  I have everything working but  I would like to be able to have him run it with out having to type a password to access the modem.   I have tryied sudo visudo -s  but I must have the wrong syntex.  Here is what I have but I'm not sure if I'm calling the right location.  

[COLOR="Blue"]# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
bob ALL= NOPASSWD: /var/run/penggy.pid
# Members of the admin group may gain root privileges[/COLOR]

Any help would be great,  Thanks

---

### Post by sebos69 on 2006-06-29
Yeah, I have a very similar problem trying to launch the omke.pl script (for keyboard mapping) at startup and it needs root privileges. I tried the same methos, without any success.

---

### Post by gyterpena on 2006-06-29
Not working, sudo still keep asking for paswd.

# User privilege specification
root    ALL = (ALL) ALL
peter   ALL = NOPASSWD: ALL
#Members of the admin group may gain root privileges
%admin ALL = (ALL) ALL

---

### Post by aysiu on 2006-06-29
This line should work: ```
bob ALL= NOPASSWD: /var/run/penggy.pid
``` but I'm not sure that /var/run/penggy.pid is really the command. Don't commands usually live in /usr/bin somewhere?

---

