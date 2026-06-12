---
title: "Hard Drive Space"
date: 2009-10-13
forum: General Help
---

### Post by cyphunk on 2009-10-13
Hi,

We are running Ubuntu Server 8.04 on our firewall. The firewall is used as a Squid Proxy and we are using Fetchmail to move our mail from our provider to the firewall and then distributes into our users mailboxes. (incidentally we are going to be discontinuing the use of the FetchMail Script from next week and will be connecting straight to the POP3 for each user) - The box also has sendmail running as an SMTP to deliver mail directly from the users on the network to external.

Now, the problem that we are having for the last 6 months is that every month at different times the machine would run out of hard drive space completely... causing Squid to stop and fetchmail to be unable to save email messages to the users mail spool.(obviously)

It would be quite difficult to free up hard drive space. We would clear and rebuild squid cache, empty users with large amounts of unread emails, remove unused packages, etc. This became increasingly more difficult every month as we were running out of things to delete. The hard drive space just kept on getting used up.

Now we reach the point where there is nothing more to delete. In fact no matter what I delete, the free space just doesnt free up. It just stays on 0 available. I've deleted around 500mb of stuff and still nothing. I have no idea what to do next. I have also reduced the reserved space for kernel/priority processes (if I have put that correctly) - still no free space is showing up.

Now, on another box of mine that we administer. We have noticed that the folder /var/mail/mqueue-client (if I remember correctly) gets fulled of a whole bunch of files which eventually end up taking up a load of space. So we are in the habit of cleaning this folder out from time to time. 

Back to the first box... we are unable to DELETE/EMPTY/REMOVE the mqueue-client folder on this first box. If we try and list the files int he folder, nothing happens. we are left with a blinking _ cursor and nothing happens. Even if you CTRL+C, nothing...

What can I do?

Chris

---

