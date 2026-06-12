---
title: "mail server help"
date: 2010-10-09
forum: General Help
---

### Post by otkaz on 2010-10-09
Hi I'm a vet tech for a non-profit high volume spay and neuter clinic. I'm wanting to set up a mail server to send email reminders to our customers when their vaccines are due. I'm going to need some kind of front end, so our employees easily add the email addresses and when their next vaccine will be due from a windows computer thats on the same network as the ubuntu box. I've been using linux for many years, but haven't ever had a use for a mail server until now, so I'm not quite sure what software I need to start looking into. I was wondering if anyone can point me in the right direction to get me started. Thanks

---

### Post by SeijiSensei on 2010-10-09
Where is the client data stored now?  If it's in an SQL database with ODBC connectivity, you could write an application in something like PHP, Python, or Perl on the Linux box that would grab the addresses from the database and generate the reminders.  Run it each day out of cron and have it make a SELECT query against the database to extract the addresses for the clients whose vaccines are coming due.

Are you using a "vertical" practice-management application in your practice?  Maybe it already has a facility to do mass-mailings.

I recently built a Linux box running sendmail that I installed at a hair salon to handle the mail their proprietary salon application generated.  This worked much better than having the proprietary application send out the messages because it could just dump them to the Linux "smart host" and let it deal with DNS resolution, queue management, and other overhead tasks that the proprietary software wasn't set up to do.

If you don't have an existing application, it might make sense to build it in PHP with a database backend using PostgreSQL (my preference) or MySQL.  Use web forms to enter the customer data and a cron job as I described above to send out the mail.  Actually the mail server part is the easiest aspect of this task.

---

### Post by otkaz on 2010-10-09
Were still doing everything on paper in the clinic at this time so no existing app in use at the moment. I was just reading about sendmail sounds like just was I'm looking for. I've already set up my box as a LAMP server. I'm not too knowledgeable with SQL I've done quite a bit of scripting in perl and python just started messing with PHP recently. I think you just gave me a general idea of how it should all come together which is what I needed. Thanks so much. Now time for me to do lots of reading.

---

### Post by SeijiSensei on 2010-10-10
I'd start by thinking about the database design and suggest you do a little reading on the "relational" model.  In a relational database, each table contains only one type of information, while other tables link those fundamental tables together.  In your case, you'd have a table of clients with names, addresses, etc.  If you have multiple practitioners, it might be good to put them in a table as well.  Then you'd have a third table where each record represents a single visit.  A visit record would consist of a client ID, a practitioner ID, and a unique visit ID so you'd know that on June 27, 2010, Joe Client brought in his cat Toby which was spayed by Dr. Smith.  (The procedures like spaying, vaccination, etc., might also be in their own table.)  This might sound like overkill to start with, but it makes managing the information much easier.  You can also enforce "referential integrity" which means that someone couldn't enter a visit without identifying the client and practitioner as well.  

If you have a copy of Microsoft Access available, you might want to play around with it to design the database. Access is entirely graphical which makes it easy for beginners to comprehend.  It can also be connected to an SQL database on the Linux server using the ODBC protocols.  If you're running PostgreSQL on the server, you can install the Postgres ODBC connector in Windows and access the remote database as if it were local to your machine.  That means you could mock up the database in Access, then create a parallel database in Postgres and copy the data from Access into it.  Access can import data from Excel and other spreadsheets which makes it more accessible to people used to those tools as well.  Access is one of the few MS Office programs I still use.

If you've used perl and Python in the past, PHP should be relatively easy to learn.  You could write everything in one of those languages instead.  The Apache web server has modules ([mod_perl]("http://perl.apache.org/"), [mod_python]("http://www.modpython.org/")) that wlll interpret scripts in those languages and display the results as HTML.

Have fun and good luck!

---

### Post by otkaz on 2010-10-10
Great thanks for all the really helpful info. Sounds like this project is going to be more complicated then I originally thought! Thats a good thing though I enjoy tinkering and learning. I really want the DB to have the least amount of info as possible. We do about 40 spays and neuters a day and have wellness customers walking in on top of that. We are extremely short staffed, so the less info we have to stop and type in the form the better. I think I'm just going to use customer name, email address, pet name, and vaccs given with some sort of check box if its a booster or initial. From that info I can determine the next due date in my script that queries the DB and sends the reminder. I have a question about sendmail. Since I will only be sending emails with it from a noreply@address would it be more secure to configure it in a way to not receive any emails? I've just been reading about a lot of security problems with it and people using miss configured sendmail servers as relays for spambots. I wouldn't imagine the security holes having anything to do with the receiving messages, but was just wondering. I'm going to be relaying to a godaddy.com smtp server if that matters. Thanks once again for the help.

---

### Post by SeijiSensei on 2010-10-10
If you're using Ubuntu Server, it runs a drop-in replacement for sendmail called postfix by default.  It's considered somewhat more secure than sendmail, but frankly, most complaints about sendmail are very out-of-date or represent geek snobbery.  Postfix is also quite a bit easier to configure than sendmail, too.  I can do pretty much anything with sendmail these days, but it's taken some years of experience to figure out all its quirks.

Is this box going to be directly on the Internet with no firewall or router in between?  You don't want that.  Either you'll need to run some type of firewall on the box itself using iptables or place it behind a router.  Then you don't need to worry about inbound security as the machine won't be visible over the Internet at all.

However you might consider using a free email account at some place like gmail as the sender rather than a noreply mailbox.  People *will* reply even if you tell them not to, so you should have a mailbox to collect them.  It takes just a few minutes to scan the mailbox and make sure there isn't anything that you need to answer there.  Remember, too, that people change email addresses often, so you'll need a place to collect non-delivery errors from other mail servers.

Given the demands on your staff, you might consider having the clients fill in the personal information form when they arrive for the first visit.  Then your staff can just pull up the record after the visit and check off what was done.

---

