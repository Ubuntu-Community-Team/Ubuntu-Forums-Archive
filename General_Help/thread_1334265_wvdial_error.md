---
title: "wvdial error"
date: 2009-11-22
forum: General Help
---

### Post by anikondemand on 2009-11-22
Configured my usb cdma dialup modem successfully. Facing problem with dialing.

wvdial gives me the following output.
> --> Ignoring malformed input line: "Auto DNS"
--> Ignoring malformed input line: "Check Def Route"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: at+crm=1;+cmux=1;+cps=33;+cta=0
at+crm=1;+cmux=1;+cps=33;+cta=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
~[7f]}#@!}!}!} }-}#}%B#}%}'}"}(}"{B~
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Sun Nov 22 14:14:07 2009
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 6746
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08][10]&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08][10]&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08][10]&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08][10]&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08][10]&#65533;[06][08]
--> Disconnecting at Sun Nov 22 14:14:10 2009
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)

All configurations are done as per the advice followed from some other thread here.
The usn/pwd given in my wvdial file is the same which I use it in Windows.

This is my wvdial configuration file.
> [Dialer Defaults]

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 = at+crm=1;+cmux=1;+cps=33;+cta=0

Modem Type = Analog Modem

ISDN = 0

Phone = #777

Modem = /dev/ttyUSB0

Username = <username>
Password = <password>
Baud = 460800

Stupid Mode = 1

Auto DNS

Check Def Route


Help.

---

### Post by AlphaLexman on 2009-11-22
When you run wvdial, try running it with sudo:

```
sudo wvdial
```

---

### Post by anikondemand on 2009-11-22
I will try it bro. You are doing a great help. Thanks a lot.

---

### Post by anikondemand on 2009-11-22
Update :

[IMG]http://i50.tinypic.com/1gp0tc.png[/IMG]

Cursor stops responding there. My phone still shows "Data call in progress".

