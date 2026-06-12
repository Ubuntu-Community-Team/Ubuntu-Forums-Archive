---
title: "Project: Storage And Utility Lock (SAUL)"
date: 2009-12-29
forum: General Help
---

### Post by Jestersage on 2009-12-29
While I am extremely happy with the way Ubuntu handle root-related stuff, many of my friends complained about that. So they asked me to make something that allows them to:
a) Do not need to memorize passwords and do all the stuff taht requires password
b) Can login without password (obviously during 9.10)
c) Can go back to using password if they want to.
d) cna still use root stuff while login as their own account — they do not want to login as root either.

After warning the consequences of using root for their entire session, I decided to see it as a personal challenge to do it. Due to the fact that I am actually giving them somethign that is actually bad (but they still wanted it), I decided to call this project SAUL.

While the rudamentary of this is simple, the question, however, is: am i reinventing the wheel? I am certain that there are many Ubuntu users out there who want to do root stuff, no need to remember password, no need to login with password, all on their own account, and I am surprise no one tried to do somethign like this.

---

### Post by Ahadiel on 2009-12-29
While I'm not entirely sure what the goal of SAUL is....

Most GNOME applications use the gnome keyring for storing sensitive data, there is already an option to have yourself logged in automatically, and sudo allows you to do things as root with your own password.

Also, you can edit your sudoers file to allow certain programs to be run as root without you inputting your password.

---

### Post by Jestersage on 2009-12-29
> **Ahadiel said:**
> 
Most GNOME applications use the gnome keyring for storing sensitive data, there is already an option to have yourself logged in automatically, and sudo allows you to do things as root with your own password.


The option is to allow yourself to be login the first time, and only for one account. It does not allow, for example, a user (of a multi user desktop) to just click on his profile to login. Also, there's no real "Guest Account", just guest session enabled by one of the user.

> **Ahadiel said:**
> 
Also, you can edit your sudoers file to allow certain programs to be run as root without you inputting your password.

I will investigate into it.

The point of SAUL, ultimately and bluntly, is to "let people have their Windows cake in Ubuntu, even if it means a huge security hole, since they don't care anyway but just want everything spoon fed but still want to use Ubuntu." I am talking about users who still leave their doors open (Remember Michael Moore's Bowling For Columbine, where the Canadians let their door unlock? That still happen quite a bit up here in the North), and want their accounts to be open.

In a way, if you understand the origin of the name of this project, you will understand the purpose of this project.

P.S. And of course it will be a GUI based.

---

