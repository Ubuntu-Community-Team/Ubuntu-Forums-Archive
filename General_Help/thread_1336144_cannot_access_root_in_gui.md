---
title: "cannot access root in gui"
date: 2009-11-24
forum: General Help
---

### Post by lex1 on 2009-11-24
If i use a terminal to access root thats no problem but when i try to access
say the package manager i am asked for my password and then I get

"failed to run/user/sbin/snyaptic as user root

the underlying authorization mechanism (sudo) does not allow you 
to run this program. contact system administrator

thanks

lex1

---

### Post by dvlchd3 on 2009-11-24
[http://ubuntuforums.org/showthread.php?t=1198166](http://ubuntuforums.org/showthread.php?t=1198166)

Hope this helps.

---

### Post by lex1 on 2009-11-24
my visudo file  now loks like this does this let all users need no password?


  GNU nano 2.0.7                                 File: /etc/sudoers.tmp                                                                        

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=NOPASSWD: ALL

---

