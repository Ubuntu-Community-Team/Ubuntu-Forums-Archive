---
title: "Terminal results"
date: 2011-12-30
forum: General Help
---

### Post by UltimateCat on 2011-12-30
;)Hi!..I typed in a command.  (trying to unpack a tar.bz2)

Code: # tar vjxf r8168-8.aaa.bb.tar.bz2

The terminal returned to me :
at@username:~$ sudo # tar vjxf r8168-8.aaa.bb.tar.bz2
 usage: sudo -h | -K | -k | -L | -V
 usage: sudo -v [-AknS] [-p prompt]
 usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u
             username|#uid] [-g groupname|#gid] [command]
 usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
             username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
 usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
             username|#uid] file ...


:(Anyone have any clue what this means? This is confusing:confused:

---

### Post by claracc on 2011-12-30
You have to run in xterm:

sudo tar vjxf r8168-8.aaa.bb.tar.bz2 , without # sign, then you will be asked for your password for sudo, you type in and it is all.

---

### Post by yetiman64 on 2011-12-30
Just as an addition, when you see a # sign in a command in Linux it indicates the use of a root shell (due to a locked root account in Ubuntu it is obtained in Ubuntu by the use of sudo to elevate the privileges for an individual command). The $ sign before a command indicates the use of a users shell.

As claracc noted removal of the # and one space should fix the command for you.

---

### Post by UltimateCat on 2011-12-30
:)  To: Claracc  and  Yetiman 64

Thank you for answering me.  Been struggling with my Ubuntu: Ultimate Edition 2.7:confused:

---

