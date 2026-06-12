---
title: "Samba4 AD login"
date: 2012-08-12
forum: General Help
---

### Post by manders2600 on 2012-08-12
Hi all, first let me say "Thanks!" in advance to anyone who can help me out.


I have installed 12.04 and am using Samba4.  I have used the Samba4 HOWTOWiki to use the machine as an Active Directory DC by joining it to a Windows Server 2008 R2 Primary DC.

Everything seems to be working correctly, as I can successfully replicate from the Windows Server 2008 R2 DC, and I can set up shares on my Ubuntu machine which are accessible by credentialed AD users on Windows machines.

All of the appropriate user and group data appears to have been successfully replicated to sam.ldb, however, I cannot log directly into the Ubuntu machine using Active Directory credentials (eg: DOMAIN\user).

My question is this: how do I get samba4 users, along with their AD credentials and rights, to become Ubuntu users?  Shouldn't an AD user be able to log into a Samba4 DC machine?

Thanks again,

Mark
[COLOR=purple][/COLOR]

---

### Post by samosamo on 2012-08-19
Great job on setting up samba. Now you need to set up authentication to your PDC.  So read up on PAM and /etc/pam.conf.  You should also learn how to use winbind.

---

