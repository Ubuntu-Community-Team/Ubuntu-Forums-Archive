---
title: "Thunderbird 3 with multiple gmail/apps accounts (IMAP)"
date: 2009-12-28
forum: General Help
---

### Post by Serguei_89 on 2009-12-28
Hi,

Does anybody have good experience setting up Gmail/Google Apps Mail with Thunderbird 3 (via IMAP)? I really want to upgrade to it, but I had several issues with it so far:

1. It seems to not sync exactly well. After a long process of downloading all my emails(9000 or so), I sort them by date and some recent ones are missing. After I star a bunch of stuff or mark things as read, most of the email changes are reflected in gmail online interface, but not all. A bunch of random emails in Thunderbird's archive folder sometimes become 'unread' for some reason too. 

2. Archiving feels weird in terms of syncing. Does archiving in Thunderbird archive in gmail too? Also, it lets you archive stuff like "Sent" and "Junk" and so on, while those don't make sense in Gmail online interface. What happens then?

3. The easy "add account" wizard has trouble adding google apps accounts, so I have to drop down to a manual setup process, but given the trouble I'm having mentioned above, I'm afraid I didn't setup something right.

If you have gmail working with google apps account together, and are experiencing no/less glitches, please say how you did it. Thunderbird 3 is much better, but there's just no good setup guides for gmail and more importantly google apps mail for it yet.

---

### Post by _sebastian_ on 2010-01-13
Setting it up was quick and easy for me. I was using the new automatic setup routine. But I'm using only gmail not the apps. so this might not be 100% similar. Have a search in the gmail help to make sure you have the correct IMAP settings.

> **Serguei_89 said:**
> 
1. It seems to not sync exactly well. After a long process of downloading all my emails(9000 or so), I sort them by date and some recent ones are missing. After I star a bunch of stuff or mark things as read, most of the email changes are reflected in gmail online interface, but not all. A bunch of random emails in Thunderbird's archive folder sometimes become 'unread' for some reason too. 

I disabled the offline copy for the Gmail folder. The Gmail folder contains all you mail. So if you have many tags you will have most of your mails twice. once in the tag folder and once in the Gmail folder.

Have a read in the [gmail help]("http://mail.google.com/support/bin/answer.py?answer=77657&topic=12762"). There is explained what action on the client resembles which action in the gmail interface.

> **Serguei_89 said:**
> 
2. Archiving feels weird in terms of syncing. Does archiving in Thunderbird archive in gmail too? Also, it lets you archive stuff like "Sent" and "Junk" and so on, while those don't make sense in Gmail online interface. What happens then?


From what I understand the Thunderbird archiving does NOT equal gmail archiving.
To have a mail *archived* in gmail via IMAP you have a read [here]("http://www.chinhdo.com/20071216/gmail-imap-tips/")

---

### Post by e24ohm on 2010-01-13
> **Serguei_89 said:**
> Hi,

Does anybody have good experience setting up Gmail/Google Apps Mail with Thunderbird 3 (via IMAP)? I really want to upgrade to it, but I had several issues with it so far:

1. It seems to not sync exactly well. After a long process of downloading all my emails(9000 or so), I sort them by date and some recent ones are missing. After I star a bunch of stuff or mark things as read, most of the email changes are reflected in gmail online interface, but not all. A bunch of random emails in Thunderbird's archive folder sometimes become 'unread' for some reason too. 

2. Archiving feels weird in terms of syncing. Does archiving in Thunderbird archive in gmail too? Also, it lets you archive stuff like "Sent" and "Junk" and so on, while those don't make sense in Gmail online interface. What happens then?

3. The easy "add account" wizard has trouble adding google apps accounts, so I have to drop down to a manual setup process, but given the trouble I'm having mentioned above, I'm afraid I didn't setup something right.

If you have gmail working with google apps account together, and are experiencing no/less glitches, please say how you did it. Thunderbird 3 is much better, but there's just no good setup guides for gmail and more importantly google apps mail for it yet.
I use Thunderbird with all 6 of my gmail accounts. I use POP3 for (1) and the other (5) are IMAP.

You are right to say that the archive and process is a little odd. This is due to the fact that Gmail uses labels, not folders to organize email. It takes a while to get use to this fact – well it took me a while, so you might fare better.

