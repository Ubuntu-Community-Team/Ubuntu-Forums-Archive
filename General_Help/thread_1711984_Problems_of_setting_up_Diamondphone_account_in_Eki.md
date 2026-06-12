---
title: "Problems of setting up Diamondphone account in Ekiga (Ekiga Call Out)"
date: 2011-03-22
forum: General Help
---

### Post by dreamon_ on 2011-03-22
Hi everyone,

I recently started using Ekiga as an open source alternative to Skype and finally decided to give Ekiga's Call Out feature a try yesterday. I went ahead and signed up for an account with Diamondcard (the service which provides the Call Out feature to Ekiga), got my payment confirmed and entered my account details in Ekiga. However, I have since been unable to get my Diamondcard account to work with Ekiga. I can log in to my Diamondcard account and send SMS from their web interface, but I haven't been able to use it with Ekiga.

I set up the following two accounts in Edit -> Accounts:

1. Ekiga.net account (for Ekiga-Ekiga calls):
Registrar: ekiga.net
User: <my Ekiga.net username>
Authentication user: <my Ekiga.net username>
Password: <my Ekiga.net password>
Timeout: 3600

2. Ekiga Call Out account (for landline/mobile phone calls & SMS):
Registrar: sip.diamondcard.us
User: <my Diamondcard ID>
Authentication user: <my Diamondcard ID>
Password: <my Diamondcard PIN>
Timeout: 3600

Shortly after enabling both accounts my Ekiga.net account shows up as "Registered", but my Call Out account says "Could not register (Failed)" and I cannot place calls to landline numbers or the Diamondcard echo test number (sip:441@sip.diamondcard.us). Of course I followed the instructions on [http://wiki.diamondcard.us/podwiki?page=EkigaPhone](http://wiki.diamondcard.us/podwiki?page=EkigaPhone) and have entered the correct account ID and PIN as I found them on the Diamondcard homepage after logging in. When right-clicking the Call Out account and selecting "Consult the balance history" I am transferred to a Diamondcard website which tells me how much money I have charged to my account and how much I have used for sending SMS from their homepage, so the credentials I have entered are correct.

So this is where I am stuck now. I would love to use Ekiga to replace Skype for PC-to-PC and PC-to-Phone (landline/mobile) calling and SMS, but I can't seem to get around this problem and hope that someone can give advice on how to fix this.

---

### Post by dreamon_ on 2011-03-22
Got in touch with Diamondphone's customer service and found out that my IP had been blocked because I was using the wrong login credentials at fist. I tried logging in using my Diamondphone user name + password before finding out that I had to use the ID + PIN which are found in the admin area on Diamondphone's website :D

So, to all newbies out there: make sure you use the right login credentials. And if you run into problems try to sign in from another IP or contact Diamondphone's customer support.

---

