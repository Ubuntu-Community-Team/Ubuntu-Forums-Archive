---
title: "How to run scripts?"
date: 2011-09-22
forum: General Help
---

### Post by Shiryu on 2011-09-22
Hello.
I want to configure two scripts.

First, I want to configure to run a bash script whenever the computer be turned on, for all users.

Second, I want to configure a script that is written by the user, and it is run whenever the user log on to the computer.

The .bashrc does not solve the problem, because it is only run when the user open the terminal.

How to configure it?

Thanks.

---

### Post by NERDMAN! on 2011-09-22
unfortunately the issue with what your trying to do, in my experience it wont run any scripts until a user actually logs in, ive never been able to have a script run for all users, but then by the same token i'm the only user on this pc so ive never needed to.

i have seen a program in the softare center called scheduled tasks, but i'm not so sure its what you want, it does however give the option of executing a terminal command which can in turn execute a script.

---

### Post by papibe on 2011-09-22
For the login script, you can use 'Startup Applications'.

For the global, it depends. What kind of task are you trying to automate?

Regards.

---

### Post by Paddy Landau on 2011-09-22
*Your second question:*

A user writes his script. To run it when he logs in, he simply adds it to his startup applications. In 10.04 you'll find it in the menu System > Preferences > Startup Applications.

*Your first question:*

To run a script when the computer starts is complex.
**EDIT: Thanks to the following posters showing that it's actually easy!**

However, you can quite easily set a script to run whenever a user logs in, whoever the user is. Test the script *thoroughly*, then add it to the end of the file [FONT=Fixedsys]/etc/profile[/FONT]. (But if the script starts a GUI program, it gets a bit more complicated.)

---

### Post by dave01945 on 2011-09-22
for the first you could try to put it in 

```
/etc/rc.local
```

that will be one of the last things run during boot and for the second you could try

```
/home/user/.profile
```

that will run when the user logs in

---

### Post by Shiryu on 2011-09-22
Thanks a lot.
It works.

When the computer starts:
/etc/rc.local

When any user logs in:
/etc/profile

When a known user logs in (written by the user):
/home/user/.profile

---

### Post by Porcini M. on 2011-09-22
> **Shiryu said:**
> 
When the computer starts:
/etc/rc.local


Note that this will be run as root.

---

### Post by Habitual on 2011-09-23
> **Shiryu said:**
> Hello.
I want to configure two scripts.

First, I want to configure to run a bash script whenever the computer be turned on, for all users.

/etc/rc.local

---

