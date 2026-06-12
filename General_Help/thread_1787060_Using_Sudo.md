---
title: "Using Sudo?"
date: 2011-06-20
forum: General Help
---

### Post by ithuwakaga on 2011-06-20
Hey everyone! Bit of a nooby question...

Is it possible to restrict users with 'sudo' from accessing certain directories? Rather than just exclude cd and ls from the sudo privileges, that is.


Thanks! :)

---

### Post by Monotoko on 2011-06-20
I'm not sure precisely how to do this, but I know that it is probably possible using the sudoers file. (/etc/sudoers) or even a chrooted virtual environment...

Why do you need to give these users sudo in the first place? Could you give them a limited set of commands and not allow them full sudo access?

---

### Post by bodhi.zazen on 2011-06-20
> **ithuwakaga said:**
> Hey everyone! Bit of a nooby question...

Is it possible to restrict users with 'sudo' from accessing certain directories? Rather than just exclude cd and ls from the sudo privileges, that is.


Thanks! :)

If a user can become root with sudo, or if they have physical access, then you need to use encryption to restrict access.

Encryption is not fool proof , but it is as good as it is going to get.

---

### Post by ithuwakaga on 2011-06-20
> **Monotoko said:**
> I'm not sure precisely how to do this, but I know that it is probably possible using the sudoers file. (/etc/sudoers) or even a chrooted virtual environment...

Why do you need to give these users sudo in the first place? Could you give them a limited set of commands and not allow them full sudo access?

Thanks for the advice!

These particular users do maintenance on the server we run. However, we have some directories for backups for other people, and I'd prefer if I could limit their poking around in other people's stuff.

> **bodhi.zazen said:**
> If a user can become root with sudo, or if they have physical access, then you need to use encryption to restrict access.

Encryption is not fool proof , but it is as good as it is going to get.

This is a good idea! Are there any good encryption tools you have in mind that can be easily implemented over many users' home directories?

(By the way, it's cool to see someone else from Montana participates on these forums.) :)

---

### Post by bodhi.zazen on 2011-06-20
ecryptfs - encrypt users home ;)

New user - [http://bodhizazen.net/Tutorials/Ecryptfs#New](http://bodhizazen.net/Tutorials/Ecryptfs#New)

Migrate (old) users - [http://bodhizazen.net/Tutorials/Ecryptfs#Migrate](http://bodhizazen.net/Tutorials/Ecryptfs#Migrate)

---

### Post by ithuwakaga on 2011-06-21
Thank you! That article was very helpful! :)

---

