---
title: "Evolution not syncing my sent items and calendar from gmail account using pop"
date: 2010-12-21
forum: General Help
---

### Post by raviepic3 on 2010-12-21
Hello people,  How do i sync my sent items, calendar and tasks and labels if possible with my evolution client from my gmail account ?

---

### Post by dcstar on 2010-12-22
> **raviepic3 said:**
> Hello people,  How do i sync my sent items, calendar and tasks and labels if possible with my evolution client from my gmail account ?

POP is an ancient protocol that only downloads messages, there is no "syncing" whatsoever and you only have the choice of leaving messages on the server or not.

---

### Post by raviepic3 on 2010-12-22
yes, i want it to be one way, thats why selected pop  i dont want to disturb the email messages on my online account.  i just want to back it up completely using a email client and store it in a disc or something  and continue to work with the original copy on the online server using webmail

---

### Post by raviepic3 on 2010-12-22
people any update on this ?  Did i choose a wrong email client to get less support ?

---

### Post by T.J. on 2010-12-23
Hi Raviepic3!

I think using IMAP rather than POP might get you what you are looking for.  IMAP connects to the server and reads messages but leaves them there.  It can make a copy on your computer and keep the two syncronised.  It doesn't delete from the server unless instructed to do so.  This works very well with most webmail services, Blackberry, and smartphones.  If you are using Gmail, you have to enable IMAP on your Gmail account in order to use it, then setup the account in Evolution. Google even provides instructions on IMAP settings.

IMAP was designed especially for what you are describing - being able to read mail remotely or over the web at the same time or in different places.  If you aren't comfortable with Evolution, Thunderbird is also available in the Ubuntu package system.


Please let me know if I can do anything more to help, or if you need more specific information!

Good Luck!
T.J.

---

### Post by raviepic3 on 2010-12-23
Hello TJ,  Thanks for replying, I am not sure about my choices, so go with whats suggested here,  My aim :   Backup email messages [inbox, sent items, drafts, labels and tasks if possible] from my gmail just for the sake of keeping a backup copy with me and nothing else.  I do not intend to send messages using my email client and sync it with webmail.  Just for the sake of backing up my entire account i am looking at a email client.  Kindly suggest me on how to proceed, and what to look at.

---

### Post by T.J. on 2010-12-23
Hi, Raviepic3 :D

Yes, IMAP can backup your messages very easily, but you might have a little bit of a learning curve if you have never used IMAP before. I'll help you over the rough spots if I can.  I use an IMAP client for all of my messages in and out  - as it lets me sort and tag messages much more efficiently than Gmail's clunky web interface.


Another possibility that you can try is Google Gears.  It makes a backup copy of your Gmail on your computer using only your browser, so that you can get to your stored messages even if you are offline.  The bad side is that Gears works only for Gmail.

---

### Post by PhantmKllr on 2010-12-23
> **raviepic3 said:**
> Hello people,  How do i sync my sent items, calendar and tasks and labels if possible with my evolution client from my gmail account ?

IMAP will sync your messages and labels(folders), so all changes made on your computer, will be reflected on your email account.

Your calendar and tasks won't sync with POP or IMAP, however, because POP and IMAP is a message access protocol. Calendar and tasks are completely different services...

---

### Post by T.J. on 2010-12-23
Yes, that is true.  IMAP won't work on calendars, but I've heard that Evolution can, as well as use IMAP. :D  I admit though, I've never used Google Calendar.

---

### Post by raviepic3 on 2010-12-29
Oh, just now installed thunderbird after uninstalling evolution.  Thunderbird 3 however just by getting my username and password configured everything by itself.  It automatically sync my labels, inbox, sent items and drafts as well !   But no tasks, contacts, calendar.  So you people suggest me to switch back to evolution ?

---

### Post by T.J. on 2010-12-31
> **raviepic3 said:**
> Oh, just now installed thunderbird after uninstalling evolution.  Thunderbird 3 however just by getting my username and password configured everything by itself.  It automatically sync my labels, inbox, sent items and drafts as well !   But no tasks, contacts, calendar.  So you people suggest me to switch back to evolution ?

Before you decide, you should look around a little bit more.  One of the advantages of Thunderbird is its plug-ins, available from Mozilla.  There is a plug-in for calendar called Lightning.  With a little effort, you can get your Contacts to sync as well as your calendar.  If you need help finding something, please post here, and I'll see what I can do.

There is plenty of information on how to interface both programs with Google's services.  For example, these may be useful to you: [http://www.techiecorner.com/178/how-to-sync-google-calendar-with-thunderbird/](http://www.techiecorner.com/178/how-to-sync-google-calendar-with-thunderbird/)  and [http://www.ehow.com/how_4488736_sync-evolution-calendar-google-calendar.html](http://www.ehow.com/how_4488736_sync-evolution-calendar-google-calendar.html)


Ultimately, whether you chose Evolution or Thunderbird is really a matter of personal taste.  You should try both and decide for yourself which you like better.  Personally, I find Thunderbird easier to setup.

---

### Post by raviepic3 on 2011-01-05
Yeah, thanks for replying and the links.

Got the contacts synced.

But the calendar plugin available in addons part of mozilla is not compatable with my thunderbird is what the message appears.

I installed thunderbird using apt-get install

RIng any bells ?

---

