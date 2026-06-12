---
title: "postfix and MX records"
date: 2011-06-28
forum: General Help
---

### Post by dbecker on 2011-06-28
just followed the guide on how to setup Ubuntu 10.04 server + postfix from here:
hxxp://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04

ports 110, 143, 25 are forwarded on my router to LAN IP of mailserver.

_postfix settings_
hostname: server1.mydomain.com
example email: [EMAIL="user@mydomain.com"]user@mydomain.com[/EMAIL]

I can receive emails in outlook, **if** they were sent** from the mailserver** using:
mailx [EMAIL="user@mydomain.com"]user@mydomain.com[/EMAIL]

However, external emails from hotmail.com to [EMAIL="user@mydomain.com"]user@mydomain.com[/EMAIL] never arrive. 

I'm thinking this is because of the DNS host records for my domain. Here's what I have. 

_**Host Records**_
_host name_ = @
_address_ = public IP
_record type_ = A Address

_host name_ = server1
_address_ = public IP
_record type_ = A Address


[B][U]Email settings
[/U][/B]_host name_ = @(none)
_record type_ = MX
_address_ = server1.mydomain.com



any input?

thanks!

---

### Post by prodigy_ on 2011-06-28
MX record isn't really necessary in your case. You need it when it's different from A record (mail.domain.com for example) or when your domain has multiple mail servers. If there's no MX, the sender's mail server will just use A.

Is TCP port 25 of your mail server reachable from the Internet? You can use an online service like [http://openportchecker.com/](http://openportchecker.com/) to find out if you're not sure.

P.S. BTW, don't forget to secure your MTA before before opening port 25. Read [this HOWTO](https://help.ubuntu.com/community/Postfix) for example.

---

### Post by dbecker on 2011-06-28
> **prodigy_ said:**
> MX record isn't really necessary in your case. You need it when it's different from A record (mail.domain.com for example) or when your domain has multiple mail servers. If there's no MX, the sender's mail server will just use A.

Is TCP port 25 of your mail server reachable from the Internet? You can use an online service like [http://openportchecker.com/](http://openportchecker.com/) to find out if you're not sure.

P.S. BTW, don't forget to secure your MTA before before opening port 25. Read [this HOWTO]("https://help.ubuntu.com/community/Postfix") for example.


nope, port 25 is not open from internet. I also called ISP and they said it's blocked; nothing they can do. 

Do I have any options?

---

### Post by t4thfavor on 2011-06-28
Try smtps its port 987 or something like that. You can call and get commercial service from most cable companies. I have it in the USA, and it's about 55/month +static IP (5) +taxes.


Other than that, most ISP's block those ports because of spammers... Personally it's kinda BS if you ask me.

---

### Post by dbecker on 2011-06-29
thanks for the replies guys. 

I guess it boils down to my postfix mail folder will not receive mail from external domains b/c my ISP is 100% blocking all inbound/outbound traffic on port 25. 

My only options, as I see it are:
1. get a new ISP. I only have 1 other choice in my area, DSL. They also block port 25
2. sign up for a mail redirection service, (dnsexit.com). They listen on port 25 for you, then send them emails to my postfix server on alternate port. 

What a load of crap.

**EDIT: **

finally got everything working. 

signed up for a $20/yr acct at dnsexit.com; selected mail-redirection port 8001. Added an MX record in my DNS manager to point to smtp.dnsexit.com. Changed the postfix listening port to 8001 in master.cf. 

added credentials to Outlook, hit send/receive............got 25 'testing testing testing' messages..LOL

working great; now onto squirelmail!

thanks again!

---

### Post by dcstar on 2011-06-30
> **prodigy_ said:**
> MX record isn't really necessary in your case. You need it when it's different from A record (mail.domain.com for example) or when your domain has multiple mail servers. If there's no MX, the sender's mail server will just use A.
..........

Some SMTP servers do not fall back use the A record, it is always a good idea to have a MX record.

---

### Post by dbecker on 2011-07-06
hey guys, another q...again my isp is complicating things; they block all in/out traffic on port 25.

I can send mail using my ISP's smpt from squirrelmail just fine. 

main.cf
relayhost = smtp.myisp.net

But, when I enter my credentials into outlook:
outgoing: server1.mydomain.com
incoming: server1.mydomain.com

It cannot connect to outgoing smtp server...because port 25 is blocked by ISP. If I change the setting in outlook to connect to outgoing server on dif. port, it connects fine, but when sending email, mail.log says "rely access denied"

So, how can I connect outlook outgoing smtp server to postfix server using any port other than 25? I just need to send the outgoing email to postfix on port 26, then once postfix gets the email, it will use the relayhost to send the email ISP's smtp port 25, (which is permitted)

thanks!

---

### Post by SeijiSensei on 2011-07-07
Did you try making smtp.myisp.net the outgoing server in Outlook?

---

### Post by dbecker on 2011-07-07
> **SeijiSensei said:**
> Did you try making smtp.myisp.net the outgoing server in Outlook?

yes, inside/outside my LAN that works fine. However, I'd have to tell all the outlook clients my credentials so they can use smtp.myisp.net outgoing server since it requires auth. 

To use smtp.myisp.net, I have to specify these settings in outlook:
[B]-outgoing server port: 465
-use the following type of encrypted connection: SSL
-smtp requires auth, enter in myisp.net credentials[/B]


My goal is to specify all of the bold info in postfix, then have outlook clients connect to:
outgoing server: server1.mydomain.com
outgoign server port: 26

is this possible?

---

