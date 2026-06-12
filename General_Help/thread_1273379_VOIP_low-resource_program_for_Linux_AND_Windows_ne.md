---
title: "VOIP: low-resource program for Linux AND Windows needed"
date: 2009-09-23
forum: General Help
---

### Post by megamania on 2009-09-23
Can anybody recommend a simple, low-resource Voip software to make computer-to-computer calls? 

On one end, it needs to run on an old P3 computer with Windows XP and 192MB ram. Not possible to install linux there because the computer is overseas and the owner is a beginner.

On the other end, it can be linux or windows xp.

It's very important because my friend needs to call her parents overseas, but she has no job and she can't afford to use a regular phone anymore.

---

### Post by Lars Noodén on 2009-09-23
If everyone on your communications group uses voice clients that support the same Open Standard, then it does not matter which specific programs are used.  SIP and H.323 are the ones to look for they are to VoIP what HTTP is to the web.  

However, each service does not like to advertise that you can receive incoming calls and would like everyone in a 'walled garden'.  It will take a bit of detective work, but you can find the full address to type in the first time you call eachother.  After that, you have the contact list.

So for legacy systems, look at tucows or someplace for SIP or H.323 clients.  Some places to start looking:

[http://packages.ubuntu.com/jaunty/kphone](http://packages.ubuntu.com/jaunty/kphone)

[http://packages.ubuntu.com/jaunty/twinkle](http://packages.ubuntu.com/jaunty/twinkle)

[http://packages.ubuntu.com/jaunty/ekiga](http://packages.ubuntu.com/jaunty/ekiga)

[http://packages.ubuntu.com/karmic/qutecom](http://packages.ubuntu.com/karmic/qutecom)

I'm surely missing some, but again be sure one or both of SIP and H.323 are supported.

If you really want a heavy-duty solution, look at Asterisk.

---

### Post by megamania on 2009-09-24
Thanks, that's a lot of useful information.

However, I'm still left with my main problem: find a lightweight voip program that will run on that old P3 computer with Windows XP.

When I solve that, I will install the linux equivalent (or something compatible) on the linux computer.

---

### Post by Lars Noodén on 2009-09-24
Check the links above for the project home pages.  There may be ports of some of the applications to your Conficker-using friend's system.  ;)  

Something "compatible" means that both clients use [SIP](http://ubuntuforums.org/search.php?do=process&sortby=lastpost&searchuser=Lars+Nood%E9n) and/or [H.323](http://www.voip-info.org/wiki/view/H.323)

---

### Post by whitethorn on 2009-09-24
You could try using mumble.  It has a client for linux, windows, and mac.  It's not exactly for making calls. You can't really make calls using it, but you can meet in an online room and talk to one another.  It should work on an older computer.

---

### Post by fluxlizard on 2009-09-24
I have used gizmo before on a pentium 2 with 192 mb ram running pcfluxboxos and gizmo ran just great- was like being on a real telephone.

gizmo has both linux and windows versions.

---

### Post by megamania on 2009-09-24
Thanks to all of you.

Sounds like Gizmo would be easier to set up for a beginner, so I'll suggest that one to my friend.

I'll let you know if it works out!

---

