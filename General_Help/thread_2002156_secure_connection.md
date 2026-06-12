---
title: "secure connection"
date: 2012-06-12
forum: General Help
---

### Post by Drenriza on 2012-06-12
Hey guys.

I'am going with an idea but i cant really get started.

I wanted to write an expect script (no problems their), where i want the expect script to connect to a remote server. But i don't want the script to send the password in clear text.

So my question is.
How can you make some sort of RSA key that you can use, which cannot be abused by local administrators to get access to the remote server, so they can login?

Hope it makes some sense.
Kind regards.

---

### Post by greenpeace on 2012-06-12
How will the users connect to the remote server?

if you're connecting over SSH, why not just use RSA key based SSH login... then no one has to send a password.

much more info here: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

