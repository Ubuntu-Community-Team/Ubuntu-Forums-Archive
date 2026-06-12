---
title: "Remove password for altering system"
date: 2010-11-13
forum: General Help
---

### Post by erikvduyn on 2010-11-13
Having recently installed Ubuntu 10.10, I'm currently looking around for different programs. However, it's already getting on my nerves that I have to type my password every time I want to install something. Where and how do I disable this? I already set myself as admin in the user settings but that doesn't seem to work.

This goes for things like changing system settings too, it's really annoying.

---

### Post by nothingspecial on 2010-11-13
What your asking for is not a good idea.

Infact, if you read the forum CoC I`m not allowed to tell you.

To paraphrase someone else.

If you have to ask, you shouldn`t do it.
If you are able to do it, you wouldn`t have to ask.
If you don`t have to ask, you wouldn`t do it.

No offence meant :)

---

### Post by amauk on 2010-11-13
```
sudo -i
```will give you a root shell if you want to remain root for extended periods of time

---

### Post by erikvduyn on 2010-11-13
> **nothingspecial said:**
> What your asking for is not a good idea.

Infact, if you read the forum CoC I`m not allowed to tell you.


Oh? Must've missed that then.

Never mind then.

---

### Post by sisco311 on 2010-11-13
Before you proceed make sure you understand the security implications.
 
Here are some useful links:
[thread=510812]Ubuntu Security[/thread]
[thread=1486138]Forum policy on log-in-as-root tutorials[/thread]
[uhelp]community/RootSudo[/uhelp]
[thread=1132821]HowTO: Sudoers Configuration[/thread]
[http://hal.freedesktop.org/docs/polkit/](http://hal.freedesktop.org/docs/polkit/)
[uhelp]Repositories/Ubuntu[/uhelp]

Now, in order to disable the password for installing software via Software Center, you have to create a polkit local authority file:
```
gksu gedit /var/lib/polkit-1/localauthority/50-local.d/software-center.pkla
```
with the following content:
```
[Software Center]
Identity=unix-group:admin
Action=org.debian.apt.install*
ResultActive=yes
```

---

