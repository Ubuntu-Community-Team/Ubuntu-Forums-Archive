---
title: "how to change password? ... i'm confused."
date: 2010-03-15
forum: General Help
---

### Post by m4lte on 2010-03-15
Hey hey,

when I installed ubuntu, I was asked to enter a password for my account. That's the only password I use and I have to enter it for log in and changing system settings.

I would like to change this password. Now, do I have to change the password of my user account or do I have to change the root password?
I would like to have just one password that I can use to log in with my account and to gain access to all system settings etc...

I had a look at some websites but that got me only more confused ;)

Thanks for help!

---

### Post by Serpher on 2010-03-15
The password you enter in at the beginning isn't the root password. Sudo asks for your user-password, not your root, to preform an action with root privileges. Anyway to change your passwords go into your terminal (Applications --> Accessories --> Terminal), and type in:


User:
```
passwd
```

Root:
```
sudo passwd
```


You will then be prompted to type in your a new password to use.

---

### Post by bodhi.zazen on 2010-03-15
> **m4lte said:**
> Hey hey,

when I installed ubuntu, I was asked to enter a password for my account. That's the only password I use and I have to enter it for log in and changing system settings.

I would like to change this password. Now, do I have to change the password of my user account or do I have to change the root password?
I would like to have just one password that I can use to log in with my account and to gain access to all system settings etc...

I had a look at some websites but that got me only more confused ;)

Thanks for help!

This is how Ubuntu is set up, one password for everything and you do not need to change anything.

Just use sudo / gksu for graphical apps.

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by m4lte on 2010-03-15
Thanks!
 I didn't know that the root account is disabled on default. Now I understand how things work

---

