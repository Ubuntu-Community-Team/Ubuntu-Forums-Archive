---
title: "Is this server or regular version?"
date: 2011-08-14
forum: General Help
---

### Post by Kissell on 2011-08-14
Anyone know how to tell if this Ubuntu server is running the regular version or the server install?  I ran the following commands, and here is there output, but I don't see anything about if this was regular or server.  I've heard that the server version is tuned better to services instead of to the user interface, and the GUI on the box is acting like it's got more important things to do, even though it's a six-core processor with 16GB RAM.

uname -a
> 
Linux SERVER 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


lsb_release -a
> 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty


cat /etc/issue
> 
Ubuntu 11.04 \n \l


---

### Post by CatKiller on 2011-08-14
The server version doesn't have a GUI.

---

### Post by Kissell on 2011-08-14
> **CatKiller said:**
> The server version doesn't have a GUI.

That's not true.  The server version doesn't come installed with a GUI.  However, you can easily add gnome to it.  

I'm having performance issues with the GUI on this box, and remember talking about maybe installing the server version on it.  I read on Ubuntu's site that the server version is tuned more for services than for the GUI, so I need to know if this is the server version.  If so, then I can accept that is why the GUI is slow.  But, because there is a GUI, I suspect this is not the server version and there is a problem.

---

### Post by sbraz on 2011-08-14
> **CatKiller said:**
> The server version doesn't have a GUI.
yes but it could have been installed manually, as well as the -generic kernel.

---

### Post by howefield on 2011-08-14
Ouput from uname -a on the desktop version is

> Linux natty-desktop 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by sbraz on 2011-08-14
> **howefield said:**
> Ouput from uname -a on the desktop version is
```
Linux **natty-desktop** 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```
that in bold is the hostname unfortunately.
this is 11.04 desktop live cd:
[[IMG]http://img6.imageshack.us/img6/9738/screenshotsbu.th.png[/IMG]](http://imageshack.us/photo/my-images/6/screenshotsbu.png/)

maybe comparing sysctl parameters shown by **sysctl -a** would yield some differences?

---

### Post by CatKiller on 2011-08-14
> **Kissell said:**
> That's not true.  The server version doesn't come installed with a GUI.  However, you can easily add gnome to it. 

Of course you can. But it isn't "better tuned to services instead of to the user interface" because there isn't one. It comes with different packages installed by default, but there isn't server pixie dust in there.

And really, can't you people think of more imaginative names for your machines? :)

---

### Post by howefield on 2011-08-14
> **sbraz said:**
> that in bold is the hostname unfortunately.

Of course, thanks for that.

Could try

> cat /etc/motd

where the desktop should spit out

> Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

but quite a bit more on the server version.

---

### Post by haqking on 2011-08-14
Linux SERVER 2.6.38-10-**generic** #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

The generic part mean Desktop instead of server, in server it replaces the generic with the word server.

Also cat/etc/motd

will show you a welcome as shown above, if it is server it also gives your system information, processes, users logged in etc

---

### Post by Kissell on 2011-08-14
Cool, thanks haqking.  I was about to lauch into some virtual machines to do some compares.  I thought that was right, it used to say server on server version, but I haven't run a server version in a long time, just love using the GUI too much and powerful machines are cheap these days, and nobody can say anything about the security of it when there are a ton of windows servers on site.

BTW: Turns out my problem wasn't it being the server version.  Last night's updates installed a new kernel that VMware Workstation didn't like.  I was unable to fix the problem by allowing it to recompile like it wanted to do, it kept hanging.  After completely uninstalling and reinstalling VMware, the performance issues with the GUI disappeared.  Weird, because Vmware wasn't running...  but I guess it had virtual network drivers or something in the kernel that were hosing the system with the new update to 2.6.38-10.

---