Also – you need to create a separate outgoing SMTP file for Thunderbird, so the application can send email from multiple accounts. It has been a while, but when I originally configured the software, it was only sending email out under the default/first created account on the application.

---

### Post by e24ohm on 2010-01-13
> **Serguei_89 said:**
> Hi,

Does anybody have good experience setting up Gmail/Google Apps Mail with Thunderbird 3 (via IMAP)? I really want to upgrade to it, but I had several issues with it so far:

1. It seems to not sync exactly well. After a long process of downloading all my emails(9000 or so), I sort them by date and some recent ones are missing. After I star a bunch of stuff or mark things as read, most of the email changes are reflected in gmail online interface, but not all. A bunch of random emails in Thunderbird's archive folder sometimes become 'unread' for some reason too. 

2. Archiving feels weird in terms of syncing. Does archiving in Thunderbird archive in gmail too? Also, it lets you archive stuff like "Sent" and "Junk" and so on, while those don't make sense in Gmail online interface. What happens then?

3. The easy "add account" wizard has trouble adding google apps accounts, so I have to drop down to a manual setup process, but given the trouble I'm having mentioned above, I'm afraid I didn't setup something right.

If you have gmail working with google apps account together, and are experiencing no/less glitches, please say how you did it. Thunderbird 3 is much better, but there's just no good setup guides for gmail and more importantly google apps mail for it yet.


3. i have never been able to get my (1) google app account to work with Thunderbird - I know...I know...i'm doing something wrong.

---

### Post by mgol on 2010-02-08
Actually, I prefer to follow this guide:
[http://mail.google.com/support/bin/answer.py?answer=78892](http://mail.google.com/support/bin/answer.py?answer=78892)
When I "delete" a message, it is only "marked as deleted" and Gmail understands it as "archive a message". I rarely really delete messages as there is a lot of space in a mailbox and I want to be able to read all messages.

Those ones I care about I leave in Inbox. The rest gets archived. I also marked the Inbox folder to be available also for offline use which means this one folder I can view even without internet connection (thus, archived mails aren't usually downloaded and that's what I wanted).

The only real problem that bugs me is how to efficiently integrate Thunderbird tags with Gmail labels... If I managed to to that, I'd have all I need.

---

### Post by sevenseeker on 2010-03-07
OK, the remaining question is:
How do I setup my google apps account.
Thanks

---

### Post by r_avital on 2010-05-16
Not sure what you mean by "apps" account, but here's what I used a minute ago in Thunderbird 3.0.4 official release for Linux:

In the Thunderbird Account Settings screen, click on Gmail (or create new account if you don't have it)

Account Name: (this can be anything you want, it's just a label for display in the left-pane tree for all your accounts).

Email address:  your gmail email address (yourusername.gmail.com, usually).

In Account settings/gmail/server settings:  
Server type should be IMAP if you created it as such.
Server name: imap.gmail.com
Port: 993
User name: your full gmail address as above.
Security settings: SSL/TLS
Use Secure Authentication: NOT checked.
The rest of the settings are up to you.
Click on the advanced button, and on the new screen that pops up:
IMAP server directory: Blank
the next 3 check boxes: checked
Max number of connections to cache: 5
Personal namespace: "" (two double quotes, no spaces)
Public and Other Users: Blank.
Last checkbox - Allow server to override - Checked.

Back in the user settings account, click on the last option at the bottom on the right pane (outgoing servers):

Add an entry for gmail if you don't have one.  If you do, select it and hit the edit button.
Desctiption: Whatever you want.
Server Name: smtp.gmail.com
Port: 465 (I tried 587 which was recommended somewhere, didn't work for me, but worked in Thunderbird 2.x.  Go figure).
Use name and password: Checked
User Name: your full gmail email address, as above.
Use secure authentication: NOT checked.
Connection security: SSL/TLS

Now go back to the account settings screen, and select Gmail again. Under Outgoing Server (SMTP), you should be able to select the gmail outgoing server you set up in the previous step.

As far as Apps, if you mean Google Calendars, I've set that up as well, you need the Lightning extention (you might already know that).  See [this thread on ubuntuforums ]("http://ubuntuforums.org/showthread.php?t=1360488")for setup.

If this works for you, please mark this thread as solved.

HTH

---

