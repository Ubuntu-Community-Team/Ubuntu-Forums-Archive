---
title: "Application settings in /tmp?"
date: 2009-11-16
forum: General Help
---

### Post by detroit/zero on 2009-11-16
Once in a while, I go in to /tmp and clear out all the collected bits & pieces that have gathered over time. Just today, I went in there and there was **tons** of folders and files that, from what I could tell at the time, were not really needed. I guess I was wrong.

Now, ever time I start Firefox, I get this error:```
An error occurred while loading or saving configuration information for firefox. Some of your configuration settings may not work properly.
```Expanding on the details button gives this info:```
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
```This error isn't limited to Firefox. Thunderbird also shows the error, and Terminator terminal emulator shows it as well. I can no longer launch a regular gnome-terminal from the applications>accessories menu. I imagine there's going to be a few more apps that throw the error when I get around to checking everything.
So, a couple questions:

[LIST=1]
[*]Why are *any* application settings being stored in /tmp of all places?
[*]If not application-specific settings, why is gconf storing settings in /tmp?
[*]Why does Firefox want NFS or tcp/ip access to load settings? Is it trying to load via NFS access to loopback or something? Why the hell is it doing it that way?
[*]What is ORBit?
[*]Why is ORBit handling my application settings?
[*]Why does ORBit think it needs NFS or tcp/ip access to load application settings?
[*]What is all this crap that being saved up inside dozens of folders inside /tmp? What's safe to delete and what must be kept?
[/LIST]
As far as I can tell, Firefox and TBird still work normally, despite what the error says. As I've noted, I lost the ability to use gnome-terminal. 

The documentation cited in the error message is everything but helpful, as far as I can see. The only thing I find in bugtracker [is this]("https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/426412"), which definitely seems related and even says it's been fixed, but it would seem to me that it hasn't.

How can I return my system to a state of normality?

EDIT: Using Karmic, of course, with all current updates.

---

### Post by Giblet5 on 2009-11-16
Reboot into recovery mode shell.

Execute rm -fr /tmp/* (Double check your spelling on that BEFORE you hit Enter).

Exit and continue a normal boot.


/tmp is used to temporarily store all kinds of things that apps need during operation.

Removing those files while the apps are running is kind of like cutting off a chickens head: it will continue to run for a bit but you can tell something is wrong right away.


ORBit is a CORBA framework that a lot of Linux apps use.

It doesn't use or expect NFS by default, but it can use it if you have it. It can do a lot of things that you might not have configured, but it has to check before it knows you haven't configured them.

---

### Post by detroit/zero on 2009-11-16
That did the trick. Thanks.

I had a feeling that the solution would be something along those lines, I just wanted to be sure before I went ahead with something like that.

---

### Post by Giblet5 on 2009-11-16
Yeah, cleaning up /tmp is something the system does on bootup. That's a good thing cuz any app that crashes may not have the sense to remove its /tmp files.

I'll wager that your terminal session died because you removed its named pipes from /tmp. That does interesting things every time!

---

