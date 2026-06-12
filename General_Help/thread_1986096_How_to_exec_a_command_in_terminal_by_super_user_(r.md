---
title: "How to exec a command in terminal by super user (root)"
date: 2012-05-24
forum: General Help
---

### Post by woxuxow on 2012-05-24
1- I just want to exec a command by root like what sudo do
2- I`m not sudoer and i don`t want to be
3- I don`t want to login with su in terminal

---

### Post by skater40165 on 2012-05-24
**/etc/sudoers Syntax**

Following is general syntax used by /etc/sudoers file:
 **USER        HOSTNAME=COMMAND**
 Where,

[LIST]
[*]** USER**:  Name of normal user
[*]** HOSTNAME**:  Where command is allowed to run. It is the hostname of the system where  this rule applies. sudo is designed so you can use one sudoers file on  all of your systems. This space allows you to set per-host rules.
[*]** COMMAND**:  A simple filename allows the user to run the command with any arguments  he/she wishes.  However, you may also specify command line arguments   (including wildcards).  Alternately, you can specify "" to indicate     that the command may only be run without command line arguments.
[/LIST]
From [http://www.cyberciti.biz/tips/allow-a-normal-user-to-run-commands-as-root.html](http://www.cyberciti.biz/tips/allow-a-normal-user-to-run-commands-as-root.html)

** **

---

### Post by woxuxow on 2012-05-24
> **skater40165 said:**
> **/etc/sudoers Syntax**

Following is general syntax used by /etc/sudoers file:
 **USER        HOSTNAME=COMMAND**
 Where,

[LIST]
[*]** USER**:  Name of normal user
[*]** HOSTNAME**:  Where command is allowed to run. It is the hostname of the system where  this rule applies. sudo is designed so you can use one sudoers file on  all of your systems. This space allows you to set per-host rules.
[*]** COMMAND**:  A simple filename allows the user to run the command with any arguments  he/she wishes.  However, you may also specify command line arguments   (including wildcards).  Alternately, you can specify "" to indicate     that the command may only be run without command line arguments.
[/LIST]
From [http://www.cyberciti.biz/tips/allow-a-normal-user-to-run-commands-as-root.html](http://www.cyberciti.biz/tips/allow-a-normal-user-to-run-commands-as-root.html)

** **

Thank you but your answer is not useful to me
sudo do a command by root user
i want to exec a command by root user but i login by a normal user that have no permission to run sudo (it is not sudoer and i don`t want to be)
when a user is sudoer the password that is asked is the password of sudoer user not root user
i`m looking for a way to exec a command like apt-get install pacjage by root but i don`t want to login as root

it`s simple 
i used to used 
sudo apt-get install package 
what can i do now with a nonsudoer to exec the apt-get without loged in as root by su

---

### Post by Erik1984 on 2012-05-24
You can probably change owner and group of apt-get to allow a user to use it without sudo. I would not do that but I imagine it must be possible.

---

### Post by wojox on 2012-05-24
If you don't want to log into root or drop to a root account that's what [COLOR="Red"]sudo[/COLOR] is for.

---

### Post by skater40165 on 2012-05-24
... Ok maybe I am missing the point yes you will HAVE to give a nonroot user the ability to run those commands by a root account but once granted the nonroot user can run ANY command specified in that file.

---

### Post by Erik1984 on 2012-05-24
btw forget my earlier comment, it makes no sense to change permissions on the executables they are executable by all users anyway. Only without temporary root rights those commands cannot do anything in 'system folders'.

---

### Post by aromo on 2012-05-24
> **MustafaJF said:**
> i want to exec a command by root user but i login by a normal user that have no permission to run sudo (it is not sudoer and i don`t want to be)
...
i`m looking for a way to exec a command like apt-get install pacjage by root but i don`t want to login as root


Basically you are asking how to hack into the root account.  That would be a security breach!

