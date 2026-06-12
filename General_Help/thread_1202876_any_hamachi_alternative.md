---
title: "any hamachi alternative?"
date: 2009-07-02
forum: General Help
---

### Post by tarekeldeeb on 2009-07-02
Hello community ..


I'd like to share my opinion and request more of your expertise about hamachi alternatives.

What's wrong with hamachi:
1- limit to 16 PC in a network (for free accounts)
2- No windows/linux chat interoperability
3- Not open source
4- ID may be lost on OS re-install

I have tried 2 alternatives so far:

A- [remobo]("http://www.remobo.com")
It solves hamachi problems 1&2&4
Remobo problems:
1- It is not that stable .. linux is still in beta!
2- GUI-only tool, cannot be daemonized, always needs sudo to run

B- [wippien]("http://wippien.com")
An early-stage open source project .. seems to solve all hamachi's problems .. It uses Jabber IDs for presence .. it's an VPN-enabled IM client .. cool :lolflag:
Wippien problems:
1- Linux is not yet well supported; only a silly command-line tool to create the network interface, login for presence .. You cannot add/remove users, chat .. no GUI what so ever .. I did not find any pidgin plugin for a good integration! I think it will be great.

I wish we can share our expertise .. for a better connected ubuntu world.

If I have an server with an internet connection (behind a router) .. would openVPN do the trick? maybe with dyndns?

Thanks a lot.
Salam

---

### Post by VeskoJl on 2009-08-08
Recently I've experienced some hamachi issues ([see this]("http://community.logmein.com/logmein/board/message?board.id=HamLinOSX&thread.id=30")) , so started looking for  alternative. I came across this two softs , but lack of linux support gave me up.
So, what's going on if logmein.com change their policy? 
Ubuntu needs alternative!

---

### Post by cesarbrod on 2009-12-05
Any progress here? Hamachi seems to be more and more unstable these days...

---

### Post by othiena on 2009-12-05
will [TINC]("http://tinc-vpn.org/") work?

It is in the repositories.

---

### Post by cesarbrod on 2009-12-05
I am just trying tinc. I am following the instructions in this simple howto: [http://www.linux.com/archive/feature/131343](http://www.linux.com/archive/feature/131343)

I was able to set up a tinc interface both in the server and the laptop. I can ping the new interface only locally -- the server won't ping the laptop or vice-versa. As I am testing inside an existing established network I know connection wise all is Ok. So, I must have somehow missed some point...

---

