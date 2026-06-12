---
title: "Is this possible with vmware?"
date: 2011-09-26
forum: General Help
---

### Post by hariskar on 2011-09-26
Is it possible if I install vmware to run a windows application that uses MS SQL and Visual basic ++?

Thank you!

---

### Post by collisionystm on 2011-09-26
> **hariskar said:**
> Is it possible if I install vmware to run a windows application that uses MS SQL and Visual basic ++?

Thank you!

VMWare player? Server? 

Yes you can run sql and and visual inside of a virtual environment. 

NOTE: If you are planning on running Server 2008 64 bit, I suggest using VMWARE. Virtualbox is sluggish when it comes to handling this OS and does not seem to handle CPU resources effectively.

You can also try hypervisor if you wish.

---

### Post by hariskar on 2011-09-26
Thank you for reply. I have Ubuntu desktop 11.04 installed and would like to run the windows application I mentioned that uses VC++ and MS SQL.
Which is the best way to achieve it?

---

### Post by collisionystm on 2011-09-26
> **hariskar said:**
> Thank you for reply. I have Ubuntu desktop 11.04 installed and would like to run the windows application I mentioned that uses VC++ and MS SQL.
Which is the best way to achieve it?

You said you want to use VMWARE to run those applications in a windows environment. I am not sure I understand your question. Install vmware to run a virtual windows session. Use WINE to run a windows program within linux itself.

---

### Post by KMKAR on 2011-09-26
I've several VM's in my computer, one of them has:
Visual Studio 2010
MSSQL Server 2008
Oracle XE
PostgreSQL 8.4

And I use it every day of my life. So yes. You can achieve whatever you want through a VM.

---

### Post by hariskar on 2011-09-26
> **collisionystm said:**
> You said you want to use VMWARE to run those applications in a windows environment. I am not sure I understand your question. Install vmware to run a virtual windows session. Use WINE to run a windows program within linux itself.

You are right, I didn't express correctly the question. What I would like to know is, which is the best way to run the program I described in ubuntu. Can I use WINE too? What about the MS SQL and VC++ requirements?
If I use vmware, which version should I use?
Thank you for helping.

---

### Post by collisionystm on 2011-09-26
Well you really only have one choice in Vmware *FREE*, and that is vmware player. Otherwise get a 60 day trial of vmware server. 

Use virtualbox, but like I said, steer away from server 2008 64 bit.
Try hypervisor on your machine and use the virtual machine manager.

---

### Post by KMKAR on 2011-09-26
> **collisionystm said:**
> Well you really only have one choice in Vmware *FREE*, and that is vmware player. Otherwise get a 60 day trial of vmware server.
As far as I know, VMWare Server is free, and VMWare Player too. All other products have trial period.

---

### Post by collisionystm on 2011-09-26
Yeah vmware server is free but is not updated anymore. Atleast, I dont think it is. I am running Sphere ESXi 5 and it is the best ever. I love it.

---

### Post by KMKAR on 2011-09-26
You're right. My mistake!
[QUOTE=Wikipedia]"In January 2010 VMware Server was declared End Of Availability; general support ended on June 30, 2011"[/QUOTE]

---

