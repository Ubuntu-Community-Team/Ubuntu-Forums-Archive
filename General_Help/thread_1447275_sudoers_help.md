---
title: "sudoers help"
date: 2010-04-05
forum: General Help
---

### Post by Abu_Dayya on 2010-04-05
Hi all,

I need help in setting up sudo on a machine to perform a specific task: 

-  I need to set /etc/sudoers to allow 'userA' to run the 'scriptA' only without the need for userA to put in his password. So userA will only run: sudo scriptA . and the script will run without requiring userA's password.

This is not Ubuntu related. So, sudo is not run and configured by default.

Thanks in advance

---

### Post by lisati on 2010-04-05
Moved from "Programming Talk" to "General Help"

---

### Post by sisco311 on 2010-04-05
Obviously you have to install sudo first, then edit the sudoers file. As root:
```
VISUAL=gedit visudo
```
replace gedit with your favorite text editor (i.e. vi or nano).

and add something like:
```
userA ALL=(root)NOPASSWD:/path/to/scriptA
```
at the end of the file.

See: [thread=1132821]HowTO: Sudoers Configuration[/thread]

EDIT: For security reasons, the script shouldn't be writable by userA.

---

### Post by Abu_Dayya on 2010-04-05
Excellent. Thanks alot. This is exactly what I wanted.

But I do have another question: 

- Do I have to specify (root)? and does that mean that with sudo, I can run a command as any other user? not specifically root? for example can I say
```
userA ALL=(userB)NOPASSWD:/path/to/scriptA
```

Thanks anyway

---

### Post by sisco311 on 2010-04-05
> **Abu_Dayya said:**
> Excellent. Thanks alot. This is exactly what I wanted.

But I do have another question: 

- Do I have to specify (root)? and does that mean that with sudo, I can run a command as any other user? not specifically root? for example can I say
```
userA ALL=(userB)NOPASSWD:/path/to/scriptA
```

Thanks anyway

Yep, that means that userA is allowed to run scriptA only as userB.

```
userA ALL=(ALL)NOPASSWD:/path/to/scriptA
```
means that userA is allowed to run scriptA as any user.

---

### Post by Abu_Dayya on 2010-04-05
Got it. Thanks

---

