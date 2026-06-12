---
title: "Evolution does not work with Google Apps"
date: 2009-09-28
forum: General Help
---

### Post by rezapiri09 on 2009-09-28
[SIZE=5]I have followed all the directions to sync my Google Apps (myname@mydomain.com) calendar and contacts with Evolution.  This is the error message Evolution spits out for the address book:  [/SIZE]

ERROR LOADING ADDRESS BOOK:

This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.

Detailed error message: Other error

[SIZE=5]For the calendar error, Evolution constantly requests my password and it does not connect[/SIZE]. [SIZE=5]I have have also tried to sync my contacts and calendar through my google phone (mytouch), but that doesn't seem to have integrated functionality either. Can someone please helpme fix this either way? Thanks in advance![/SIZE]

---

### Post by LowSky on 2009-09-28
What istructions did you use,
was it these?
[http://www.linux.com/news/software/applications/8226-how-to-sync-evolution-with-googles-pim-apps](http://www.linux.com/news/software/applications/8226-how-to-sync-evolution-with-googles-pim-apps)
did you check to make sure each step was doe correctly?

AND PLEASE please dont use giant text, people get offended by its use, oh, and welcome to the forums!

---

### Post by rezapiri09 on 2009-09-28
Got it Sky. When I try to extract the archive of Gcaldaemon onto usr/local/sbin I get this error message:

You don't have the right permissions to extract archives in the folder "file:///usr/local/sbin"

I know I have to login as root and I tried to in the terminal (su), but it still did not allow me to extract the files.  what am I doing wrong here?

---

### Post by lasleym on 2009-10-01
LowSky & rezapiri09 - I am having this exact problem, and I did follow the instructions exactly.  

Click new, pick Google, enter user name.  The calendar either won't retrieve the list and/or continuously asks for my PW, whereas the contacts does exactly as rezaprir09 states.  

I installed ubuntu for the first time last week, and it worked.  I messed things up and reinstalled it yesterday with these new Google conflicts.  Any suggestions for fixing would be great.

Thanks.

---

### Post by fazavon on 2009-10-01
I am running Google apps Email, Cal, Contacts all through Evo with no issues. Granted Evolution 2.26.1 was the first one that did not give me issues with my contacts but the rest has been working since 7.04.

Here is what I used to get it working [http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/) Make sure you have IMAP or POP enabled on your account first or it will try to piss on your leg.

As for the Cal, you might need the xxxxx.xml link form your cal, don't remember as I set it all up in 7.04 and have just been restoring from backups as I move up in versions.

//j

---

### Post by LowSky on 2009-10-01
> **rezapiri09 said:**
> Got it Sky. When I try to extract the archive of Gcaldaemon onto usr/local/sbin I get this error message:

You don't have the right permissions to extract archives in the folder "file:///usr/local/sbin"

I know I have to login as root and I tried to in the terminal (su), but it still did not allow me to extract the files.  what am I doing wrong here?

Sorry for taking so long to get back. Ubuntu doesn't have a root account like other Linux distros

you need to use the sudo command at the begining of any command that requires root command for instance

```
sudo apt-get update
```

---

### Post by Michael Steinberg on 2009-10-01
I have the same problem as lasleym--I'd been using Google Calendar for a few months and suddenly today I got the same problems you've related.

---

### Post by m.mannes on 2009-10-02
Me too. I've using both Calendar and Contact integration with Google accounts just fine. Today I got the same errors. In Calendar, Evolution ask for password all the time, without get my google appoinments. And Contacts give me the following message: 
> ERROR LOADING ADDRESS BOOK:

This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.

Detailed error message: Other errorI'm using Evolution 2.26.1

---

### Post by nandelbosc on 2009-10-02
I have the same problems (can't sync google calendar and contacts) for two days ago! (I have it runnig ok for half an year)


It's a problem about google or an ubuntu update?

---

### Post by nandelbosc on 2009-10-05
[http://ubuntuforums.org/showthread.php?t=1282319](http://ubuntuforums.org/showthread.php?t=1282319)

---

### Post by m.mannes on 2009-10-06
Today my google apps started to work in Evolution without changing anything. Seems like a Google problem that was solved...

---

### Post by lasleym on 2009-10-06
Sure enough, so did mine.  :)  Still a little buggy (some of my all-day recurring events don't transfer, but they didn't before) but at least they are there!

---

