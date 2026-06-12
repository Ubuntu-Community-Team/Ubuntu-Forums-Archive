---
title: "sudo password disappear"
date: 2012-02-15
forum: General Help
---

### Post by yaacovk on 2012-02-15
Hello.
my ubuntu ver. is 11.10
i locked my PC and can work after typing my password in logging screen.
after few weeks i changed the password in the system environment
in the user account to another password.
some how the password reflect on the sudo password and changed it to unknown password.
i tried to change by typing "sudo passwd" command in the terminal, but the system say that the password wrong.
i reboot the PC.... and i stuck in the login password screen and unable to log in to the system.
i tried to reboot the system by holding the SHIFT key and getting the recovery screen, after that i choose the root, but i don't know the command to proceed.

PLEASE HELP, what can i do to solve this problem.

Thanks in advance.
Yaacov.

---

### Post by Wayne_V on 2012-02-15
after selecting the recovery mode boot are you at a shell prompt (#) or is it prompting you for a password again?

---

### Post by yaacovk on 2012-02-15
yes, i'm in the shell prompt (#).
there is no asking for password.

---

### Post by nothingspecial on 2012-02-15
```
passwd [COLOR="Red"]username[/COLOR]
```

Where [COLOR="Red"]username[/COLOR] is your actual username.

---

### Post by yaacovk on 2012-02-15
but before that i need to pass the login screen...

---

### Post by yaacovk on 2012-02-15
Is there any option to command "passwd username" by using the live cd?

---

### Post by nothingspecial on 2012-02-15
If you are at a root recovery console then you are logged in as root. No need to log in.

---

### Post by yaacovk on 2012-02-15
in this ubuntu vertion (11.10).
when i press on SHIFT key when the system start up,
i get the recovery menu.
one of the option to choose is ..."Recovery..."
if i choose this option, i get a terminal command with my name#
what is the next command?

---

### Post by nothingspecial on 2012-02-15
Choose root recovery shell.

---

