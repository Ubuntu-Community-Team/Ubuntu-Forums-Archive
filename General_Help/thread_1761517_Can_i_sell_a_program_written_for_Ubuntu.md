---
title: "Can i sell a program written for Ubuntu"
date: 2011-05-18
forum: General Help
---

### Post by moosethemucha on 2011-05-18
I am developing a POS system to run ubuntu and creating a POS system to run on it. Now i will be selling the hardware with ubuntu running on them and with my software, ubuntu will be free but the customer will pay for the hardware and the software. Is this legal, ubuntu is open source but does that mean any software developed for the platform, is it also open source. Than you.

---

### Post by Frogs Hair on 2011-05-18
Hi and Welcome

Take a look at the link and additional searches should answer your questions. [http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)

---

### Post by CoolJohnB on 2011-05-18
> **moosethemucha said:**
> I am developing a POS system to run ubuntu and creating a POS system to run on it. Now i will be selling the hardware with ubuntu running on them and with my software, ubuntu will be free but the customer will pay for the hardware and the software. Is this legal, ubuntu is open source but does that mean any software developed for the platform, is it also open source. Than you.

Not necessarily for example Crossover is a program you have to pay for and there are others as well.  I guess if your program is NOT open source then you can charge for it.  Maybe there is a legal person who can confirm or deny this.

---

### Post by rg4w on 2011-05-18
Technically, you can charge for anything, even open source apps, but it's hard to make a living if you're dependent on revenue from something anyone can access the source of for free.

It's my understanding (I'm not a lawyer) that as long as you don't use FOSS code you have no FOSS requirements to share the source.  The specifics will vary from license to license, but you're free to choose any license for your own code.

Marketability is another story.  One the one hand, there are some who will use only free software, and will reject a proprietary app no matter how good or cost-effective it is.  But on the other hand, if you provide unquestionable value in the app relative to the price you're asking, there are those who will pay for a Linux version just as they would for Mac or Windows.

Best of luck with your launch.

---

### Post by mcduck on 2011-05-18
Open source has nothing to do with being free of charge, so yes, you definitely can sell open source software, and software made for open source OS like Linux.

What limitations there might be depend on the actual license of the software, but assuming you don't use any existing libraries etc. then you are free to pick whatever licensing scheme you want to.

(if you do use such libraries, or code made by other people, then you should check the licenses of those libraries/code. For example using GPL-licensed code would mean you'd ave to use the GPL license as well, which would still allow you to sell the software if you want to.)

---

### Post by abrianb on 2011-05-18
There is a big Linux presence in retail already(ie. Walmart, AutoZone). Companies do purchase/use mixed bag software packages (free and none free). Retailers will be more concerned with system stability and in use costs than with the cost of initial purchase. I have worked in retail for 25 years and used Linux and windows systems. I have never heard a single word uttered about free software, open source etc. I think businesses look at the cost of operating pos as a whole and the ability of the pos system to fulfill needs.  Good luck with this venture.

---

### Post by moosethemucha on 2011-05-21
thank you for everyones reply its been a great help

---

### Post by grahammechanical on 2011-05-21
If I open the Ubuntu software Centre and click Get Software I see a heading called For Purchase. And under that heading are programs for download which you must buy. So, the principle is established.

In fact Canonical is looking for quality programs for purchase to include in the Software Centre. It is my understanding some of this money goes to supporting Ubuntu and the rest goes to the developer. 

Regards.

---

### Post by perspectoff on 2011-05-21
Look up the LGPL license, in specific.

AFAIK, you can sell things that have that license. (You just can't make them proprietary -- anyone else can sell them, too.)

---

### Post by perspectoff on 2011-05-21
> **rg4w said:**
> Technically, you can charge for anything, even open source apps, but it's hard to make a living if you're dependent on revenue from something anyone can access the source of for free.



That's not at all true.

"Open source" is an ambiguous term that means many different things to many people. It is not a license.

The original meaning meant merely that the code was required to remain open to examination (versus a binary-only, non-examinable format) so that bugs, malicious code, or merely poor coding could be ("easily") recognized.

The connotation that the code is free for use by anyone ("free" as in a "free-for-all") is a separate issue and is not the original meaning, although many have mistakenly believed so.

That concept is specified through licensing, and both the reference in the previous post to the Gnu licenses and the Wikipedia article on software licenses are informative reads.

There are several licenses (GPLv3 and Affero GPL the best known) that require products that use these licenses to remain "free" as in "free-for-all", but there are many restrictions against selling the software that are commonly affixed to the license.

Further, there are many licenses that prohibit trademarking, preserve editorial control, and forbid monetarization of software that is otherwise free to use and whose code is open to examination. (Canonical has such a license, AFAIK, for the Unity UI.)

The issue of libraries is a sticky wicket. Many libraries are GPLv3 and can not be incorporated into any software that is not also GPLv3 (the so-called "copyleft" license mentality).

If you plan to sell your software, you ought to be careful about using such libraries. Use LGPL-licensed (or similar) libraries instead, or use no external libraries at all (or ones you have written). 

Lastly, be aware that there is plenty of proprietary "open-source" (in the "examinable code" meaning of the term) software available for Linux, and there is plenty of binary (non-open-source) software available for Linux (such as games) as well. 

I personally don't know anything about the Ubuntu marketplace -- does it actually require software sold there to be open source?

---

### Post by rg4w on 2011-05-21
Perspectoff, perhaps it's just because I'm writing pre-coffee but I couldn't find anything in your excellent post which contradicted mine.  Instead, it seems to reinforce my main point:  you can put a price code on object code if you like (within, of course, the bounds of any applicable trademark, patent, and copyright restrictions), but if you use a license that requires that you make the source code available the world is always just one make file away from having your object code at no cost.

Philosophically, of course there is a fundamental distinction between "free as in freedom" and "free as in beer".  But for a software publisher the practical implication is simply that FOSS-governed works are hard to sell.  They're easy to give away, and some have been able to sustain themselves through supplemental services.  But making a living selling FOSS-governed software seems a hard enough thing that I can't think of any publishers who've been able to do it.

---

### Post by Thewhistlingwind on 2011-05-21
This is something you should investigate yourself. (IANAL) But the answer is yes, it is perfectly alright to distribute a proprietary application with open source software. HOWEVER: It is NOT alright to use code or libraries from certain open source licenses in your product. (Primarily the GPL.) So, if your proprietary product has open code in it thats GPL based, remove and replace it. (For anything else, check the license.)

---

