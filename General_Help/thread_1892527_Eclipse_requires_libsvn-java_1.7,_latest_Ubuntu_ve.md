---
title: "Eclipse requires libsvn-java 1.7, latest Ubuntu version is 1.6"
date: 2011-12-08
forum: General Help
---

### Post by shumifan50 on 2011-12-08
I am trying to move to Linux development from Visual Studio and find that Eclipse is as good is VStudio. However, I would like to integrate subversion as a repository and it seems that subclipse is the way to go(not subversive). So I tried to install it, but it fails as the libsvn-java available from Ubuntu is 1.6 and Eclipse requires 1.7 or later.

So I have 2 questions:
1. Is the version of libsvn-java in Ubuntu going to be updated(otherwise Eclipe is a non-starter or much more difficult to get going with subversion).
2. Is it possible to get libsvn-java from elsewhere and make it work with Ubuntu(I am using Maverick).

Any assistance greatly appreciated.

---

### Post by shumifan50 on 2011-12-08
OK, I found this link and it has version 1.7 for Ubuntu.
I don't know whether I can post it here. Could the admins please remove if not.
[http://www.wandisco.com/node/92/done?sid=22859](http://www.wandisco.com/node/92/done?sid=22859)

Sadly it does not include libsvn-java,

---

### Post by shumifan50 on 2011-12-08
In the end I did not manage to install libsvn-java 1.7.
So I uninstalled subclipse 1.8.x from within eclipse and installed version 1.6.x instead and now it works fine using the Ubuntu libraries.

So the moral of the story, at the moment, is to only use subclipse 1.6.x on Ubuntu until they release libsvn-java 1.7.:(

A useful link for svn beginners(like myself) to set up subversion is 
[http://www.howtoforge.com/debian_subversion_websvn](http://www.howtoforge.com/debian_subversion_websvn)
If subversion is not set up correctly for apache2 use, the whole lot still fails and the error looks like an incompatible library(just to confuse the issue further).

---

### Post by oldtimer7777 on 2011-12-08
Did you try installing JRE 1.7 this way:

[https://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/](https://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/)

And if that does the trick?

> **shumifan50 said:**
> I am trying to move to Linux development from Visual Studio and find that Eclipse is as good is VStudio. However, I would like to integrate subversion as a repository and it seems that subclipse is the way to go(not subversive). So I tried to install it, but it fails as the libsvn-java available from Ubuntu is 1.6 and Eclipse requires 1.7 or later.

So I have 2 questions:
1. Is the version of libsvn-java in Ubuntu going to be updated(otherwise Eclipe is a non-starter or much more difficult to get going with subversion).
2. Is it possible to get libsvn-java from elsewhere and make it work with Ubuntu(I am using Maverick).

Any assistance greatly appreciated.

---

### Post by albertmatyi on 2011-12-20
Install svn from WANdisco - worked for me.
Small explanation with solution: [http://is.gd/pMCcJI](http://is.gd/pMCcJI)

Script to run (found in the post above too), which will install the svn and libsvn 1.7
[http://pastebin.com/H7YjU1c3](http://pastebin.com/H7YjU1c3)

It worked for me

---

### Post by Ruazinn on 2012-02-16
Thanks Albert, that seems to work for me.  Now I can start trying to reinsert the hair I pulled out.

---

