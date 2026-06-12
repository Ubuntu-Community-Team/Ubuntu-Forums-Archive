---
title: "SSH over only one interface?"
date: 2009-10-21
forum: General Help
---

### Post by GandalphCerebrum on 2009-10-21
Hey, so,  I am trying to set up my ubuntu desktop as a firewall between my small network and a campus network, and I use ssh heavily to administer the machines on the inside of the network, because they are headless.

So I want to know, how can I be sure that the ssh traffic only goes into the network and not out into the campus?

---

### Post by Lars Noodén on 2009-10-21
One way is to configure tcpd to help with that:

/etc/hosts.allow:
sshd: 192.168.0.0/16

/etc/hosts.deny:
sshd: ALL

Are you going to allow SSH in to your ubuntu desktop-firewall from the outside?

---

### Post by GandalphCerebrum on 2009-10-21
That's the plan, I still want to be able to get into my desktop remotely, but it's fine if I can't get through the desktop and into the machines inside the network remotely. They're just doing some grid computing and won't be needing much administering anyway.

---

### Post by Lars Noodén on 2009-10-21
Ok.  Using tcpd like above should do the trick, just be sure to make the whitelist as narrow as possible.  You may even list individual ip numbers.

There are, AFAIK, two ways past it.  One is using your firewall as a stepping stone.  That requires a log-in there.  The other is using a reverse tunnel from the inside machines.  That requires being logged in already on the inside somehow at least once.

---

### Post by GandalphCerebrum on 2009-10-21
Thanks for the tip, I'll try it out once I get everything together!

---

### Post by Lars Noodén on 2009-10-22
Just an afterthought:

Be sure remote login for root is disabled in sshd_config.  You can do what you need to via sudo or via a single-purpose account plus sudo.

---

