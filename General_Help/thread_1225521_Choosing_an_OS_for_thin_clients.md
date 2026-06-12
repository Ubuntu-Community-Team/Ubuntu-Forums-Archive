---
title: "Choosing an OS for thin clients"
date: 2009-07-28
forum: General Help
---

### Post by Jago6060 on 2009-07-28
Hi all!  Just wanted to get some opinions from the Ubuntu Community.  My office is looking to setup all employees on thin clients eventually, so right now we're just getting into the planning stage.  Does anyone have an opinion for the best Linux variant to use for thin clients(both client and server)?

Currently I'm pretty well versed in Ubuntu, CentOS 5, and Slackware 10

---

### Post by RJ12 on 2009-07-28
Wow we have the same Avatar :rolleyes::lolflag:
I would say Ubuntu its very Stable even the 9.04 release is stable for me. So that is just my prediction or answer and is very customisable.

---

### Post by Jago6060 on 2009-07-28
Haha that's pretty funny.  A guy that I work with is a "Windows Guy" so I take every opportunity to prove to him Linux is better, so I thought a Vista style Ubuntu case would show him the way :-P

Thanks for the input!

---

### Post by t4thfavor on 2009-07-28
Check out the ltsp package for ubuntu, make sure your thin clients have at least 128mb of ram, and boot them direct off the network.

I had a few older machines booting that way, and they were screamin fast. Best thing is it only takes a mildly fast server to get great performance.

I think the recommended specs are a dual(core) CPU, 2GB of ram (for the first 10 clients), and 50MB more ram for each additional client after 10. Im not sure what the recommended hdd size is, but I would assume you know your space requirements.

---

### Post by Jago6060 on 2009-07-29
> **t4thfavor said:**
> Check out the ltsp package for ubuntu, make sure your thin clients have at least 128mb of ram, and boot them direct off the network.

I had a few older machines booting that way, and they were screamin fast. Best thing is it only takes a mildly fast server to get great performance.

I think the recommended specs are a dual(core) CPU, 2GB of ram (for the first 10 clients), and 50MB more ram for each additional client after 10. Im not sure what the recommended hdd size is, but I would assume you know your space requirements.

Thanks for the suggestion!  At the moment, I'm petitioning for a new server.  Right now we're running a server with an Intel Xeon 3.2, 2GB RAM, and a 300GB hdd, so it's not really capable of handling everything we're doing now AND thin clients.

---

### Post by shel-hall on 2009-07-29
> **Jago6060 said:**
> Thanks for the suggestion!  At the moment, I'm petitioning for a new server.  Right now we're running a server with an Intel Xeon 3.2, 2GB RAM, and a 300GB hdd, so it's not really capable of handling everything we're doing now AND thin clients.
I'd suggest having several servers, in fact.  You don't need to put everything on the same machine.

You will want a complete hot-spare LTSP (or whatever) server, too.  Having a single point of failure whose loss will bring down the whole office is not a good plan.

-Shel

---

### Post by Jago6060 on 2009-07-29
I definitely agree with you.  Both myself and the IT director feel that the setup is *** backwards, but the head boss thinks everything is fine.  We have a Dell 2003 Server also but it randomly reboots every few days.  Just experiences a stop error and down it goes.

---

