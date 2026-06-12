---
title: "Can I create accounts from the terminal?"
date: 2010-03-17
forum: General Help
---

### Post by adamkleiner on 2010-03-17
I was told to create accounts from the GUI through K > Applications > System > User Manager or something like that, but the "user manager" icon is missing. Would it be possible to make new accounts through the terminal (bash, Konsole, whatever you want to call it)?
 
If it is possible, please provide an explanation of how. Thanks!

---

### Post by srs5694 on 2010-03-18
Yes. The adduser utility does this. Type "man adduser" for all the details, but in most cases just typing the command name followed by the username (such as "adduser linus" to add a user called linus) will do the job. This program is actually a script that prompts for various pieces of information. It then creates the account, including a home directory for the user.

A lower-level alternative is useradd, which creates the account with default values. It doesn't set the password or even create a home directory, so you'd need to do these things manually.

---

### Post by Chame_Wizard on 2010-03-18
System Settings>Advance tab menu>User Management(in the System Section).Now you can modify or add an account,change groups etc.

Konsole is the the name of the terminal emulator for KDE.

Bash is one of the may Unices shells.

:guitar:

---

### Post by adamkleiner on 2010-03-18
> **srs5694 said:**
> Yes. The adduser utility does this. Type "man adduser" for all the details, but in most cases just typing the command name followed by the username (such as "adduser linus" to add a user called linus) will do the job. This program is actually a script that prompts for various pieces of information. It then creates the account, including a home directory for the user.

A lower-level alternative is useradd, which creates the account with default values. It doesn't set the password or even create a home directory, so you'd need to do these things manually.
Thanks!

---

### Post by adamkleiner on 2010-03-18
> **Chame_Wizard said:**
> System Settings>Advance tab menu>User Management(in the System Section).Now you can modify or add an account,change groups etc.

Konsole is the the name of the terminal emulator for KDE.

Bash is one of the may Unices shells.

:guitar:
You didn't answer my question. I wanted to know *how* to do it in the terminal, not *what* the terminal is and how to do it in the GUI.

---

