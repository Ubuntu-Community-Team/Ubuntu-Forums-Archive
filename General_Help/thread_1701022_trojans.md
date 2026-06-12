---
title: "trojans"
date: 2011-03-05
forum: General Help
---

### Post by mmsmc on 2011-03-05
i know linux is very unlikely to get viruses and malware, but what about trojans?

---

### Post by mikewhatever on 2011-03-05
It won't get any trojans if the user doesn't install them, as trojans usually require user interaction. Install software from the repositories only, and you should be relatively safe.

---

### Post by Frogs Hair on 2011-03-05
Don't run applications or scripts  you don't trust.
[http://en.wikipedia.org/wiki/Trojan_horse_%28computing%29](http://en.wikipedia.org/wiki/Trojan_horse_%28computing%29)

---

### Post by jerome1232 on 2011-03-05
So yeah, I'm just echoing what's been said but a Trojan is a malicious virus disguised as a desired program.

Stick to the repositories and never, ever install software if they are not authenticated by apt-get.


Never install 3rd party software unless you trust the software author and the distrubitor of the software.

This is how you steer clear of trojans.


That and the fact that there are no **known** viruses that currently can infect an up-to-date linux system.

---

### Post by Habitual on 2011-03-06
Run like hell from POP mail client setup.
Use IMAP.

---

### Post by mmsmc on 2011-03-06
ive never heard of any of those habitual, can you explain further?

---

### Post by Habitual on 2011-03-06
IMAP:
Internet message application protocol (commonly known as IMAP) is one of the two most prevalent Internet standard protocols for e-mail retrieval, the other being the Post Office Protocol (POP).[1] Virtually all modern e-mail clients and mail servers support both protocols as a means of transferring e-mail messages from a server.

POP:
In computing, the Post Office Protocol (POP) is an application-layer Internet standard protocol used by local e-mail clients to retrieve e-mail from a remote server over a TCP/IP connection. POP and IMAP (Internet Message Access Protocol) are the two most prevalent Internet standard protocols for e-mail retrieval. Virtually all modern e-mail clients and servers support both. The POP protocol has been developed through several versions, with version 3 (POP3) being the current standard. Like IMAP, POP3 is supported by most webmail services such as Hotmail, Gmail and Yahoo! Mail.

Although Linux is not susceptible to Windows virii, using the POP protocol that downloads email messages in their entirety certainly doesn't help stop the transmission of them.

If you use IMAP, the messages stay on the server and lessens the likelihood of transmitting infected emails to your friends, family and co-workers. 

And has the added benefit of your inbox, folders, etc all behave and look the same across all interfaces that also use IMAP. It's very synchronous.

POP is a nightmare to backup. 1000s of megs to backup a POP mail client vs. 100s for only an IMAP backup of the same client.

Hope that helps.

---

### Post by mmsmc on 2011-03-06
thanks, great info!

---

### Post by Habitual on 2011-03-06
Always glad to help.

---

### Post by lithopsian on 2011-03-06
If you are stupid enough to run unsolicited programs you receive by email then whether you downloaded them using POP or IMAP isn't going to make a lot of difference.

---

### Post by Old *ix Geek on 2011-03-06
> **Habitual said:**
> Although Linux is not susceptible to Windows virii, using the POP protocol that downloads email messages in their entirety certainly doesn't help stop the transmission of them.I have to disagree. I've used POP for my Earthlink and domains' mail, forever, and have never had any issues.
> POP is a nightmare to backup. 1000s of megs to backup a POP mail client vs. 100s for only an IMAP backup of the same clientAgain, I disagree. Now, *I* happen to have mail dating back to the early '90s that I've carried from computer to computer, mail client to mail client (SeaMonkey for years now), so in that regard, yes, it does mean multiple GBs to back up, but that's my choice. If I weren't carrying those e-mails along for the ride, the overall size would be a LOT smaller! :eek:

---

### Post by lithopsian on 2011-03-06
IMAP is mostly claimed to be better by snobs who think POP is solely for noobs.  Both have their pros and cons, so use the one that suits your situation best.  IMAP is not available from many ISPs, but getting more common now.

---

