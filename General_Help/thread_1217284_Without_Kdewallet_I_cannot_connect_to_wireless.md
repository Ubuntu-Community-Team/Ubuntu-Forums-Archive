---
title: "Without Kdewallet I cannot connect to wireless"
date: 2009-07-19
forum: General Help
---

### Post by creedog on 2009-07-19
So i picked up an EeePC the other day and loaded 9.04 Kubuntu on in. I have never cared for kdewallet so I have never used it, and have never had any issues. Well, I cannot connect to my wireless connection if the wallet subsystem is disabled. Its very annoying. I just keep getting prompted for my wpa passfrase.... if I turn on the wallet, and attempt to connect again, I am prompted for the wallet password and everything works great. 

I do not have to disable the wallet, I just want to be able to auto connect without a password or a passphrase. Never had this issue before.

---

### Post by Chris Musampa on 2009-07-19
Install WICD.

---

### Post by creedog on 2009-07-19
Looks interesting, and I will give it a try.

Question for you, why are you sugguesting this as a work around? Can this issue with kwallet not be fixed.Is there some sort of bug with kde4 network manager.

---

### Post by Chris Musampa on 2009-07-19
> **creedog said:**
> Looks interesting, and I will give it a try.

Question for you, why are you sugguesting this as a work around? Can this issue with kwallet not be fixed.Is there some sort of bug with kde4 network manager.

Yeah I guess it is a workaround rather than a fix, from my experience (about 18 months of *buntu) NM has failed miserably. WICD is vastly superior to NM so to save myself any hassle I install it immediately after the OS therefore I can't help you with wallet advice.

---

### Post by creedog on 2009-07-19
Cool, thanks.

Can you give the procedure that you use to replace NM with Wicd, for example, making NM not start with KDE and getting wicd to start.

Not much of an expert when it comes to the GUIs.

---

### Post by Chris Musampa on 2009-07-19
> **creedog said:**
> Cool, thanks.

Can you give the procedure that you use to replace NM with Wicd, for example, making NM not start with KDE and getting wicd to start.

Not much of an expert when it comes to the GUIs.

They won't coexist, installing one will remove the other.

Open a terminal and paste the following:
```
sudo apt-get update
sudo apt-get install wicd
```
That should download wicd and install it for you.

---

### Post by creedog on 2009-07-19
Yup you are correct they cannot coexist. So I tried this on my desktop and boom, lost networking. Log was complaining about /etc/resolv.conf not being a symlink to /etc/resolvconf/run/resolv.conf. so I fixed it to point to this and was able to start wicd up. Is their not some sort of widget for the taskbar like network manager had?

Also note that it had my name server wrong. My ip is 192.168.254.4, but it set my  /etc/resolvconf/run/resolv.conf nameserver to 192.168.0.1

---

### Post by Chris Musampa on 2009-07-20
Hmmm I've never had those problems with it.  Re the tray icon, I think you have to run it manually from your apps menu just after install, after that the tray icon appears automatically on login.

---

### Post by creedog on 2009-07-20
i think if i rebooted i might have been ok.. Thanks for your help. I am going to let it burn in for a few on my desktop before I try it on the laptop.

---

