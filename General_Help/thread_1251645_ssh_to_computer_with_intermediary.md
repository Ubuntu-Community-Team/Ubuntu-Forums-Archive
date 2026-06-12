---
title: "ssh to computer with intermediary"
date: 2009-08-27
forum: General Help
---

### Post by Mykle87 on 2009-08-27
Ultimately, I am trying to use a network resource on computer C but I cannot directly connect to it. I have to connect from A to B to C. I have ssh access from A to B and from B to C. I will use this tunnel as a proxy setting for the network program. What command should I use to setup a dynamic tunnel straight from my computer (A) to C? Thanks.

---

### Post by hwttdz on 2009-08-28
ssh -t userb@machineb 'ssh userc@machinec'

I had never really thought of that, I always just ssh'd twice.  Interestingly when you close out the inner it closes out both.

---

### Post by Mykle87 on 2009-08-28
Do I have to setup a dyanmic tunnel with -D so I can point the program to a proxy?

---

### Post by hwttdz on 2009-08-28
Yeah, I guess so, I had never looked at setting up a tunnel.  You would have to do -D at each step. 

ssh -t -D port userb@machineb 'ssh -D port userc@machinec'

I'm assuming to set it up in two steps you do?

ssh -D port userb@machineb
ssh -D port userc@machinec

---

### Post by Mykle87 on 2009-08-28
I hope it is that easy. I'll give it a shot thanks.

---

### Post by SoftwareExplorer on 2009-08-29
You could also make computer B trust computer A based on encryption keys and do the same for B to C. That way you wouldn't have to put in any passwords. From computer a you would run from computer A ```
ssh-keygen -t rsa
``` and then ```
cat ~/.ssh/id_rsa.pub | ssh user@ComputerB 'cat - >> ~/.ssh/authorized_keys2'
``` and then ```
ssh user@ComputerB 'chmod 600 ~/.ssh/authorized_keys2'
``` Then do the same on computer B, but change the commands to Computer C wherever it uses computer B.

---

### Post by SoftwareExplorer on 2009-08-29
[COLOR="Silver"]Oops, double post, sorry![/COLOR]

Since I accidentally double posted, I'll actually try to make this post helpful.
When you do the ssh-keygen, it will ask you if you want to make a pasphrase. If you do set one, it will ask you for that password before connecting. The flip side is that it protects the computers identity from being used if the computer is stolen. So you may want to set one on computer a, but you might not want to on computer b.

---

### Post by Mykle87 on 2009-08-30
Thanks for the advice software. Unfortunately, I do not really have permission to give a key to computer B as it is a University server. What I am trying to do is get a dormitory IP address on the campus but first I need to connect to the university from off campus. I can do this either with ssh or vpn. I used my friends account and got him banned so I may not be able to follow through with this plan.

---

### Post by hwttdz on 2009-08-30
The key goes in your home directory, so there's no permissions issue there.

---

### Post by jerome1232 on 2009-08-30
So apparently this University doesn't want you to use their server as a proxy.

> I used my friends account and got him banned so I may not be able to follow through with this plan.

---

