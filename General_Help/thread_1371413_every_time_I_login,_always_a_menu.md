---
title: "every time I login, always a menu"
date: 2010-01-03
forum: General Help
---

### Post by davidtuti on 2010-01-03
Hi,

Imagine that I have only the password of an user. Every time that I log in the host with this user it shows me a menu, but I would like that it shows me the prompt. If I try to do Ctr+C, I logout the session.

Any help?
Many thanks and sorry for my english!

---

### Post by Iowan on 2010-01-03
You want to login to a command line prompt?

---

### Post by davidtuti on 2010-01-03
> **Iowan said:**
> You want to login to a command line prompt?

Yes.
I login in this server by telnet from other linux or by ssh, but it shows me the menu and I cant obtain the prompt

---

### Post by sebastianabate on 2010-01-03
> **davidtuti said:**
> Yes.
I login in this server by telnet from other linux or by ssh, but it shows me the menu and I cant obtain the prompt

What menu shows you?

Is this your server? do you have root/sudo access?

If the server is managed by another person, you must ask him/her to do that (enable shell access to your user)

---

### Post by davidtuti on 2010-01-03
> **sebastianabate said:**
> What menu shows you?

Is this your server? do you have root/sudo access?

If the server is managed by another person, you must ask him/her to do that (enable shell access to your user)

Thanks, I think that is a menu that is in the profile.

---

### Post by sebastianabate on 2010-01-03
> **davidtuti said:**
> Thanks, I think that is a menu that is in the profile.

If you are not the administrator (or you are the administrator, but dont have another user to login as), and there is no option in the menu to disable it, you have no options.

The only thing that you can do is ask an administrator to disable it, or boot the remote system in single mode and modify your profile.

---

