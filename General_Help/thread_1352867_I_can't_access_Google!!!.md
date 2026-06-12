---
title: "I can't access Google!!!"
date: 2009-12-12
forum: General Help
---

### Post by Elludium_Q-36 on 2009-12-12
This system has always been a little wonky but I have Jaunty and had been able to access Google and Gmail but after I tried to upgrade and install a few files, no dice.

I can get to images.google.com fine, msn.com, yahoo.com but not google.com, [www.google.com](www.google.com), mail.google.com

I tried with every browser I have on the box but no joy!  I have to use a proxy to get to google or gmail.

Also the upgrade/install did not execute the scripts properly via adept as no new items appeared in the application launcher menu automatically.  I'd have to do it manually.

I only upgraded to Jaunty for Barry but I have corrupted files and synaptic doesn't completely remove them as nothing is downloaded when installing anew. 

Is there a global command to backup my data & preferences?  Maybe I should get a later copy of Jaunty from Ubuntu.  I'm on Kubuntu and have read that may be part of the trouble.

---

### Post by bruno9779 on 2009-12-12
To determine if it is a DNS error, try to open this IP: 209.85.229.99

It is google IP, if your browser opens it you have a DNS issue.

You could back up your /home entirely, or better yet, move it to its own partition.

[Here]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/") a good tutorial for that

---

### Post by Elludium_Q-36 on 2009-12-12
Thanks Bruno!

Yes I can access 209.85.229.99 but can only go to images.google.com or video.google.com .

Some sort of gatekeeper daemon?

I hadn't touched any configuration.  I don't have guidedog configured to do anything and didn't touch guarddog in a while.  I have as blocked: google-analytics.com googlesyndication.com and googleapis.com but that's never been a problem in the past.

So if I do a fresh install with the same distro and version on the same branch, just replacing my /home files should do the trick, once I've reinstalled any applications?

---

### Post by bruno9779 on 2009-12-12
it seems like it is a dns issue.

Go to [http://www.opendns.com/](http://www.opendns.com/) and replace your dns servers.

that should do the trick

---

### Post by bruno9779 on 2009-12-12
and, when you reinstall, copy your /home only after installing all the applications, or the config files (in the .* folders in /home) may get overwritten.

PS: you should address your questions on backing up /home on a different thread

---

### Post by hartl_vienna on 2009-12-12
I have the same problem since yesterday evening. I didn't change anything. I only have problems with google every other site is OK. Sometimes it works and 5  Minutes later it stops working.

bruno9779: I'm not able to open 209.85.229.99. Wether with Karmic nor with Win7.

---

### Post by Elludium_Q-36 on 2009-12-12
Mine is a single Kubuntu desktop box accessing via KPPP over a tethered connection and is not a network/lan/server setup.

Hartl, I used a proxy as a stop-gap 'till I can get it resolved.  I found some on [http://proxy.org/](http://proxy.org/)

---

### Post by hartl_vienna on 2009-12-12
Thanks, I'll try it. But this is a really strange problem! Is it possible that Google has a problem? Because it's only occurs with Google sites.

---

### Post by Elludium_Q-36 on 2009-12-12
Seems doubtful that Google itself is on the fritz as access is their fuel and they're BIG business.  Countless scores of people would be screaming!

As Bruno suggest, it seems DNS related but at our ISP, routing tables, etc.
If I knew their structure for a query string I could see if 209.85.229.99 could take me to a successful search.

Odd that you can't even get to the IPv4 IP address... You say you tried with windows-7...  

Actually I think I did just upgrade KPPP to Version: 4.4.2.4-0ubuntu1~jaunty2 (jaunty-backports).  It's set to automatic DNS.  Maybe someone could suggest a few and I'll try them in Manual setting or I could revert to 4.4.2.2.


-Version-
Kernel		: Linux 2.6.28-15-generic (i686)
Compiled		: #48-Ubuntu SMP Wed Jul 29 08:54:56 UTC 2009
C Library		: GNU C Library version 2.9 (stable)
Distribution		: Ubuntu 9.04
-Current Session-
Computer Name		: kubuntu
User Name		: kubuntu (kubuntu)
Home Directory		: /home/kubuntu
Desktop Environment		: Unknown (Window Manager: KWin)
-Misc-
Uptime		: 1 day, 9 hours and 38 minutes
Load Average		: 1.22, 1.14, 0.99

-Computer-
Processor		: AMD Athlon(tm) XP 3200+
Memory		: 703MB (627MB used)
Operating System		: Ubuntu 9.04
User Name		: kubuntu (kubuntu)

X11 Vendor		: The X.Org Foundation
-Multimedia-

---

### Post by Elludium_Q-36 on 2009-12-13
I did some searching, without Google...

They want you to replace your ISP's DNS with theirs ( 8.8.8.8 & 8.8.4.4).  I just added them to the current list but that did nothing!!!

I found a way to get to the normal widget/gui page with the following URL/query/string:  
http://209.85.229.99/search?hl=en&site=universal&q=linux&btnG=Search

It works normally and I can just type a search phrase into the text box in place of "Linux".

No luck getting to Gmail normally or Googlemail.com by domain name or IP but they may just redirect to mail.google.com/mail/?ui=2 or thusandsuch.

Any ideas?

---

### Post by Elludium_Q-36 on 2010-01-04
Anyone else have any ideas?

It seems to come and go randomly but it's usually not accessible.

The proxys are SOMEWHAT usable but not really and the ones I've tried are not secure, no https://   or ssl.

---

### Post by Elludium_Q-36 on 2010-01-31
All but solved...

From my Blocked area of Guarddog, I removed: 

google-analytics.com

googlesyndication.com

googleapis.com

and can now use Google services.
It had not been a problem before, blocking those websites but apparently ol' Google wants more compromise in privacy and security, in exchange for the convenience of it's services.

I have only allowed google.com in the No-Script add on of Firefox.
I note that for these forums, yahooapis.com wants to run scripts...

If I can remove any of the google sites and still have the services, I will repost.

---

