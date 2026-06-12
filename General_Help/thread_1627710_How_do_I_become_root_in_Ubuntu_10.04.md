---
title: "How do I become root in Ubuntu 10.04"
date: 2010-11-21
forum: General Help
---

### Post by jacatone on 2010-11-21
I'm trying to become root in Ubuntu 10.04, but I get the following error:

[jacatone@compaq glippy-0.1]$ su
Password: 
su: Authentication failure

What am I doing wrong here? I know I'm using the correct password for my system. Thanks.

---

### Post by Hippytaff on 2010-11-21
Is the username in the sudoers file?

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by mick222 on 2010-11-21
As far as i know you cant become root in Ubuntu you must use sudo inatead of su.

---

### Post by matt_symes on 2010-11-21
Hi

You can use 

sudo su

or 

sudo -i

to become root. 

Type 

exit 

to get back to your account

But i would _really_ not recommend this method. It circumvents one of Linux's basic security structures.

Just use sudo and the command, to run that command at roots privilege level.

Kind regards

---

### Post by Hippytaff on 2010-11-21
Sorry, I missed the point - it's sudo su to become root but> 
but i would _really_ not recommend this method. Just use sudo and the command
+1

---

### Post by uRock on 2010-11-21
The following link will tell you how to set up the super user account, which is not recommended because you can easily ruin your system. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by garvinrick4 on 2010-11-22
##Do not want to type password using sudo for length of time:
#Notice the line Defaults: ,timestamp_timeout=-1 (has been added -1 means for length of
session. If you put 30 means 30 minutes, 40 means 40 minutes and so on.) 
This is in Ubuntu.com community but cannot find link.
```

[CODE]gksudo gedit /etc/sudoers
```# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset,timestamp_timeout=-1


# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
[/code]
##Found link:[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

---

### Post by amite on 2010-11-22
hey, to become root authentication in terminal use $sudo su
and for GUI use $gksu nautilus

---

### Post by phickman68 on 2011-01-20
how do you become root like sudo su but in the graphical desktop?

---

### Post by WorMzy on 2011-01-20
```
gksu <applicationname>
```

Will run an application as root.

---

### Post by WorMzy on 2011-01-20
<double-post>

---

