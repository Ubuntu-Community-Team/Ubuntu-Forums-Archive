---
title: "Remote desktop over the Internet (UFW)"
date: 2010-04-13
forum: General Help
---

### Post by SpinningAround on 2010-04-13
I would like to set up a remote desktop connection between two computers over the Internet. I already tested remote desktop within a local network¹ but it's far from secure enough this time. I will try to follow this guide [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC) (ssh portforward and internet) if there is something I should know beside that please tell me. This still leaves ufw and how it should be configured.

Let's say I have this setup, server computer has ip 12.341.245.124 and the client has 78.12.543.234 how should ufw be configured to be secure?

¹ This remote desktop wont be connected to a local network

---

### Post by J V on 2010-04-13
SSH and a set of large GPG keys should protect you from anything, never used ssh though so thats something you will have to fix yourself...

---

