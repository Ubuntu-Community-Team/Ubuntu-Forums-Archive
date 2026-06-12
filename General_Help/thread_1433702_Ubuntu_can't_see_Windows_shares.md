---
title: "Ubuntu can't see Windows shares"
date: 2010-03-19
forum: General Help
---

### Post by Jerry N on 2010-03-19
I posted this on the networking forum with no responses but I have now reduced it to the simplest form.  I used a mixed Ubuntu/Windows LAN.  My Dlink DI-524 router died and I replaced it with a DIR-615.  

Now the Ubuntu machines can no longer see the Windows shares or the SMB shares on other Ubuntu machines.  The Windows machines do see the SMB shares on the Ubuntu machines and all machines see the internet.  Further all machines can ping all others.  Obviously I am missing something on the setup of the new router.  Any thoughts?

Jerry

---

### Post by partloer on 2010-03-19
Hi Jerry N,

I wouldn't think that the problem is the new router (usually this is a permission or firewall problem).  It could be a few other possibilities such as: 
1. The new router might assign a new IP address for the Windows machine and if you have the Windows computer mounted by IP address this would cause a problem
2. Also similar if there is a new IP address the firewall settings on the Windows machine might be blocking access

What version of Windows are you running?  Also how do you normally connect to the Windows machine (fstab mount, Connect to Server, manually mount, etc)?

---

### Post by sw40c on 2010-03-19
I had a similar issue a few months back when we switched routers... I had to ping the Windows share - ekg. \\SfaX\Share$ - and re-route mapping to the IP address instead.  Don't ask me why, but it worked...

---

### Post by Jerry N on 2010-03-19
I don't think the problem is the Windows firewall (Zonealarm) because two Ubuntu machines on the network (one wired, the other wireless) don't see each others SMB shares, although one Ubuntu machine can see the shared printer on the other Ubuntu machine.  The Ubuntu machine does not see the shared printer on the Windows machine but the Windows machine sees the shared printer on the Ubuntu machine.  All this worked fine with the DI-524 router.  IP addresses are as assigned by the DHCP server in the router.

Jerry

---

### Post by Jerry N on 2010-03-19
The Windows machines run Win XP SP3 (I haven't checked the new router out with Win 7 yet).  The wireless Ubuntu machine with the shared printer has 9.10 and I have exactly the same problems on the other Ubuntu machine with both 9.04 and 10.04.  I normally connect to the Windows server with "Connect to Server".  

What is ekg?

---

### Post by partloer on 2010-03-22
When using "Connect to Server" what do you enter in the fields?

---

### Post by Jerry N on 2010-03-22
> **partloer said:**
> When using "Connect to Server" what do you enter in the fields?

I tried both the computer name and the IP address without success several times over a period of a couple of days.  Interestingly enough though, I just now tried it again and while it still rejects the computer name it actually accepted the IP address.  Now I need to have another look at the router configuration to figure out why it can't resolve the computer name.  This was never a problem on the old router.  I could, of course, define static IPs.  [COLOR="Red"]Thanks for goading me into checking it again![/COLOR]

BTW, I set the service type to "Windows share".

Jerry

---

