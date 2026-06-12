---
title: "barracuda email block"
date: 2011-02-09
forum: General Help
---

### Post by giles.wheatley on 2011-02-09
Hi

My understanding of how email is routed etc is a limited. I am using Evolution on my Ubuntu client and use a email server provided by an external hosting company to simplify changing ISP. My current ISP is Talk Talk and I have a dynamically allocated IP address for broadband. About once a week when trying to send an email I get a pop-up error message from Evolution telling me that my outgoing email is blocked by barracuda:

Welcome response error: mtpd: 85.211.211.103 pid 6768: 451 [http://www.barracudanetworks.com/reputation/?pr=1&ip=85.211.211.103](http://www.barracudanetworks.com/reputation/?pr=1&ip=85.211.211.103)

The IP address specified is my allocated broadband IP address as checked on my router. It is registered to Tiscali UK Ltd (taken over by Talk Talk).  

I have chased this through and unblocked it by request to Barracuda. I have rebooted my router to get a new IP address. Both of these will work but it does not take many days for the newly allocated or unlisted IP address to be re-listed and my outgoing email blocked.

My domain hosting company says it is nothing to do with them - it is not their server. I have a number of email accounts on the same server/domain all coming from Ubuntu machines using Evolution. These are all family users and none that are sending out spam. 

I only have one Windows machine but that has no email accounts set up on Outlook.

Please can someone give me some advice because this is beginning to drive me crazy.

Many thanks
Giles

---

### Post by Habitual on 2011-02-09
Giles:

Here's how it works. email providers sign up for what are called SBLs (Spam Blacklists). There are dozens but some of the ones I recall atm are sorbs and spamhaus.

Any email provider, bulk sender, ISP, whatever, etc that signs up to use the SBL will have the sending IP checked against that blacklist. If it is in an SBL list that they subscribed to, guess what. No email for you. You can receive all day long, just can't send.

That sending IP could be yours specifically, or any other system that mail gets routed through.
Your IP could be clean (for example) but your "external hosting company" could suddenly wind up on an SBL and that machine or network block of IPs will no longer be able to transmit email to any network that subscribes to an SBL where that IP or netblock of IPs is listed.

Spamhaus has blacklisted the entire netblock of 85.211.0.0/17 
It's not your IP specifically, but spam is coming from the talk talk assigned IPs in a **range** owned by talk talk.

Spamhaus says all this about the 85.211.0.0/17 range:

85.211.0.0/17 is listed on the Policy Block List (PBL)
Reason: This IP range has been identified by Spamhaus as not meeting our policy for IPs permitted to deliver unauthenticated 'direct-to-mx' email to PBL users.

Since your IP is in that range, you are therefore blacklisted.
85.211.211.103 is listed in the PBL

You have to **get the Abuse Team involved** of the owners of the 85.211.211.103 IP.

Send an email to  [email]abuse@uk.tiscali.com[/email]
with this url and ask them to remove the block.
[http://www.spamhaus.org/pbl/query/PBL286210](http://www.spamhaus.org/pbl/query/PBL286210) since they own the IP.

HTH

---

### Post by giles.wheatley on 2011-02-10
Many thanks HTH, I have sent an email (using the browser interface to my email account!) to tiscali as you suggested. I will let you know what happens.
Giles

---

### Post by Habitual on 2011-02-10
Giles:

You're Very Welcome.
HTH means **H**ope **[B]T**[/B]hat **H**elps.

Did/does any of make any sense to you?
I sought to make your understanding of the process more clear.

JJ/Habitual

---

