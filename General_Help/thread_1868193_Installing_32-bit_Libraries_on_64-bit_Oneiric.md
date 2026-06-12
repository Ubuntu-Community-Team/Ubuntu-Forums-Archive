---
title: "Installing 32-bit Libraries on 64-bit Oneiric"
date: 2011-10-23
forum: General Help
---

### Post by crokett on 2011-10-23
I'm sure this has been asked before but my searches weren't coming up with anything relevant.  My company has Linux pre-loads for Fedora and RHEL x86_64 and Ubuntu.  Currently only 32-bit Ubuntu is supported since 64-bit won't run 32-bit apps.  I'd much rather run Ubuntu but I need the 64-bit support for some apps I run at work.   I am attempting an install my company's packages on 64-bit Oneiric but it is looking for several 32-bit libraries.  I am using getlibs to attempt to install them, but it can't find the libraries I need in the repositories. How can I enable the 32-bit repositories to attempt the install?

---

### Post by oldtimer7777 on 2011-10-23
> **crokett said:**
> I'm sure this has been asked before but my searches weren't coming up with anything relevant.  My company has Linux pre-loads for Fedora and RHEL x86_64 and Ubuntu.  Currently only 32-bit Ubuntu is supported since 64-bit won't run 32-bit apps.  I'd much rather run Ubuntu but I need the 64-bit support for some apps I run at work.   I am attempting an install my company's packages on 64-bit Oneiric but it is looking for several 32-bit libraries.  I am using getlibs to attempt to install them, but it can't find the libraries I need in the repositories. How can I enable the 32-bit repositories to attempt the install?

They should come installed by default in 64-bit systems as of 11.10 release. 

But here is a walkthrough so you can install them anyways..  Look for Google Earth about half the way down and it should show you how to install them just in case:

[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by crokett on 2011-10-23
Hmmm

thanks then maybe the 32 bit libs aren't the problem.  I tried

sudo apt-get install ia32-libs

and I get "ia32-libs already installed and the latest version"

There are a lot of libraries I need for some of the packages that aren't there. 

I will work on this a little more.

Will the support for 32-bit apps be any better in 12.04?

---

### Post by oldtimer7777 on 2011-10-24
> **crokett said:**
> Hmmm

thanks then maybe the 32 bit libs aren't the problem.  I tried

sudo apt-get install ia32-libs

and I get "ia32-libs already installed and the latest version"

There are a lot of libraries I need for some of the packages that aren't there. 

I will work on this a little more.

Will the support for 32-bit apps be any better in 12.04?

That is a very good question. We will have to wait and see what 12* brings.

---

### Post by crokett on 2011-10-24
I hope so.  At least where I work, most of the linux community considers Ubuntu somewhat of a toy.  This late in the game and not having true multi-arch support does not help that perception.  Last week I was talking with another guy about a new machine we got that is going to become a VMWare server.  It has quad-core processors and something like 16 GB of RAM.  I was joking about putting Ubuntu on it. His comment was 'Would Ubuntu know what to do with so much machine?'

My company is considering dropping Ubuntu as officially supported.  For now, nothing past 10.10 is official any more.

---

