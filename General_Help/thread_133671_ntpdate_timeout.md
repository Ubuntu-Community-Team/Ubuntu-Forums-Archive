---
title: "ntpdate timeout"
date: 2006-02-20
forum: General Help
---

### Post by monkblah on 2006-02-20
Hi,

When I boot my ubuntu 5.10 laptop, sometimes it connects to the internet on bootup, sometimes it doesn't, depending on whether its plugged into a network or not, or if there is a wifi connection it can connect to, or if wifi WEP encryption is on, etc.  This is all fine, no problem.

However, when I boot it, if it cannot connect successfully to the internet, the boot process gets hung up on 'ntpdate' for a long time before finally continuing.

I know I can hit Ctrl-C to stop it, and I know I can disable ntpdate. But I don't want to do either of these things. I want ntpdate to work correctly -- that is, try to sync, but timeout in a reasonable time if it can't.

According to the ntpdate man page, its supposed to timeout after 1 second by default. Obviously that's not happening.

I tried adding a '-t 2' to the /etc/defaults/ntpdate file, but it has no effect... ntpdate still just sits there for around a minutes on boot unless interupted.

Why doesn't ntpdate timeout in a reasonable time like it should? How can I get it to do so?

---

### Post by dcstar on 2006-02-20
[QUOTE=monkblah]
.......
Why doesn't ntpdate time-out in a reasonable time like it should? How can I get it to do so?[/QUOTE]
Probably because ntpdate is not waiting for a server, the underlying TCP/IP network is waiting to time out.

If the network was working ntpdate would quite possibly get a response from the system that the request was sent, and then it would start its time-out countdown, without a network ntpdate is probably just waiting for a network acknowledgement and that has its own time-out (as you experience......)

The easiest thing to do would be to disable the initial ntpdate, and set up your system to run it when you login to a session (then it will run in background without interfering with you) by:

System-Preferences-Sessions-Startup Programs

---

### Post by monkblah on 2006-02-21
Hi David thanks for the reply.

Would it be safe to run ntpdate AFTER I login, after I make sure I am connected correctly to the internet? 

Or, if I run it in the background on login as you suggest, will it keep trying to connect & run successfully if I connect to the internet later, some time after logging in?

---

