---
title: "How to secure ubuntu?"
date: 2010-02-19
forum: General Help
---

### Post by karthick87 on 2010-02-19
I have completely switched to ubuntu..Being a beginner i like to know some ways to keep my system secure..So pls tell me the way to protect my system from hackers and viruses..

---

### Post by bumanie on 2010-02-19
By default, ubuntu is quite secure as per this "By default, Ubuntu does not install default services that listen on open network ports. (The astute reader will note that local network service clients like DHCP and Avahi are the only exception.) This reduces the chances that a system would be compromised through a service that was installed without the explicit knowledge of the administrator." from [here]("htthttp://www.ubuntu.com/products/whatisubuntu/serveredition/features/securityp://").Re viruses - there is virtually no linux viruses in the wild. Read [this]("http://linuxmafia.com/~rick/faq/index.php?page=virus").

---

### Post by Benster900 on 2010-02-19
As most people will tell you. Ubuntu and Linux/Unix don't need a firewall, or an anti-virus. Out of about 40 years theres only been about 40 viruses pointed toward Linux. Ubuntu is has alot of security features. Such as when you want to install, or change important things you need a password. Bottom line is you don't need a firewall, or anit-virus. If you want you can install KlamAV, or Avast for anti-virus, and firestarter for a firewall. 



p.s I thought the same thing when I switched, but I don't use any anti-virus, or fiewalls. If you really think you need more security look into IP-Tables.

---

### Post by hobo14 on 2010-02-19
There's no such thing as a truly secure system, of course, but just installing Ubuntu has made you safe from the vast majority of viruses and hackers.

Just give your administrator account a good strength password, and don't login as root (if you don't know what that means you aren't doing it) and the chances of you ever having virus or hacker trouble again are extremely remote.

---

### Post by Ordes on 2010-02-19
if however you are running services that listen on ports, e.g samba, ssh, ftp, daemons , etc.. you should use a firewall. 

firestarter is a nice and easy gui tool to configure your firewall / IP-tables.

i also like guarddog. but in the beginning firestarter is the easier one. and it also monitors your eth when you load it up

---

### Post by Julita on 2010-02-19
I would disagree that Ubuntu doesn't need firewall. If you are interested in safety, you would like to see man iptables (or here [http://linux.die.net/man/8/iptables](http://linux.die.net/man/8/iptables))

---

### Post by ghostborg on 2010-02-19
I had clam installed and updated and found clam did not detect an infected file.
I installed Avast and it flagged the file.
I don't think Avast scans files as they are downloaded.
Clam seems to have better integration but bummed me out when I tried to copy the scanned file to a Winblows machine and the alarms went off in Winblows.

Clam has a Nautilus-clamscan in Synaptic which gives you the ability to right click on a file to open the scanner.

Clamtk recommends installing first from the Ubuntu repo then update by downloading their latest package due to making sure things are installed properly with apparmour..etc.
I had to reboot before the clamtk anti virus icon showed up in the accessories menu.

My whole thing is Linux can be dangerous for non-linux computers on the network. The tools function like there from the Win 3.1 era.

---

### Post by Julita on 2010-02-19
ghostborg, please look at [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

