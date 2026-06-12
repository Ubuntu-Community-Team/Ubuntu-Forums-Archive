---
title: "Pinging a VB host.....Problem...!"
date: 2010-05-01
forum: General Help
---

### Post by hakermania on 2010-05-01
Hello all [IMG]http://forums.virtualbox.org/images/smilies/icon_smile.gif[/IMG]
I am not totally new to VB. I am using it up to 1 year.
I have a problem on pinging the VB host running WinXP Pro.
My local address is 192.168.1.4 (this address is shown when running ifconfig)
In Xp, running ipconfig shows 10.0.2.15.
Xp **can** ping the 192.168.1.4 and 10.0.2.15 as well....
Although Ubuntu cannot ping  10.0.2.15 (Xp's address)
How can I solve this problem ?
(Actually the main purpose of this is doing experiments with metasploit against the Xp running in VB, but something like that is impossible if I cannot even ping the Xp....)
i would appreciate very much any help...
Cheers! [IMG]http://forums.virtualbox.org/images/smilies/icon_smile.gif[/IMG]

---

### Post by dino99 on 2010-05-01
first i will glance at logs for errors.

have you tweaks some rerouting, sandbox, proxy, firewall, iptable, network rules, ssh denyhost, bastille ... ?

---

### Post by Ryan Dwyer on 2010-05-01
You need to change your VirtualBox network settings for the client - it needs to be a bridged connection. The client machine should then receive an IP address in the same range as the host, assuming you have a DHCP service. If you don't, you'll need to configure the client's IP address manually from within the client.

---

### Post by hakermania on 2010-05-01
dino99 I have no idea what are u talking about
[Ryan Dwyer]("http://ubuntuforums.org/member.php?u=1004210") plz explain more things about how I should do this...
Should I change smthing on the Xp's Settings from the VB?

---

### Post by hakermania on 2010-05-01
Ok guys nevermind, I got it. I had to change the NAT network seeting to Briged or something like that...
SOLVED

---

