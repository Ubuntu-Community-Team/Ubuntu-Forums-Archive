---
title: "Evolution and Exchange 2007"
date: 2009-09-13
forum: General Help
---

### Post by paulw2 on 2009-09-13
I just don't get it...

My BlackBerry can sync with my Exchange server using software called AstraSync - I believe it connects using OWA, but I wouldn't swear to it.  It took 5 minutes to setup and I have access to mail, folders, calendar and contacts (personal and company wide.).

WHY is it SO hard to get Evolution do to the same???

Am I missing something?

Is it just me??

Evolution 2.26.1 is supposed to be able to connect with Exchange 2007.  I have tried MAPI.  I have tried Exchange server type.  I cannot get a connection at all.

IT SHOULD NOT BE THIS DIFFICULT!

Can anyone suggest some sane way to do this?

I have setup Thunderbird/Lightning using DavMail - I'm not a fan. Evolution looks like it should do the job nicely, I feel that I'm just having trouble setting it up.

Please help!

Paul

---

### Post by paulw2 on 2009-09-14
Any thoughts anyone?  Any expetaction that 9.10 will deal with this better?
 
While these forums are great, I find that there are common problems that have probably been solved, and I wonder if there is a repository of these solutions?
 
Questions like mine (setting up Evolution and Microsoft Exchange), or using BlackBerry with Ubuntu, or setting up a dual boot environment with two drives.  Issues that many new converts may have that experienced users have struggled with and found something that works with step-by-step instructions.
 
Thanks,
 
Paul
 
PS: I really want to make the transition full time - I'm sick of XP, but while I find Linux fairly easy to "use" I find every setup to be a challenge.  Until I can do MOST of what I do under XP, I will have a hard time convincing the rest of my family to stop booting the computer in XP.

---

