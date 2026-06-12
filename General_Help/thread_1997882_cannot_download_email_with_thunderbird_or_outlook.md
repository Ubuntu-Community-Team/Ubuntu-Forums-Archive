---
title: "cannot download email with thunderbird or outlook"
date: 2012-06-05
forum: General Help
---

### Post by honestann on 2012-06-05
[FONT=Book Antiqua]I have 2 computers:[/FONT]
[FONT=Book Antiqua]#1: 64-bit ubuntu 12.04[/FONT]
[FONT=Book Antiqua]#2: windoze xp 64-bit[/FONT]
 
[FONT=Book Antiqua]Until 5 days ago I read and sent email with outlook2000 on my winxp64 system. Then 5 days ago my winxp64 boot disk crashed. I installed a fresh copy of winxp64 and outlook2000 on a new disk drive, and copied over the file that contains my emails (outlook.pst). Unfortunately, that file does not contain email account information, so I had to create and configure my email accounts, which should not be a problem since I've done that dozens of times.[/FONT]
 
[FONT=Book Antiqua]When I "send and receive" email, the appropriate dialog appears and displays a green check-mark next to each email account as it downloads the emails. The problem is, no emails are downloaded (nothing appears in the inbox).[/FONT]
 
[FONT=Book Antiqua]So I logged into the cpanel interface on the host that contains my 6 domains, clicked on the "web-mail" icon/app, and looked through my email accounts. My several email accounts contain more and more emails every day, which is usual.[/FONT]
 
[FONT=Book Antiqua]So I futzed with my account settings for the past 3 days, until I realized "hey, I've been meaning to completely switch over everything to linux anyhow", so I ran the "thunderbird" email client on my ubuntu64 system for the first time, set up my email accounts, and tried to download my email in thunderbird. The only problem is... the behavior is the same --- no errors are given, but no emails appear in the inboxes of the various accounts I set up.[/FONT]
 
[FONT=Book Antiqua]Can anyone explain this behavior?[/FONT]
 
[FONT=Book Antiqua]My incoming port is 110 and my outgoing port is 25. My incoming ports are of the form "mail.domainname.com" and my outgoing ports are of the form "smtp.west.cox.net" which sends via my cox cable-internet service which has worked fine for years. So, "nothing fancy" at all.[/FONT]
 
[FONT=Book Antiqua]I'd love to switch over to thunderbird at this point, but I need to be able to receive and sent emails. But I find it very strange that neither email client is working. Neither computer has ever had anti-virus installed or firewalls installed/enabled, though I guess there are typically basic firewalls on wireless routers. RJ45 cables connect both my computers to my netgear wireless router, which in turn connects to my cable-modem via another RJ45 cable, and the cable-modem connects directly to the cable-connector in the drywall. Nothing fancy, and nothing changed in the physical configuration for years.[/FONT]
 
[FONT=Book Antiqua]I guess the fundamental question is this. What would make email clients (two of them on different OS, no less) appear to be receiving emails... but not actually receive them? Fortunately they are not being deleted from the server either (which both email clients are configured to do).[/FONT]
 
[FONT=Book Antiqua]Any ideas?[/FONT]

---

### Post by traditionalist on 2012-06-05
The only thing that will cause that is if they are wrongly configured. Check your settings again.

---

