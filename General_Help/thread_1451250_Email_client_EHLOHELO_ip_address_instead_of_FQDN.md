---
title: "Email client EHLO/HELO ip address instead of FQDN"
date: 2010-04-10
forum: General Help
---

### Post by dmrazor on 2010-04-10
When the mailclient on my workstation sends an email using smtp, it connects to my smtp server and the following header is added to the mail:
```
Received: from Received: from [192.168.1.51] (rock.bluepoint.lan [192.168.1.51])
	by stone.bluepoint.nl (Postfix) with ESMTP id 9B763E86
	for <pipo@hotmail.com>; Wed,  7 Apr 2010 22:13:18 +0200 (CEST)
```
My question is, why does the mailclient connect with EHLO/HELO [192.168.1.51] and not with its FQDN?

This behaviour happens with both Evolution and Thunderbird. Is this the normal way for an email client to make itself know to a mailserver, or should it use its name?

Thanks,

Raz.

---

### Post by minaev on 2010-04-10
This header is appended by the SMTP daemon, not by the mail client. If it's sendmail, the format of the header is defined in the sendmail configuration file. I believe that other mail servers also provide a way to change the default format.

---

### Post by dcstar on 2010-04-10
> **dmrazor said:**
> 
........
My question is, why does the mailclient connect with EHLO/HELO [192.168.1.51] and not with its FQDN?
........

**All** IP connections are done with IP addresses, DNS names are just convenient aliases for humans to use.

---

### Post by dmrazor on 2010-04-12
> **minaev said:**
> This header is appended by the SMTP daemon, not by the mail client. If it's sendmail, the format of the header is defined in the sendmail configuration file. I believe that other mail servers also provide a way to change the default format.
Yeah, I know the header is added by the mailserver (Postfix in my case). But the mailserver adds data to the header based on what it receives. I tested it with a telnet 25 and a manual smtp connect. The first entry after "from" is the EHLO/HELO, so it must be the emailclient that sends [192.168.1.51] instead of something verbose. I'm just curious why its doing that instead of using the workstation's name.

@dcstar: everything being IP based, that's kinda stating the obvious, and beside the point. 

Raz.

---

