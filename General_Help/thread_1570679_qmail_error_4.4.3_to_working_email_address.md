---
title: "qmail error 4.4.3 to working email address"
date: 2010-09-08
forum: General Help
---

### Post by LCPSWolf on 2010-09-08
Hey all,
 
This is my first post to Ubuntu Forums, so I hope I'm putting this in the right place. Here goes:
 
We have a company (rosworks) that's using qmail for their email server. Wonderful. However, rosworks cannot email one of our users (jonesvc). I get their emails fine. She has a valid email address, and rosworks is emailing her correct address. On their end, they get the following:
 
> 
[FONT=Times New Roman][SIZE=3][FONT=Times New Roman][FONT=Times New Roman][SIZE=3][FONT=Times New Roman]-------- Original Message -------- [/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Times New Roman]**[FONT=Times New Roman][FONT=Times New Roman]Subject: [/FONT][/FONT]**[FONT=Times New Roman][FONT=Times New Roman]failure notice[/FONT][/FONT]
**[FONT=Times New Roman][FONT=Times New Roman]Date: [/FONT][/FONT]**[FONT=Times New Roman][FONT=Times New Roman]8 Sep 2010 13:56:10 -0000[/FONT][/FONT]
**[FONT=Times New Roman][FONT=Times New Roman]From: [/FONT][/FONT]**[FONT=Times New Roman][EMAIL="MAILER-DAEMON@rosworks.com"][FONT=Times New Roman][COLOR=#0000ff]MAILER-DAEMON@rosworks.com[/COLOR][/FONT][/EMAIL][/FONT]
**[FONT=Times New Roman][FONT=Times New Roman]To: [/FONT][/FONT]**[FONT=Times New Roman][EMAIL="support@rosworks.com"][FONT=Times New Roman][COLOR=#0000ff]support@rosworks.com[/COLOR][/FONT][/EMAIL][/FONT]
  
[SIZE=2]Hi. This is the qmail-send program at rosworks.com.[/SIZE][SIZE=2]I'm afraid I wasn't able to deliver your message to the following addresses.[/SIZE][SIZE=2]This is a permanent error; I've given up. Sorry it didn't work out.[/SIZE][SIZE=2][COLOR=#0000ff]jonesvc@EMAIL.DOMAIN.REMOVED[/COLOR][/SIZE][SIZE=2]:[/SIZE][SIZE=2]CNAME lookup failed temporarily. (#4.4.3)[/SIZE][SIZE=2]I'm not going to try again; this message has been in the queue too long.[/SIZE][/FONT][/SIZE][/FONT][FONT=Times New Roman]
 
[SIZE=3][FONT=Times New Roman]This occurs after 4 hours in their queue. I'm running 2 postfix / spamassassin mail relays in our district - I can see the emails coming in to me, but nothing to jonesvc from [EMAIL="support@rosworks.com"]support@rosworks.com[/EMAIL]. I'm thinking it's never leaving their server, but don't know what to tell them to fix it. [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Any ideas? I see there may be issues with an unpatched qmail MTA when dealing with large #'s of MX records, but we only have 3. In case this is an issue, our MX records do not have reverse DNS set up; however, my address is on the same domain as jonesvc - why can they email me but not her?[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Thanks for anything you can do.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Damian[/FONT][/SIZE][/FONT]

---

