---
title: "Centralize email between several computers?"
date: 2006-04-03
forum: General Help
---

### Post by vayu on 2006-04-03
I have several computers and OS's that each retreive pop mail from my ISPs mail server.  How can I set up a situation where one program downloads the mail, then all the clients access it from a central place on the network?

The clients are 2 each of Outlook Express and Kmail and 1 Thunderbird (the Thunderbird is not as important).

---

### Post by dmizer on 2006-04-03
it's going to be alot easier if you use the same client on all the computers, but not impossible.

what you're looking for is imap.  it doesn't do exactly as you are suggesting in your post because it leaves copies of the messages on the server rather than download them.  but imap will allow all computers to view all mail.  along with all your inbox mail, it will also load all your folders etc.

even though you say your isp is a pop server, most isp's also support imap for the same email.  if you're interested, read more about it here: [http://www.imap.org/](http://www.imap.org/)

---

### Post by vayu on 2006-04-03
[QUOTE=dmizer]
what you're looking for is imap.  it doesn't do exactly as you are suggesting in your post because it leaves copies of the messages on the server rather than download them.[/QUOTE]

That seems like it could be one piece of the puzzle.  I want a program that downloads all my different ISP email accounts onto one of my computers at home.  Then it seems like I could use IMAP on my clients to all access them from there, no?

If that's the case, what will download all my emails on a regular basis and put them somewhere that can allow them to be viewed by any of my clients that have access to that place?

And then there are matters like I want them sorted into various folders based on filter rules and I also want them deleted once they are downloaded.

---

### Post by johnnymac on 2006-04-03
What you could do is have one system (with IMAP running - look at squirrel mail - it's awesome) pull the mail from the account in question and then have your other systems pull mail from the IMAP system.

---

### Post by nocturn on 2006-04-04
Put an Imap and SMTP server on one of the systems (I recommend Cyrus and Postifx) and use fetchmail on that system to get mail from your ISP.

You can also install Mailscanner with ClamAV and Spamassassin to do virus/spam filtering, it's quite easy to set up.

---

### Post by jmb365 on 2006-04-04
I use Thunderbird on Linux PCs and copy my ~/.thunderbird/XXXXXX.defaults directory to a backup PC.  On the backup's Thunderbird I created a new default user then configured it to use the subdirectory that was mirrored (using rsync - unattended) in the night.

For me this works because:

a) I needed to have a routine backup of some sort!
b) I do not read email that often on the backup PC.

This methodology may be extended to multiple PCs & more frequent synchronization than just nightly, but it has limitations.

If this rudimentary method is sufficient for you and you still have questions, I will gladly help.

JMB



[QUOTE=vayu]I have several computers and OS's that each retreive pop mail from my ISPs mail server.  How can I set up a situation where one program downloads the mail, then all the clients access it from a central place on the network?

The clients are 2 each of Outlook Express and Kmail and 1 Thunderbird (the Thunderbird is not as important).[/QUOTE]

---

