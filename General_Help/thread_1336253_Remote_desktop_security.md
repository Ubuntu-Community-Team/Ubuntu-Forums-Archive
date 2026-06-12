---
title: "Remote desktop security"
date: 2009-11-24
forum: General Help
---

### Post by svcta on 2009-11-24
Good day, all, 
     yesterday I was looking at the monitor on my home theatre PC (which is my television) and noticed that "another user was controlling my desktop".   Sure enough someone had gotten control of that computer and was messing with it.  There is nothing but media on it, thankfully.  

I don't know if it was through my wireless network or the internet itself by which he gained access.  I changed all my wireless settings and assigned a much stronger password to my network.  But it occurs to me that the remote desktop feature (by which I control my HTPC via my netbook) is a glaring security loophole.  

Question:  Is there a way to password protect my remote desktop access?

thanks!

---

### Post by Darael on 2009-11-24
I suggest disabling it and using the instructions [here]("http://help.ubuntu.com/community/VNC#accessing-your-pc").  VNC over SSH is extremely secure, and much more so than the default "remote desktop" feature.

---

### Post by XCan on 2009-11-24
> **svcta said:**
> Good day, all, 
     yesterday I was looking at the monitor on my home theatre PC (which is my television) and noticed that "another user was controlling my desktop".   Sure enough someone had gotten control of that computer and was messing with it.  There is nothing but media on it, thankfully.  

I don't know if it was through my wireless network or the internet itself by which he gained access.  I changed all my wireless settings and assigned a much stronger password to my network.  But it occurs to me that the remote desktop feature (by which I control my HTPC via my netbook) is a glaring security loophole.  

Question:  Is there a way to password protect my remote desktop access?

thanks!

In the Remote Desktop Preferences window there is a box called "Require the user to enter this password:", enable that and you'll get your password protection.

You can, however, go even further with relative ease. If the only thing you use remote desktop for is to control your HTPC (inside your network), and you always control it using a fixed set of computers, it should be quite easy to secure VNC. 

1) Lock your wireless router's IP assignment to your computers' MAC addresses, ensuring that they always get the same IP from your router.

2) Configure iptables on the HTPC, perhaps using GUFW to only accept connections from the IPs of your computers.

3) Done.

---

### Post by svcta on 2009-11-24
Cool, thanks for the steer on the remote desktop pref.   

That should be all I need to do to take care of it, I hope.

---

### Post by t0p on 2009-11-24
> **svcta said:**
> Cool, thanks for the steer on the remote desktop pref.   

That should be all I need to do to take care of it, I hope.

If you're going to rely on password protection, at least make sure that you use a *strong* password.

A strong password is one that's long (at least 16 characters, I say), using a combination of letters (both lower and upper case), numbers and "special characters" (like $ and &).

It is relatively simple to crack a password that appears in a dictionary.

---

### Post by DapperMe17 on 2009-11-24
Try the NX trio from NoMachines! 

Fast remote desktop, with SSH & very easy to set up.

---

### Post by XCan on 2009-11-25
> **t0p said:**
> If you're going to rely on password protection, at least make sure that you use a *strong* password.

A strong password is one that's long (at least 16 characters, I say), using a combination of letters (both lower and upper case), numbers and "special characters" (like $ and &).

It is relatively simple to crack a password that appears in a dictionary.

Unfortunately, the protocol seems to only be able to use the first 8 characters unless you manage to hack it.

> **DapperMe17 said:**
> Try the NX trio from NoMachines! 

Fast remote desktop, with SSH & very easy to set up.

FreeNX is nice and all, but I don't think it's considered to be a remote desktop application. More like remote session application. The shadow feature does not seem easy at all to get working, and not too supported.

---

