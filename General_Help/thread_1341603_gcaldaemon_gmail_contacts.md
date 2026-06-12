---
title: "gcaldaemon gmail contacts"
date: 2009-11-29
forum: General Help
---

### Post by slimx3m on 2009-11-29
this is probably not the place to request support, but i am wondering if anybody has the same problem that i am currently having.

i installed and configure GCALDaemon just like is posted on their website ([http://gcaldaemon.sourceforge.net/usage11.html#top](http://gcaldaemon.sourceforge.net/usage11.html#top)). now, i am trying to have my Gmail contacts on my computer with Thunderbirs and whenever i run the stand-alone.sh i am receiving the following error message:

> ERROR | Unable to load contact list!
java.lang.Exception: Login failed (check username/password)!
	at org.gcaldaemon.core.GmailEntry.connectLDAP(GmailEntry.java:231)
	at org.gcaldaemon.core.GmailEntry.connect(GmailEntry.java:147)
	at org.gcaldaemon.core.GmailPool.borrow(GmailPool.java:98)
	at org.gcaldaemon.core.ldap.ContactLoader.loadContacts(ContactLoader.java:274)
	at org.gcaldaemon.core.ldap.ContactLoader.run(ContactLoader.java:220)


what i have noticed is that every time i run the password-encoder.sh and i input the same password...... the encoding is different every time.

any thoughts on how i should persuade this situation is appreciated.
thnx.

---

### Post by slimx3m on 2009-12-01
no body?  :(

---

### Post by Chadarius on 2009-12-01
I am getting the same problem

```
2009-12-01 15:41:11 | ERROR | ContactLoader  | Unable to load contact list!

  [1 ] java.lang.Exception: Login failed (check username/password)!
  [2 ] at org.gcaldaemon.core.GmailEntry.connectLDAP(GmailEntry.java:231)
  [3 ] at org.gcaldaemon.core.GmailEntry.connect(GmailEntry.java:147)
  [4 ] at org.gcaldaemon.core.GmailPool.borrow(GmailPool.java:98)
  [5 ] at org.gcaldaemon.core.ldap.ContactLoader.loadContacts(ContactLoader.java:274)
  [6 ] at org.gcaldaemon.core.ldap.ContactLoader.run(ContactLoader.java:220)
```

I found this great .deb package at [http://blog.philippheckel.com/2008/09/30/gcaldaemon-deb-package-for-ubuntu-kubuntu/](http://blog.philippheckel.com/2008/09/30/gcaldaemon-deb-package-for-ubuntu-kubuntu/). I like the way he set it up for individual users. 

I had hoped that perhaps that .deb install would help me find whatever I was doing wrong with the manual install. But instead it has confirmed to me that something is busted with the contacts section. I'll have to poke around on the boards here and see if someone has already figured out the issue.

---

### Post by Chadarius on 2009-12-01
Looks like everyone has this problem.

Someone on the GCALDaemon support forums created a hack to solve the problem. I haven't tried it yet. But I wanted to get the link up here for you to check out right away.

[http://sourceforge.net/projects/gcaldaemon/forums/forum/643348/topic/3417160](http://sourceforge.net/projects/gcaldaemon/forums/forum/643348/topic/3417160)

---

### Post by slimx3m on 2009-12-02
> **Chadarius said:**
> Looks like everyone has this problem.

Someone on the GCALDaemon support forums created a hack to solve the problem. I haven't tried it yet. But I wanted to get the link up here for you to check out right away.

[http://sourceforge.net/projects/gcaldaemon/forums/forum/643348/topic/3417160](http://sourceforge.net/projects/gcaldaemon/forums/forum/643348/topic/3417160)
thnx for the info.  i will giving it a try tonight.

---

### Post by axel206 on 2009-12-05
Have you tried the proposed solution slimx3m?

I've tried to make the changes but I still get the same error message.

---

### Post by Skiro'n on 2009-12-06
I was facing the same problem, and replacing the existing gcal-daemon.jar by the one made by vin-c in the [sourceforge forum]("https://sourceforge.net/projects/gcaldaemon/forums/forum/643348/topic/3417160/index/page/1") did the trick!

---

### Post by axel206 on 2009-12-06
Replacing the existing gcal-daemon.jar indeed allowed me to connect to gmail. However when I tried to add the contacts from gmail to KAddressbook only the name and the phone number were recognised. :/ Did you have this problem?

Two way syncrhonization isn't possible, right?

---

### Post by axel206 on 2009-12-13
I found another way of synchronizing my contacts and calendar. It is two way synchronization. Here is a guide:

[How to synchronize Google contacts and calendar with KAddressbook and KOrganizer](http://www.my-guides.net/en/content/view/178/26/)

---

### Post by slimx3m on 2010-06-03
sorry for the huge delay :)...... i've tried everything, but still fails.

---

### Post by axel206 on 2010-06-06
> **slimx3m said:**
> sorry for the huge delay :)...... i've tried everything, but still fails.

I've been using akonadi-googledata along with libgcal from the above link for a few months now (on KDE) and along with some patches from the git repo of libgcal I have no problem with the synchronization...

---

