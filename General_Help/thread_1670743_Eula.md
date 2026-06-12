---
title: "Eula?"
date: 2011-01-19
forum: General Help
---

### Post by weaver4 on 2011-01-19
The attorney for our company would like to see the Ubuntu EULA.  Can someone tell me where I can find a printable copy of it?

---

### Post by ajgreeny on 2011-01-19
There is no such thing for most of it, only for the proprietary parts, eg flash, nvidia drivers, skype, etc etc!

Ubuntu is open source.  Show him all about GPL, though that may take hours for him to read, as there are different versions of GPL, LGPL, BSD and several other licenses, none of which have or need a standard EULA, as far as I'm aware.

---

### Post by weaver4 on 2011-01-19
Well that is what I thought.  But the Ubuntu License page does not say that it only includes GPL software.

So our attorneys want to verify that it is OK to redistribute the software that is included in Ubuntu on our product.

---

### Post by Simian Man on 2011-01-19
> **weaver4 said:**
> So our attorneys want to verify that it is OK to redistribute the software that is included in Ubuntu on our product.

It depends exactly what you are doing.  "Ubuntu" is just a package that includes a lot of other projects written by scores of different people and licensed in different ways.  What exactly is it you are doing?

---

### Post by endotherm on 2011-01-19
here is most of the info you require, but on the topic of licenses and redistribution, you will find they punt to the GPL that all the components of ubuntu are licensed under.

[http://www.ubuntu.com/legal](http://www.ubuntu.com/legal)

[http://www.gnu.org/licenses/](http://www.gnu.org/licenses/)

basically redistribution without changes is unconstrained by the license as long as you ship a link to the GPL or otherwise pass on it's contents. if you choose to make changes to code, and then redistribute, you must provide access to the source code, with the gpl advisory.

---

### Post by rg4w on 2011-01-19
> **endotherm said:**
> here is most of the info you require, but on the topic of licenses and redistribution, you will find they punt to the GPL that all the components of ubuntu are licensed under.

[http://www.ubuntu.com/legal](http://www.ubuntu.com/legal)

Which says:

> Use of Ubuntu software Your use of any software obtained  from this site is subject to the terms of any license agreement **provided  with the software**.


Isn't there something accessible in the OS itself?

---

### Post by rg4w on 2011-01-19
(duplicate post)

---

### Post by oldos2er on 2011-01-19
> **rg4w said:**
> Isn't there something accessible in the OS itself?

There's *man gpl*

---

### Post by weaver4 on 2011-01-19
That statement: "Use of Ubuntu software Your use of any software obtained from this site is subject to the terms of any license agreement provided with the software. "  is the one that scares our attorneys.  

So their question is do we have to review the license agreement on every piece of software in Ubuntu?

Our software is a simple turnkey solution to monitor some systems in a hospital.

---

### Post by bab1 on 2011-01-19
> **rg4w said:**
> 
Isn't there something accessible in the OS itself?

The OS is Linux not Ubuntu.  As stated earlier: Ubuntu is a disto of Linux and other applications.  

Your lawyers need to do their job, not you.  If it says *"Use of Ubuntu software Your use of any software obtained from this site is subject to the terms of any license agreement provided with the software."*, Then ***they ***should research it.

In reality the attorney you use should already be familiar with GPL.  If not then they are learning while earning your fee.

---

### Post by tgm4883 on 2011-01-19
> **bab1 said:**
> The OS is Linux not Ubuntu.  As stated earlier: Ubuntu is a disto of Linux and other applications.  

Your lawyers need to do their job, not you.  If it says *"Use of Ubuntu software Your use of any software obtained from this site is subject to the terms of any license agreement provided with the software."*, Then ***they ***should research it.

In reality the attorney you use should already be familiar with GPL.  If not then they are learning while earning your fee.

While I'm not really trying to start a war here, you brought it up. The OS is Ubuntu, the Kernel is Linux.

---

### Post by weaver4 on 2011-02-03
Are there any legal firms that "specialize" in Ubuntu or Linux.

I am looking for a legal firm that will "bless" Ubuntu and say that we are safe.

We went to our "regular" outside legal firm and they said they need to investigate every single application in Ubuntu...give me a break.

---

### Post by weaver4 on 2011-02-07
Bounce

---

### Post by Matt__ on 2011-02-07
The answer to this is surely dependant on what software sources you intend to use.
Ubuntu main can be used and modified by anyone as long as the source is made available. so if you are not installing additional software with more restrictive licensing there shouldn't be a problem.

> **About Ubuntu Licensing]All of the application software installed by default is free software. In addition, we install some hardware drivers that are available only in binary format, but such packages are clearly marked in the restricted component[/quote]

have you looked at this page?
[http://www.ubuntu.com/project/about-ubuntu/licensing](http://www.ubuntu.com/project/about-ubuntu/licensing)

there is also this post here on the forums in a similar vein
[http://art.ubuntuforums.org/showthread.php?t=1449770&page=2](http://art.ubuntuforums.org/showthread.php?t=1449770&page=2)


[QUOTE=bab1 said:**
> 
Your lawyers need to do their job, not you.  If it says *"Use of Ubuntu software Your use of any software obtained from this site is subject to the terms of any license agreement provided with the software."*, Then ***they ***should research it.

In reality the attorney you use should already be familiar with GPL.  If not then they are learning while earning your fee.

100% agree with this.

---

### Post by SeijiSensei on 2011-02-07
You might consider a distribution like Debian or Fedora which have stricter rules about what they'll redistribute.  You obviously cannot redistribute any proprietary drivers, nor can you redistribute software from ubuntu-restricted-extras (at least in the US).  Any GPL-licensed software can be redistributed providing you make the source code available per the GPL license.  Most other "free" software under licenses like BSD, MIT or the Mozilla Public License is typically less constrained than GPL code.  

I actually think the attorney who says you need to know the licenses for each piece of software has a point.  If you distribute something commercially, you should know whether your actions will come back and bite you in the butt.  Your best bet is to create your own Linux distribution containing only the software needed to support your application and determine the licensing for the packages in your distribution.  Something like [DamnSmallLinux]("http://www.damnsmalllinux.org/") might be a good starting point.

---

