---
title: "To root and back"
date: 2010-07-16
forum: General Help
---

### Post by puma1 on 2010-07-16
hey guys, i am switching to root by typing in sudo su... my question is how to reverse thing command so i can go back to my reg user?

thanks

---

### Post by jwbrase on 2010-07-16
```
exit
```

sudo su opens a root shell under your currently running shell. When you type exit, it goes back to the shell that you invoked sudo su from.

---

### Post by prodigy_ on 2010-07-16
If you want to abandon root shell you can use **exit** or **logout**. Otherwise it's ```
su <user_name>
```

---

### Post by puma1 on 2010-07-16
you guys rock, thanks

---

### Post by capscrew on 2010-07-16
> **prodigy_ said:**
> If you want to abandon root shell you can use **exit** or **logout**. Otherwise it's ```
su <user_name>
```

And the difference is: exit closes the sub-shell -- so does logout -- but su <user name> keeps that shell in use.  The next question is: What env variables are you using in this still open shell?

---

### Post by puma1 on 2010-07-16
uh i duno. so even though i go back to my username su user, i am still in admin type mode?  even though i switched back from root?

---

### Post by sidzen on 2010-07-16
> **puma1 said:**
> hey guys, i am switching to root by typing in sudo su... my question is how to reverse thing command so i can go back to my reg user?

thanks
Why not use <Ctrl-Alt-F2> to get to console, then
<Ctrl-Alt-F7> to get back to GUI?

---

### Post by sisco311 on 2010-07-16
> **puma1 said:**
> hey guys, i am switching to root by typing in sudo su... my question is how to reverse thing command so i can go back to my reg user?

thanks

To log out type:
```
exit
```
or press Ctrl+d

But, you don't need two [setuid]("http://en.wikipedia.org/wiki/Setuid") root commands to switch to root. 

To start a root shell use:
```
sudo -i
```

Of course, you can use sudo su, sudo bash (or even *pkexec sudo su - -c "ping 127.0.0.1"* :evil: ) but you should know exactly what you are doing. ;)

For a brief overview of some of the differences between su, su -, and sudo -{i,s} see [unutbu's post]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4")

[uhelp]community/RootSudo[/uhelp]

---

### Post by capscrew on 2010-07-16
> **puma1 said:**
> uh i duno. so even though i go back to my username su user, i am still in admin type mode?  even though i switched back from root?

Well, these are the things that will trip us up later on.

The first su was *sudo su* and I believe the only thing it changes is the the use, not the env.  So subsequent changes will do the same thing.

As sisco311 points out *sudo -i *changes both the user and environment.  If you su <normal user> you will leave the environment.

Use sudo and su with caution.

---

