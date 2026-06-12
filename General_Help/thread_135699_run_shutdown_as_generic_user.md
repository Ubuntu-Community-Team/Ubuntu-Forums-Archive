---
title: "run shutdown as generic user"
date: 2006-02-24
forum: General Help
---

### Post by Skeletonix on 2006-02-24
Hello! I found here small [HOW-TO: non-root user shutdown]("http://www.ubuntuforums.org/showthread.php?t=134968&highlight=nopasswd+shutdown")...but it dosn't work. when I write *sudo shutdown -r now* I must write the pasword! Pleas, Do you know where is mistake :cry:  ? 

[COLOR="Black"]**What I did:**[/COLOR]

**1.** /etc/group :        *[HTML]shutdown:x:334:skeletonix[/HTML]*

**2.** /etc/sudoers : 

 [I]# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

%shutdown ALL=(root) NOPASSWD: /sbin/reboot
%shutdown ALL=(root) NOPASSWD: /sbin/halt
%shutdown ALL=(root) NOPASSWD: /sbin/shutdown

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL)  ALL

 
# Members of the admin group may gain root privileges
%admin	ALL=(ALL)  ALL[/I][/INDENT][/LEFT][/CENTER]

**3.** then I make 3 scripts in /usr/bin/ and owner is : *root* and group is : *shutdown*. I set mod as 0775. 

[I]#! /bin/sh
sudo /sbin/shutdown $*[/I]          ..and..    
              [I]#! /bin/sh
sudo /sbin/halt $*[/I]                   ...and...;) ....   
       [I]#! /bin/sh
sudo /sbin/reboot $*[/I]

**4.**   *chgrp shutdown /usr/bin/reboot /usr/bin/halt /usr/bin/shutdown*

**5.**   *chmod g+x /usr/bin/reboot /usr/bin/halt /usr/bin/shutdown*

**6.**  rebot computer 

now ,if I write to the console *sudo shutdown -r now* or *sudo /sbin/shutdown -r now* I need  password....[SIZE="2"]WHY?[/SIZE] Pleas Help!!

---

### Post by Skeletonix on 2006-02-25
YEAH!! I got it!!..mistake was in sudoers file. The right form of this file is:

[I][INDENT][INDENT]# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults



Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL


# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

%shutdown ALL=(root) NOPASSWD: /sbin/reboot
%shutdown ALL=(root) NOPASSWD: /sbin/halt
%shutdown ALL=(root) NOPASSWD: /sbin/shutdown
[/indent][/left][/center][/INDENT][/INDENT][/I]
......\\:D/

---