### Post by P4man on 2009-09-14
I take it you've already seen this:
[http://library.gnome.org/users/evolution/stable/exchange-configure.html.en](http://library.gnome.org/users/evolution/stable/exchange-configure.html.en)

As for synching with a blackberry.. yeah one wonders what so hard about reverse engineering everything needed to make it work :s. Perhaps you could ask RIM whats so hard about releasing specifications or making a linux client?

---

### Post by P4man on 2009-09-14
BTW, Im not sure if you've seen or tried barry for your blackberry (a new version was released a few weeks ago it seems):
[http://netdirect.ca/software/packages/barry](http://netdirect.ca/software/packages/barry)

In case you're wondering why its so crude, perhaps its worth reading how they are trying to  make it:

[http://netdirect.ca/software/packages/barry/hacking.php](http://netdirect.ca/software/packages/barry/hacking.php)

They run a snoop filter on a USB port while synching a BB in windows, and they are trying to decypher the traffic on the USB cable to work out at the same time the communication protocols and the database structures used in the blackberry from those raw logs.
Like you said, how hard can it be?

You know its fine if people criticize linux for its flaws, but its also good to understand how much of the code you are using came to be: its by such reverse engineering that they made wifi cards work, videocards, that they 'hacked' bioses to make acpi work, while oem's offer no help at all. Sometimes even on the contrary, actively try to make it as hard as possible to do this, like apple with ipod and iphone. After some linux demigods  finally cracked the protocols and filesystem and wrote software to use that, Apple moved to an encypted system. So now linux again "sucks" because it can't even put songs on an ipod or sync with an iPhone.

---

### Post by t0p on 2009-09-14
> **paulw2 said:**
> My BlackBerry can sync with my Exchange server using software called AstraSync - I believe it connects using OWA, but I wouldn't swear to it.  It took 5 minutes to setup and I have access to mail, folders, calendar and contacts (personal and company wide.).

WHY is it SO hard to get Evolution do to the same???


Please try to bear in mind, **Evolution != Exchange**!  Just because Exchange can do something, doesn't mean that Evolution can - nor that it should even be able to.

Also remember that coders have been coding with Windows apps in mind since the dawn of creation.  You know the Big Bang?  That was the Goddess smacking her pc because it had just BSODed on her again.

Saying all that: are you *sure* no one's figured out how to do that which you seek?  Have you googled long and hard on the subject?  Reason I ask is, although I have no interest in Blackberries, I seem to remember seeing stuff about this in these very forums.  But the UF search engine is pretty crappy.  You'd be better off using Google with search parameter **site:ubuntuforums.org**.  Even better, use [Scroogle]("https://ssl.scroogle.org/") - just cos I think it's better-intentioned than Google and could use our support! :p

---

### Post by P4man on 2009-09-14
> **t0p said:**
> Please try to bear in mind, **Evolution != Exchange**!  Just because Exchange can do something, doesn't mean that Evolution can - nor that it should even be able to.

Also remember that coders have been coding with Windows apps in mind since the dawn of creation.  You know the Big Bang?  That was the Goddess smacking her pc because it had just BSODed on her again.

The issue is not how long ppl have been coding. The issue is one of non disclosed protocols. Evolution can connect to Exchange (ab)using the outlook webinterface. Thats the only way, because the protocols outlook uses to sync with exchange or not disclosed. As a result its complex, and rather slow. But it does work cause its not so hard to reverse engineer a webpage. 

If MS would open their protocols or use industry standard protocols, there would be no such issues, but now linux devs have to jump through loops and use hacks to get anything working with proprietary solutions. If the company of the OP would use an opensource or at least open protocol groupware solution, there would be no issue either.

---

### Post by paulw2 on 2009-09-14
I really appreciate the suggestions.  My issue is really with Exchange - the BlackBerry thing was just an example (something I will probably have to do in the future).  I do understand that reverse engineering software can be very difficult, especially when the protocols change at random.  I have googled (I've probably spent 15 hours on this.) Honestly, can't even get a clear cut answer if it is even do'able.  There are many threads that state that Evolution cannot connect with Exchange 2007.  Then there are others that purport to say how to do it, but often without a lot of detail.  I assume older versions of Evolution cannot, but the current version is supposed to.  I am sure that the answers exist out there, but they are really hard to find.  Thats why a section with solutions to common problems would be so useful for us newbies - proven solutions broken down into basic steps.
 
I'm going to speak with the IT people at my University and get some info about their implementation of Exchange to see if this helps with my quest.
 
In terms of the "reverse engineering" to connect with Exchange, I'm just surprised that the company that makes AstraSync has worked it out - all I had to put in was my account name and the name of the exchange server - and that the team working on Evolution hasn't.  In fact, I suspect that they have worked it out but that a mear mortal like me is missing something in the setup process.
 
Can anyone confirm that Evolution can, in fact, connect to Exchange 2007?
 
BTW, I hope nobody thought I was implying in any way that Linux sucks.  I think it is great, and I really look forward to having my system completely setup.  I think, though, that the learning curve for a newbie is underestimated.  Sites like this are really helpful, but I suspect the same questions are asked over and over because sometimes it is hard to find a definitive and clear answer.
 
Thanks again to everyone who has helped.
 
Paul

---

### Post by P4man on 2009-09-14
> **paulw2 said:**
> 
Can anyone confirm that Evolution can, in fact, connect to Exchange 2007?

I was about to say, yes, and then i checked, and our company still uses exchange 2003.
So i googled a bit more and found this:

[http://www.go-evolution.org/FAQ](http://www.go-evolution.org/FAQ)

>  Why can't I connect to Exchange?

First of all, make sure the package "Evolution Exchange" is installed beside Evolution. Make sure the "Exchange plugin" is enabled under "Edit | Plugins". Also, **Evolution Exchange only supports Microsoft Exchange 2000/2003** with OWA (Outlook Web Access) turned on (for WebDAV access). If you would like to connect to an Exchange 5.5, 2000, 2003 or 2007 server via MAPI (as would Outlook), get the Evolution Brutus Plugin at [http://www.omesc.com/node/22](http://www.omesc.com/node/22). Evolution Brutus supports complete access to your Exchange mail, calendar and tasks. If this still does not work, make sure you use "domain\user" and not "domain/user" in the "Evolution Account Editor > Windows Username". 

The link mentioned doesn't work, and further googling suggests its needs a server component to be installed before it works, so its probably not an option either. 

I guess none of this helps you, other than confirming it might be a bit of a problem :s

---

### Post by paulw2 on 2009-09-14
I had found that thread, but I believe it refers to an older version of Evolution.  I have come accross other posts suggesting that the current version of Evolution can do this, but again, with no clear confirmation.
 
Paul

---

### Post by tmugan on 2009-11-13
FYI

I'm able to use Exchange 2007 under Karmic if I grab the latest updates to the MAPI plugin and install manually.
 (It has not been added to the Ubuntu repos yet for Karmic.)

Follow the steps here...

[http://www.mugan.com/2009/11/03/usin...exchange-2007/]("http://www.mugan.com/2009/11/03/using-evolution-with-exchange-2007/")

---

### Post by jcampen on 2010-03-27
For older MS Exchane servers, Evolution is a nightmare and I never managed to get it to work on Evolution. I finally went back to using Thunderbird with the DeMail handler installed and this works well. I posted the forum a solution titled "Thunderbird & DavMail to recieve MS Exchange Server Mail.Need Help" if you want to see the detail

---

