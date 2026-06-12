---
title: "Email roadblock after switching from Windows to Ubuntu"
date: 2010-03-14
forum: General Help
---

### Post by robot682 on 2010-03-14
Hello,  I have Googled a bunch for this and have found that it may not be possible, but I would love to find out I am wrong since this is the issue keeping me from switching from Windows full time.  

My school uses an Exchange server hosted by Microsoft and accessible, from Outlook 2007 through Outlook.com via http proxy.  We have laptops with MS office 2007 installed and can use the Outlook connector to connect to this server.

Is it possible to use an email client in Linux to connect to this server and retain the use of mail and calendar.  My whole life is organised in this calendar so, it's something of a deal breaker...

Thank you for your time,
Sam

---

### Post by bobcollard on 2010-03-14
> **robot682 said:**
> 

My school uses an Exchange server hosted by Microsoft and accessible, from Outlook 2007 through Outlook.com via http proxy.  We have laptops with MS office 2007 installed and can use the Outlook connector to connect to this server.
Sam
Have a look at this about Thunderbird in Ubuntu:
[http://kb.mozillazine.org/RSS_proxy_%28Thunderbird%29](http://kb.mozillazine.org/RSS_proxy_%28Thunderbird%29)

---

### Post by dcstar on 2010-03-14
> **robot682 said:**
> Hello,  I have Googled a bunch for this and have found that it may not be possible, but I would love to find out I am wrong since this is the issue keeping me from switching from Windows full time.  

My school uses an Exchange server hosted by Microsoft and accessible, from Outlook 2007 through Outlook.com via http proxy.  We have laptops with MS office 2007 installed and can use the Outlook connector to connect to this server.

Is it possible to use an email client in Linux to connect to this server and retain the use of mail and calendar.  My whole life is organised in this calendar so, it's something of a deal breaker...


So the Evolution Exchange access does not work?

---

### Post by bobcollard on 2010-03-14
> **dcstar said:**
> So the Evolution Exchange access does not work?
I don't know, I use Thunderbird on Xfce.  Evolution would work possibly.  Do a Google search for "http proxy evolution"

---

### Post by ellgor on 2010-03-15
Hi,

Take a look at Kmail/Kontact (seperate, but complimentary apps) has all the features you might want.

Regards, Ellgor.

---

### Post by dcstar on 2010-03-16
> **bobcollard said:**
> I don't know, I use Thunderbird on Xfce.  Evolution would work possibly.  Do a Google search for "http proxy evolution"

The question was (clearly) directed to the OP.

---

### Post by bobcollard on 2010-03-16
> **dcstar said:**
> The question was (clearly) directed to the OP.
Sorry didn't check the username.

---

### Post by g-a-c on 2010-03-16
> **robot682 said:**
> Hello,  I have Googled a bunch for this and have found that it may not be possible, but I would love to find out I am wrong since this is the issue keeping me from switching from Windows full time.  

My school uses an Exchange server hosted by Microsoft and accessible, from Outlook 2007 through Outlook.com via http proxy.  We have laptops with MS office 2007 installed and can use the Outlook connector to connect to this server.

Is it possible to use an email client in Linux to connect to this server and retain the use of mail and calendar.  My whole life is organised in this calendar so, it's something of a deal breaker...

Thank you for your time,
SamFrom what I've seen, the Evolution Exchange connector doesn't support Exchange 2007, and doesn't support the RPC-over-HTTP tunnel method available in Exchange 2003 and later. Evolution also doesn't support the Exchange 2007 version of OWA, so I think for the moment you are out of luck and will have to rely on OWA in a web browser for your messaging/calendar needs. I'm sure the full version of OWA rather than Light would work just fine in Firefox/Chrome/other browsers, you would need to change the User Agent for OWA to allow this though.

---

### Post by dcstar on 2010-03-17
> **gavinchappell said:**
> From what I've seen, the Evolution Exchange connector doesn't support Exchange 2007, and doesn't support the RPC-over-HTTP tunnel method available in Exchange 2003 and later. Evolution also doesn't support the Exchange 2007 version of OWA, so I think for the moment you are out of luck and will have to rely on OWA in a web browser for your messaging/calendar needs. I'm sure the full version of OWA rather than Light would work just fine in Firefox/Chrome/other browsers, you would need to change the User Agent for OWA to allow this though.

[http://www.go-evolution.org/FAQ#Evolution_Exchange_.28formerly_known_as_Connector.29](http://www.go-evolution.org/FAQ#Evolution_Exchange_.28formerly_known_as_Connector.29)

There seem to be HOWTOs around saying that they can successfully connect to Exchange 2007 using MAPI.

---

### Post by robot682 on 2010-03-19
> **gavinchappell said:**
> From what I've seen, the Evolution Exchange connector doesn't support Exchange 2007, and doesn't support the RPC-over-HTTP tunnel method available in Exchange 2003 and later. Evolution also doesn't support the Exchange 2007 version of OWA, so I think for the moment you are out of luck and will have to rely on OWA in a web browser for your messaging/calendar needs. I'm sure the full version of OWA rather than Light would work just fine in Firefox/Chrome/other browsers, you would need to change the User Agent for OWA to allow this though.

Sorry it took me so long to reply.  I have been very busy.  This post sums up the impression I had when I made this post initially.  I looked into other suggestions and followed other links.  It seems, at this time, neither Evolution or Thunderbird have a way to interact with the new Outlook Connector functionality needed for Microsoft Hotmail.  Given this issue it is impossible for me to use the calendar features which make life much easier.  

Thank you to everyone for your suggestions and hopefully the future will resolve this issue considering the fact that more businesses are starting to shift to outsourced mail servers managed by Microsoft.  The last 2 colleges I have attended have transitioned to email accessible only through the Windows Live Hotmail site.  I do see this as something of a Linux business adaptation issue while, also realizing that a large part of the issue is Microsoft refusing to play nice with anyone.

Thank you,
Sam

---

### Post by belkinsa on 2010-06-28
> **dcstar said:**
> [http://www.go-evolution.org/FAQ#Evolution_Exchange_.28formerly_known_as_Connector.29](http://www.go-evolution.org/FAQ#Evolution_Exchange_.28formerly_known_as_Connector.29)

There seem to be HOWTOs around saying that they can successfully connect to Exchange 2007 using MAPI.

Sorry for the bump, but, when I try to do it one of the links to a plug-in doesn't work anymore.  (the:  [http://www.omesc.com/node/22](http://www.omesc.com/node/22) one)  Does anyone have a link to that Plug-in?  Thanks.

---

### Post by GnomeMax on 2010-07-04
Ummm...

It's easy to connect to Exchange 2007 via MAPI.  First, the Exchange server has to be configured to use MAPI and you set your client (Evolution, Thunderbird, etc.) up with an account using MAPI.

The problem is that you can't get to all the functions and features of Exchange this way.  Basically, you get access to the mailbox.

It used to work.  With Exchange 2003 there were a couple of clients that worked well, but Exchange 2007 broke all that and now the only client that works with Exchange is Outlook.

Welcome to Proprietary Software...  ;)

---

### Post by belkinsa on 2010-07-04
I **only **need my inbox, I don't need the other extras.  Do you have a guide for setting it up?

---

### Post by GnomeMax on 2010-07-04
Ummm...

Oops - my bad.  Too many acronyms.  I was thinking IMAP when reading MAPI.

MAPI is Microsoft only unless you've paid for it (how Apple gets access, I think.)  A quick scan of the 'web and there are some who appear to be trying to write a work-around, but it doesn't look like it's been successful yet.

I've been having problems with recipients from my Exchange'07 server getting messages they can't read or attachments they can't open.  It seems tied to this protocol that Microsoft uses to custom wrap a mail message.  When the recipients get it they get the text of the message and a Winmail.dat file (which has all the rest of the message - rich text formatting and attachments and such...)  It forces my users to send in plain text only so the custom wrapper isn't activated.  I'm suspicious it's having to do with MAPI.

If your exchange server has allowed POP or IMAP you can get into the mailbox with most clients using POP or IMAP (and SMTP to send.)  If they are not enabled then your only access, I think, is through Outlook Web Access or the Outlook client, (or whatever client on Apple OSX has paid for the rights) unless you can convince your admin to turn the other protocols on.  I for one am waiting (patiently... ;)) for a solution that doesn't involve Outlook.

Sorry for getting your hopes up...

---

### Post by belkinsa on 2010-07-04
Thanks for your advice, maybe the University of Cincinnati IT Connect people will listen to me.  But in meanwhile, I will use Wine and Thunderbird 3.0.

---

### Post by borobudur on 2010-07-22
I was able to install the MAPI plugin over synaptic (version 0.28.3-0ubuntu1). Like this I was able to connect to the ms exchange server 2007 here at work (intranet). 

The mail account works just fine (identically like outlook) but the calendar doesn't seem to work.

Anyone has solved this problem??

---

### Post by trundlenut on 2010-07-22
I use thunderbird and davmail, it can be rather slow as I run davmail on my laptop rather than the exchange server but it works.

---

