---
title: "root password"
date: 2010-08-24
forum: General Help
---

### Post by LG83 on 2010-08-24
hi,

I'm trying to get rid of the password that appears when ubuntu starts up.
In the terminal I type:

sudo passwd -l root

, then type my current passwd, then it tells me: password expiry information changed.

Why on earth then I'm asked to enter the passwd again when ubuntu restarts?

Thanks.

---

### Post by QLee on 2010-08-24
[QUOTE=LG83]...
I'm trying to get rid of the password that appears when ubuntu starts up.
In the terminal I type:

sudo passwd -l root

, then type my current passwd, then it tells me: password expiry information changed.[/QUOTE]

That command is to lock the password of root, is that what you wanted to do?



[QUOTE=LG83]Why on earth then I'm asked to enter the passwd again when ubuntu restarts?...[/QUOTE]

A user has to log on in order to use the system.

Are you trying to get one user automatically logged on, or something else?

---

### Post by scouser73 on 2010-08-24
**1** - Go to **Accessories > Passwords & Encryption Keys**
**2** - Select **Passwords: Login**
**3** - Right click on **Passwords: Login** & select change password
**4** - Enter your password, now in order to not have a password box appear at login leave blank and select **OK**

---

### Post by LG83 on 2010-08-24
I'm trying to learn how to do it through the shell,but thanks.

What I wanted is to start up ubuntu each time without entering any password...

What exactly does it mean locking?
And what do I type do disable/enable root password?

Thanks.**[FONT=Verdana][/FONT]**

---

### Post by QLee on 2010-08-24
[QUOTE=LG83]What I wanted is to start up ubuntu each time without entering any password...[/Quote]

Well, you didn't answer if what you mean by this is, are you trying to get one user automatically logged on, or something else?

This might help with that:
[https://help.ubuntu.com/community/AutoLogin](https://help.ubuntu.com/community/AutoLogin)

[QUOTE=LG83]What exactly does it mean locking?
...[/QUOTE]

Where did you find the command you tried, why did you try a command you didn't understand, that is an unsafe practice. Open a terminal and enter the command, man passwd, that will open the manual page for the command passwd which you used, you can read what it will do.

---

### Post by Calash on 2010-08-24
Part of the problem is that you are trying to make changes to the root account.  Unless you did something deliberate you are not the root account.

in a terminal type the following

```

whoami

```

This will return your account name.  Any changes you try should be done to that account.

By default the root account is disabled in Ubuntu.  You may want to double check to make sure you did not accidentally enable it in your attempts as this can open a security hole, especially if you blanked out it's password.

---

### Post by LG83 on 2010-08-24
Ok, then I mistakingly confused my user with the root...

I think the real command I needed was this:

passwd -d <my_user_name>

But the shell tells me in response  that permission is denied...how do I fix that?

---

### Post by screaminfakah on 2010-08-24
sudo needed maybe?

---

