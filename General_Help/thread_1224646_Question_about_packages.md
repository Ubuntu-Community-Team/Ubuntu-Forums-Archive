---
title: "Question about packages"
date: 2009-07-27
forum: General Help
---

### Post by Jago6060 on 2009-07-27
This post is in relation to a CentOS 5 virtual machine that I'm running.  I know this is an ubuntu forum but the CentOS forum replies are few and far between.

I noticed when I start the virtual machine and watch the services boot, a service called pound fails.  I have a sneaking suspicion that pound failing to start is the reason why I've lost networking capabilities on the virtual machine(correct me if I'm wrong).  So is there a way to(via command line) say "recompile pound then install".  I tried using yum --reinstall but I need internet access, and I looked at rpmbuild but I don't think thats what I'm looking for.  Any ideas?

---

### Post by Jago6060 on 2009-07-30
~Bump~

---

### Post by DaithiF on 2009-07-30
Hi,
which comes first, the chicken or the egg, :)
probably equally likely that pound failing to start is due to networking not being up.  Pound is a load-balancing proxy server, for INCOMING traffic, i wouldn't have thought a failure would affect your ability to communicate OUT.  So my guess would be that your networking isn't working, and the pound failure is a consequence of that.

In any case, it would be helpful to find the reason reported by pound for failing to start -- have a grep in /var/log directory for errors, either pound or network related.

---

### Post by Jago6060 on 2009-07-30
You're absolutely right.  I was having trouble with the VMware server so I switched to workstation.  That fixed the networking and subsequently pound.

---

