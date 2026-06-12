---
title: "Curious - no /usr/bin/mail"
date: 2011-04-07
forum: General Help
---

### Post by LinuxLars on 2011-04-07
New Amazon EC2 install of an Ubuntu Server 10.10 AMI (20101225), and there's no /usr/bin/mail.

I know this sounds dumb, but isn't that supposed to be included on a base install? 

Second, apt-get reports that I can install it from heirloom-mailx or mailutils. 

Does anyone know the advantage/disadvantage of heirloon-mail vs. mailutils? And which one is "normally" used? We just need to send the admin a log report.

---

### Post by SeijiSensei on 2011-04-08
The absence of a command-line mail program in Ubuntu server is perhaps its most glaring omission. That decision breaks pre-existing scripts that send mail notices among other issues. "heirloom-mailx" will give you what you need.

---

