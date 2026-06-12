---
title: "Evolution - exchange-connector, Rackspace global catalog server"
date: 2011-03-04
forum: General Help
---

### Post by Handle123 on 2011-03-04
I'm (trying to) switch to Ubuntu from Windows XP on my work laptop. Unfortunately, one of the dealbreakers is that I need full Exchange contact/calendar syncing.

Our email is hosted by Rackspace (owa.mailseat.com). We login using the usernames of the format [email]first.lastname@ourcompany.com[/email].

I'm trying to set up Evolution to use this account, using exchange-connector-setup-2.32. The first step, entering the OWA URL, usename and password works, and progresses to step 2, where I need to enter a Global Catalog server. I have no idea what to enter here. Everything fails.

My questions are
- What is the "Global Catalog server" - can I enter/run some dummy server here?
- If its necessary, where can I get the information from this? I have a Windows XP machine synced up using Outlook 2007, so if I need to gather any information from that setup I can.

---

### Post by Handle123 on 2011-03-05
Tried Thunderbird as well, but I couldn't figure out how to get it to even accept Exchange settings.

---

### Post by dcstar on 2011-03-05
> **Handle123 said:**
> I'm (trying to) switch to Ubuntu from Windows XP on my work laptop. Unfortunately, one of the dealbreakers is that I need full Exchange contact/calendar syncing.
..........

You should probably install and use the MAPI connector.

---

### Post by Handle123 on 2011-03-06
Tried it - no luck there either.

---

### Post by dcstar on 2011-03-06
> **Handle123 said:**
> Tried it - no luck there either.

If that web server uses "Outlook Anywhere" RPC over HTTPS protocols then you are out of luck, Evolution will only work with the old OWA protocols.

Some people claim to have got Evolution working with Exchange 2007, but I have never been able to do so.

---

### Post by dcstar on 2011-03-06
> **Handle123 said:**
> 
..........
My questions are
- What is the "Global Catalog server" - can I enter/run some dummy server here?
- If its necessary, where can I get the information from this? I have a Windows XP machine synced up using Outlook 2007, so if I need to gather any information from that setup I can.

Actually the Global Catalog Server should be the LDAP settings that you should be able to obtain from the Outlook properties (somewhere).

---

