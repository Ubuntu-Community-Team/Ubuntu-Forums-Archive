---
title: "Cannot connect to my Ubuntu Server anymore!"
date: 2010-04-04
forum: General Help
---

### Post by ZJ88 on 2010-04-04
I have had my server for quite some time now with a website running, but just recently I cannot connect in any possible way. Even from the server itself.  I've tried the domain name, ip address, and internal address but it always comes up cannot connect to server.  The only thing I can think of is we recently installed nortan security suite on our main computer.  I've checked all the settings however and I didn't find anything wrong.  Does anybody have any idea what may be causing this?  I'm a little tempted to just re-install everything and start from scratch.

---

### Post by Rocket2DMn on 2010-04-04
Is your server physically accessible or is it remote?  You haven't even been able to ping the box?  What OS are you trying to connect from?  If you're running on the box that you installed the security suite on, what happens if you temporarily disable it and then try to connect?

---

### Post by theozzlives on 2010-04-04
Norton don't run on Linux, are you using Linux?

---

### Post by ZJ88 on 2010-04-04
I have physical access to my server.  I can ping it just fine from any computer which is weird.  And the computer that has security suite is just a windows 7 computer but I'm wondering if it's restricting routing or something.  My server is a whole different computer though

---

### Post by itiswhatitis on 2010-04-04
If it started after you installed Norton...

Check your norton security settings, you can disable the firewall for a short period - it  offers you something like 5 min, 15 min, 1 hour, 1 day...

Once you disable the firewall, try again.

There is also a configuration within norton to tell it what your trusted network is - I had trouble accessing my appletv from my windows box until I set all that up.

---

### Post by Jive Turkey on 2010-04-04
You said you cant log in to the server with a monitor and keyboard attached either?  If that's the case you should probably boot with a live cd and do some forensic investigation.  I'm not really an expert on that but the files I would look at first are /var/log/auth, /etc/passwd, and /etc/hosts{.allow|.deny}, and of course /var/log/messages

Also I would double check all of the physical connections, ie monitor, keyboard, mouse.  If you can ping the server but not connect to any service or log in to the os with physical access I would suspect the following in order of likely hood.

1) Software misconfiguration/bug (particularly hosts.deny, or, glurp...Norton)
2) hardware problem (either broken or improper connection)
3) Hax!

Hopefully you're only talking about the free trial version and you haven't yet paid for it.  If you are thinking about buying an av program the best IMHO is NOD32 from Eset.  Lots of people use Norton or MacAfee for the same reason they use windows, it came with thier computer.  Additionally, they don't uninstall cleanly and you can end up breaking your network stack unless you pay either norton or macafee.  Can you say ransomeware kids?

---

### Post by terrrorr on 2010-04-04
Ok.

Here is couple questions for you:

1. Is your server connected directly to router and there is no other computer between your server and ISP

2. Have you tried to ping ie. google.com from your server? Does it reply?

3. Is your server's IP static or dynamic. Is it public or local (ie 192.XXX.XXX.XXX or 172.XXX.XXX.XXX)

It sounds like your main computer acts like a router and your Norton drops all the connections to the server.

---

