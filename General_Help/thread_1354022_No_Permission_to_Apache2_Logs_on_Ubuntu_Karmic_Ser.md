---
title: "No Permission to Apache2 Logs on Ubuntu Karmic Server"
date: 2009-12-13
forum: General Help
---

### Post by jasonhudnutt on 2009-12-13
I installed Splunk to give it a whirl on my Ubuntu servers with RackSpace Cloud and after hearing the price for Splunk (5k) I decided to uninstall it. Now I am unable to check my error logs for Apache2. 

My first step is to verify where the logs are kept. I am assuming Splunk did not move them and they exist in:

[FONT="Courier New"]/var/logs/apache2/error.log[/FONT]

The problem is that I cannot access the apache2 directory. Permission is denied, I am running (not as root) but with root permissions, sudo is not working either.

Permissions on the directory are [FONT="Courier New"]root:adm[/FONT]

Any help is GREATLY appreciated.

---

### Post by fcefan00 on 2010-05-18
Splunk just indexes the Logfiles.
Assuming owner and group are correct and the permissions are set correct also(something like 755) I can't imagine any reasons. What does "ls -l" says? Do you have full access to this machine?

---

