---
title: "Major QA needed on programs repositories!"
date: 2009-09-10
forum: General Help
---

### Post by JEBB on 2009-09-10
In order to help a number of seniors get rid of their virus and malware trashed XP systems I have been trying to set up my netbook with 9.04UNR and a minimum number of programs that they can model.  But I have found that too many of the programs in the repositories don't work right or are out of date.  Telling those seniors to update Software Sources, to do arcane terminal processes or to download and install programs for which no clear and consistent install procedures have been defined is idiocy.  If Ubuntu Linux ever wants to become mainstream problems with the programs have got to be fixed.  

After all it is the programs that make a computer useful, an operating system is only an enabler.  

Sincerely,
A highly frustrated new Ubuntu user.

---

### Post by Whiffle on 2009-09-10
How about some examples?

---

### Post by JEBB on 2009-09-11
Here are three:  Firefox, KAddress, Abiword.  There are more if you wish.

---

### Post by Whiffle on 2009-09-11
See this is the problem:

"There is something wrong with firefox."

Okay?  Now what?  Not much can be done without specifics.  

If you really want to help with these problems, get a Launchpad account, and submit bug reports.  I doubt the devs spend much time on the forum anyway.

---

### Post by jocko on 2009-09-11
> **JEBB said:**
> Here are three:  Firefox, KAddress, Abiword.  There are more if you wish.

What's your problem?

You can't just say "problems with the programs have got to be fixed" without explaining *what* those problems are.
And from the  thread title I got the impression you had questions that you want answers to. Where are those questions?

---

### Post by Whiffle on 2009-09-11
> **jocko said:**
> What's your problem?

You can't just say "problems with the programs have got to be fixed" without explaining *what* those problems are.
And from the  thread title I got the impression you had questions that you want answers to. Where are those questions?

I think QA in this context is Quality Assurance ;)

---

### Post by flicman on 2009-09-11
Some of us just have problems, man.  Problems.

FWIW, Firefox works fine in every installation of Ubu I've ever done.  Seems like user error to me.

---

### Post by wojox on 2009-09-11
I use AbiWord and Firefox, what problems are you having?

---

### Post by appier on 2009-09-11
> **JEBB said:**
> Here are three:  Firefox, KAddress, Abiword.  There are more if you wish.

My advice would be to start a separate thread for each problem with each program.  Specifically, put a real short description of the problem in the title field followed by more specifics in the body of the message.

The members of this forum are helpful and will try to assist you.  So far, with their help, I have been able to fix a number of various issues on several different machines running various desktops on Ubuntu.  Often, I have found what I needed just by searching the forum.

Don't give up!

---

### Post by JEBB on 2009-09-11
1. Firefox is stuck at version 3 not 3.5 plus removing or adding large number of bookmarks is glacially slow.
2. Abiword, not my browser, opens when I click on a link in an email
3. KAddress required updates via added Software Sources to eliminate problems with records that have more than one email address.

I have started separated threads but in most of them there were no replies.

---

### Post by P4man on 2009-09-11
> **JEBB said:**
> Firefox is stuck at version 3 not 3.5 

Yes, that is ubuntu policy: "*Ubuntu releases a new version of its OS every 6 months. After a release, the version of all packages stays constant for the entire 6 months*."

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Im kinda wondering why your seniors want FF 3.5.2 ?

> plus removing or adding large number of bookmarks is glaciallty slow.

They have that many? Never seen it take even a second, but I'll take your word for it.

> Abiword, not my browser, opens when I click on a link in an email

I didn't know abiword was part of the default install. But yeah, there seems to be bug there. Last post here might help:
[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/19076](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/19076)

> KAddress required updates via added Software Sources to eliminate problems with records that have more than one email address.

KAddressbook? In ubuntu UNR? Gee, if you're gonna mix and match gnome and KDE apps, then no wonder you're getting those seniors confused.

Anyway, if that is the worst of the list, things really ain't too bad IMHO. Its also kind of weird you want at the same time the latest version of everything like FF 3.5 which is like 5 weeks old, and perfect 100% working everything. These usually dont match. 

BTW, I think there are a lot more serious bugs to be worked on in UNR.. It is new, and needs more work. Its usable but not perfect. If you want "perfect", use a LTS version or debian.

---

### Post by StuartN on 2009-09-11
> **JEBB said:**
> Firefox is stuck at version 3 not 3.5

There is a one-click link at Mozilla, if you really believe 3.5 has some essential feature, or that 3.0 is broken.

> **JEBB said:**
> Abiword, not my browser, opens when I click on a link

Your Preferred applications (System->Preferences) are probably incorrect.

I don't see a QA issue with these, and don't know anything about KAddress - Thunderbird meets my needs.

---

