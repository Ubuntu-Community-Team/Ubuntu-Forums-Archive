---
title: "how does the security work on Ubuntu?"
date: 2011-03-10
forum: General Help
---

### Post by Alexnadra on 2011-03-10
hey 

I just wonder how does the security work over here

I got no anti-virus no firewall no thing

and I use Linux mint 24h/7 

I got some important stuffs in my system I'm so a fried to lose them or someone hacking me 

so please explain to me I'm I running save system here?

sorry for my newbies question and ty

---

### Post by flipper T on 2011-03-10
read this thread, it addressed my concerns and may address yours

[http://ubuntuforums.org/showthread.php?t=1698650](http://ubuntuforums.org/showthread.php?t=1698650)

---

### Post by lithopsian on 2011-03-10
You should get some interesting answers.  Hopefully more intelligent than the "Linux can't get viruses" type :)

Linux can get viruses, trojans, and just about anything else that Windows can get but they are quite rare because it isn't worth the trouble of writing them just for a few Linux machines.  The ones that are written tend to be specialised and going after commercial targets.  Anti-virus software isn't all that clever about spotting and stopping viruses anyway and most troublesome viruses are written to disable toe AV.  The last thing is that most viruses and trojans are installed by people doing stupid things like running email attachments or unsafe applets in their browsers.

Linux does have a firewall although by default you won't be using many features of it.  In many ways Linux itself is the firewall.  You also probably have a router with many firewall features and should consider checking its configuration.  If you plan to run Linux as a standard desktop then it will be fairly impervious to attacks from outside, except perhaps through browser vulnerabilities so keep your browser up to date.  If you enable features such as packet routing or ssh then you will have to be much more careful about security.

One of the major security features of Linux is that you the user don't have permission to do anything.  That's why many commands keep asking you for your password, and you have to type sudo in front of things.  Of course if an attacker gets your password then they can do anything too, but most drive-by attacks won't be able to do anything much.  If an attack broke in as root you would be in trouble, but root shouldn't even be enabled on your machine so that can't happen.

One vulnerability that many people don't think about is the router itself, usually in wireless mode.  Make sure you are using the most recent encryption type possible for your system with a strong password.  Don't use wireless at all unless you need to, you can turn it off on most routers.

---

