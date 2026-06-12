---
title: "SCP Connection Refused"
date: 2011-02-06
forum: General Help
---

### Post by ilovesoup on 2011-02-06
Hi all,
I'm newbie.
My environment is:
Ubuntu 10.10 as guest OS on virtualbox 4 hosted by win7
NAT with port 22 forwarding on a wireless card

When I tried to connect my Ubuntu using WinSCP it showed connection refused.
I've my OpenSSH server installed and putty connection is OK.
I've also add WinSCP in my firewall rule...

Anyone can help me out?

Thanks in advance indeed..

PS: I've posted a same thread in Networking & Wireless but got no reply...I'm not sure if I can post here again.

---

### Post by [Snc] on 2011-02-06
Are you trying to connect from the machine, that is also the host (win7)?

PS. And yes, double posting is not good.

---

### Post by ilovesoup on 2011-02-06
1. Yes. I use WINSCP on win7, the host machine. 

2. Sorry about the double posting. But I really have no other ways since there was no reply for days...

---

### Post by [Snc] on 2011-02-06
1. So, SCP-ing from host to guest (on the same physical machine)
In windows try ipconfig in the command prompt, this should give you the IP of the host.
I see no need to add any rules to the firewall, since it is not an outbound or inbound connection.
In Virtualbox check settings -> display -> remote display [tab] (RDP)
and settings -> network -> advanced [drop-down], maybe the way the network is "*attached to*" the host network, is not "*good enough*", i have NAT. IMHO NAT is not the right way to go in many situations (since Network Address Translation isolates everything ...) I might be wrong here tho ;)

Some more reading here :)
```
http://forums.virtualbox.org/viewtopic.php?f=7&t=17712
http://serverfault.com/questions/190976/virtualbox-windows-vms-dont-work-with-a-bridged-adapter
http://winscp.net/forum/viewtopic.php?t=6014
```... note, that i gave you some articles, that may be outdated


2. Well, sometimes one just gives up and double posts ;) OPs can merge threads tho ...


added!
[http://ubuntuforums.org/archive/index.php/t-444323.html](http://ubuntuforums.org/archive/index.php/t-444323.html)

---

### Post by ilovesoup on 2011-02-08
Thank you very much~
I've tried hard to make the bridged mode work but failed..Maybe not so easy to make it on wireless card.
However....the problem was solved...
I'm now using filezilla instead of winscp.
Filezilla with SFTP protocol seems OK without change any settings in my case.
Nevertheless, I'm still confused about the root cause of the problem.

Again, thank you very much my friend!

---

### Post by ilovesoup on 2011-02-08
Problem solved for WinSCP also. Thanks to [email]prikryl@winscp.net[/email]
Here is the solution:

[http://winscp.net/forum/viewtopic.php?p=33827#33827](http://winscp.net/forum/viewtopic.php?p=33827#33827)

And again, thank you [Snc]

---

