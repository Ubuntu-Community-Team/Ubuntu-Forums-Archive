---
title: "Printing to Windows print queues"
date: 2012-05-01
forum: General Help
---

### Post by mwmsje on 2012-05-01
I'm trying to integrate Ubuntu systems into a Windows environment. I've been successful thus far however having some problems with printing integration. I'm using Samba at the minute and it's been giving me some hassle, particularly when the SSLF GPO is enabled in Windows (security hardening). 

Regardless, without SSLF, I'm seeing the following behaviour:

**Add Printer** -> Select **Windows Printer via SAMBA** -> click '**Browse**' and it sees my domain, I select the computer, authenticate to Windows to view print queues, then select the print queue. So, the print queue is selected and I now need to supply authentication information. 

I have two options: Authenticate later, where I'd need to supply credentials for each printing job or authenticate now and save the password typing later. I opt for the latter firstly, type in the username and password, click verify and nothing... says it isn't valid. I've tried EVERY combination of username and cannot get it to work.

Now, if I select the former (authenticate later), I can create a document, print it, verify it's UNSUCCESSFUL in CUPS administration screen (obviously, it's not authenticated to Windows) and I can right-click the job in the Linux print queue, click authenticate, type in the same username/password combination as before, and it'll get sent and arrive on Windows - happy days.

Finally, is anyone aware what protocols Ubuntu uses to authenticate to Windows for the printing? Is it LM, NTLM or NTLMV2? If it isn't NTLMV2, does anyone know how I can choose this one? As SSLF requires this.

Thanks for any information or help people can offer.

---

