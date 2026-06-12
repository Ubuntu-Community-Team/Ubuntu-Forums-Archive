---
title: "Cn anybody help me with Samba an NFS?"
date: 2012-05-23
forum: General Help
---

### Post by the lemming on 2012-05-23
Hello

I have a small home network and everything can communicate with everything including my small iomega NAS device.  At the moment I can get my Windows PCs and my Android tablet and phone to see and communicate with each other.

My problem is that I have never been able to get any Linux Distro to see or connect to my network.

The Linux Distro only ever sees a windows workgroup but can't even mount that.

Any ideas would be vey much appreciated.

---

### Post by scottbomb on 2012-05-23
Not sure if I'll have the answer but I'm curious:

Can the Linux box connect to the internet? Can the other computer see your Linux box? Have you installed Samba? Which version of Ubuntu are you using? It may also be helpful to post the output of cfconfig.

---

### Post by tumutanzi.com on 2012-05-23
If you just want to sync your files between different devices, I recommend dropbox, since it support Lan synchronizing that is also super fast.

---

### Post by the lemming on 2012-05-24
> **scottbomb said:**
> Not sure if I'll have the answer but I'm curious:

Can the Linux box connect to the internet? Can the other computer see your Linux box? Have you installed Samba? Which version of Ubuntu are you using? It may also be helpful to post the output of cfconfig.

The Ubuntu 12-04 could connect to the internet and I did have Samba installed.

I did not check my other computers to see if they could find the Linux compute.  And, even though I did not know what or how it worked, I was able to ping my NAS box and get a 100% reply but I could not see it on my network.  I could only see the Windows Workgroup but I could not mount the location.

At the moment Ubuntu has been scrubbed from the laptop however if you have anything that may help then I will of course put Ubuntu back on as I do like the look of Unity.

Cheers

---

### Post by the lemming on 2012-05-29
> **the lemming said:**
> Hello

I have a small home network and everything can communicate with everything including my small iomega NAS device.  


Desperate Bump.

Please help.

---

### Post by Aries68 on 2012-06-03
Do you have them all set to the same workgroup name?

---

### Post by the lemming on 2012-06-03
> **Aries68 said:**
> Do you have them all set to the same workgroup name?



Thicko question

I really would appreciate advice on how to connect to the same work group.

However I am confused about the work group idea.  When my Windows box is turned off, should this really affect a NAS box which uses a flavour of Linux to work it?

I genuinely am confused and really need help.

Cheers

---

### Post by steeldriver on 2012-06-03
> **the lemming said:**
> Thicko question

I really would appreciate advice on how to connect to the same work group.

However I am confused about the work group idea.  When my Windows box is turned off, should this really affect a NAS box which uses a flavour of Linux to work it?

I genuinely am confused and really need help.

Cheers

if the nas is exporting shares via samba / smb / cifs then even if it's Linux under the hood it's essentially pretending to be a windows box in that respect - there will be something in the nas setup where you can tell it what workgroup name to use - on my netgear nas it's on the same panel as where the hostname is set, don't know exactly where it would be on your iogear

for nfs exports the workgroup doesn't mean anything afaik

obviously you can export the same shares as both cifs and nfs (and possibly afp) - Windows clients will connect via smb while Linux clients can connect via either smb or nfs (or both)

---

### Post by Jose Catre-Vandis on 2012-06-03
In Tutorials and Tips, two of the best howtos for straight forward connectivity

SAMBA
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

NFS
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

