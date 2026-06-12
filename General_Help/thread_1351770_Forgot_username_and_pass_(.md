---
title: "Forgot username and pass :("
date: 2009-12-10
forum: General Help
---

### Post by Gizenshya on 2009-12-10
Like the title says, I forgot the username and pass to one of my comps.  It is a dual-boot with Vista, for what it's worth.

It is a base isntall, with only one program (very hard-to-find driver) installed.  So it wouldn't be that big of a deal to reinstall if it would be easier.

---

### Post by jbrown96 on 2009-12-10
When the grub menu loads, choose the second Ubuntu option, which should be "recovery mode". Once that boots choose "root shell" and run the following. 

```
cat /etc/passwd | grep 1000
``` this should show you a line with your username 

you can change the password with ```
passwd user
``` change password to match what you just found. When you type the new password, you won't see anything, but it's working

---

