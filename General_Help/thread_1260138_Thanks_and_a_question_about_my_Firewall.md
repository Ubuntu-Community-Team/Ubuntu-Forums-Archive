---
title: "Thanks and a question about my Firewall"
date: 2009-09-07
forum: General Help
---

### Post by Irvine_himself on 2009-09-07
Thanks again, I have it installed Ubuntu and am using it to make this post :)

Since I am not very confident with IPchains, (or is it IPtables?) I managed to install the Firestarter GUI for the firewall, 

Anyway, my next stupid question is, if I have used the basic set up [illustrated here]("https://help.ubuntu.com/community/Firestarter"), and allow a "permissive by default" outbound policy and no "inbound exceptions" Then I can assume that while on the learning curve I am secure?

---

### Post by blueridgedog on 2009-09-07
Welcome to Ubuntu.  Ubuntu "out of the box" has no open ports to the network (meaning that there is no process or service listening for connections).  As such, there is no direct need for a firewall, especially if you are behind a typical home router.

But the direct answer to your question is yes, permissive outbound and no inbound will work (and is the same effect you had without a firewall).

It is also worth noting that out of the box, your new OS has no anti-virus software either and that too is OK.

---

### Post by 3rdalbum on 2009-09-07
> **Irvine_himself said:**
> Thanks again, I have it installed Ubuntu and am using it to make this post :)

Since I am not very confident with IPchains, (or is it IPtables?) I managed to install the Firestarter GUI for the firewall, 

Anyway, my next stupid question is, if I have used the basic set up [illustrated here]("https://help.ubuntu.com/community/Firestarter"), and allow a "permissive by default" outbound policy and no "inbound exceptions" Then I can assume that while on the learning curve I am secure?

Blueridgedog is right: If you have a router with a firewall built-in, then there's not really any reason to run a personal firewall. And Ubuntu doesn't listen to incoming connections on its default install, anyway.

If you want to be sure, then do a google search for "Shields Up" which is an online port scanner that you can use to scan your own machine for open ports.

---

### Post by Irvine_himself on 2009-09-07
Thanks, I have a bizarre free internet connection through a business line, with modem attached, to a local business man friend.

Usually, I am behind a network router, but this is not always the case and there is some doubt about whether the firewall built into the router is working!

Could you recommend a simple, idiot level, tutorial on setting in/out permissions using "FireStarter"

I was aware about the lack of anti-virus and how currently the only real need is as a courtesy to Microsoft users. Though how long that happy state will continue is anybody's guess. I mean, while the percentage of Linux users appears to be a small target, 5% of a very large number is still a large number.

---

### Post by DeMus on 2009-09-07
> **3rdalbum said:**
> 

If you want to be sure, then do a google search for "Shields Up" which is an online port scanner that you can use to scan your own machine for open ports.

Look [_Here_]("https://www.grc.com/x/ne.dll?rh1dkyd2")

---

### Post by winotree on 2009-09-07
> **Irvine_himself said:**
> Thanks, I have a bizarre free internet connection through a business line, with modem attached, to a local business man friend.

Usually, I am behind a network router, but this is not always the case and there is some doubt about whether the firewall built into the router is working!

Could you recommend a simple, idiot level, tutorial on setting in/out permissions using "FireStarter"

I was aware about the lack of anti-virus and how currently the only real need is as a courtesy to Microsoft users. Though how long that happy state will continue is anybody's guess. I mean, while the percentage of Linux users appears to be a small target, 5% of a very large number is still a large number.
I found this [http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php) on-line just now -- but I thought I'd read on these forum that *Firestarter* was no longer being supported, although I've been known to be wrong before.  :?  ;)

---

### Post by Irvine_himself on 2009-09-07
Thanks, I think the Docs should help? 

I not sure about FireStarter not being supported,  I installed it  using the Terminal 

sudo get-app install firestarter

It was so easy, when I played with Fedora a few years ago, I really struggled trying to install apps, even when I could use Yum-Yum!

---

### Post by winotree on 2009-09-07
> **Irvine_himself said:**
> Thanks, I think the Docs should help? 

I not sure about FireStarter not being supported,  I installed it  using the Terminal 

sudo get-app install firestarter

It was so easy, when I played with Fedora a few years ago, I really struggled trying to install apps, even when I could use Yum-Yum!
Yes, I know it's in synaptic.  Perhaps I should have used the words: no longer maintained, and not: no longer supported.  :?   I'm not trying to start any rumors, but I believe that what I stated is correct.  This should not stop you or anyone else from using it.  

Not to dissuade you, but *gufw* [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html) is simple, straightforward and in the repositories, too.  Good luck whatever you choose to use!  ;)

---

### Post by Irvine_himself on 2009-09-07
So if I decided to go for Gufw it would be

sudo get-app install Gufw 

I know, it is probably a very stupid question, but I only have a couple of hours experience with Ubuntu

---

### Post by winotree on 2009-09-07
> **Irvine_himself said:**
> So if I decided to go for Gufw it would be

sudo get-app install Gufw 

I know, it is probably a very stupid question, but I only have a couple of hours experience with Ubuntu
No -- it's **sudo apt-get install gufw **-- it's spelled (all lowercase) gufw in the Synaptic Package Manager (which I prefer using) and Linux is notoriously case-sensitive so keep that in the back of your mind.  ;)

EDIT -- correced comment

---

### Post by Hobgoblin on 2009-09-07
> **Irvine_himself said:**
> 
Could you recommend a simple, idiot level, tutorial on setting in/out permissions using "FireStarter"


There is no need to set anything up with a default install unless you have installed server applications to your system or have some reson to block certain outbound connections.

---

