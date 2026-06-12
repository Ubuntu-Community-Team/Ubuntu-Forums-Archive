---
title: "Slow SSH, suggested solution not working"
date: 2011-01-22
forum: General Help
---

### Post by Dave M G on 2011-01-22
Ubuntu Forum,

I have a three computer network, with two Ubuntu machines, and one Mythbuntu machine. I often run programs from one computer on another by connecting via SSH. For years this ran perfectly, and running an application from another computer on my LAN ran as smoothly as if I was running the program from the same machine I was in front of.

About two weeks ago, programs I ran over SSH seemed incredibly slow. If I clicked in an interface, it would take forever to respond. As I write this now, testing using Amarok, it takes about four seconds for a click to register.

Another symptom of this issue is that if I reboot all the machines, the problem is reduced. I get better response times. However, after some amount of time, I don't know how long, the problem comes back and gradually gets worse.

I searched the forums and the web in general for an answer, and found that others had reported similar issues.

In all cases, they reported that the solution was to edit the file /etc/ssh/sshd_config and add the line "UseDNS no" to the botton.

While this fix seems to have worked for everyone else, it has not helped my situation. I have made that edit on all of my machines, but they are all still slow.

A further note: Whatever the problem is, it seems universal to all the machines on my network. Regardless of which machine I connect to and which machine I connect from, the problem of slowness is the same, with the same behaviour.

I think it's most likely that since I set all my computers and their network up, that I have set, or not set, some feature on each of them.

This is extremely aggravating, and I'm really hoping someone can help me fix this problem.

Thank you for any advice.

---

### Post by Dave M G on 2011-01-23
This appears to have been a router problem.

Rebooting the router solved the issue.

---

### Post by ubudog on 2011-01-23
> **Dave M G said:**
> This appears to have been a router problem.

Rebooting the router solved the issue.

Lol, that happens.   :p

---

### Post by Dave M G on 2011-01-23
I went through hell and back before I figured it out, too. :oops:

As embarrassing as it is to admit, though, you gotta post your solutions, or the next guy might not think to reboot his/her router.

---

### Post by ubudog on 2011-01-23
> **Dave M G said:**
> I went through hell and back before I figured it out, too. :oops:

As embarrassing as it is to admit, though, you gotta post your solutions, or the next guy might not think to reboot his/her router.

Yeah, I agree.  Stuff like that happens to all of us.  :)

---

