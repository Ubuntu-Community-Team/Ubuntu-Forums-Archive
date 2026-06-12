---
title: "Executing a program as root"
date: 2010-07-28
forum: General Help
---

### Post by dyslexia on 2010-07-28
I guess this is sort of a newbie question, but I'm sure there are a lot of people who want to know how to do this so I thought I'd ask anyways.

I want to be able to execute

/usr/sbin/pm-suspend

as a regular user, without having to 'authenticate'.

Actually there are a bunch of commands I need to 'open up' so it will become necessary to type the a password only rarely.

Setting sticky bits doesn't seem to be working; and my understanding of the sudoer file syntax doesn't seem to be sufficient;

I thought perhaps

<USER>      <HOSTNAME> = NOPASSWD :  /usr/sbin/pm-suspend

would work but it does not.

---

### Post by endotherm on 2010-07-28
well, my advice is just put in your password, but if you really want to loosen up admin control, here is some documentation.
be sure to open sudoers for editing with the visudo command. you can make it use nano or whatever editor you like if you are not into vi.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by davidmohammed on 2010-07-28
I presume you've read through [this]("https://help.ubuntu.com/community/Sudoers")?

Why do you need to do this? - opening up various stuff could in theory open up various security holes etc.

---

### Post by dyslexia on 2010-07-28
From the sudoers man page it seems this guy *Bacchus* already has  unlimited access...

---

### Post by endotherm on 2010-07-28
> **dyslexia said:**
> From the sudoers man page it seems this guy *Bacchus* already has  unlimited access...
well he is the god of drunkenness and insanity

---

### Post by RabbitWho on 2010-07-28
You could enable root and just do all your business on that? 
Risky business.. 

sudo users-admin


Click on root, enable it, set password, log out, log in as root.

---

### Post by dyslexia on 2010-07-28
Tried

<username> ALL=(ALL) NOPASSWD: /usr/sbin/pm-suspend

Which seems to allow the gnome panel launcher applet (which runs /usr/sbin/pm-suspend) will do the suspend without requiring a password, but executing it from gnome-terminal as <username> still gives me "This utility may only be run by the root user".

---

### Post by endotherm on 2010-07-28
> **dyslexia said:**
> Tried

<username> ALL=(ALL) NOPASSWD: /usr/sbin/pm-suspend

Which seems to allow the gnome panel launcher applet (which runs /usr/sbin/pm-suspend) will do the suspend without requiring a password, but executing it from gnome-terminal as <username> still gives me "This utility may only be run by the root user".
it is probably an issue with the environment vars. you may not be able to run that app without impersonating root.

---

