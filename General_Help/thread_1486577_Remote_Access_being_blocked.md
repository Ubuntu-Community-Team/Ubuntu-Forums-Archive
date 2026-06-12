---
title: "Remote Access being blocked"
date: 2010-05-18
forum: General Help
---

### Post by djuniah on 2010-05-18
I can't seem to remotely SSH or VNC into my machine.  If i'm on the LAN and try accessing via LAN IP, it works fine.  If i go in through a remote address (my dyndns) or even my home IP, i can't connect (yes, all of the ports are forwarded, i've triple checked this multiple times).  Interestingly enough, port 80 works just fine.  It would seem as though some sort of firewall is blocking me.  I've done this plenty of times before with various machines, and this has me quite perplexed.  Any idea why this is happening?

---

### Post by Peter09 on 2010-05-18
For more information use the -v switch 
 
> **-v**      Verbose mode.  Causes **ssh** to print debugging messages about its
             progress.  This is helpful in debugging connection,
             authentication, and configuration problems.  Multiple **-v** options
             increase the verbosity.  The maximum is 3.

this might help you get more information on the cause.

---

### Post by djuniah on 2010-05-18
The error i'm getting is "Connection Refused".

---

### Post by Peter09 on 2010-05-18
If this is at the target host then check in the log files for more information. I suspect somewhere you are set up only to allow local access.

---

### Post by djuniah on 2010-05-19
I tried looking at the logs last night and it showed nothing.  No connection attempts (i was looking in /var/log/auth.log).  I triple checked again that i had the ports forwarded and even added the machine to the DMZ for a little while just to be sure.  I checked my ssh_config and everything there seems pretty standard.  I really doubt that its related to anything that is specific to SSH since neither SSH nor VNC work.  I tried completely disabling ufw as well and that didnt help either.  I looked at the hosts file and that seemed normal as well.  Another reason that i'm not blaming the router is that i have port 80 forwarded to the machine and i can see the default apache page remotely, so the connections definitely can get through to it. Any other suggestions?

---

### Post by Peter09 on 2010-05-19
Can you look at your router logs to see if you are actually getting to your router - perhaps your ISP is blocking that port or perhaps you are coming in on a different port.

---

### Post by djuniah on 2010-05-20
well i know that i'm coming in on the right ports, its definitely trying to connect on 22, 5900, 5920, and 5925.  (I have multiple ports in the 5900s for a couple different VNC sessions, some persistent and some that log out when you close the connection)

I'm running DD-WRT on my router, but sadly its a micro version and its logging isnt too robust or accessible.  Anything else i can try?

EDIT:
If it matters, here's the guide i followed:
[http://ubuntuforums.org/newreply.php?do=newreply&p=9244160](http://ubuntuforums.org/newreply.php?do=newreply&p=9244160)
I did everything except for the "/etc/X11/xserver/SecurityPolicy" part
That also works fine on LAN, but not when i try remotely.  I find it odd that my ISP would be blocking ALL of those ports, so i really doubt it.  It's Comcast by the way.

---

### Post by Peter09 on 2010-05-20
Well my guess is
 
- you can connect through your LAN
- you cannot see connection attempts at your target machine from the Internet in the Logs
- you see a simple connection refused message
 
All seems to point to routing in someway.
 
Where are you trying to get a connection from when you try the internet? Could it be that that site is blocking ssh.

---

### Post by djuniah on 2010-05-20
Ok, i seem to have solved the problem.  The software firewall on the machine that i was testing from seems to have gone a little crazy.  I had checked to make sure that it had no rules against the software and ports that i was using, but when i disabled it, everything started working.  Seems like some sort of bug popped up in it and it went into a pseudo lockdown mode that still allowed my other apps through so i hadn't noticed it. (and of course it never notified me of any of this).

Sorry for wasting your time like that.  At one point i had tried using multiple machines and got results similar to what i was getting, so i never even looked at my test machine as being the issue.

---

### Post by Peter09 on 2010-05-20
We have all been there - and I'm sure most of us will be there again :)

---

### Post by 3rdalbum on 2010-05-20
> **djuniah said:**
> Ok, i seem to have solved the problem.  The software firewall on the machine that i was testing from seems to have gone a little crazy.

I'll guess: Firestarter?

Try using gUFW instead. Or, if that computer is permanently behind your router's firewall, then don't bother with a software firewall.

---

