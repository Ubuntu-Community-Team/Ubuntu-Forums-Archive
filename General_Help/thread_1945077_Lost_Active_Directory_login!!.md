---
title: "Lost Active Directory login!!"
date: 2012-03-22
forum: General Help
---

### Post by baberb on 2012-03-22
Hello all, I'm rather new to the linux world...But i have a new Ubuntu server 11.10, and it was connected to Active Directory domain controller with Centrify.  I had it so that all my users in AD could login to the server with their usual domain credentials, and everything was great.

Then I started messing around with mail, trying to send mail from command line.  It would have had to go out through the smart host mail server, so I was trying to install mailutils, exim4.....then I ended up trying ssmtp, which I think is what messed things up.  I quickly realized that my sudo password wasn't working, and then I found out that I can't authenticate with domain credentials to the linux server at all!  I must have broken something lol

Please help!

---

