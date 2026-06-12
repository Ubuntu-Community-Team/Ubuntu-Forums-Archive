---
title: "ssh rsa key authentication cache"
date: 2010-09-18
forum: General Help
---

### Post by garvint on 2010-09-18
I have ubuntu 10.04 set-up with correctly with SSH and an RSA key authentication.

However after restarting the OS on the client side and connecting to the server, on the first login it asks me for the password. Once that is done then it doesn't task for that password any more, or re-logging in, until the next restart.

SSH Key Agent is in start-up programs (gnome-keyring-daemon --start --components=ssh)

How can this be set-up so I don't have to enter the password on each restart? I thought the point of private/public keys was to store the password?

---

