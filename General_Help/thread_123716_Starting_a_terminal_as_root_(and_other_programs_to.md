---
title: "Starting a terminal as root? (and other programs too!)"
date: 2006-01-30
forum: General Help
---

### Post by Jiketsu on 2006-01-30
Hi hi,

As most of us know, Ubuntu does not use the traditional userlevels where there is a regular username account, and then there is a root account. They are sort of merged together, into some crazy super account. When we need to use a priviledged command, we have been prefixing them with **sudo** to assist with this.

Well, not all commands work with sudo, such as the instructions for masquerading at this thread:

[http://www.ubuntuforums.org/showthread.php?t=91370](http://www.ubuntuforums.org/showthread.php?t=91370)

I still get permission errors. Well before I upgraded from 5.04 to 5.10 I had a shortcut in my Applications menu for running a terminal as root. This alleviated the need for any sudo prefixes; and I was able to perform the masquerading instructions just fine.

I would very much so like to get this back, but I have no idea how to create a shortcut for a terminal (or any program for that matter) to run as root or a different user.

If someone could kindly explain this to me I would be very much appreciative. It would sort of be nice if Ubuntu could be installed using the old method of having a separate root account. It would be much nicer.

Thank you for your help!

---

### Post by zappa86 on 2006-01-30
If you open a regular terminal and you type:
```
sudo -s -H
```
and enter your password you should get a root shell. Does that work.

If not, go into the terminal and type:
```
groups
```
and see if you see 'admin' as one of your groups.

finally post back your /etc/sudoers file so we can see if the permissions are in the right place.

---

### Post by dcstar on 2006-01-30
[QUOTE=Jiketsu]Hi hi,
.....
I still get permission errors. Well before I upgraded from 5.04 to 5.10 I had a shortcut in my Applications menu for running a terminal as root. This alleviated the need for any sudo prefixes; and I was able to perform the masquerading instructions just fine.

I would very much so like to get this back, but I have no idea how to create a shortcut for a terminal (or any program for that matter) to run as root or a different user.
......[/QUOTE]

Root Terminal: gksudo /usr/bin/x-terminal-emulator

File Browser (Root): gksudo "nautilus --browser %U"

---

### Post by Jiketsu on 2006-01-30
sudo -s -H worked perfectly, Thank you.

And also:

```
root@taminaru:/home/chibi # cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
```What can I do with this?

==== 

dcstar I am grateful for your response as well. I think the file manager one is especially usefull, I know I've needed it before.

Thanks.

---

### Post by Sutekh on 2006-01-30
[QUOTE=Jiketsu]What can I do with this?
[/QUOTE]
I don't think you need to do anything.  You *can* edit /etc/sudoers to allow use of 'sudo' without supplying a password.  IMO it's not really necessary and could lead to problems, so I'd leave things as they are.

---

