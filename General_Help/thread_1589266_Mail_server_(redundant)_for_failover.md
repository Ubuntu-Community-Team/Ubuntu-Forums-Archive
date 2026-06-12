---
title: "Mail server (redundant) for failover"
date: 2010-10-06
forum: General Help
---

### Post by c0d3sl1ng3r on 2010-10-06
OK, here we go:

**Site A** - static IP address on a 4mb BT leased line.

LAN is almost all Windows Server 2003 Standard with Exchange 2003 as primary mail server, serving just over 100 clients, all on 10.0.10.x range.

NAS and SAN duties are delivered with Ubuntu Server :)

Mail server has existing A and MX records and reverse DNS all set up and playing nicely.

So far so good.

**Site B** - static IP address on another 4mb BT leased line, linked WAN to WAN over VPN to Site A.

Single Windows Server 2003 Standard DC with another 30-odd clients, all on 10.0.0.x range.

So that's:

10.0.10.x - public_IP_1 - VPN - public_IP_2 - 10.0.0.x

I am looking to drop a redundant mail server at Site B, with the relevant A and MX records to receive emails in the event that Site A is offline for any reason (line failure, router dies, Exchange takes a hissy fit, etc, etc...)

To be honest, as long as I can get at the emails it receives in some fashion I don't need anything exotic. It is meant as a repository and little more, so an inbound (getmail/fetchmail ?) server is the goal here.

Obviously if I could offer clients webmail access to their accounts on the redundant server in the event that it kicks in then that would be a huge plus, but the main intention here is so that we don't lose emails in the event of serious outage. Even if I have to knife-and-fork the emails from the redundant server back out to another location (Exchange) once things are back to normal this would be sufficient for my purposes.

I can rebuild the entire Exchange server from scratch in a day, and recovery from backup takes around 4 hours, so the likelihood is that this system will (hopefully) never be used, but I prefer the condom principle of "better to have and not need than to need and not have"...

:)

Any ideas of how best to tackle this using Ubuntu ?

Pointers, suggestions and rationale all appreciated.

---

### Post by dirty_harry on 2010-10-06
As far as I understand you your aim is to have a fall back solution for downtime of your primary mailserver.

Maybe you are looking for a Postfix Configuration as backup MX:
> The backup MX 
A *target server*, i.e. one that knows how to deliver to the relevant user's [e-mail mailbox]("https://secure.wikimedia.org/wikipedia/en/wiki/E-mail_mailbox") is typically one which is the most preferred. Lower priority servers, a.k.a. *backup MX* or *secondary MX*,  usually keep the messages in a queue waiting for the primary server to  become available. If both servers are online or in some way connected to  one another, the backup MX will typically queue a message briefly and  immediately forward it to the primary MX. The backup MX acts as a [store-and-forward]("https://secure.wikimedia.org/wikipedia/en/wiki/Store-and-forward") mail server.
 quote form [https://secure.wikimedia.org/wikipedia/en/wiki/MX_record#The_backup_MX](https://secure.wikimedia.org/wikipedia/en/wiki/MX_record#The_backup_MX)
[B]
Postfix howto for backup mx:[/B]
[http://www.postfix.org/STANDARD_CONFIGURATION_README.html#backup](http://www.postfix.org/STANDARD_CONFIGURATION_README.html#backup)
**Spam is very important on low priority mx records:**
[http://www.cyberciti.biz/faq/postfix-backup-mx-server-anti-spam/](http://www.cyberciti.biz/faq/postfix-backup-mx-server-anti-spam/)
**For adding webmail take a look at postfix addons:**
[http://www.postfix.org/addon.html](http://www.postfix.org/addon.html)
**Maybe a allinone-bundle(postfix+webmail) would be an solution(some of them have support or are expensive):**
[http://wiki.samba.org/index.php/Exchange_Server_Alternatives](http://wiki.samba.org/index.php/Exchange_Server_Alternatives)

One question is how to forward/sync composed messages form the backup system to the primary system in case of failure? I mean if the primary system is down people will use the backup system to answer or even to write new emails. These messages should also appear in the normal INBOX ones the primary system is up again. (e.g. Exchange 2003 behaved like this... back then I didn't found a solution). And another question is how you configure login authentic? Ldap for win-clients?

Anyway, doing something like this is fun and a pain in *beep* at the same time. Would be interesting to hear how it goes?

---

