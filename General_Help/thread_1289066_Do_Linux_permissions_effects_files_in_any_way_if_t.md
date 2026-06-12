---
title: "Do Linux permissions effects files in any way if they go to Windows?"
date: 2009-10-12
forum: General Help
---

### Post by Roasted on 2009-10-12
Reason I ask is - Say I have a Samba file server. An XP machine backs up to it. Say the Windows machine crashes and I have to bring all of the data back over.

Does it matter what permissions were on the files on my file server? Would they effect the usage of those files in Windows in any way? Does Windows tack on its own permissions once Windows thereby takes control of the data when it's transferred to the Windows hard drive?

---

### Post by pmlxuser on 2009-10-12
permission matters, but usually doen't cause alot of problems. if you put files on a smaba server and bring them back you don't have problems because the permisions are not set by the server but by the authoring machine be it windows or linux..

the server has got its own set of permission as to who and what program can store files in a certain folder wwho can access them etc..

---

### Post by lavinog on 2009-10-12
What are you using to backup the files from the windows machine?

---

### Post by Roasted on 2009-10-12
> **lavinog said:**
> What are you using to backup the files from the windows machine?

I'm using a program known as Syncback SE. There's 3 variants of it, with the lower end one being the free version. I just simply set up my Ubuntu rig as a Samba file server, which I already had going for my own personal use. I just plopped a 250gb spare SATA drive in I had and hooked up more Samba accounts + Samba shares on that drive. 

Within Syncback, I just set the path to my file server as their directory to synchronize to. Then I just made "My Documents" the source and their share on my file server as the destination. AKA - \\Area51\Jason  - Which on my Ubuntu machine, routes to /media/storage/jason

Check it out, it's a pretty sweet program. It even has a scheduler, so I set it up so each user synchronizes to my computer 10 minutes apart from the next person. 3:00, 3:10, 3:20 AM is when backups hit my PC.

To add to the original topic - that's what I thought. I thought as long as the Windows machine has permission to read the files and copy/paste them to the Windows local drive, then at that point Linux permissions had no involvement in the permissions of the files any longer since they would thereby reside on the Windows machine at that point. But, alas, I wasn't sure - and had to ask. :guitar:

---

