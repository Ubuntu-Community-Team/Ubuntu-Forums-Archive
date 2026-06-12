---
title: "Virtualbox dns server?"
date: 2009-12-12
forum: General Help
---

### Post by pwhipped on 2009-12-12
I have two questions really. I have Ubuntu 9.10 as my base installation. I run virtualbox with three different host distros (often not concurrently). Is it possible to run rhel as a local dns server virtually with virtualbox? My second question is regarding dynaDNS. Is it possible to run a external (ie: Internet resolving) webserver virtually (through virtualbox, not vmware)? Thanks for your help ahead of time.

---

### Post by pwhipped on 2009-12-12
bump

---

### Post by dcstar on 2009-12-12
> **pwhipped said:**
> I have two questions really. I have Ubuntu 9.10 as my base installation. I run virtualbox with three different host distros (often not concurrently). Is it possible to run rhel as a local dns server virtually with virtualbox? My second question is regarding dynaDNS. Is it possible to run a external (ie: Internet resolving) webserver virtually (through virtualbox, not vmware)? Thanks for your help ahead of time.

Firstly, VM questions should be in the Virtualization forum, secondly any service that can run in a host can run in a VM.

As well, it is extremely inefficient running services that could be in the host in a VM unless there is a very good reason for doing so.

---

### Post by pwhipped on 2009-12-12
I was not aware of the vitalization sub forum. I figured running a local dns/webserver wouldn't be too intensive. I won't be getting hardly any volume. Setting up a local dns server is more of an exercise than a permanent solution. Thanks for the reply. :)

---

### Post by lmarmisa on 2009-12-12
The virtual machines of VirtualBox are really virtual computers. But one remark: you will have some limitations in the communication with other VM  (and computers of your LAN) if you use the NAT mode in the network interfaces. So, I recommend strongly to change to bridge mode. This is very important. Defining the network interface in this way, every VM within your PC is 100% equivalent to an independent physical computer connected to your LAN.

Now the answers to your questions are easier:

1) Yes, of course.

2) Frankly speaking, I don't understand your question. My answer is generic: if that is possible with a physical computer, then it is also possible with a VM and VirtualBox.

Best regards,

Luis

---

