---
title: "Newbie needing help"
date: 2009-07-07
forum: General Help
---

### Post by AntiHeroUK on 2009-07-07
I have just started using Ubuntu recently and I am looking to install the latest Catalyst drivers to allow the proper resolution to be set on my monitor amongst other features.

I have been reading [this]("http://ubuntuforums.org/showthread.php?p=7496210#post7496210") thread and I would like to know how I check for the **lib-ia32 **file, and if it's not there how I would go about installing it. Thanks!

---

### Post by c0mput3r_n3rD on 2009-07-07
You should be to just go to,  System -> Administration -> Hardware Driver.  And it will search for propriety drivers for you.  See if that works

---

### Post by issih on 2009-07-07
You need to learn about installing packages:

read this:
[https://help.ubuntu.com/9.04/add-applications/C/installing.html](https://help.ubuntu.com/9.04/add-applications/C/installing.html)

paying particular attention to the synaptic package manager section.

Normally, everything you install in ubuntu is handled using the package manager, be it a library an application or a driver.

So in this case you just need to check if that library is installed using the package manager.

If it isn't just select it for installation and hit apply.

Once that is done you can use the .run file to install the fglrx driver.

To be honest, however, unless you have some reason to need the very latest driver, I'd just use synaptic to install the version of fglrx in the repositories, it will make your life less painful.

Hope that helps

---

### Post by AntiHeroUK on 2009-07-07
[URL="http://ubuntuforums.org/newreply.php?do=newreply&p=7578114"]> **c0mput3r_n3rD said:**
> You should be to just go to, System -> Administration -> Hardware Driver. And it will search for propriety drivers for you. See if that works[/URL]

I know that, but if I install proprietary drivers without the lib file will that not cause a black screen upon rebooting?

> **issih said:**
> You need to learn about installing packages:

read this:
[https://help.ubuntu.com/9.04/add-applications/C/installing.html](https://help.ubuntu.com/9.04/add-applications/C/installing.html)

paying particular attention to the synaptic package manager section.

Normally, everything you install in ubuntu is handled using the package manager, be it a library an application or a driver.

So in this case you just need to check if that library is installed using the package manager.

If it isn't just select it for installation and hit apply.

Once that is done you can use the .run file to install the fglrx driver.

To be honest, however, unless you have some reason to need the very latest driver, I'd just use synaptic to install the version of fglrx in the repositories, it will make your life less painful.

Hope that helps

Thank-you for the reply. I'm not sure my graphics card would be supported in the older version which is why I want to install the latest. I am using a 4770.

---

### Post by issih on 2009-07-08
The whole point of the package manager is that it handles all the dependancies.

So if you clicked on the fglrx package and chose to install it, then the package manager will know that you need the lib-ia32 package and will automatically install it for you.

The package manger...well it handles packages.

The only reason you have to worry about this is that you are using a non standard install method (i.e. the run file) so you have to manually manage its dependencies.

As for the version in the repositories (which is basically the list of packages the manager knows about) not being good enough for your card...well it might be, or it might not. personally I'd try it first and if things didn't work then move on to manual installation.

Do bear in mind that all the other little install utilities that ubuntu gives you (add/remove, hardware drivers etc) are all really little front ends to the package manager designed to simplify a specific task (installing apps and drivers respectively).

Hope that helps

---

