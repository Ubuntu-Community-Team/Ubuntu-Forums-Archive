---
title: "Lightening storm/server out"
date: 2009-09-17
forum: General Help
---

### Post by mfrag on 2009-09-17
This has nothing to do with Ubuntu but everyone here is generally so helpful and knowledgeable, so I hope I can ask this.  

Question:  A server running Fedora at school went down today possibly related to a lightening storm.  I logged in to the server as I had physical access and all my files were there and the machine seemed like it was running fine.  I figured there was a router or something else that had went down that was causing the problem.  The IT folks checked all routers, switches, cords, etc. and found nothing wrong by testing all network connections with a laptop.  They seem to think the network settings were somehow erased on the server and simply just need to be reset.  Unfortunately it was late today when we got help and no one helping us had root access. 

Does this make sense?  I don't see these settings getting reset myself.  But I know little of such things.  I'll be looking at the machine tomorrow with someone who has root access.

Just looking for some input on what might be wrong.  Perhaps a port on the sever itself went bad?  First thing we will check will be the current network settings. 

Thanks in advance for any input.

mfrag

---

### Post by hwttdz on 2009-09-17
You can try loggin in with ssh -v and see what sort of output you get from there, it might give you a clue (I'm just shooting in the dark).

---

### Post by Cmndr Hippofiralkus on 2009-09-17
Same problem occured recently on a Bloxx server (Which uses a variant of the RedHat linux system). The same problem occured in that the system refused to accept ANY incoming connections and outgoing had failed. The problem was eventually traced to a cable that had become live in the wrong parts and caused a surge.
The solution was surprisingly macabre, reboot the dhcp using super user privileges. Don't know how or why but all traffic was restored miraculously, even after the server had been repeatedly rebooted and cabling, routers and switches transferred to backup units. Ranks among one of my many 'Marie Celeste' moments.

MORAL:Expect the Strange!

---

### Post by mfrag on 2009-09-17
Certainly a 'Marie Celeste' (or is it Mary?) moment for us.  A root user logged in and found that all network settings were correct.  A simple 'ifup eth0' got things up and running again.  I would have thought a reboot would have initiated this, but apparently not.

One more thing: before the storm one could run the command 'ps' and get reasonable output whereas now we are getting a segmentation fault?

Any ideas?  Otherwise, so far, things seem in order.

I think we might be reinstalling soon...

---

