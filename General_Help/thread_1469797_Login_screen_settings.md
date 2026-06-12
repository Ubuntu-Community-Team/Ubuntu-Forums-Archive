---
title: "Login screen settings"
date: 2010-05-02
forum: General Help
---

### Post by ankit singh on 2010-05-02
i installed lucid yesterday and whenever i run gdmsetup i encounter foll problems



ankit@ankit-desktop:~$ sudo gdmsetup
[sudo] password for ankit: 

** (gdmsetup:2101): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): Key not found

** (gdmsetup:2101): WARNING **: Error calling GetValue('daemon/TimedLoginDelay'): Key not found
** (gdmsetup:2101): DEBUG: init delay=30
** (gdmsetup:2101): DEBUG: "/usr/share/xsessions/une-efl-guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:2101): DEBUG: "/usr/share/xsessions/guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:2101): DEBUG: "/usr/share/xsessions/une-guest-restricted.desktop" is hidden or contains non-executable TryExec program


** (gdmsetup:2101): WARNING **: Error calling GetValue('daemon/DefaultSession'): Key not found
** (gdmsetup:2101): DEBUG: Init default session found:'(null)'
** (gdmsetup:2101): DEBUG: Failed to identify the current session: Unable to lookup session information for process '2101'

** (gdmsetup:2101): WARNING **: Unable to find users: no seat-id found
** (gdmsetup:2101): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:2101): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:2101): DEBUG: adding monitor for '/home/ankit/.face'
** (gdmsetup:2101): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:2101): DEBUG: Found 1 sessions for user ankit
** (gdmsetup:2101): DEBUG: GdmUserManager: not adding session on other seat: /org/freedesktop/ConsoleKit/Session2


as u can see i cannot edit any login settings.
Pls reply

---

### Post by rnerwein on 2010-05-02
hi
looks like the default - same on my box :-)
ciao

---

