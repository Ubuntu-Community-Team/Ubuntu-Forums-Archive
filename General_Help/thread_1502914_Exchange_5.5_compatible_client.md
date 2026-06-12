---
title: "Exchange 5.5 compatible client"
date: 2010-06-06
forum: General Help
---

### Post by Gevorg on 2010-06-06
Hi,

I just switched to Ubuntu from Win7 and want to find replacement for my MS Office Outlook. I tried Evolution client to connect to my mailbox and got following error:

The Exchange server is not compatible with Exchange Connector.

The server is running Exchange 5.5. Exchange Connector 
supports Microsoft Exchange 2000 and 2003 only.

Could you please suggest mail client compatible with Exchange 5.5?

Thank you in advance!

Best,
Gevorg

---

### Post by Leppie on 2010-06-06
i'm not sure if it supports ms exchange 5.5, but i know that thunderbird has had exchange support for quite a while now.
```
sudo apt-get install thunderbird
```

---

### Post by Gevorg on 2010-06-06
I need calendar sync also, but Thunderbird doesn't support it. I found plugins solution which is evolution-brutus, but it is not available for Ubuntu.

---

### Post by Leppie on 2010-06-06
not sure about their capabilities, but there's lightning and sunbird. sunbird is the standalone version.

---

### Post by davidmohammed on 2010-06-06
> **Gevorg said:**
> Hi,

I just switched to Ubuntu from Win7 and want to find replacement for my MS Office Outlook. I tried Evolution client to connect to my mailbox and got following error:

The Exchange server is not compatible with Exchange Connector.

The server is running Exchange 5.5. Exchange Connector 
supports Microsoft Exchange 2000 and 2003 only.

Could you please suggest mail client compatible with Exchange 5.5?

Thank you in advance!

Best,
Gevorg

Do you have the option to change the configuration of your exchange 5.5 server ?  If you do, suggest make the necessary changes on exchange 5.5 to connect via OWA/Pop3/IMAP.

---

### Post by Gevorg on 2010-06-06
> **davidmohammed said:**
> Do you have the option to change the configuration of your exchange 5.5 server ?  If you do, suggest make the necessary changes on exchange 5.5 to connect via OWA/Pop3/IMAP.

Thing is that Evolutions is working with OWA URL, but Exchange 5.5 version is not supported currently. POP3 and IMAP do not support calendar sync that is why I not use them.

---

### Post by davidmohammed on 2010-06-06
then you are out of luck - you have to use MS Outlook to connect to exchange 5.5 if you want calendar sync.

Either change your exchange server to exchange 2003 or run MS outlook via a virtualbox windows guest - for example in seamless mode.

---

### Post by sehrgut on 2010-06-18
Try installing the package exchange-mapi. That supports recent versions of exchange.

[http://www.go-evolution.org/MAPI_FAQ#Account_Setup](http://www.go-evolution.org/MAPI_FAQ#Account_Setup)

---

### Post by dcstar on 2010-06-18
> **sehrgut said:**
> Try installing the package exchange-mapi. That supports recent versions of exchange.

[http://www.go-evolution.org/MAPI_FAQ#Account_Setup](http://www.go-evolution.org/MAPI_FAQ#Account_Setup)

Exchange 5.5 is **not** a "recent version of exchange", it is an ancient version that was pensioned off long before Evolution existed.

---

### Post by krinderlin on 2010-06-18
Actually, I know for a fact that our current server is Exchange 2007 and we receive the Exchange 5.5 is not supported error.

You may want to double check the version of Exchange Server with your network administrator.  Also, he or she may have a brutus server set up for interfacing with the MAPI server.

---

### Post by dcstar on 2010-06-19
> **krinderlin said:**
> Actually, I know for a fact that our current server is Exchange 2007 and we receive the Exchange 5.5 is not supported error.

You may want to double check the version of Exchange Server with your network administrator.  Also, he or she may have a brutus server set up for interfacing with the MAPI server.

All later versions of Exchange still have legacy 5.5 interfaces and settings (if fact this can be a real pain having these) so yes, it could well be something like Exchange 2007/2010 that might work with the Evolution MAPI connector, but the Exchange server may need things like Outlook Anywhere & RPC over HTTP enabled.

---

### Post by Goatrancer on 2010-09-17
I've been getting the 5.5 error too. Which is odd because my workplace is NOT using 5.5 (they arent sure which one they are using, probably 2007, soon to be upgraded to 2010 they tell me).
It's my understanding that I can ONLY access my work email via OWA, which logs me out and forces me to clear my cache every 5 minutes or so.

Any suggestions??

---

### Post by Chalkygbg on 2010-11-01
> **Goatrancer said:**
> I've been getting the 5.5 error too. Which is odd because my workplace is NOT using 5.5 (they arent sure which one they are using, probably 2007, soon to be upgraded to 2010 they tell me).
It's my understanding that I can ONLY access my work email via OWA, which logs me out and forces me to clear my cache every 5 minutes or so.

Any suggestions??

I'm encountering the same problem over here, I know I have a Exchange Server 2008 with OWA enabled but Evolution still tells me that "Exchange 5.5 is not a compatible client"...

I absolutely hate Microsoft Outlook so I was hopping Evolution would be a good replacement but no luck:(

Is there no one who have managed to get this to work?

Thanks for any help provided...

---

