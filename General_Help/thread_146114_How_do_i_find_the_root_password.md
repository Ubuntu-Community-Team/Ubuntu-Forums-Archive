---
title: "How do i find the root password?"
date: 2006-03-17
forum: General Help
---

### Post by robertall on 2006-03-17
I installed ubuntu 2 days ago, and i have never got any root access. I create the account as 'robert' and a password. I used 'su' and the same password in terminal, and it failed to give me root access. During setup, no root password was given, and i have tryed to get root with no password. Ubuntu loads fine, bootmanager (GRUB) was installed fine, nothing appears to be incorrect.

Any idea what the root password is or how i find it out?

---

### Post by SickTwist on 2006-03-17
[QUOTE=robertall]I installed ubuntu 2 days ago, and i have never got any root access. I create the account as 'robert' and a password. I used 'su' and the same password in terminal, and it failed to give me root access. During setup, no root password was given, and i have tryed to get root with no password. Ubuntu loads fine, bootmanager (GRUB) was installed fine, nothing appears to be incorrect.

Any idea what the root password is or how i find it out?[/QUOTE]

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by bjweeks on 2006-03-17
The passoword for you first account is your sudo password.

---

### Post by AndrewCaul on 2006-03-17
Use "sudo [command]" to run a command as root.
The password you need is the password you used to log in.

---

### Post by robertall on 2006-03-17
Thanks people, i have fixed the problem and i went back to standard root.

Robert.

---

