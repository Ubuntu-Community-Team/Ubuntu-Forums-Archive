---
title: "Keeping Elevated Privileges"
date: 2011-03-28
forum: General Help
---

### Post by _joecrawford on 2011-03-28
Ok, I get really annoyed when I am in command line or doing a big purge of software and I have to enter my root password every minute or so. 

How to change the length my elevated privileges are up?

---

### Post by blueridgedog on 2011-03-28
sudo -i 

will give you a shell with elevated privileges until you exit.

Be careful...

---

### Post by _joecrawford on 2011-03-29
This is helpful, but I was also interested in keeping privileges when using software center.

---

### Post by Rubi1200 on 2011-03-29
You can change the default timeout, but be very careful!
[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

Personally, I would advise against it. How often do you *really* need to have a default longer than 15 minutes?

---

### Post by earthmeLon on 2011-03-29
You might also want to look into modifying your sudo configuration.

It is possible to allow a user, or group of users to gain super-user privileges to a specific set or all commands either with or without prompting for their password.

You will need to read up some information about sudo and how it works. ** visudo is what you will use to modify sudo configuration.**

Although someone will have to be logged in to your system as a specific user or as a member of a specific group, you may or may not want to allow passwordless sudo access.  Please read more before making the decision.


For example, I have this in my sudo configuration:
```
%sudo ALL=(ALL) NOPASSWD: ALL
```


This means that anybody in the group (%)  sudo is able to access ALL commands as super-user without prompting for a password.


[COLOR="Red"]Incorrect sudo configuration can lead to you being unable to use sudo. Tread lightly.[/COLOR]

---

### Post by blueridgedog on 2011-03-29
> **_joecrawford said:**
> This is helpful, but I was also interested in keeping privileges when using software center.

Perhaps...

```
sudo /usr/bin/software-center
```

---

### Post by Nutria on 2011-03-29
> **_joecrawford said:**
> Ok, I get really annoyed when I am in command line or doing a big purge of software and I have to enter my root password every minute or so. 

How to change the length my elevated privileges are up?

Real Men (and possibly fools like me) open a terminal window and type "su -" then minimize it.  Whenever I need to check syslog or install an app, I unminimize it, do what I have to do, then minimize it again.

We also have the discipline to not "live" in that window.

---

### Post by llamabr on 2011-03-29
> **Nutria said:**
> Real Men (and possibly fools like me) open a terminal window and type "su -" then minimize it.  Whenever I need to check syslog or install an app, I unminimize it, do what I have to do, then minimize it again.

We also have the discipline to not "live" in that window.

Unfortunately, that sort of advise is prohibited by this forum, and the ability to do so is disabled on ubuntu by default.  Maybe for good reason.  Leaving a window open with root privileges will eventually catch up with you.

---

### Post by oldos2er on 2011-03-29
> **Nutria said:**
> Real Men (and possibly fools like me) open a terminal window and type "su -" then minimize it. 

All this will gain you on a default Ubuntu install is "su: Authentication failure"

**sudo -i** is the preferred method (also typing **exit** when you're done).

---

### Post by towheedm on 2011-03-29
> **blueridgedog said:**
> Perhaps...

```
sudo /usr/bin/software-center
```

All graphical apps should use gksudo as opposed to sudo for root privileges.

---

### Post by earthmeLon on 2011-03-29
I'm not trying to be rude, but modifying sudo privileges seems to be the real solution here.  The rest of these seem like bad practices and hacks to work around the actual issue (except the suggestion of increasing the timeout for privileges.) OP, please try what I suggested.  

Also, let us know what you've done once you get it the way you like it and mark the thread as solved.

---

### Post by bodhi.zazen on 2011-03-29
> **earthmeLon said:**
> I'm not trying to be rude, but modifying sudo privileges seems to be the real solution here.  The rest of these seem like bad practices and hacks to work around the actual issue (except the suggestion of increasing the timeout for privileges.) OP, please try what I suggested.  

Also, let us know what you've done once you get it the way you like it and mark the thread as solved.

sudo -i is the preferred method to solve the original question:

> I get really annoyed when I am in command line.

The other methods, including modifying sudo (visudo / configuring sudo) are by far less optimal.

When running graphical applications, use gksu rather then sudo.

See also: 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by blueridgedog on 2011-03-29
> **towheedm said:**
> All graphical apps should use gksudo as opposed to sudo for root privileges.

What is the functional difference other than a graphical password prompt?  The man page indicates it is just a GTK front end for su and sudo.

---

### Post by oldos2er on 2011-03-29
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by blueridgedog on 2011-03-29
> **oldos2er said:**
> [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

Thanks.  The "user profile" component is still hard for me to adapt to, but I can see it from the link.  gksudo will not harm user specific settings, but will non-the-less give a root privileged application.

---

### Post by Nutria on 2011-03-29
> **llamabr said:**
> Unfortunately, that sort of advise is prohibited by this forum

You're kidding, right?

> and the ability to do so is disabled on ubuntu by default.

It's a **default**, not a GNOMEish We Know What's Good For You And Won't Let You Do Anything Else.

> Maybe for good reason.

Good for weaned-on-Windows noobies who don't understand that Unix is concurrently multi-user to the core, and that's the attitude that users must have.

> Leaving a window open with root privileges will eventually catch up with you.

And when it does, it'll be **my** fault, and I won't blame Ubuntu.  Until then, I'm going to ride my bike w/o training wheels.

---

### Post by blueridgedog on 2011-03-29
> **Nutria said:**
> You're kidding, right?


Item 22 of the forum rules applies: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy) 

The objective is to help users make their systems work within the framework of Ubuntu.  keeping a root terminal open is not a good practice and could be harmful to the new or non-unix veteran user.  We are trying to make an operating system that all can use, and a root terminal is a risk for a newcomer.  That said, I too come from the land of the sysadmin and generally kept a root terminal open "back in the day", but would not dream of recommending it to a person who is just starting out using Linux.

---

### Post by bodhi.zazen on 2011-03-29
> **blueridgedog said:**
> What is the functional difference other than a graphical password prompt?  The man page indicates it is just a GTK front end for su and sudo.

gksu adds some security for X not included in simply running X apps with sudo.

I do not recall the exact details (sorry), something about xauthority.

[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

There is some discussion here as well:

[http://askubuntu.com/questions/11825/is-the-difference-between-sudo-and-gksu-the-same-as-the-difference-between-sudo](http://askubuntu.com/questions/11825/is-the-difference-between-sudo-and-gksu-the-same-as-the-difference-between-sudo)

But if you want to know the exact details you will need to look over some technical documentation and I can not give you a better link to start.

---

### Post by _joecrawford on 2011-03-30
> **bodhi.zazen said:**
> sudo -i is the preferred method to solve the original question:



The other methods, including modifying sudo (visudo / configuring sudo) are by far less optimal.

When running graphical applications, use gksu rather then sudo.

See also: 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Thanks for the help, sudo -i was what I was looking for. Also, gksu is handy.  Thanks again!

---

