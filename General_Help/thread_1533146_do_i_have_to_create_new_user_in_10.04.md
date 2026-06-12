---
title: "do i have to create new user in 10.04"
date: 2010-07-17
forum: General Help
---

### Post by yashar on 2010-07-17
hello,

no need to say i'm new to it :D

so, do i have to create a new user for security reasons in ubuntu lucid?

when i run wireshark it prompts it is dangerous to run as root so what do i have to do?

Regards...

---

### Post by sgosnell on 2010-07-17
You should have set up a user account at install.  Just don't run a program using 'sudo', and you'll be running as the logged-in user.

---

### Post by Cavsfan on 2010-07-17
Yea, when you need to do certain things you have to type your password.
Like install stuff or update but, other than that, you are good to go.

---

### Post by Cavsfan on 2010-07-17
You could open a terminal (Applications > Accessories > Terminal and type in
"man sudo" this will show you the manual (man) for the command sudo.

Basically "sudo allows a permitted user to execute a command as the superuser".
It prompts you for your password and you become the administrator for a few minutes to
do what you need to do. Then after several minutes it times out.

This is to prevent you from accidentally messing your system up.

EDIT: you press Ctrl and trouch Z to get out of man mode in terminal.

---

### Post by yashar on 2010-07-17
i'm a bit confused , during installation there is no root user, i just create one and after installation finished i log as it, so this must be a super user right? 
so if a program needs privilege then there is no need to create additional user and that super user is enough also even if i log as that superuser ubuntu will prompt me in danger zones to use sudo , so this is harmless to login as superuser, am i right?

this is also applied on server edition? in command prompt mode? no need to create additional users if i'm the only server administrator?

---

### Post by dino99 on 2010-07-17
you are right, never use an app with superuser rights for your security. You still have your login asked by gdm when you open your session after boot.

more info below

---

### Post by yashar on 2010-07-17
happy for answers, thank you.

---

### Post by Joe of loath on 2010-07-17
I may add, however, that for me wireshark only works when running as root.

---

### Post by Cavsfan on 2010-07-17
> **yashar said:**
> i'm a bit confused , during installation there is no root user, i just create one and after installation finished i log as it, so this must be a super user right? 
so if a program needs privilege then there is no need to create additional user and that super user is enough also even if i log as that superuser ubuntu will prompt me in danger zones to use sudo , so this is harmless to login as superuser, am i right?

this is also applied on server edition? in command prompt mode? no need to create additional users if i'm the only server administrator?

You never, ever want to login as superuser. It is [COLOR=Red]not[/COLOR] harmless.
Just prefix whatever command you need with "sudo" and you will be prompted for your password.

This will provide you with temporary superuser rights.

---

