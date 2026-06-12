---
title: "Evolution and Exchange 2007"
date: 2009-09-05
forum: General Help
---

### Post by paulw2 on 2009-09-05
I am a total Linux newbie.  My Windows XP was getting slower and buggier each day and I thought I would try Linux before going out and getting a new computer.  In general I like what I see, but I was expecting that Evolution would allow me the same access to my Microsoft Exchange 2007 e-mail/calendar/contacts that Outlook does.  Alas I now understand that Evolution is only compatible with Exchange 2003.  I have come across a few potential solutions, but as a complete newbie many of them scare me.  I HATE using web access - I just don't consider that a viable option.  For now, I am connected by IMAP but of course that means no calendar/contacts.

Question one: Advise re: the best way to get around this - plugin for evolution, different e-mail client, other solutions.

Question two: How does someone who knows nothing about Linux implement the suggestion given in question one!  Step, by step instruction (written for dummies ideally) would be really appreciated.

Thanks for the help!

Paul

Evolution 2.26.1
Ubuntu 9.04

---

### Post by sethhikari on 2009-09-05
I am not sure if it had been totally implemented thus far but here is the help results from the evolution developers  

** Evolution Exchange (formerly known as Connector) **

 Questions regarding problems with Evolution Exchange (Connector). 


 [[edit]("http://www.go-evolution.org/index.php?title=FAQ&action=edit&section=111")]
