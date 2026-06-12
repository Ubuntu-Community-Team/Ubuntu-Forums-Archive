---
title: "setting up squirrelmail on ubuntu 10.10 x64"
date: 2011-04-19
forum: General Help
---

### Post by stunet on 2011-04-19
hi,

I'm trying to setup squirrelmail and i keep getting this error:

> 
Error connecting to IMAP server: localhost.
111 : Connection refused


i added the port i had setup on the firewall, but still nothing.

now i installed xinetd, but i cant find much on how to set it up.

i have postfix installed for my mail server and that does work.

i hope i gave enough to help, if not, please let me know what you need to know to better help me.

thanks :)

---

### Post by bmathis on 2011-04-22
The errors pretty clear. squirrelmail is attempting to connect to an imap server on the same machine but is getting rejected. Can you give us a better run down of your setup. What IMAP server? Are SM/IMAP on the same box, SSL?, etc...

Try running squirrelmail-configure and ensure that you have the you are pointed to the right server with the right port, etc...

---

### Post by SeijiSensei on 2011-04-22
Install dovecot.

---

### Post by stunet on 2011-04-22
installing dovecot solved that, thank you :)

---