You have (in one way or another) to authorize the regular user to do stuff (even if that goes about best practices).

You cannot pretend to simply run privileged commands with a regular user without being authorized to do so.

---

### Post by evilsoup on 2012-05-24
I think he's asking if it is possible to set a separate password for sudo, rather than using the same one you log in with. Is that possible?

---

### Post by wojox on 2012-05-24
[RootSudo]("https://help.ubuntu.com/community/RootSudo") explains alot. ;)

---

### Post by NadirPoint on 2012-05-24
> **MustafaJF said:**
> 1- I just want to exec a command by root like what sudo do
2- I`m not sudoer and i don`t want to be
3- I don`t want to login with su in terminal
This is not logically possible.

---

### Post by zombifier25 on 2012-05-24
Like the others have said, it's impossible to sudo without being a sudoer. You can't ask the admin of a forum to let you modify others' posts if you're not a moderator.

If you want unprivileged users to do system stuffs, have a look at PolicyKit. It's safer that way.

---

### Post by woxuxow on 2012-05-24
I think my question was not clear

Let me make it clear
my acount (MustafaJF) was a member of sudoers group. when i tried to do(execute) a program by sudo the password was requested to do that program was MustafaJF`s password not root password
i don`t want my account to have that power to do anything by it`s password

now i ask my question in other word
is there a way to do programs (any programs not just apt-get) by sudo that ask for the root password not sudoers password

---

### Post by woxuxow on 2012-05-24
> **evilsoup said:**
> I think he's asking if it is possible to set a separate password for sudo, rather than using the same one you log in with. Is that possible?

Yeah it will be better if the separate password be the root password

---

### Post by haqking on 2012-05-24
> **MustafaJF said:**
> I think my question was not clear

Let me make it clear
my acount (MustafaJF) was a member of sudoers group. when i tried to do(execute) a program by sudo the password was requested to do that program was MustafaJF`s password not root password
i don`t want my account to have that power to do anything by it`s password

now i ask my question in other word
is there a way to do programs (any programs not just apt-get) by sudo that ask for the root password not sudoers password

you need to read the information already supplied above.

Root is root with roots password if you enabled one (which by default in Ubuntu it is not)

Sudo or superuser do/switchuser do/setuser do is not the same as root.

You can su (set user, switch user, superuser) to root if you want and if you have the root account enabled which if no other credentials are supplied defaults to root..

Other than that NO and read the information already supplied, particulary [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

---

### Post by woxuxow on 2012-05-24
> **haqking said:**
> you need to read the information already supplied above.

Root is root with roots password if you enabled one (which by default in Ubuntu it is not)

Sudo is something else, so no you cant make sudo request the root password thats nonsense.

Sudo or superuser do/switchuser do/setuser do is not the same as root.

You can su (set user, switch user, superuser) to root if you want and if you have the root account enabled which if no other credentials are supplied defaults to root..

Other than that NO and read the information already supplied, particulary [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

I know su is substitute user but when i installed ubuntu i logged in su and defined a password for it
sudo su
passwd

as i said i don`t want my account to be much powerful and i don`t want to login as su (in terminal) to do things that i want

my computer is shared with my brother and we have same account it`s too danger that my brother have a password that can do anything
please  just don`t tell me create another account there must be a way to away have a administrator account

---

### Post by haqking on 2012-05-24
> **MustafaJF said:**
> I know su is substitute user but when i installed ubuntu i logged in su and defined a password for it
sudo su
passwd

as i said i don`t want my account to be much powerful and i don`t want to login as su (in terminal) to do things that i want

my computer is shared with my brother and we have same account it`s too danger that my brother have a password that can do anything
please  just don`t tell me create another account there must be a way to away have a administrator account

So you dont want to use su or sudo but want to perform a su or sudo action ?

As i said....NO, thats why su and sudo exists.

I would like to be able to burn a blu-ray movie image to a floppy disk but i cant....LOL

---

### Post by Tamalin on 2012-05-24
Perhaps if you really don't want to log into an administrative account graphically, you could try switching from a normal user to an administrator to root:
```

