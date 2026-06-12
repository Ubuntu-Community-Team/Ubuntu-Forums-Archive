---
title: "How to add an AD group to local users group?"
date: 2011-04-11
forum: General Help
---

### Post by portopalermo on 2011-04-11
Hello everybody,

I just finished installing an Ubuntu Server 10.4 and joined it to a Windows environment Domain using Likewise.
I am planning to use this machine as a terminal server, so lots of domain users will logon using X2Go Client.

At the first test, I tried adding only one user (DOMAIN\User1). He could logon to the server and Likewise created his HOME folder. But, when I open System-Administration-Users and Groups, this user doesn't appear anywhere. As a result, I can't add him to X2Go group. Without being member of this group, he doesn't have the rights to connect remotely in terminal.

Actually, this configuration must be done with an entire group in AD.
I would like to add this group automatically to the Ubuntu Server's Users and Groups, so the first time the users connect through terminal, they'll get their profile.
Do you know how this can be done?

Thank you very much for sharing your knowledge and time.

PP

---

