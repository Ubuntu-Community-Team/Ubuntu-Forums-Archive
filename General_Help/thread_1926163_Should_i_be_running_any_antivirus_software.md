---
title: "Should i be running any antivirus software?"
date: 2012-02-15
forum: General Help
---

### Post by kush2burn on 2012-02-15
I was wondering if ubuntu is safe. should I run a firewall or anything.

---

### Post by imachavel on 2012-02-15
firewall yes, anti virus never heard of it being needed for linux

how to configure firewall?


sudo ufw enable
[sudo] password for danel: 
Firewall is active and enabled on system startup

how to open a port:

sudo ufw allow 22
Rule added
Rule added (v6)

(port won't be opened in router - to do that open router settings by entering routers i.p. address into the address bar)

---

### Post by kush2burn on 2012-02-15
thankyou. and do i need to use the command to open a port or can i log into my firwall and open it. im really new to networking so excuse me if i sound stupid lol

---

### Post by jasonrisenburg on 2012-02-15
If you run windows I defiantly suggest that you do. My wife has had a few nasty ones, even with a anti-virus. There is a few anti-virus's out there but I have used Ubuntu for 3 or so years and have never had a virus.

---

### Post by imachavel on 2012-02-15
no problem at all, computers are confusing and a pain in the ***. ask any questions you need.....

---

### Post by imachavel on 2012-02-15
> **jasonrisenburg said:**
> If you run windows I defiantly suggest that you do. My wife has had a few nasty ones, even with a anti-virus. There is a few anti-virus's out there but I have used Ubuntu for 3 or so years and have never had a virus.

yes for windows I suggest malware bytes, microsoft security essentials, and c cleaner for the registry

---

### Post by kush2burn on 2012-02-15
what if i have windows installed and ubuntu installed. and boot in ubuntu can any virus still be running from the windows?

---

### Post by matbluvenger on 2012-02-15
> **kush2burn said:**
> what if i have windows installed and ubuntu installed. and boot in ubuntu can any virus still be running from the windows?

I don't think that would happen due to them being in different partitions... but then again I'm still a bit new.

---

### Post by yetiman64 on 2012-02-15
> **matbluvenger said:**
> I don't think that would happen due to them being in different partitions...
Right, the Windows install is inactive and any virus on the Windows install can't run under Ubuntu anyhow so can't "spread".

You can install an AV product for Linux and scan your Windows install when it is offline or even just specific Windows folders etc, I have used Avast for Linux in the past and found it works ok. Scanning for viruses in Linux itself is a bit of a waste of time really, the scanners only scan for Windows viruses which don't affect Linux itself. There are currently no known Linux viruses "in the wild" as far as I'm aware - it would be big news here if there were any :).

For firewalls if you are behind a routers firewall (eg an adsl modem or wireless access point often has a firewall active) you generally don't need to activate the OS firewall (ufw). If you connect directly to the net with no hardware firewall, then yes, set up ufw.

Even with a firewall set up, if certain code can be executed on your machine (especially with root privileges) you can be compromised. Stick to the trusted repositories, don't just load any packages off the general internet (without first thoroughly investigating the source of the package). Use script blocking in your browser against malicious sites installing software automatically etc (generally referring to "zero day" browser attacks there).

Regards, yetiman64

---

### Post by 3Miro on 2012-02-15
The AV question is convoluted, but the answer is that you don't need to run AV program and the only AV programs available for Linux search for Windows viruses. The only time it makes sense to install AV under Linux is when you have a machine that is constantly interfacing with Windows machines.

For the firewall, so long as you stick to the official repositories, then you don't need a firewall. By default, Ubuntu doesn't accept any traffic from the outside (as good as a firewall) and if you configure a service then you need it to be visible on the outside (if you are running a wall will need to add an exception anyway). If you are using your computer for regular web, mail, office, games things, then you don't need a firewall.

---

