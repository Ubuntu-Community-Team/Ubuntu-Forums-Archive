---
title: "antivirus on virtual machine??"
date: 2009-10-17
forum: General Help
---

### Post by abhilashm86 on 2009-10-17
i've ubuntu 9.04, i use sun virtualbox and newbie to this, just using virtualbox for VC++ project and adobe products.......

should i install antivirus on virtual host windows?? since the network and others are shared between ubuntu, is there any threat or viruses??

also how is internet now working on windows, if its passing ports of host machine ubuntu and then going through windows, it would be a lifesafer!!

---

### Post by howefield on 2009-10-17
> **abhilashm86 said:**
> should i install antivirus on virtual host windows?? since the network and others are shared between ubuntu, is there any threat or viruses??

also how is internet now working on windows, if its passing ports of host machine ubuntu and then going through windows, it would be a lifesafer!!

Install anti virus, Windows, whether it is a guest or host will need protecting from itself. 

Not completely clear on whether Windows is the guest or host, you have written contradictory statements., so can't answer your second question.

---

### Post by 3rdalbum on 2009-10-17
You should take the precautions in a virtual machine that you would take in a real installation - so yes, if you'd install anti-virus in a real Windows, then you should install it into a virtualised Windows.

Ubuntu is not directly affected by Windows viruses, but it might be a good idea to restrict access to any Samba shares available on your local network or local machine, so any viruses on Windows can't modify files in your shares.

I'm not sure of the specifics behind the sharing of the host network connection with the guest, but I do know that virtualisation software presents a generic "Ethernet" networking device to Windows that piggybacks off your host's network connection, no matter how it is connected.

---

### Post by Sam on 2009-10-17
No need to install an antivirus if you do something like this:

Install your VM, and all the software you need (be careful not to deploy a virus by now), then make a snapshot of the VM state. After that, if you (or a virus) mess something, you can easily rollback to the previous snapshot.

---

### Post by howefield on 2009-10-17
> **Sam said:**
> No need to install an antivirus if you do something like this:

Install your VM, and all the software you need (be careful not to deploy a virus by now), then make a snapshot of the VM state. After that, if you (or a virus) mess something, you can easily rollback to the previous snapshot.

Bad idea, imho.

---

### Post by CharlesA on 2009-10-17
> **howefield said:**
> Bad idea, imho.

This. Snapshots won't replace having an AV.

---

### Post by Sam on 2009-10-17
Different approach, but not as bad you may think... It depends if you store your work on the VM or on the host.

---

### Post by howefield on 2009-10-17
> **Sam said:**
> Different approach, but not as bad you may think... It depends if you store your work on the VM or on the host.

Perhaps you might put all the caveats to your original proposal in your first post, that way, anyone reading will see the plus and the down sides to your idea.

---