regular-user@computer $ su admin-user
admin-user@computer $ sudo somecommand

```

This is, of course, assuming that you have access to or can create some administrative account that can use sudo.

---

### Post by haqking on 2012-05-24
> **Tamalin said:**
> Perhaps if you really don't want to log into an administrative account graphically, you could try switching from a normal user to an administrator to root:
```

regular-user@computer $ su admin-user
admin-user@computer $ sudo somecommand

```This is, of course, assuming that you have access to or can create some administrative account that can use sudo.


which is what you are supposed to do, but as the OP keeps saying they dont want to use su or sudo, or in other words they dont want to do things the way they are supposed to and designed to do

---

### Post by Tamalin on 2012-05-24
I believe that root is locked by default.  If you want a separate password for root, you could try 'sudo passwd root' to set a new root password, but you have to use sudo to do it...

---

### Post by grahammechanical on 2012-05-24
I am very confused about what the problem is.

If you set automatic login then your brother can use the computer without needing to use a password to log in but he cannot do any administrative tasks without knowing the password that you set when you installed Ubuntu.

Ubuntu is different from other Linux distributions. When we install Ubuntu it creates one user account. That user has administrative privileges but only when he needs administrative privileges. The rest of the time he is working as standard user.

So, if a user tries to make certain changes to the operating system he is asked to authenticate. Without the administrator password the action cannot be performed.

If a person tries to bypass this way of doing things by using a terminal he will find that certain commands will not run without putting the word sudo in front of the command and then he will be asked to put in the administrator password.

So, if your brother does not know your password then he will not be able to do what you as administrator can do.

If you want to limit the programs that your brother can run or in some other way restrict your brother's use of the computer, then you may need to create a separate account for your brother and set the limitations there.

Regards.

---

### Post by haqking on 2012-05-24
> **Tamalin said:**
> I believe that root is locked by default.  If you want a separate password for root, you could try 'sudo passwd root' to set a new root password, but you have to use sudo to do it...

LOL

are you reading any of this thread ?

Thats already been said and the user already said he set a root password.

---

### Post by Tamalin on 2012-05-24
> **haqking said:**
> LOL

are you reading any of this thread ?

Thats already been said and the user already said he set a root password.

This is a very confusing thread :)...

[QUOTE=grahammechanical]
I am very confused about what the problem is.
[/QUOTE]
+1 on that...

---

### Post by WorMzy on 2012-05-24
> **haqking said:**
> you cant make sudo request the root password thats nonsense.

It certainly isn't. Does Ubuntu's version of sudo not have the rootpw, runaspw or targetpw Defaults options?

```
man sudoers
```

```

       rootpw          If set, sudo will prompt for the root password instead
                       of the password of the invoking user.  This flag is off
                       by default.

       runaspw         If set, sudo will prompt for the password of the user
                       defined by the runas_default option (defaults to root)
                       instead of the password of the invoking user.  This
                       flag is off by default.

       targetpw        If set, sudo will prompt for the password of the user
                       specified by the -u option (defaults to root) instead
                       of the password of the invoking user.  In addition, the
                       timestamp file name will include the target user's
                       name.  Note that this flag precludes the use of a uid
                       not listed in the passwd database as an argument to the
                       -u option.  This flag is off by default.

