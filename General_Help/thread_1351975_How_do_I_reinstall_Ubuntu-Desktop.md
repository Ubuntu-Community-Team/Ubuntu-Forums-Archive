---
title: "How do I reinstall Ubuntu-Desktop?"
date: 2009-12-11
forum: General Help
---

### Post by Donalb on 2009-12-11
Hi all,

I've been having a problem with Karmic showing the wrong login-in screen.

I think it's Bug 446439 on Bugzilla, (where login got screwed up after selecting invert colour, and not being able to revert to correct login).

Anyway, while one fix was suggested it's not working for me.

Someone else suggested reinstalling GDM & Ubuntu-desktop, that it worked for them.
GDM can be simply selected as re-install in Synaptic.

But in Synaptic Ubuntu-desktop is currently not shown as installed.

I remember doing something with ubuntu-desktop a year ago and it being fairly straightforward to reinstall, but I can't find anything. 

Suggestions?
Just select the Install option for Ubuntu-Desktop in Synaptic?

Cheers

---

### Post by lisati on 2009-12-11
> **Donalb said:**
> Hi all,

I've been having a problem with Karmic showing the wrong login-in screen.

I think it's Bug 446439 on Bugzilla, (where login got screwed up after selecting invert colour, and not being able to revert to correct login).

Anyway, while one fix was suggested it's not working for me.

Someone else suggested reinstalling GDM & Ubuntu-desktop, that it worked for them.
GDM can be simply selected as re-install in Synaptic.

But in Synaptic Ubuntu-desktop is currently not shown as installed.

I remember doing something with ubuntu-desktop a year ago and it being fairly straightforward to reinstall, but I can't find anything. 

Suggestions?
Just select the Install option for Ubuntu-Desktop in Synaptic?

Cheers
Small u, not U?

---

### Post by Donalb on 2009-12-11
Thanks but makes no difference. Type either in Synaptic and you get the same result ("ubuntu-desktop"), which is not currently installed.

---

### Post by Physical Hook on 2009-12-11
As you see, it doesn't contain anything new and at the same time, installing it will not allow you to reinstall the whole set of applications you have there.
If you have problems with the login screen, reinstall and|or reconfigure GDM.

```
dainis@ubuntu:~$ sudo apt-get install ubuntu-desktop
[sudo] password for dainis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ubuntu-desktop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
[COLOR=Red]Need to get 30.6kB of archives.[/COLOR]
After this operation, 57.3kB of additional disk space will be used.
Get:1 http://lv.archive.ubuntu.com karmic/main ubuntu-desktop 1.175 [30.6kB]
Fetched 30.6kB in 0s (316kB/s)      
Selecting previously deselected package ubuntu-desktop.
(Reading database ... 155679 files and directories currently installed.)
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.175_i386.deb) ...
Setting up ubuntu-desktop (1.175) ...

```

---

### Post by Donalb on 2009-12-11
And...this actually worked and fixed my login screen after 2 months!

It also actually updated 9 packages.

Thanks for the help.

My list of open issues with Karmic very slowly getting shorter.

---

