---
title: "E-mail disappears in Claws Mail."
date: 2011-02-04
forum: General Help
---

### Post by casbahdk on 2011-02-04
I am suddenly experiencing problems with disappearing e-mails in Claws Mail. They seem to disappear somehow during the download process. Running Claws Mail from the terminal gives me the following errors, but I am not sure that this is related to the problems with my other accounts: ```
** (claws-mail:12020): WARNING **: [11:45:58] IMAP error on imap.gmail.com: STATUS error

** (claws-mail:12020): WARNING **: [11:45:59] IMAP error on imap.gmail.com: STATUS error

** (claws-mail:12020): WARNING **: [11:46:00] IMAP error on imap.gmail.com: STATUS error
``` I am using Claws Mail version 3.7.4 with Linux Mint 9 (LXDE). I have googled a lot, but I haven't been able to come up with a satisfactory answer. It may have something to do with some upgraded gnu utilities, but I am not sure what this is in reference to. BTW, all of my accounts use IMAP.

---

### Post by edwardp on 2011-02-22
Hi.

Please go to the Claws Mail web site:  [http://www.claws-mail.org/](http://www.claws-mail.org/) they have a "users" mailing list that you can join, the list is very active.

If you post your comment to the list, I'm sure you will receive a response in no time.

I just installed Claws Mail on my Ubuntu systems and love it!  :D

Gmail uses secure servers/connections.  You would need to set the account in Claws Mail to use secure connections, the default IMAP port should be 993 and the SMTP port should be 465, in order to successfully communicate with their mail servers using SSL.

Hope this helps.

---

### Post by casbahdk on 2011-02-23
Cheers. Been there, done that. The interesting thing was that they seemed to be uninterested in the problem, possibly because the debug crashed as well. I gave up and decided to try Evolution bloatware.

---

