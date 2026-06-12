---
title: "What to do with Hosted Exchange 2010 on Ubuntu.."
date: 2012-01-25
forum: General Help
---

### Post by MacTribe on 2012-01-25
Hey guys

There are a lot of older posts around the internet about people who managed to get their own personal or companies exchange 2010 working on their machines, however the email system I'm forced to use is a hosted exchange 2010 system provided by one of the many online similar to Rackspace or Cobweb etc, which means they don't support MAPI like the older versions of exchange do.

I've tried running the MAPI plugin in mozillas mail client with no luck, tried all the different combos of IP address, DNS names, usernames and passwords I could think of.

Does anyone have any new ideas or developments for running exchange 2010 over OWA on ubuntu? I know of Davmail but hoping for something a little more solid. 

Thanks for your input..

---

### Post by e79 on 2012-01-25
I'm not sure I fully understand what you mean, but OWA is working fine on any system that has a browser. Simply type : [https://FDQN/owa](https://FDQN/owa) (ex: [https://mail.domain.com/owa](https://mail.domain.com/owa))

or you could also build Windows virtual machine and install Outlook in it so you would then have the native Microsoft client.

Hope this helps

---

### Post by SeijiSensei on 2012-01-25
If you configure the Exchange Server to support IMAP, you can use a client like Thunderbird.

---

### Post by MacTribe on 2012-01-25
Basically when I say 'connect via OWA' I mean how Outlook 2011 on Mac or Apple Mail connects to the server. It uses owa.servername.com/EWS/Exchange.asmx whereas the MAPI plugin connects differently.

The older versions of exchange require servername.domainname.local as the server address (within the LAN) and you would configure a HTTPS proxy using the OWA address to connect remotely. 

The newer versions of exchange are a little easier to connect to - simply put in the owa address i.e owa.servername.com and it uses that address with EWS/Exchange.asmx at the end to connect - or - it uses autodiscover + your email address to set itself up. 

So.. Back to my original question. Are there any applications at the moment that would connect the same way as Mac Mail currently does? i.e via OWA / EWS?

P.S Thanks for the IMAP suggestion however I'm looking to sync calendars and contacts too. I'm not keen on the Windows VM idea either if I can help it, but would do it last resort. :(

---

### Post by e79 on 2012-01-25
I see what you mean now.

I personally never hook up a MAC / Apple clients to Exchange 2010 using EWS :( (only did 1 Exchange 2010 installation and there were only 2 MAC clients on 30 total PCs so I did not break my head too much)

So I opened PoP3 for those MAC clients (LAN only) as they didn't need calendar nor contact sync.

Sorry as I cannot help you on this.

Best of Luck

---

### Post by dcstar on 2012-01-25
> **MacTribe said:**
> Hey guys

There are a lot of older posts around the internet about people who managed to get their own personal or companies exchange 2010 working on their machines, however the email system I'm forced to use is a hosted exchange 2010 system provided by one of the many online similar to Rackspace or Cobweb etc, which means they don't support MAPI like the older versions of exchange do.
........

[http://www.petenetlive.com/KB/Article/0000378.htm](http://www.petenetlive.com/KB/Article/0000378.htm)

---

### Post by MacTribe on 2012-01-26
Thanks DCstar for the link however thats the MAPI plugin thats causing all the problems I've been describing. Hosted exchange doesn't accept MAPI as a connection.

I may have found the answer just encase anyone else is looking for this. Someone has started developing evolution-ews which would allow you to connect the same way Apple Mail or Entourage 2008 / Outlook 2011 connects:

[http://ubuntuforums.org/showthread.php?t=1912819](http://ubuntuforums.org/showthread.php?t=1912819)

I havent tested it yet, but I hope it works for you!

---

