---
title: "Evolution's compatability with Microsoft Exchange"
date: 2010-06-04
forum: General Help
---

### Post by pearldrums on 2010-06-04
I recently started working for a company that uses "Microsoft Online Services" or "BPOS" which I believe is just a client for a microsoft exchange server. I did some snooping on good old wikipedia and it said that Evolution was compatable with Microsoft exchange, but in other parts it said it was not compatable with the 2007 version, then it said the evolution2 has updated support for MS exchange.
 
1) I've never heard of evolution 2, is it the default mail for 10.04, or is regular evolution standard?
 
2)Is Evolution (or Evolution 2) compatable with microsoft exchange 2007 for e-mail, contacts, and calendaring?
 
I'll try when I get home today, just thought I'd ask if anyone knows some information I should look into if I find some free time while I'm at work today.
 
Thanks.

---

### Post by A Feyn Man on 2010-06-18
I would really like to know too

---

### Post by dcstar on 2010-06-19
[http://live.gnome.org/Evolution/FAQ#Evolution_Exchange_.28formerly_known_as_Connector.29](http://live.gnome.org/Evolution/FAQ#Evolution_Exchange_.28formerly_known_as_Connector.29)

---

### Post by ravikiran189 on 2011-10-16
How about Microsoft BPOS...???

---

### Post by NoahsMyBro on 2012-06-12
Given the age of this post I doubt ravikiran is still paying attention, but I'd like to find an answer for this myself.

I work with Microsoft Online daily (was known as BPOS, now called Office 365), and Exchange Online is the Microsoft hosted-Exchange service piece of Office 365.

Last week I tried configuring Evolution, with the Exchange components, to connect to my Exchange Online mailbox. I was not successful.

Exchange Online is multi-tenant, meaning multiple customers (companies) share the same Exchange infrastructure. That infrastructure is enormous.

Users sign on using account names that include their SMTP domain -
{user@company.com}, rather than just {user}. The "@company.com" is how the authentication processes at Microsoft Online know what organization & domain the user belongs to.

The problem (as I believe it to be) is that the Evolution account-sign-in interface forces the user to enter a value in the 'Domain' field. For Exchange Online, the domain field must be left blank.

I've tried all sorts of different values in the domain field that I hoped might work (company.com, outlook.com, onmicrosoft.com, company.onmicrosoft.com, pod51xxx.outlook.com, etc...) and all failed.

I don't know how EWS or MAPI work at a detailed level, but I expect that if Evolution was updated to allow a user to leave the domain field blank, and the client then submitted just the username and password to the Exchange Online service, then Evolution would work successfully with Exchange Online.

I hope this comes to pass as I'd like to try it out.

---

### Post by oldos2er on 2012-06-13
Please start a new thread for your question.

---

