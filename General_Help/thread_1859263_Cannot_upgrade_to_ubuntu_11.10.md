---
title: "Cannot upgrade to ubuntu 11.10"
date: 2011-10-13
forum: General Help
---

### Post by Raaaaay on 2011-10-13
Hi, I was upgrading to 11.10 from 11.04, realise that it was taking too long, and cancelled it. Now when I try to upgrade again by pressing the button in Update Manager, a message box appears after a long pause and says "Could not download the release notes", and asks me to check my internet connection. I'm absolutely sure that my internet connection is fine. Does anyone have any suggestions as to why that is? Is it because I cancelled it earlier?

Many thanks in advance.

---

### Post by rogere84 on 2011-10-13
I've got the exact same problem here. I had the alert when I was in the middle of backing everything up, I dismissed it, and now when I click the Upgrade button it says it can't download the release notes and that I need to check my internet connection.
Something tells me I shouldn't have dismissed it :(

---

### Post by effenberg0x0 on 2011-10-13
System -> Administration -> Update Manager -> Setting -> Tab  "Ubuntu Software" (the first tab)-> "Download from" 

Change it to  Main server.

Alt+F2
update-manager -d

Report back results.

Regards,
Effenberg

---

### Post by Raaaaay on 2011-10-13
SOLVED!!!

Thank you Effenberg! That seemed to work. The upgrade is under way now, and we'll hope that all goes well.

The "Download from" entry, the one you mentioned on my computer was set to "Server from United Kingdom", and I changed it to "Main server" as you instructed. After then, a few more updates were found, I installed them and tried to start the upgrade to 11.10 again, and it started working! Thanks again!

---

### Post by effenberg0x0 on 2011-10-14
Sometimes servers are out of sync or even laggy or unavailable. 
Cool that it worked. Vote me for president, ok?

Regards,
Effenberg

---

