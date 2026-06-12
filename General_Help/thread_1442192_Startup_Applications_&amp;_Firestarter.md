---
title: "Startup Applications &amp; Firestarter"
date: 2010-03-29
forum: General Help
---

### Post by dowtish on 2010-03-29
Hi

I'm trying to make Firestarter launch as a startup application but it tells me that I need root privileges when logging in with my one and only account!

Can this be achieved without giving this account to much privileges?

Laymen terms peeps I'm a Linux Newbie!

Many thanks

---

### Post by marshmallow1304 on 2010-03-29
Why does Firestarter need to be a startup application?  It's just a "configurator"; it doesn't have to be running all the time.

---

### Post by Helkaluin on 2010-03-29
May I ask why do you want Firestarter as a startup app? For one it's just a graphical frontend of the kernal-built-in firewall (ufw for Ubuntu, I believe). You don't need Firestarter to be running to have a functioning firewall. See: <http://ubuntuforums.org/showthread.php?t=510812> Scroll to firewall section.

And of course I could also bombard you with the alleged better alternative gufw due to the reason that Firestarter is supposedly being phased out in favour of gufw so far as Ubuntu support is concerned. (Someone correct me if I'm wrong.)

And if after all for some reason you still want to run Firestarter at startup with root privileges, try: <https://help.ubuntu.com/community/RcLocalHowto> and post #3 in: <http://ubuntuforums.org/showthread.php?t=1033077>

EDIT: Firestarter doesn't configure your ufw, but your iptables. Nonetheless, you still don't need to run it in background for the firewall to work.

---

### Post by dowtish on 2010-03-29
> **marshmallow1304 said:**
> Why does Firestarter need to be a startup application?  It's just a "configurator"; it doesn't have to be running all the time.

When I was using it was showing that it had blocked traffic but I have not configured anything!

So from the way you have replied I can assume that you have to configure it to block traffic?

I don't think I'm cut out for Linux! lol

---

### Post by sisco311 on 2010-03-29
> **dowtish said:**
> When I was using it was showing that it had blocked traffic but I have not configured anything!

So from the way you have replied I can assume that you have to configure it to block traffic?

I don't think I'm cut out for Linux! lol

If you don't run any server software and/or you use a hardware firewall (i.e. router), then a software firewall is redundant.

Check out this: [thread=510812]Ubuntu Security[/thread].

---

### Post by dowtish on 2010-03-29
[QUOTE=EDIT: Firestarter doesn't configure your ufw, but your iptables. Nonetheless, you still don't need to run it in background for the firewall to work.[/QUOTE]

So could you configure Firestarter to run something like how peerblock does in windows?

---

### Post by Helkaluin on 2010-03-30
I suppose yes. Heck, that's the basic principle of many personal software firewalls anyway: restrictions on network traffic based on source and destination IPs and ports.

But it remains that you don't need to be running Firestarter (or gufw, or that regard) for the firewall to function in Linux - they are just graphical frontends for iptables and ufw respectively, which are more or less always 'running' anyway once you've configured them using the graphical frontends. (ufw is, in turn, frontend of iptables.) (They aren't really 'running' in the sense of a userspace application - the ultimate backend of iptables is inherently builtin in the networking functionality...)

It is therefore possible to not install those Firestarter and gufw at all but type in configuration into iptables... But someone has written a nice and easy GUI so why the hell not.

---

### Post by dowtish on 2010-03-30
Cheers People!

---

