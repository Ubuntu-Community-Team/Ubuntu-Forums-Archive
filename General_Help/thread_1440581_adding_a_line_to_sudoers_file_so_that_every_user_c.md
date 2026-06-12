---
title: "adding a line to sudoers file so that every user can run a particular program as root"
date: 2010-03-27
forum: General Help
---

### Post by perham on 2010-03-27
is it possible to do so? I mean, I want every user to be able to run '/bin/x' for example, as root without entering a password. I know the security risks, but I'm trying this in a risk-free environment which security does not matter very much.

---

### Post by nothingspecial on 2010-03-27
Might be a better idea to change the permission of /usr/bin/X

But add the users to a group that can run X without the password rather than just give anyone access to it. If you see what I mean.

Just initial thoughts, never considered this before.

---

### Post by perham on 2010-03-27
> **nothingspecial said:**
> Might be a better idea to change the permission of /usr/bin/X

But add the users to a group that can run X without the password rather than just give anyone access to it. If you see what I mean.

Just initial thoughts, never considered this before.

good ideas. I will look into them too.

seems that the simplest way would be to add this line to sudoers:

ALL ALL=NOPASSWD: /bin/x

but this may not be appropriate because as you mentioned, it's not a good idea to allow everyone to access a program as root.

---

