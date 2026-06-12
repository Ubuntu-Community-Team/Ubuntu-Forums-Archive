---
title: "Is Ubuntu making a correct use of passwd's database?"
date: 2010-12-13
forum: General Help
---

### Post by HotForLinux on 2010-12-13
[SIZE=1][COLOR=Black]**$sudo pwck -r**[/COLOR][/SIZE][SIZE=1][COLOR=Black]
user lp: directory /var/spool/lpd does not exist
user news: directory /var/spool/news does not exist
user uucp: directory /var/spool/uucp does not exist
user list: directory /var/list does not exist
user irc: directory /var/run/ircd does not exist
user gnats: directory /var/lib/gnats does not exist
user nobody: directory /nonexistent does not exist
user dhcp: directory /nonexistent does not exist
user syslog: directory /home/syslog does not exist
user klog: directory /home/klog does not exist
user hplip: directory /var/run/hplip does not exist
user haldaemon: directory /home/haldaemon does not exist
user sshd: directory /var/run/sshd does not exist
user festival: directory /home/festival does not exist
user pulse: directory /var/run/pulse does not exist
user ntp: directory /home/ntp does not exist
pwck: no changes

Doesn't look nice. 
I ignore if it is really necessary but wouldn't it be enough with the [/COLOR][/SIZE][SIZE=1][COLOR=Black]/nonexistent directory?[/COLOR][/SIZE]
[SIZE=1][COLOR=Black] 
[/COLOR][/SIZE]

---

### Post by bodhi.zazen on 2010-12-13
Those are all system users / daemons and they do not typically get a home directory. 

Otherwise I did not see anything wrong with that output, is there something you are specifically concerned about ?

---

### Post by HotForLinux on 2010-12-13
> **bodhi.zazen said:**
> Those are all system users / daemons and they do not typically get a home directory. 

I know. It never seemed odd to me until I saw the output of this command. It made me think the reasons why it is done like that; if it is necessary and if wouldn't be better to establish the home folders in another way.

> **bodhi.zazen said:**
> Otherwise I did not see anything wrong with that output, is there something you are specifically concerned about ? 
Just that. It is odd to have warnings when it is perfectly ok.

---

### Post by bodhi.zazen on 2010-12-13
> **HotForLinux said:**
> I know. It never seemed odd to me until I saw the output of this command. It made me think the reasons why it is done like that; if it is necessary and if wouldn't be better to establish the home folders in another way.


Just that. It is odd to have warnings when it is perfectly ok.

These system users do not log in (run an interactive shell) so, for security reasons, do not need a home or a login shell (some people harden their systems so the shell is /bin/false).

I think the point is to read and understand why that is, then do as you wish.

---

### Post by HotForLinux on 2010-12-13
> **bodhi.zazen said:**
> These system users do not log in (run an  interactive shell) 
I know.

> **bodhi.zazen said:**
> do not need a home or a  login shell.
Yes, I know that. What I don't know is the rest.


> **bodhi.zazen said:**
> f(some people harden their systems so the shell is  /bin/false).
Ok, but I was talking about the inexistent home directories (those which the command **pwck** 'talks' about).... and so many! Why?

> **bodhi.zazen said:**
> I think the point is to read and understand why that is, then do as you wish.
Yes, exactly, that's my point.

---

### Post by bodhi.zazen on 2010-12-14
> **HotForLinux said:**
> Ok, but I was talking about the inexistent home directories (those which the command **pwck** 'talks' about).... and so many! Why?

You say you know, but then you do not know.

These users do not need a home directory for the same reason they do not need a log in shell.

There is no problem here, this is normal behavior.

It would be abnormal to have a user, bodhi, who you wanted to log in to your boxen, but that user had no shell or home directory. This second case would be a problem and this is what you are checking for.

just because pwck gives output does not mean there is a problem, you need to interpret the output.

Why not run

```
pwck -q
```

---

### Post by HotForLinux on 2010-12-19
> **bodhi.zazen said:**
> You say you know, but then you do not know.

hehe ...  :-) 
Well ... I say I know something, but then I don't know a different thing.


I say I know that _system users do not log in_ and that, therefore, _need  not a home directory nor a login shell_ (that is what I know and understand). What I do not understand is why do they need a nonexistent home directory and why do they need so many different personalized  non-existent home directories?
(By the way,.... if they are all non-existent, are they different?)
And why do they have different (non-existent, false, nologin) login shells but not so many as the non-existent login directories?)

> **bodhi.zazen said:**
> These users do not need a home directory for the same reason they do not need a log in shell.

There is no problem here, this is normal behavior. 

Yes, I know that and I didn't say there's a problem. I just said and asked: "[SIZE=1][COLOR=Black]it doesn't look nice. But I ignore if it is really necessary. Wouldn't it be enough with the [/COLOR][/SIZE][SIZE=1][COLOR=Black]*/nonexistent* directory?"[/COLOR][/SIZE]

> **bodhi.zazen said:**
> It would be abnormal to have a user, bodhi, who you wanted to log in to your boxen, but that user had no shell or home directory. This second case would be a problem and this is what you are checking for.

just because pwck gives output does not mean there is a problem, you need to interpret the output.

Why not run

```
pwck -q
```

Because it doesn't display warnings. What are these warnings for, anyway?

But what seems more strange to me is that the rbash shell doesn't let you go upwards in the directory tree, but you can go upwards executing any other shell inside rbash.

---

### Post by bodhi.zazen on 2010-12-19
Just as they do not need a log in shell they do not need a home directory.

You can edit the passwd file if you wish, no harm will come from it.

You could also file a bug report on Launchpad so the developers are aware of your concerns.

---