** Why can't I connect to Exchange? **

 First of all, make sure the package "Evolution Exchange" is installed beside Evolution. Make sure the "Exchange plugin" is enabled under "Edit | Plugins". Also, Evolution Exchange only supports Microsoft Exchange 2000/2003 with OWA (Outlook Web Access) turned on (for WebDAV access). If you would like to connect to an Exchange 5.5, 2000, 2003 or 2007 server via MAPI (as would Outlook), get the Evolution Brutus Plugin at [http://www.omesc.com/node/22](http://www.omesc.com/node/22). Evolution Brutus supports complete access to your Exchange mail, calendar and tasks. If this still does not work, make sure you use "domain\user" and not "domain/user" in the "Evolution Account Editor > Windows Username". 
 [[edit]("http://www.go-evolution.org/index.php?title=FAQ&action=edit&section=112")]
** Where do I add the user name and the OWA URL in the setup dialog? **

 If you do not see any fields to enter your user name and the OWA URL, most likely the Exchange plugin is not enabled. Please enable it (go to "Edit | Plugins") and try to create the account. You will see the username and OWA URL fields. And you will be able to proceed, once you authenticate. 
 [[edit]("http://www.go-evolution.org/index.php?title=FAQ&action=edit&section=113")]
** How can I access other users' Exchange calendars? **

 Evolution Exchange supports viewing other user's folders of all types. In Evolution 2.4 or later, there should be a menu item called "Subscribe to other user's Calendar", under the "File" option in the Calendar component. In Evolution 2.2, go to Exchange view and subscribe to the other user's folder ("Actions > Subscribe to other user's folder"), then go to the particular view to access the folder you have subscribed to.

---

### Post by paulw2 on 2009-09-05
Yes, I had come across that too, but the link to Evolution Brutus Plugin is broken, which doesn't inspire much confidence...

Have you actually accomplished this?

Paul

---

### Post by flipper9 on 2009-09-06
The developers won't support OWA for political reasons or nobody has the will to support Microsoft's products.  If you are left out in the cold, like me, with no control over my Exchange server you just have to resort to using OWA through Firefox and ditch Evolution.

---

### Post by paulw2 on 2009-09-06
I would have thought this would be easier than it is...
 
I have tried to follow the suggestions from Evolution's FAQ about connecting to Exchange, but I am stuck on the very first step.  I cannot confirm that I have "Evolution Exchange".  I have the default installation of Ubuntu 9.04 which seems to be just plain Evolution.  I do not have a plugin for Exchange listed in the plugins.
 
As a newbie, I have no idea how to install the "Evolution Exchange" version.  I am only able to find source code, and was not able to compile it as some libraries are missing.  I'm probably going about this all wrong...
 
Any suggestions, anybody??
 
Paul

---

### Post by makariolewis on 2009-09-06
Do you know if the package "evolution-mapi" is installed? That is the evolution extension for MS Exchange 2007. You can check by going to System > Administration > Synaptic Package Manager, and searching for "evolution-mapi." (Or you can just type "sudo apt-get install evolution-mapi" into a terminal.)

---

### Post by twright on 2009-09-06
I think that 9.04 supports exchange - it was one of the big feature in 9.04 and as far as I know should work with 2009.

If not then Outlook 2007 works well under wine

---

### Post by paulw2 on 2009-09-06
OK, I feel like I am getting closer...

I have installed the MAPI plugin.

Now when I try to setup my account in Evolution, I have the option of "Exchange MAPI" for the server type.  However, I still can't seem to connect to the server.  I have tried the IP addresses (i.e. as numbers rather than names.)  This doesn't seem to help.  When I try to authenticate the server, there is a LONG delay, and then I get:[INDENT]Authentication failed.
MapiLogonProvider:MAPI_E_NETWORK_ERROR
[/INDENT]Configuring Outlook to connect to my exchange server was moderately complicated, so I wonder if this all has something to do with how my Exchange server is setup.  I have the instructions for setting up Oulook that I got from IT at my University.  When I asked for help setting up Evolution they told me that Evolution does not support Exchange 2007.  Here are the instructions - maybe someone can figure out how to translate this to Ubuntu...[INDENT][SIZE=2]Part 1: Add the DNS suffix campus.mcgill.ca (Windows XP or higher)[/SIZE] 
[SIZE=2]1. Right-click on My Network Places and select Properties.[/SIZE]  
[SIZE=2]2. Right-click on Local Area Connection and select Properties.[/SIZE]  
[SIZE=2]3. Select Internet Protocol (TCP/IP) and click Properties.[/SIZE]  
[SIZE=2]4. In the General tab, click Advanced.[/SIZE]  
[SIZE=2]5. In the DNS tab, select Append these DNS suffixes (in order) and click Add.[/SIZE]  
[SIZE=2]6. Type campus.mcgill.ca and click on Add, then OK.[/SIZE] 
[SIZE=2]****************************************[/SIZE] 
[SIZE=2]Part 2 : Configuring Outlook 2003[/SIZE] 
[SIZE=2]1. From My Computer, click on Control Panel and select Mail.[/SIZE]  
[SIZE=2]2. Click on E-mail accounts if available. If not, you will be prompted to create a profile. Click Add.[/SIZE]  
[SIZE=2]3. Choose Add a new e-mail account, and click Next.[/SIZE]  
[SIZE=2]4. Select Microsoft Exchange Server, and click Next.[/SIZE] 
[SIZE=2]5. Fill in the fields:[/SIZE]  
[SIZE=2]Microsoft Exchange Server - 'exchange2vs1.campus.mcgill.ca'[/SIZE]  
[SIZE=2]User Name - enter your name[/SIZE] 
[SIZE=2]6. click More Settings and go to the Connection tab[/SIZE]  
[SIZE=2]7. at the bottom of the Connection tab check "Connect to the Microsoft Exchange Server using HTTP and then click "Exchange Proxy Settings..."[/SIZE]
[SIZE=2]8. Fill in the fields:[/SIZE]  
[SIZE=2][https://exchange.mcgill.ca]("https://exchange.mcgill.ca/")[/SIZE]  
[SIZE=2]check "Connect using SSL Only"[/SIZE]  
[SIZE=2]check "On slow networks, connect using HTTP first, then connect using TCP/IP[/SIZE]  
[SIZE=2]Proxy authentication settings: NTLM Authentication[/SIZE]  
[SIZE=2]the press OK to go back to the Connection tab then press OK again[/SIZE] 
[SIZE=2]9. Press Check Name. Outlook will attempt to find your email address in the Global Address List (GAL). Note: You must have first published your McGill Email Address in the Staff Directory.[/SIZE]
[SIZE=2]10. Fill in the appropriate information, depending on which window is displayed:[/SIZE]
[SIZE=2]User Name - McGill Username (firstname.lastname@mcgill.ca)[/SIZE]
[SIZE=2]Password - McGill Password[/SIZE]
[SIZE=2]Domain Name - campus[/SIZE]
[SIZE=2]11. Click Next and click Yes at the warning message. Click Finish.[/SIZE]
[SIZE=2]12. Click on E-Mail Accounts again.[/SIZE]
[SIZE=2]13. Choose View or change existing e-mail account and click Next.[/SIZE]
[SIZE=2]14. Under Deliver new e-mail to the following location, choose Mailbox - and click Finish.[/SIZE]
[SIZE=2]15. Click OK at the warning message and close the Mail Setup window.[/SIZE][/INDENT]Thanks, everyone, for all the help.

Paul

---

### Post by twright on 2009-09-07
I think that you could just about do the equivalent of those steps after a bit of pain. First I recommend finding and adding the advanced network preferences tool for the first step.

---

### Post by knight187 on 2009-09-07
Evolution won't work, use thunderbird and davmail to connect to exchange 07 here is a link

[http://www.brucerenner.org/linux-and-exchange-2007](http://www.brucerenner.org/linux-and-exchange-2007)

Good luck, Cheers

---

### Post by paulw2 on 2009-09-07
Failed on both accounts.  Even with the advanced network preferences, I cannot seem to connect:

I installed the package.
I'm not sure if I ran it correctly - I used System>Administration>Network
I then added DNS Search domain "campus.mcgill.ca"
I cannot figure out where to add a proxy.
Then made several more attempts to configure Evolution - all failed.

With respect to DavMail:

Downloaded and installed it.  I noted that there were some messages in the window as it was installing, but it seems to have installed.
I then tried to add a calendar.  I've gotten to the point where it asks me to "Enter username and password for 'DavMail Gateway" at http://localhost:1080'" - I have tried "\home\paul" and "\[my computer name]\paul" but it just keeps re-asking.

Any suggestions?

Paul

---

### Post by paulw2 on 2009-09-07
What a moron I am...  Thunderbird was asking for my account settings for Exchange - I thought it was asking for my user account on the computer!  It seems to work now.

I got a lot of messages about the server and local calendar having different values (somehow related to the dozens of "reminders" it found.)  I hope that doesn't mess up my calendar...

Thanks to everyone for all the help.

I would still be happier if I could get Evolution to connect...

Paul

---

### Post by tmugan on 2009-11-13
I'm able to use Exchange 2007 under Karmic if I grab the latest updates to the MAPI plugin and install manually.
(It has not been added to the Ubuntu repos yet for Karmic.)

Follow the steps here...

[http://www.mugan.com/2009/11/03/usin...exchange-2007/]("http://www.mugan.com/2009/11/03/using-evolution-with-exchange-2007/")

:p

---

### Post by paulw2 on 2009-11-14
Thank you so much for this information.  I was able to do the installation without any difficulty.  Unfortunately I still seem unable to get past the authenticate step in the Evolution setup assistant.  According to the instructions I have for how to setup my account on Outlook, I need to add a DNS suffix.  I did this by System Settings > Network Settings.  I then edited my network connections, clicked on IP Address, changed Configure to "Automatic (DHCP_ addresses only and added the DNS to "Search Domains").

I also require a proxy which is setup within Outlook.  I have tried adding this as a proxy server in network settings for HTTPS addresses.

For my Server I have used the server that is marked in Outlook (EXMBXVS2.campus.wherever.ca).  Username - my name before the @ in my e-mail address, Domain - that which is after the @.

When I authenticate I get a request for the password for [email]first.last@EXMBXVS2.campus.wherever.ca[/email].

After a few minutes delay. I get this error: Authentication failed.
MapiLogonProvider:MAPI_E_NETWORK_ERROR

Any suggestions?

Paul

---

### Post by jeb800e on 2009-11-14
Have you tried Zimbra? According to osalt.org, it is a Microsoft Exchange Server 2003 open sourced alternative, and, of course, it is available for Linux!

---

### Post by twright on 2009-11-16
> **jeb800e said:**
> Have you tried Zimbra? According to osalt.org, it is a Microsoft Exchange Server 2003 open sourced alternative, and, of course, it is available for Linux!
It is a nice idea but not much use when your IT department etc. already mandates Exchange :-)

---

### Post by tobydeemer on 2009-11-20
I also have this authentication issue. 

I have tried the server FQDN, IP Address, owa address, etc. All result in the same authentication error.

I also tried the updating process provided by tmugan here:
[http://www.mugan.com/2009/11/03/using-evolution-with-exchange-2007/](http://www.mugan.com/2009/11/03/using-evolution-with-exchange-2007/)

I'm stuck in an "authentication loop".

Anyone have any ideas?

Thanks.

---

### Post by PhrygianCat on 2009-12-02
tobydeemer, if your email address is [email]tobydeemer@domain.com[/email], you should try using tobydeemer as the username and domain.com (including the .com). That's what 'worked' for me on 0.28.0. I put worked in quotes because it wasn't stable. I'll probably try 0.28.1 soon.

---

### Post by tobydeemer on 2009-12-31
Sorry it's been a while.... work and life are crazy. 

I am trying this now..

Will update w/ success (hopefully) or otherwise when completed.

Thanks.

---

### Post by tobydeemer on 2010-01-02
> **tobydeemer said:**
> Sorry it's been a while.... work and life are crazy. 

I am trying this now..

Will update w/ success (hopefully) or otherwise when completed.

Thanks.

No luck here...

---

### Post by rafitaa` on 2010-01-07
HI I am currently running Davmail version 3.6.1-853 with Thunderbird 2.0.0.23 on Karmic. Now the weird thing is that when I am at my office (on the corporate network) using the internal OWA link it works just fine, however I just change the server to the external link and it is giving me the following errors (note that I am able to login to the external OWA link on Firefox without issues)

*****************************************************************************
Date:            Thu Jan 07 08:35:58 CST 2010 (1262874958699)
Thread:        ImapConnection-51123
Message #:    9
Level:        ERROR
NDC:            
Category:    davmail
Message:        DavMail configuration exception:
Connect exception: davmail.exception.DavMailException Unable to connect to OWA at [https://mail.extranet.domain.com/OWA/rafaell@domain.com](https://mail.extranet.domain.com/OWA/rafaell@domain.com), status code 500, check configuration
Location:    davmail.ui.tray.DavGatewayTray.displayMessage(DavGatewayTray.java:113)
Thrown:
davmail.exception.DavMailException: DavMail configuration exception:
Connect exception: davmail.exception.DavMailException Unable to connect to OWA at [https://mail.extranet.domain.com/OWA/rafaell@domain.com](https://mail.extranet.domain.com/OWA/rafaell@domain.com), status code 500, check configuration
    at davmail.exchange.ExchangeSessionFactory.handleNetworkDown(ExchangeSessionFactory.java:206)
    at davmail.exchange.ExchangeSessionFactory.checkConfig(ExchangeSessionFactory.java:185)
    at davmail.imap.ImapConnection.run(ImapConnection.java:66)

*****************************************************************************

And

*****************************************************************************
Date:            Thu Jan 07 08:35:58 CST 2010 (1262874958710)
Thread:        ImapConnection-51123
Message #:    10
Level:        DEBUG
NDC:            
Category:    davmail
Message:        > * BYE unable to handle request: DavMail configuration exception: Connect exception: davmail.exception.DavMailException Unable to connect to OWA at [https://mail.extranet.domain.com/OWA/rafaell@domain.com](https://mail.extranet.domain.com/OWA/rafaell@domain.com), status code 500, check configuration
Location:    davmail.ui.tray.DavGatewayTray.displayMessage(DavGatewayTray.java:96)
Thrown:
*****************************************************************************


And

*****************************************************************************
Date:            Thu Jan 07 08:43:35 CST 2010 (1262875415932)
Thread:        CaldavConnection-60231
Message #:    27
Level:        ERROR
NDC:            
Category:    davmail
Message:        Exchange login exception: Connection timed out
Location:    davmail.ui.tray.DavGatewayTray.displayMessage(DavGatewayTray.java:113)
Thrown:
davmail.exception.DavMailException: Exchange login exception: Connection timed out
    at davmail.exchange.ExchangeSession.<init>(ExchangeSession.java:236)
    at davmail.exchange.ExchangeSessionFactory.getInstance(ExchangeSessionFactory.java:106)
    at davmail.caldav.CaldavConnection.run(CaldavConnection.java:162)
*****************************************************************************
And

*****************************************************************************
Date:            Thu Jan 07 08:43:35 CST 2010 (1262875415933)
Thread:        CaldavConnection-60231
Message #:    28
Level:        DEBUG
NDC:            
Category:    davmail
Message:        > HTTP/1.1 503 Service Unavailable
Location:    davmail.ui.tray.DavGatewayTray.displayMessage(DavGatewayTray.java:96)
*****************************************************************************

And finally


*****************************************************************************
Date:            Thu Jan 07 08:43:35 CST 2010 (1262875415934)
Thread:        CaldavConnection-60231
Message #:    29
Level:        DEBUG
NDC:            
Category:    davmail
Message:        Exception sending error to client Socket closed
Location:    davmail.ui.tray.DavGatewayTray.displayMessage(DavGatewayTray.java:113)
Thrown:
java.net.SocketException: Socket closed
    at java.net.SocketOutputStream.socketWrite(SocketOutputStream.java:99)
    at java.net.SocketOutputStream.write(SocketOutputStream.java:136)
    at java.io.BufferedOutputStream.flushBuffer(BufferedOutputStream.java:65)
    at java.io.BufferedOutputStream.flush(BufferedOutputStream.java:123)
    at davmail.AbstractConnection.sendClient(AbstractConnection.java:113)
    at davmail.AbstractConnection.sendClient(AbstractConnection.java:93)
    at davmail.caldav.CaldavConnection.sendHttpResponse(CaldavConnection.java:1000)
    at davmail.caldav.CaldavConnection.sendHttpResponse(CaldavConnection.java:985)
    at davmail.caldav.CaldavConnection.sendErr(CaldavConnection.java:914)
    at davmail.caldav.CaldavConnection.sendErr(CaldavConnection.java:891)
    at davmail.caldav.CaldavConnection.run(CaldavConnection.java:179)

*****************************************************************************


Any ideas wll be appreciated.

THNX!

---

### Post by LittleLebowski on 2010-04-14
What's the best way to get Evolution 2.22.31 or later running in 9.10?  It supports Exchange 2007.

---

### Post by PeteLong on 2011-01-19
I know this is an old thread so apologies - but It appears to work fine with Exchange 2007 and Exchange 2010 now

[Connecting Evolution Mail Client to Exchange 2010 (and Exchange 2007]("http://www.petenetlive.com/KB/Article/0000378.htm"))

Pete

---

### Post by nicolito on 2011-03-23
I like Petelongs solution. 
No matter how I try though, together with the IT-staff at my university, we can't make it connect to the server.
For some reason imap+ connected and synched to the mailbox imediately. 
This does not connect the calendar as far as I can see.
I am not totaly familiar with these protocols. Is there any other drawback to using imap+ over mapi (which doesn't work anyway)?

---

### Post by sundman on 2012-08-23
The message [http://gnome-evolution-general.1774414.n4.nabble.com/Problems-with-Exchange-MAPI-tp2992416p2994075.html]("http://gnome-evolution-general.1774414.n4.nabble.com/Problems-with-Exchange-MAPI-tp2992416p2994075.html") lead me to in the right direction identifying which server actually provides MAPI. You find it in OWA's Settings - About - Mailbox Server Name.

---

### Post by smcclenahan on 2012-08-23
> **sundman said:**
> The message [http://gnome-evolution-general.1774414.n4.nabble.com/Problems-with-Exchange-MAPI-tp2992416p2994075.html]("http://gnome-evolution-general.1774414.n4.nabble.com/Problems-with-Exchange-MAPI-tp2992416p2994075.html") lead me to in the right direction identifying which server actually provides MAPI. You find it in OWA's Settings - About - Mailbox Server Name.

Nice find, but as someone said there's a known issue with the plugin that it does not support proxied connections. It looks like the OP has exactly this problem.

---

