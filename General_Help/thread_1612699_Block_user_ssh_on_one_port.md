---
title: "Block user ssh on one port"
date: 2010-11-03
forum: General Help
---

### Post by Psycho.mario on 2010-11-03
I have an ssh server listening on two ports, one is forwarded to the outside world and the other isn't. Is it possible to disable logins from one account ONLY on from the outside world, so i can still log in with that account from the LAN? I have set up a less privileged user (no sudo) for accessing the server remotly, but i still want to be able to access a sudo user from the LAN. i know you can restrict users in the sshd_config, but i do not know how to do it for seperate ports.

Thanks

---

