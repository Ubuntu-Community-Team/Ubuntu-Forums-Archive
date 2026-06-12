---
title: "Making Evolution work with Exchange"
date: 2010-07-27
forum: General Help
---

### Post by selittl on 2010-07-27
I seem to have a problem that a lot of people have: My work uses exchange server 5.5/2007.  Does evolution still not support this?  I tried to set it up and it tells me that it won't work with exchange 5.5.  Was wondering if anyone has come up with an add-on or work around.

Thanks

---

### Post by Wiredfixer on 2010-08-18
Well, im working on this because i need to adapt Ubuntu desktop to a Enterprise Enviroment..

I have Ubuntu 10.04 and i can setup my Evolution via OWA/Exchange, but i cant see the GAL...

 I find another solution, DavMail Gateway, works with Thunderbird but i dont try with evolution..

 Both Solutions are working but when you have an ISA Server Proxy the things make more hard...

 My Actual setup is like this:

- Login to the Domain with Likewise Open 6 (not from APT, is buggy)
- Evolution working with OWA Url
- NTLMAPS if i need to authenticate apt-get or skype.

 If you describe your actual situation, may can i help you :D

---

### Post by genfinch on 2010-10-19
I have DavMail and Thunderbird set up together as follows

DavMail
OWA URL [https://mail.companyname.com/owa](https://mail.companyname.com/owa)
IMAP port 1143
SMTP port 1025
HTTP port 1080
LDAP port 1389

as for the proxy I'm behind, I've tried both entering it in DavMail itself and telling DavMail to use the system's settings. I have entered my username and password for the proxy.

Thunderbird
incoming: IMAP, server localhost
outgoing: SMTP, server localhost
Ports exactly the same as in DavMail, including the 1 in front. 

With this setting, when I hit "Get Mail" in TB, it's just busy for a while, then nothing happens. 
When I set the URL to [https://mail.companyname.com/owa/auth/logon.aspx](https://mail.companyname.com/owa/auth/logon.aspx), I get an error message from DavMail
```
DavMail configuration exception:
Connect exception: java.net.SocketException Broken pipe
```
I've tried googling this, but I don't even begin to understand what they are talking about in the forums I find, and none of it seems to be related specifically to DavMail anyway.

This is the whole log from DavMail
```
2010-10-19 08:45:39,281 INFO  [main] davmail  - DavMail Gateway 3.8.5-1480 listening on SMTP port 1025 IMAP port 1143 CALDAV port 1080 LDAP port 1389 
2010-10-19 08:45:56,175 DEBUG [davmail.imap.ImapServer] davmail  - Connection from /0:0:0:0:0:0:0:1 on port 1143
2010-10-19 08:46:23,812 DEBUG [CheckRelease] davmail  - Unable to get released version
2010-10-19 08:46:39,217 ERROR [ImapConnection-38784] davmail.exchange.ExchangeSession  - Connect exception: java.net.SocketException Broken pipe
2010-10-19 08:46:39,223 ERROR [ImapConnection-38784] davmail  - DavMail configuration exception:
Connect exception: java.net.SocketException Broken pipe
davmail.exception.DavMailException: DavMail configuration exception:
Connect exception: java.net.SocketException Broken pipe
    at davmail.exchange.ExchangeSessionFactory.handleNetworkDown(ExchangeSessionFactory.java:219)
    at davmail.exchange.ExchangeSessionFactory.checkConfig(ExchangeSessionFactory.java:198)
    at davmail.imap.ImapConnection.run(ImapConnection.java:82)
2010-10-19 08:46:39,233 DEBUG [ImapConnection-38784] davmail  - > * BAD unable to handle request: DavMail configuration exception: Connect exception: java.net.SocketException Broken pipe
```

I hope you can help me, Wiredfixer.

---

### Post by Wiredfixer on 2010-10-22
Well, this maybe is a software error, at day i have this:


- Evolution Configured With Exchange
- I've Changed NTLMaps, now i have CNTLM, is a single DEB and does install without any dependencies in a fresh offline sistem.
- Im Working on a Script for Evolution Config, This makes a request to the DC with my username, find the email, find the mailserver and gal server (usually is the AD Server)

 This script works with the machine logged in the domain with Likewise Open 6, maybe only you need less things for the Thunderbird Configuration.

 Personally, i prefer Evolution, because it works more seamlessly with Exchange than Thunderbird, Thunderbird only Works with IMAP and with Davmail, but i think Davmail is not the solution, you need to run DavMail, Configure It and Run everytime you need download Mail for thunderbird.

 For Exchange in Evolution, only you need to configure with OWA, or With IMAP, or if you enable the POP and SMTP in your Exchange Enviroment, maybe you can use with Thunderbird.

 In this case, you need to put your OWA Adress, Autenticate and if you have it, the GAL Address (servername.domain.example)

 How do you Work with Exchange in Windows? How do you configure? maybe is a good place for start.

 Im not an expert, but Evolution is my Client and it works :)

---

### Post by tomvoss on 2011-02-15
I wrote up [_detailed step-by-step instructions for connecting Evolution to Exchange 2007 Global Address List via LDAP_]("http://tomvoss.blogspot.com/2011/01/connecting-evolution-to-exchange-2007.html").

---