```

May be of use to the OP if they are present. Simply use

```
visudo
``` as root (via su, sudo, or pkexec), and add one of those options to the end of the Defaults declaration. e.g.

```
Defaults timestamp_timeout=0,editor=/usr/bin/vim:/usr/bin/vi:/usr/bin/nano,targetpw
```

---

### Post by haqking on 2012-05-24
> **WorMzy said:**
> It certainly isn't. Does Ubuntu's version of sudo not have the rootpw, runaspw or targetpw Defaults options?

```
man sudoers
``````

       rootpw          If set, sudo will prompt for the root password instead
                       of the password of the invoking user.  This flag is off
                       by default.

       runaspw         If set, sudo will prompt for the password of the user
                       defined by the runas_default option (defaults to root)
                       instead of the password of the invoking user.  This
                       flag is off by default.

       targetpw        If set, sudo will prompt for the password of the user
                       specified by the -u option (defaults to root) instead
                       of the password of the invoking user.  In addition, the
                       timestamp file name will include the target user's
                       name.  Note that this flag precludes the use of a uid
                       not listed in the passwd database as an argument to the
                       -u option.  This flag is off by default.

```May be of use to the OP if they are present. Simply use

```
visudo
``` as root (via su, sudo, or pkexec), and add one of those options to the end of the Defaults declaration. e.g.

```
Defaults timestamp_timeout=0,editor=/usr/bin/vim:/usr/bin/vi:/usr/bin/nano,targetpw
```

ahh interesting.

I have only ever used sudo in Ubuntu which i dont use, i didnt know it had those options, i stand corrected on that so thanks for the information.

as for the rest, the OP said they didnt want to use sudo or su, if rootpw is set they still need to use sudo

Peace

---

### Post by woxuxow on 2012-05-24
> **haqking said:**
> LOL

are you reading any of this thread ?

Thats already been said and the user already said he set a root password.

I read them all carefully

---

### Post by woxuxow on 2012-05-24
> **WorMzy said:**
> It certainly isn't. Does Ubuntu's version of sudo not have the rootpw, runaspw or targetpw Defaults options?

```
man sudoers
```

```

       rootpw          If set, sudo will prompt for the root password instead
                       of the password of the invoking user.  This flag is off
                       by default.

       runaspw         If set, sudo will prompt for the password of the user
                       defined by the runas_default option (defaults to root)
                       instead of the password of the invoking user.  This
                       flag is off by default.

       targetpw        If set, sudo will prompt for the password of the user
                       specified by the -u option (defaults to root) instead
                       of the password of the invoking user.  In addition, the
                       timestamp file name will include the target user's
                       name.  Note that this flag precludes the use of a uid
                       not listed in the passwd database as an argument to the
                       -u option.  This flag is off by default.

```

May be of use to the OP if they are present. Simply use

```
visudo
``` as root (via su, sudo, or pkexec), and add one of those options to the end of the Defaults declaration. e.g.

```
Defaults timestamp_timeout=0,editor=/usr/bin/vim:/usr/bin/vi:/usr/bin/nano,targetpw
```

Thanks aaaaaaaaaaaaaaaaaaaaaaaaaaaaa lot
that is what i was looking for
and thanks all you commented here to help me

---

### Post by woxuxow on 2012-05-24
What a great day 
thanks WorMzy

the line you mentioned was not exist so i added it to visudo and now i enjoy myself

Defaults timestamp_timeout=0,editor=/usr/bin/nano,rootpw

---

### Post by WorMzy on 2012-05-24
No problem, glad to help.

Just to make sure though: you don't need "timestamp_timeout=0" to use "rootpw". Setting that option to 0 makes sudo ask for a password *every* time you run something with it. If you're happy with that (I prefer it over the default behaviour -- only asking for a password once every five minutes) then no worries. If it starts to annoy you, remove it from the list of Defaults using visudo as root again.

---

### Post by woxuxow on 2012-05-25
> **WorMzy said:**
> No problem, glad to help.

Just to make sure though: you don't need "timestamp_timeout=0" to use "rootpw". Setting that option to 0 makes sudo ask for a password *every* time you run something with it. If you're happy with that (I prefer it over the default behaviour -- only asking for a password once every five minutes) then no worries. If it starts to annoy you, remove it from the list of Defaults using visudo as root again.

no it`s just great 
timestamp_timeout=0 is what i want ask about root password everytime
thank you

---

