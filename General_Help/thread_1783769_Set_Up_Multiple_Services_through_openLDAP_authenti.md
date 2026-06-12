---
title: "Set Up Multiple Services through openLDAP authentication."
date: 2011-06-16
forum: General Help
---

### Post by satyanash on 2011-06-16
Hi,
I have 3 servers set-up at our office here.
Server 1:
[INDENT]It is the gateway, through which all the Internet traffic passes. It hosts the DHCP, DNS, shorewall, squid proxy and the openLDAP(doesn't work much) server.[/INDENT]
Server 2:
[INDENT]It is the LAMP server, that hosts mysql, Apache2 servers.[/INDENT]
Server 3:
[INDENT]It is the Virtual Machine host, which runs VirtalBox and is the host for the test servers et cetera.
[/INDENT]
All three run Ubuntu 10.04.2 Lucid Lynx.

I have been trying to set up Openfire IM using the Jabber protocol for our office's own personal IM server, a mail server using corier and postfix or dovecot, on Server 1. I want all the authentication to take place using the openLDAP server set up. I also would like to know what would be a better way to organize the openLDAP directory. my current structure is shown in the picture.
Can anybody point me to a definite guide to do all this?

My current progress has been the following:
[LIST=1]
[*]I have been able to login into any of the ubuntu desktop clients in my office using my LDAP credentials, thus creating my home folder, et al in the client.
[*]I have have been partially successful in hooking up openfire(Jabber) to LDAP. I can log in using my LDAP credentials, and contact the server, however when i add someone to my roster in Pidgin it says not authorized by that user.
[*]I have had zero success in setting up the mail server. I tried using the iRedMail package, but it did too many things without telling me, would not create new users other than the default ones created by it.
[*]I have also been able to enable authentication for Apache2 using openLDAP.
[/LIST]

I have searched numerous guides, some were for different OSs, some for older versions of Ubuntu, not many working ones, some weren't as detailed as they ought to be, while some describe only a part and do not provide a working installation.
I also have a test VM ready to test whatever guide/tutorial i have to follow. Without affecting the real server.

Any help would be appreciated.

Thank You.
Satyajeet
:popcorn:
[IMG]http://i54.tinypic.com/2djupuf.png[/IMG]

---

