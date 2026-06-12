---
title: "Forgot Admin Password in Ubuntu 10.10. Help please!"
date: 2011-04-24
forum: General Help
---

### Post by SugarBlush on 2011-04-24
Hi guys!

So, I have completely forgotten the admin password. I can only log into usual account & I can't install stuff since I need the password to authenticate in order to install things. 

I Googled for help and I found these 3 websites.
[http://hacker.pk/how-to-reset-forgotten-ubuntu-1004-password](http://hacker.pk/how-to-reset-forgotten-ubuntu-1004-password)
[http://www.botskool.com/geeks/how-recover-your-ubuntu-1004-password](http://www.botskool.com/geeks/how-recover-your-ubuntu-1004-password)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

So, with the help of those tutorials, I was able able to login to the system as root after choosing "drop to root sheel prompt". So then I typed in the command "passwd [my username]" but **I wasn't prompted for a new password**. It showed a whole lot of options instead! :(

Please help! Anyone?

Thank you so much,
SugarBlush

---

### Post by withjigs on 2011-04-24
Hi there,
I am guessing by Admin you meant root password. 
By default root user is disabled in Ubuntu. To install stuff, you need to run commands preceded by 'sudo'. e.g.
```

sudo apt-get install acroread 

``` 
If you are installing using synaptic or Software center, provide your password (the user you created during installation).

Also, I tried to boot the recovery mode and drop to root shell. The 
```

passwd user

```
command works for me. What sort of options do you get ?
Let us know!

Thanks,
Jigs

---

### Post by WorMzy on 2011-04-24
There is no admin password, there is only your login password.

---

### Post by SugarBlush on 2011-04-24
Thanks for your reply!

By admin, I meant super user.

Well, as for the options given, it's something like..

```
-a, --a  reset password if expired
-b, --b report password
-c, --c blah blah blah
-d, --d blah blah blah
```

And so on. Not exactly that but something like that if I remember correctly :confused:

---

### Post by Mud.Knee.Havoc on 2011-04-24
> **SugarBlush said:**
> Thanks for your reply!

By admin, I meant super user.


It's confusing for people new to Ubuntu, but you don't need to be root.  You just use "sudo" before a command, which temporarily gives your user root privileges.  If it asks for a password, just use your own user password.

Once you get the hang of it, you'll never want to live without sudo again. :)

EDIT: Just reread... by "you don't need to be root", I mean "you don't need to be the user 'root'".  Sudo does temporarily make you "root", but you're still logged in as your normal user.

---

### Post by SugarBlush on 2011-04-24
Well, when I try to install an app from Ubuntu Software Centre, it says:

> **To install or remove software, you need to authenticate.**

An application is attempting to perform an action that requires privileges. Authentication as the super user is required to perform this action.

And then it asks me to type in the password for the super user. That's why I need to recover the password for the super user.

---

### Post by ~Plue on 2011-04-24
> **SugarBlush said:**
> 
And then it asks me to type in the password for the super user. That's why I need to recover the password for the super user.
run *gksu-properties* and set the authentication mode to sudo instead of su.
after that, your regular login password should work fine for administrative tasks

---

### Post by |{urse on 2011-04-24
[http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)

This howto is what I usually use to recover forgotten passwords.

---

### Post by SugarBlush on 2011-04-24
> **~Plue said:**
> run *gksu-properties* and set the authentication mode to sudo instead of su.
after that, your regular login password should work fine for administrative tasks
Did that & it still wants the password for super user :(

---

### Post by ~Plue on 2011-04-24
> **SugarBlush said:**
> Did that & it still wants the password for super user :(
thats odd.. 
do as the normal user
```
*gconftool-2 --recursive-unset */apps/gksu
rm -r ~/.gconf/apps/gksu
```then try again

---

### Post by naklinaam on 2011-04-25
> **SugarBlush said:**
> Did that & it still wants the password for super user :(

I am guessing you have 2 users set up on your system, and are logged in as the second user you created. If this is not the case, ignore the rest of this reply.

The first user you created while installing ubuntu is the "admin/superuser" by default. or in ubuntu speak, this user can use sudo.
The subsequent users are not sudo enabled by default.
If you have 2 users, and are logged in as the second user, you can NOT use sudo (again this is default settings only).
You need to log in as the first user you created, and ill be able to use sudo (or install applications, etc) using the password for this user.

---

### Post by SugarBlush on 2011-04-25
> **~Plue said:**
> thats odd.. 
do as the normal user
```
*gconftool-2 --recursive-unset */apps/gksu
rm -r ~/.gconf/apps/gksu
```then try again
That didn't work either :(

> **naklinaam said:**
> I am guessing you have 2 users set up on your system, and are logged in as the second user you created. If this is not the case, ignore the rest of this reply.

The first user you created while installing ubuntu is the "admin/superuser" by default. or in ubuntu speak, this user can use sudo.
The subsequent users are not sudo enabled by default.
If you have 2 users, and are logged in as the second user, you can NOT use sudo (again this is default settings only).
You need to log in as the first user you created, and ill be able to use sudo (or install applications, etc) using the password for this user.
Yes, exactly! I need to reset the password for the first user :-k

---

### Post by Elfy on 2011-04-25
Boot into recovery mode and do it from there.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by SugarBlush on 2011-04-25
> **forestpiskie said:**
> Boot into recovery mode and do it from there.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Yes I did that. Like I said in the first post, I got into recovery mode, I chose "drop to sheel prompt". I typed in the command "passwd [username]" BUT the problem is **I wasn't prompted for a new password**. Instead, it showed a whole lot of options :???:

---

### Post by Elfy on 2011-04-25
mmm - you sure you are trying to change the password using the right username.

The command's not 

passwd [username] but passwd bert

assuming bert is the user you're changing the password for

---

### Post by SugarBlush on 2011-04-25
> **forestpiskie said:**
> mmm - you sure you are trying to change the password using the right username.

The command's not 

passwd [username] but passwd bert

assuming bert is the user you're changing the password for
Yes, that's what I did. I replaced the *[username]* with my username.

---

### Post by Elfy on 2011-04-25
Have you got a camera or phone that can take a shot of the screen when you try and do it?

All looking a bit bizarre atm.

---

### Post by SugarBlush on 2011-04-26
Alright, will do that tomorrow first thing in the morning.

---

