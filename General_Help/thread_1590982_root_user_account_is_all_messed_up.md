---
title: "root user account is all messed up"
date: 2010-10-08
forum: General Help
---

### Post by Meph1st0 on 2010-10-08
A while back I don't know what I did but I messed up my root user account and now the password that I think is supposed to be for the account doesn't work anymore.

In an attempt to fix it I rebooted and went into recovery mode and then edited the sudoers file.  This appears to have been good enough to be me by but now I'm running into problems installing or changing configurations in gnome.  For example, I just installed Asterisk via the terminal the other day and had no problems because I could use sudo.  But just now I tried installing Gastman via the Ubuntu Software Center and of course it asked for the root password.  I entered my usual root password when I use sudo and it doesn't work.

I then went to the terminal and entered sudo apt-get install gastman and it worked fine becuase I used my sudo password for my account.  So it seems I can do things just fine via the terminal but when in gnome it doesn't work.  I went into the Users and Groups section in Gnome to attempt to set or change the root password but of course I have to unlock the application which requires the root password.  Is there any way I can change the root password or fix it without having to reinstall Ubuntu?

---

### Post by lisati on 2010-10-08
The "root" account is disabled by default in Ubuntu. Please take a look at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Meph1st0 on 2010-10-08
Okay, that's fine.  I don't have to enable the root account.  Can you then tell me why it works when I use sudo in a terminal but when I attempt to make a configuration change (or install an application) in gnome and it asks me for the root password it doesn't work?  I guess this is the main problem I'm having.  I can't use any of the forms in Gnome that require it to be unlocked or I can't use the Ubuntu Software Center because it asks for the password anytime I make a change.  If I do it at the terminal then it works fine.

---

### Post by sandyd on 2010-10-08
> **Meph1st0 said:**
> Okay, that's fine.  I don't have to enable the root account.  Can you then tell me why it works when I use sudo in a terminal but when I attempt to make a configuration change (or install an application) in gnome and it asks me for the root password it doesn't work?  I guess this is the main problem I'm having.  I can't use any of the forms in Gnome that require it to be unlocked or I can't use the Ubuntu Software Center because it asks for the password anytime I make a change.  If I do it at the terminal then it works fine.
it should not be asking you for the **root **password. It should be asking for your acct password.

In the future, change root password by
```

sudo passwd root
```
(and no, other curious users, please don't run this)

---

### Post by Meph1st0 on 2010-10-08
Well that appears to have worked.  I changed the password using the code you provided.  I've also attached a picture of it asking for the root password and not my account password just so you can see.  It's weird that it's asking for the root password and not my own password though.

A little sidebar here: I checked out your website.  It looks very nice.  Well done.

---

