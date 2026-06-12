---
title: "AntiVirus"
date: 2010-03-11
forum: General Help
---

### Post by FahadMKS on 2010-03-11
I have a valid McAfee account, I am using the Ubuntu OS on my computer.
 
Can i get that McAfee installed on my Ubuntu as Avast and some other AntiVirus seems to be working?

---

### Post by FahadMKS on 2010-03-11
I think I cannot, but all your opinions wil be help ful

---

### Post by bumanie on 2010-03-11
I don't think McAfee has a linux version - really if you want an anti-virus, clamav is probably as god as any of the commercial varieties. Anti-virus is not necessary for most linux users, unless they are sharing files with windows or running lots of things in wine, but again, clamav is more than sufficient. Read [this for more information]("http://linuxmafia.com/~rick/faq/index.php?page=virus") - it describes why linux is resistant to viruses as long a due care is taken by the administrator of the system.

---

### Post by Ferb on 2010-03-11
I agree with bumanie. The only reason why I have a virus program on my ubuntu box is to make sure I don't send viruses along to my Microsoft friends.

---

### Post by HermanAB on 2010-03-11
Howdy, 

you can use ClamAV and SpamAssassin to get rid of junk in your email, but you need not worry about it.

---

### Post by BiggoCharley on 2010-03-11
I'm running XP on a virtual machine (sun VirtualBox) hosted by Ubuntu 9.04.
Is there any point on installing and running Norton 360 on this virtual machine-- or possibly running clamAv or clamtk instead on the host?

---

### Post by uRock on 2010-03-11
> **BiggoCharley said:**
> I'm running XP on a virtual machine (sun VirtualBox) hosted by Ubuntu 9.04.
Is there any point on installing and running Norton 360 on this virtual machine-- or possibly running clamAv or clamtk instead on the host?

You will want an AV running in the VBox to protect the Windows install. Norton is a resource hog, but if that is what you have, then be sure to give it enough RAM to run it.

---

### Post by FahadMKS on 2010-03-11
Hi thank you guys

---

### Post by dcstar on 2010-03-11
> **BiggoCharley said:**
> 
Is there any point on installing and running Norton 360 on this virtual machine-- or possibly running clamAv or clamtk instead on the host?

No point whatsoever. Hosts and VMs are totally separate.

---

### Post by BiggoCharley on 2010-03-12
> **dcstar said:**
> No point whatsoever. Hosts and VMs are totally separate.


Thanks David.  I really was wondering if the VM (in this case Windows XP) would be as susceptible to a virus as Windows would be on its own partition.
I think you answered that.
Thanks again
Charley

---

### Post by uRock on 2010-03-12
> **BiggoCharley said:**
> Thanks David.  I really was wondering if the VM (in this case Windows XP) would be as susceptible to a virus as Windows would be on its own partition.
I think you answered that.
Thanks again
Charley

It is still susceptible. He meant there is no reason to install ClamAV if you are already using and AV within the Windows VM.

---

