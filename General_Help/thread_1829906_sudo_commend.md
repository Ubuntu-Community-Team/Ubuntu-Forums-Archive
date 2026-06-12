---
title: "sudo commend?"
date: 2011-08-20
forum: General Help
---

### Post by pua06 on 2011-08-20
salmo allikm warhmat allah wabrakato

i want to write bash acriprt for sudo commend like

sudo su
 
when run script in terminal he asks me about password i know password and want to add it in script but i don't know how
 i tried to do

sudo su<<EOF
 password 
EOF

but  he still asking me
any suggestion ?
or any way to remove password

thanks

---

### Post by pua06 on 2011-08-21
any suggestion?

---

### Post by dino99 on 2011-08-21
[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)
[http://linuxconfig.org/Bash_scripting_Tutorial](http://linuxconfig.org/Bash_scripting_Tutorial)

---

### Post by 3rdalbum on 2011-08-21
You want 'sudo -S', and then sudo will read the password from stdin like you've been trying.

The manpage for sudo explains the -S option, take a look.

---

### Post by WorMzy on 2011-08-21
Writing down your password in plain text is not a very clever idea.

Rather than using "sudo blahblahblah" in a script, just write the script as though it's being called by the root user, then call the *script* with sudo instead.

---

