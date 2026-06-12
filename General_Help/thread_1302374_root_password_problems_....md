---
title: "root password problems ..."
date: 2009-10-27
forum: General Help
---

### Post by samuraitor on 2009-10-27
hi everyone,

I just have installed root system for karmic koala however when I go to terminal and type "su" and type in my correct password it says unauthentic.

I need this to sign a java  applet to use wireless at my university. 

I have changed my password more than 3 times and it is still complaining about unauthentic.

What to do?

---

### Post by dominiquec on 2009-10-27
Use sudo instead of su.  By default, Ubuntu disables the su command.

---

### Post by mcduck on 2009-10-27
Actually Ubuntu doesn't disable "su" command in any way. What Ubuntu does is that it disables the root user.

Since root has no password, you can't use "su" to switch to root, since "su" asks for target user's password. Which doesn't exist in this case.

"sudo" uses your own password, so you can use that for admin tasks. And if you need a root shell, use "sudo -i".

You can read more about details and reasons behind this here: 
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by lisati on 2009-10-27
This might be of interest: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MelDJ on 2009-10-27
> **samuraitor said:**
> hi everyone,

I have changed my password more than 3 times and it is still complaining about unauthentic.

What to do?

type 'sudo' followed by your command. then type your password. if you type your password in terminal, it will be invisible

---

### Post by dominiquec on 2009-10-27
D'oh! What was I thinking? Thanks for pointing it out.

---

