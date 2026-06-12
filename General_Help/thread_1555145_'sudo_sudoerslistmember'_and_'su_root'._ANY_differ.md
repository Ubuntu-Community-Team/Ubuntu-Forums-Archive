---
title: "'sudo sudoerslistmember' and 'su root'. ANY difference?"
date: 2010-08-17
forum: General Help
---

### Post by kaurman on 2010-08-17
Hi!

The question that bothers me isn't actually ubuntu related but since it concerns linux, I consider it appropriate.

I recently happened to install Debian on a rather old laptop. By the end of the installation, I had been asked to set passwords for 2 users, one of them being root. The other user (henceforth the regular user) did not even have the right to sudo... I could've added it to the sudoers list but I thought I'd use 'su root' instead when need be.

As I had not installed a desktop environment of any kind during the installation, I had to do it now using apt-get / aptitude. And so I did. I installed both, xfce and xdm (naturally, using su root => being logged in as root while doing so).

All was nice, except for the fact that the regular user could not restart or shut down the system from within xfce (I'm not sure about root). The only reasonable explanation I could think of was the lack of user privileges which in turn was probably the consequence of the fact that the regular user did not belong into a group with sufficient privileges, right?

Anyway, at some point I decided that Xfce was a bit too resource hungry, logged in as root using 'su root' in the terminal and installed lxde instead while retaining the xdm login manager and rejecting the gdm which is the default for lxde, AFAIK. 

The result was nice, but neither of the users (this time I really tested with both of them) could initiate a shutdown or restart from within lxde. Actually, the menu only had the log off entry...

As the system started to complain about missing themes anyway, I removed xdm and gave gdm a try after all (installed & removed by using 'su root'). GDM was, as expected, considerably slower but having logged in to lxde through gdm the users could shut down and restart without any problems.

Explanations?



All this made me think about user privileges. Was it ok to use 'su root' for installing & removing the desktop environments or would it have been better to add the regular user to the sudoers list and install using 'sudo' while being logged in as the regular user?

The way I see it, these methods are equal, as while using 'sudo' a regular user is equal to root, at least when it comes to installing & removing stuff via apt-get. AFAIK, any kind of such activity is actually done by the root user, even if it is done by a user using sudo. This is the only way, right? 

I'd be happy, if anyone would confirm my understanding or enlighten me if I'm wrong. I just want to be sure that I did not create a possible security risk by installing those environments through 'su root'.

All the best,

K

---

### Post by snowpine on 2010-08-17
Hi there, I don't know about Debian (you can ask [on their forums]("http://forums.debian.net") if you like) but the use of 'su root' is never recommended in Ubuntu (yet most of us manage to shut down just fine).

Here's some documentation to get you started: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by kaurman on 2010-08-17
> **snowpine said:**
> Hi there, I don't know about Debian (you can ask [on their forums]("http://forums.debian.net") if you like) but the use of 'su root' is never recommended in Ubuntu (yet most of us manage to shut down just fine).

Here's some documentation to get you started: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
Hi!

Thanks for your reply. Unfortunately, the link is unavailable at the moment but I think I read it before.

I am not saying that one needs to be logged in as root to shut down. Of course, regular users can shut down as well. I believe that is because the regular users (more precisely, some specific scripts (?)) belong to a certain group which has the appropriate priviledges. What I'm saying is, that technically you still need sudo to initiate a shutdown or restart. Ok, that's not the best way to put it but I believe you understand what I mean.

As for the use of su root being discouraged in ubuntu, I believe this has two main reasons:

1) using 'su root' gives you a permanent root status untill you log off / exit the root user. This means that you can possibly do many stupid things by accident. With sudo you only gain the privileges for specific commands.

2) root login is disabled by default. The reason for that is probably what I wrote in 1

Any fyrther info is much apriciated. 

K

---

### Post by snowpine on 2010-08-17
Actually, the reason is

3) 'su root' is bad syntax. It's not even mentioned in the [Ubuntu]("https://help.ubuntu.com/community/RootSudo") or [Debian]("http://wiki.debian.org/Root") literature on the topic.

I just checked and the link is back up, it should answer all of your questions:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sisco311 on 2010-08-17
> **snowpine said:**
> Actually, the reason is

3) 'su root' is bad syntax, a meaningless and redundant command. It's not even mentioned in the Ubuntu or [Debian]("http://wiki.debian.org/Root") literature, and I can't think of a single modern distro that recommends it. (Feel free to prove me wrong.)

I just checked and the link is back up, it should answer all of your questions:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

It's redundant, but not meaningless. Invoked without a username, su defaults to becoming the superuser (see **man su**).

---

### Post by snowpine on 2010-08-17
> **sisco311 said:**
> It's redundant, but not meaningless. Invoked without a username, su defaults to becoming the superuser (see **man su**).

Thanks for the clarification... edited my post above. :)

---

### Post by NiGhtMarEs0nWax on 2010-08-17
> **kaurman said:**
> Hi!
Explanations?


afaik the shutdown process is initiated through suid, that is just a guess though. installing gdm obviously took care of that. as to fix it for lxde, i have no idea.

just a guess though.

---

### Post by sisco311 on 2010-08-17
@OP, check out 

[http://www.freedesktop.org/software/ConsoleKit/doc/ConsoleKit.html](http://www.freedesktop.org/software/ConsoleKit/doc/ConsoleKit.html)

[http://hal.freedesktop.org/docs/polkit/](http://hal.freedesktop.org/docs/polkit/)

---

### Post by kaurman on 2010-08-17
Thanks for the answers.

Ok, so one of the differences between su root and sudo is that you can restrict sudo to certain commands...

Still, if you say sudo is 'redundant' which I admit it may be, then I'm somewhat confused. What should I have done instead using su root then? And don't say I should've used just 'su' ;)
And... Is my system in any way more insecure being set up as it is? (lxde, gdm installed using su root)?

K

PS

Sisco311, I'll check the links, thanks.

---

### Post by snowpine on 2010-08-17
> **kaurman said:**
> What should I have done instead using su root then? And don't say I should've used just 'su' ;)

Ubuntu wiki recommends using 'sudo'
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Debian wiki says you can use 'su' but it is preferable to configure and use 'sudo' 
[http://wiki.debian.org/Root](http://wiki.debian.org/Root)

I am a Debian user and I always use sudo.

---

### Post by JKyleOKC on 2010-08-17
Most distributions have an administrative group and anyone who's a member of that group is able to use sudo (in the usual default configuration of sudoers). For many of the older distributions that group is known as "wheel" but in *buntu it's "admin" and the first user created, during installation, is automatically made a member of it.

As for the su command, it defaults to "su root" if you don't specify some other user name, so typine "su root" is simply entering five keystrokes that are not needed. While most of us think of it as being a contraction of "super user" I believe it actually means simply "set user" since it can be used to masquerade as another user temporarily without having to logout and log back in as that other user. However it always asks for a password, and that password has to be the one for the account being "su-ed" to. In other words, a simple "su" needs the root password to proceed. The sudo command, on the other hand, needs the password of the user who's issuing it rather than the one of the user being switched to for one command.

Good arguments can be made for both ways of dealing with the need for administrative access; the *buntu way is slightly less risky for newcomers, but can be horribly frustrating to them when they are setting up their system and have to re-enter their password every few steps...

---