Screenshots :
[http://tinypic.com/r/1gp0tc/6](http://tinypic.com/r/1gp0tc/6)

[http://i50.tinypic.com/1gp0tc.png](http://i50.tinypic.com/1gp0tc.png)

---

### Post by AlphaLexman on 2009-11-22
> **anikondemand said:**
> Update :
Cursor stops responding there. My phone still shows "Data call in progress".
  

Yes, it will and should. You should be online if you are getting IP and DNS entries.
If you close the terminal it will kill your connection.

Option: [Alt-F2]

```
gksu wvdial
```

---

### Post by anikondemand on 2009-11-22
Tried gksu wvdial. No response.

---

### Post by anikondemand on 2009-11-23
Help.

---

### Post by anikondemand on 2009-11-23
Pls help.

---

### Post by t0p on 2009-11-23
When you run

```
sudo wvdial
```wvdial runs, you get output, then wvdial appears to "hang", right?  Well, you are connected to the internet, and you should be able to browse the web.  You kill the internet connection by going back to the wvdial terminal and hitting Ctrl-C.

Try this: run "sudo wvdial", then, when output appears to "hang", open another terminal and type in 

```
ping -c 5 google.com
```What output do you get?

---

### Post by anikondemand on 2009-11-23
> **t0p said:**
> When you run

```
sudo wvdial
```wvdial runs, you get output, then wvdial appears to "hang", right?  Well, you are connected to the internet, and you should be able to browse the web.  You kill the internet connection by going back to the wvdial terminal and hitting Ctrl-C.

Try this: run "sudo wvdial", then, when output appears to "hang", open another terminal and type in 

```
ping -c 5 google.com
```What output do you get?

Will check it and post the result here.

---

### Post by anikondemand on 2009-11-23
> **t0p said:**
> When you run

```
sudo wvdial
```wvdial runs, you get output, then wvdial appears to "hang", right?  Well, you are connected to the internet, and you should be able to browse the web.  You kill the internet connection by going back to the wvdial terminal and hitting Ctrl-C.

Try this: run "sudo wvdial", then, when output appears to "hang", open another terminal and type in 

```
ping -c 5 google.com
```What output do you get?

This output I'm getting.
[IMG]http://i47.tinypic.com/rtgr45.png[/IMG]

Does this mean that I'm online now? No loss is pinging.

Then what is the problem? My network connection icon in the taskbar is not active. I'm not able to browse through any browsers:(.

Help pls.

---

### Post by anikondemand on 2009-11-23
Help pls.

---

### Post by t0p on 2009-11-23
> **anikondemand said:**
> This output I'm getting.

Uh, what output?  You haven't actually posted the output you're getting from the ping command.
[IMG]http://i47.tinypic.com/rtgr45.png[/IMG]
> **anikondemand said:**
> 
Does this mean that I'm online now? No loss is pinging.

Then what is the problem? My network connection icon in the taskbar is not active. I'm not able to browse through any browsers:(.

Help pls.

Okay, I need you to post more details.

What output do you get from the following commands:

```
ping -c 5 google.com
```and

```
whois google.com
```If you're getting meaningful output (ie not just "can't resolve host blah blah" kind of stuff) then yes, you are online.

Don't worry about the fact that the Network Manager applet doesn't show you're online.  You're not actually using the Network Manager - wvdial is a separate process.

I'm going to assume that Firefox isn't working.  So type the following command into a terminal:

```
firefox
```and post the output here.

Please post here the actual output that you get from the commands.  We may be able to diagnose the problem if you cut and paste the output.  If you just say "Yes it worked" or "No it didn't work" we can't actually determine what might be happening.

---

### Post by anikondemand on 2009-11-23
Will post the output here. Let me check it.

---

### Post by anikondemand on 2009-11-23
Output of "ping -c 5 google.com" :

[IMG]http://i47.tinypic.com/302422w.png[/IMG]

Actually, I'm getting this output only. I think this is supposed to be the output of a ping command.

Output of "whois google.com" :

> Whois Server Version 2.0

Domain names in the .com and .net domains can now be registered
with many different competing registrars. Go to [http://www.internic.net](http://www.internic.net)
for detailed information.

   Server Name: GOOGLE.COM.ZZZZZ.GET.LAID.AT.[WWW.SWINGINGCOMMUNITY.COM](WWW.SWINGINGCOMMUNITY.COM)
   IP Address: 69.41.185.195
   Registrar: TUCOWS INC.
   Whois Server: whois.tucows.com
   Referral URL: [http://domainhelp.opensrs.net](http://domainhelp.opensrs.net)

   Server Name: GOOGLE.COM.ZZZZZ.DOWNLOAD.MOVIE.ONLINE.ZML2.COM
   IP Address: 64.28.187.63
   Registrar: DIRECTI INTERNET SOLUTIONS PVT. LTD. D/B/A PUBLICDOMAINREGISTRY.COM
   Whois Server: whois.PublicDomainRegistry.com
   Referral URL: [http://www.PublicDomainRegistry.com](http://www.PublicDomainRegistry.com)

   Server Name: GOOGLE.COM.ZOMBIED.AND.HACKED.BY.[WWW.WEB-HACK.COM](WWW.WEB-HACK.COM)
   IP Address: 217.107.217.167
   Registrar: DOMAINCONTEXT, INC.
   Whois Server: whois.domaincontext.com
   Referral URL: [http://www.domaincontext.com](http://www.domaincontext.com)

   Server Name: GOOGLE.COM.ZNAET.PRODOMEN.COM
   IP Address: 62.149.23.126
   Registrar: DIRECTI INTERNET SOLUTIONS PVT. LTD. D/B/A PUBLICDOMAINREGISTRY.COM
   Whois Server: whois.PublicDomainRegistry.com
   Referral URL: [http://www.PublicDomainRegistry.com](http://www.PublicDomainRegistry.com)

   Server Name: GOOGLE.COM.WORDT.DOOR.VEEL.WHTERS.GEBRUIKT.SERVERTJE.NET
   IP Address: 62.41.27.144
   Registrar: KEY-SYSTEMS GMBH
   Whois Server: whois.rrpproxy.net
   Referral URL: [http://www.key-systems.net](http://www.key-systems.net)

   Server Name: GOOGLE.COM.VN
   Registrar: ONLINENIC, INC.
   Whois Server: whois.onlinenic.com
   Referral URL: [http://www.OnlineNIC.com](http://www.OnlineNIC.com)

   Server Name: GOOGLE.COM.UY
   Registrar: DIRECTI INTERNET SOLUTIONS PVT. LTD. D/B/A PUBLICDOMAINREGISTRY.COM
   Whois Server: whois.PublicDomainRegistry.com
   Referral URL: [http://www.PublicDomainRegistry.com](http://www.PublicDomainRegistry.com)

   Server Name: GOOGLE.COM.UA
   Registrar: DIRECTI INTERNET SOLUTIONS PVT. LTD. D/B/A PUBLICDOMAINREGISTRY.COM
   Whois Server: whois.PublicDomainRegistry.com
   Referral URL: [http://www.PublicDomainRegistry.com](http://www.PublicDomainRegistry.com)

   Server Name: GOOGLE.COM.TW
   Registrar: WEB COMMERCE COMMUNICATIONS LIMITED DBA WEBNIC.CC
   Whois Server: whois.webnic.cc
   Referral URL: [http://www.webnic.cc](http://www.webnic.cc)

   Server Name: GOOGLE.COM.TR
   Registrar: DIRECTI INTERNET SOLUTIONS PVT. LTD. D/B/A PUBLICDOMAINREGISTRY.COM
   Whois Server: whois.PublicDomainRegistry.com
   Referral URL: [http://www.PublicDomainRegistry.com](http://www.PublicDomainRegistry.com)

   Server Name: GOOGLE.COM.SUCKS.FIND.CRACKZ.WITH.SEARCH.GULLI.COM
   IP Address: 80.190.192.24
   Registrar: EPAG DOMAINSERVICES GMBH
   Whois Server: whois.enterprice.net
   Referral URL: [http://www.enterprice.net](http://www.enterprice.net)

   Server Name: GOOGLE.COM.SPROSIUYANDEKSA.RU
   Registrar: MELBOURNE IT, LTD. D/B/A INTERNET NAMES WORLDWIDE
   Whois Server: whois.melbourneit.com
   Referral URL: [http://www.melbourneit.com](http://www.melbourneit.com)

   Server Name: GOOGLE.COM.SERVES.PR0N.FOR.ALLIYAH.NET
   IP Address: 84.255.209.69
   Registrar: GODADDY.COM, INC.
   Whois Server: whois.godaddy.com
   Referral URL: [http://registrar.godaddy.com](http://registrar.godaddy.com)

   Server Name: GOOGLE.COM.SA
   Registrar: OMNIS NETWORK, LLC
   Whois Server: whois.omnis.com
   Referral URL: [http://domains.omnis.com](http://domains.omnis.com)

   Server Name: GOOGLE.COM.MX
   Registrar: DIRECTI INTERNET SOLUTIONS PVT. LTD. D/B/A PUBLICDOMAINREGISTRY.COM
   Whois Server: whois.PublicDomainRegistry.com
   Referral URL: [http://www.PublicDomainRegistry.com](http://www.PublicDomainRegistry.com)

   Server Name: GOOGLE.COM.IS.****.SQUAREBOARDS.COM
   IP Address: 203.170.84.81
   Registrar: AUST DOMAINS INTERNATIONAL PTY LTD DBA AUST DOMAINS, INC.
   Whois Server: whois.syra.com.au
   Referral URL: [http://www.syra.com.au](http://www.syra.com.au)

   Server Name: GOOGLE.COM.IS.NOT.HOSTED.BY.ACTIVEDOMAINDNS.NET
   IP Address: 217.148.161.5
   Registrar: ENOM, INC.
   Whois Server: whois.enom.com
   Referral URL: [http://www.enom.com](http://www.enom.com)

   Server Name: GOOGLE.COM.IS.HOSTED.ON.PROFITHOSTING.NET
   IP Address: 66.49.213.213
   Registrar: NAME.COM LLC
   Whois Server: whois.name.com
   Referral URL: [http://www.name.com](http://www.name.com)

   Server Name: GOOGLE.COM.IS.APPROVED.BY.NUMEA.COM
   IP Address: 213.228.0.43
   Registrar: GANDI SAS
   Whois Server: whois.gandi.net
   Referral URL: [http://www.gandi.net](http://www.gandi.net)

   Server Name: GOOGLE.COM.HAS.LESS.FREE.PORN.IN.ITS.SEARCH.ENGINE.THAN.SECZY.COM
   IP Address: 209.187.114.130
   Registrar: TUCOWS INC.
   Whois Server: whois.tucows.com
   Referral URL: [http://domainhelp.opensrs.net](http://domainhelp.opensrs.net)

   Server Name: GOOGLE.COM.DO
   Registrar: GODADDY.COM, INC.
   Whois Server: whois.godaddy.com
   Referral URL: [http://registrar.godaddy.com](http://registrar.godaddy.com)

   Server Name: GOOGLE.COM.CO
   Registrar: NAMESECURE.COM
   Whois Server: whois.namesecure.com
   Referral URL: [http://www.namesecure.com](http://www.namesecure.com)

   Server Name: GOOGLE.COM.CHIQUITASEXY.COM
   IP Address: 97.74.144.165
   Registrar: DIRECTI INTERNET SOLUTIONS PVT. LTD. D/B/A PUBLICDOMAINREGISTRY.COM
   Whois Server: whois.PublicDomainRegistry.com
   Referral URL: [http://www.PublicDomainRegistry.com](http://www.PublicDomainRegistry.com)

   Server Name: GOOGLE.COM.BR
   Registrar: ENOM, INC.
   Whois Server: whois.enom.com
   Referral URL: [http://www.enom.com](http://www.enom.com)

   Server Name: GOOGLE.COM.BEYONDWHOIS.COM
   IP Address: 203.36.226.2
   Registrar: TUCOWS INC.
   Whois Server: whois.tucows.com
   Referral URL: [http://domainhelp.opensrs.net](http://domainhelp.opensrs.net)

   Server Name: GOOGLE.COM.AU
   Registrar: PLANETDOMAIN PTY LTD.
   Whois Server: whois.planetdomain.com
   Referral URL: [http://www.planetdomain.com](http://www.planetdomain.com)

   Server Name: GOOGLE.COM.AR
   Registrar: ENOM, INC.
   Whois Server: whois.enom.com
   Referral URL: [http://www.enom.com](http://www.enom.com)

   Domain Name: GOOGLE.COM
   Registrar: MARKMONITOR INC.
   Whois Server: whois.markmonitor.com
   Referral URL: [http://www.markmonitor.com](http://www.markmonitor.com)
   Name Server: NS1.GOOGLE.COM
   Name Server: NS2.GOOGLE.COM
   Name Server: NS3.GOOGLE.COM
   Name Server: NS4.GOOGLE.COM
   Status: clientDeleteProhibited
   Status: clientTransferProhibited
   Status: clientUpdateProhibited
   Status: serverDeleteProhibited
   Status: serverTransferProhibited
   Status: serverUpdateProhibited
   Updated Date: 18-nov-2008
   Creation Date: 15-sep-1997
   Expiration Date: 14-sep-2011

>>> Last update of whois database: Mon, 23 Nov 2009 19:52:57 UTC <<<

NOTICE: The expiration date displayed in this record is the date the 
registrar's sponsorship of the domain name registration in the registry is 
currently set to expire. This date does not necessarily reflect the expiration 
date of the domain name registrant's agreement with the sponsoring 
registrar.  Users may consult the sponsoring registrar's Whois database to 
view the registrar's reported date of expiration for this registration.

TERMS OF USE: You are not authorized to access or query our Whois 
database through the use of electronic processes that are high-volume and 
automated except as reasonably necessary to register domain names or 
modify existing registrations; the Data in VeriSign Global Registry 
Services' ("VeriSign") Whois database is provided by VeriSign for 
information purposes only, and to assist persons in obtaining information 
about or related to a domain name registration record. VeriSign does not 
guarantee its accuracy. By submitting a Whois query, you agree to abide 
by the following terms of use: You agree that you may use this Data only 
for lawful purposes and that under no circumstances will you use this Data 
to: (1) allow, enable, or otherwise support the transmission of mass 
unsolicited, commercial advertising or solicitations via e-mail, telephone, 
or facsimile; or (2) enable high volume, automated, electronic processes 
that apply to VeriSign (or its computer systems). The compilation, 
repackaging, dissemination or other use of this Data is expressly 
prohibited without the prior written consent of VeriSign. You agree not to 
use electronic processes that are automated and high-volume to access or 
query the Whois database except as reasonably necessary to register 
domain names or modify existing registrations. VeriSign reserves the right 
to restrict your access to the Whois database in its sole discretion to ensure 
operational stability.  VeriSign may restrict or terminate your access to the 
Whois database for failure to abide by these terms of use. VeriSign 
reserves the right to modify these terms at any time. 

The Registry database contains ONLY .COM, .NET, .EDU domains and
Registrars.
MarkMonitor is the Global Leader in Enterprise Brand Protection.

Domain Management
MarkMonitor Brand Protection&#8482;
AntiFraud Solutions
Corporate Consulting Services

Visit MarkMonitor at [www.markmonitor.com](www.markmonitor.com)
Contact us at 1 800 745 9229
In Europe, at +44 (0) 20 7840 1300 


The Data in MarkMonitor.com's WHOIS database is provided by MarkMonitor.com
for information purposes, and to assist persons in obtaining information
about or related to a domain name registration record.  MarkMonitor.com
does not guarantee its accuracy.  By submitting a WHOIS query, you agree
that you will use this Data only for lawful purposes and that, under no
circumstances will you use this Data to: (1) allow, enable, or otherwise
support the transmission of mass unsolicited, commercial advertising or
solicitations via e-mail (spam); or  (2) enable high volume, automated,
electronic processes that apply to MarkMonitor.com (or its systems).
MarkMonitor.com reserves the right to modify these terms at any time.
By submitting this query, you agree to abide by this policy.

Registrant:
        Dns Admin
        Google Inc.
        Please contact [email]contact-admin@google.com[/email] 1600 Amphitheatre Parkway
         Mountain View CA 94043
        US
        [email]dns-admin@google.com[/email] +1.6502530000 Fax: +1.6506188571

    Domain Name: google.com

        Registrar Name: Markmonitor.com
        Registrar Whois: whois.markmonitor.com
        Registrar Homepage: [http://www.markmonitor.com](http://www.markmonitor.com)

    Administrative Contact:
        DNS Admin
        Google Inc.
        1600 Amphitheatre Parkway
         Mountain View CA 94043
        US
        [email]dns-admin@google.com[/email] +1.6506234000 Fax: +1.6506188571
    Technical Contact, Zone Contact:
        DNS Admin
        Google Inc.
        2400 E. Bayshore Pkwy
         Mountain View CA 94043
        US
        [email]dns-admin@google.com[/email] +1.6503300100 Fax: +1.6506181499

    Created on..............: 1997-09-15.
    Expires on..............: 2011-09-13.
    Record last updated on..: 2009-06-21.

    Domain servers in listed order:

    ns2.google.com
    ns1.google.com
    ns3.google.com
    ns4.google.com
    



MarkMonitor is the Global Leader in Enterprise Brand Protection.

Domain Management
MarkMonitor Brand Protection&#8482;
AntiFraud Solutions
Corporate Consulting Services

Visit MarkMonitor at [www.markmonitor.com](www.markmonitor.com)
Contact us at 1 800 745 9229
In Europe, at +44 (0) 20 7840 1300 


Output of "firefox" :
Firefox browser opens up. I tried entering url. Got this result :
[IMG]http://i46.tinypic.com/fbkowi.png[/IMG]

---

### Post by t0p on 2009-11-23
The output of the "whois" command shows you definitely have internet connection.

Unfortunately you haven't actually posted the output I need from the "firefox" command.  Look at your post above.  You have posted the following:

> Output of "firefox" :
Firefox browser opens up. I tried entering url. Got this result :but you haven't actually shown me the result of the command.

When you type "firefox" into the terminal, the browser window will open.  When you type in an URL, you probably won't get taken to a web page, right?  Well, once you've done that, I want to see *the output that appears in the terminal*; *not* what appears in the browser window.  You see, when you run firefox by typing its name into the terminal, then it can't show you a webpage, error messages will appear in the terminal.  I want to see those error messages.

**EDIT:**  Also, can you type the following into a terminal:

```
w3m www.google.com
```and tell me what happens.  Does an all-text version of the Google homepage appear?  Or do you get an error message?  If so, please post the error message here.

**EDIT2:**  If you click on [this link]("http://www.google.co.uk/#hl=en&safe=off&newwindow=1&q=ubuntu+ping+works+but+no+browser+site%3Aubuntuforums.org&meta=&aq=f&oq=&fp=bb2a258dea5f506b"), you'll see a number of links to other threads in this forum that deal with the same problem.  Maybe reading them will help you.

---

### Post by anikondemand on 2009-11-23
> **t0p said:**
> The output of the "whois" command shows you definitely have internet connection.

Unfortunately you haven't actually posted the output I need from the "firefox" command.  Look at your post above.  You have posted the following:

but you haven't actually shown me the result of the command.

When you type "firefox" into the terminal, the browser window will open.  When you type in an URL, you probably won't get taken to a web page, right?  Well, once you've done that, I want to see *the output that appears in the terminal*; *not* what appears in the browser window.  You see, when you run firefox by typing its name into the terminal, then it can't show you a webpage, error messages will appear in the terminal.  I want to see those error messages.
No response in console even when browser fails.
[IMG]http://i47.tinypic.com/34grf5u.png[/IMG]

> **t0p said:**
> 
**EDIT:**  Also, can you type the following into a terminal:

```
w3m www.google.com
```and tell me what happens.  Does an all-text version of the Google homepage appear?  Or do you get an error message?  If so, please post the error message here.
Got it!
I am able to browse through console. Entered a site, and posted something there. Its working!

But what is wrong when I try using browser?
Any special browser-wvdial configuration required?

---

### Post by anikondemand on 2009-11-23
.

---

### Post by hwttdz on 2009-11-23
It's likely that firefox is being set to offline mode (check to see if file->work offline is checked).  If so you need to uncheck it before you will be able to browse with firefox.  Solutions include removing the network manager and disallowing firefox and pidgin from asking network manager if connected (see post #6 here [http://ubuntuforums.org/showthread.php?t=800179](http://ubuntuforums.org/showthread.php?t=800179) ).

Also realize that people help you here out of the goodness of their hearts and your last post might have come across as ungrateful.

---

### Post by niteshifter on 2009-11-23
Hi,

Ok, wvial is working. To solve the firefox problem:

Connnect with wvdial like you have been.

Start firefox.

When the browser window appears, click File. There's probably a checkmark showing beside the item "Work Offline". If there is:

Click on "Work Offline". This will put Firefox in on-line mode.

Click the Try Again button, or a bookmark, or enter a URL. It should work now.

---

### Post by anikondemand on 2009-11-24
> **hwttdz said:**
> It's likely that firefox is being set to offline mode (check to see if file->work offline is checked).  If so you need to uncheck it before you will be able to browse with firefox.  Solutions include removing the network manager and disallowing firefox and pidgin from asking network manager if connected (see post #6 here [http://ubuntuforums.org/showthread.php?t=800179](http://ubuntuforums.org/showthread.php?t=800179) ).

Also realize that people help you here out of the goodness of their hearts and your last post might have come across as ungrateful.

Thak you. It did work!
I am able to use Firefox now. Sorry if any of my words did not suit the situation.

---

### Post by anikondemand on 2009-11-24
> **niteshifter said:**
> Hi,

Ok, wvial is working. To solve the firefox problem:

Connnect with wvdial like you have been.

Start firefox.

When the browser window appears, click File. There's probably a checkmark showing beside the item "Work Offline". If there is:

Click on "Work Offline". This will put Firefox in on-line mode.

Click the Try Again button, or a bookmark, or enter a URL. It should work now.

Thanks a lot. Working now.

---

### Post by anikondemand on 2009-11-24
> **t0p said:**
> The output of the "whois" command shows you definitely have internet connection.

Unfortunately you haven't actually posted the output I need from the "firefox" command.  Look at your post above.  You have posted the following:

but you haven't actually shown me the result of the command.

When you type "firefox" into the terminal, the browser window will open.  When you type in an URL, you probably won't get taken to a web page, right?  Well, once you've done that, I want to see *the output that appears in the terminal*; *not* what appears in the browser window.  You see, when you run firefox by typing its name into the terminal, then it can't show you a webpage, error messages will appear in the terminal.  I want to see those error messages.

**EDIT:**  Also, can you type the following into a terminal:

```
w3m www.google.com
```and tell me what happens.  Does an all-text version of the Google homepage appear?  Or do you get an error message?  If so, please post the error message here.

**EDIT2:**  If you click on [this link]("http://www.google.co.uk/#hl=en&safe=off&newwindow=1&q=ubuntu+ping+works+but+no+browser+site%3Aubuntuforums.org&meta=&aq=f&oq=&fp=bb2a258dea5f506b"), you'll see a number of links to other threads in this forum that deal with the same problem.  Maybe reading them will help you.
You are awesome man. Its working perfectly now. Thanks a lot for helping.

---

