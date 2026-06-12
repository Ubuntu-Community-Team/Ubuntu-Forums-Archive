---
title: "Can't add Hotmail account to Evolution"
date: 2010-04-12
forum: General Help
---

### Post by Liso22 on 2010-04-12
I had no problems setting up my gmail account but I cannot set up my hotmail account on evolution, I keep getting "cannot connect to pop server" when I enter my password, I didn't do any configuration just kept clicking forward through the set up, it seemed to work on gmail, I did it reading every step carefully but I couldn't find anything wrong.

---

### Post by 2hot6ft2 on 2010-04-12
Receiving settings
Type: POP
Configuration
Server: pop3.live.com
Security
Use secure connection: SSL Encryption
Authentication: Password

Sending settings
Server type: smtp.live.com
Security
Use secure connection: TLS Encryption
Authentication: Login
:popcorn:

---

### Post by darolu on 2010-04-12
You need to set the right pop3 adress; it needs to read from port 995. So use:

Server: pop3.live.com:995

And smtp port 587:

Server type: smtp.live.com:587

That's how I have it on Thunderbird and works great; I tried it in Evolution (my default e-mail client) but it can only handle one single inbox for all pop accounts and I wanted them separated (why don't all web-based email services use IMAP?) so it was a mess.

---

### Post by 2hot6ft2 on 2010-04-12
> **darolu said:**
> You need to set the right pop3 adress; it needs to read from port 995. So use:

Server: pop3.live.com:995

And smtp port 587:

Server type: smtp.live.com:587

That's how I have it on Thunderbird and works great; I tried it in Evolution (my default e-mail client) but it can only handle one single inbox for all pop accounts and I wanted them separated (why don't all web-based email services use IMAP?) so it was a mess.
I took the settings right out of the configuration on mine and I didn't need to set the ports like that. On the other hand I think I had to set gmail to port 587 like you're saying.

---

### Post by darolu on 2010-04-12
> **2hot6ft2 said:**
> I took the settings right out of the configuration on mine and I didn't need to set the ports like that. On the other hand I think I had to set gmail to port 587 like you're saying.

When I configured Evolution I had to include the port like that, I couldn't find a text field to include it separately like in Thunderbird; it works the same.

---

### Post by tsgouvea on 2010-11-05
Just make sure that in the username field on the Receiving email tab you type your email as 'username@hotmail.com', and not only as 'username'

---

