---
title: "Alpine &lt;&gt; GMail Help Needed"
date: 2012-05-25
forum: General Help
---

### Post by Jose Catre-Vandis on 2012-05-25
I have been seeking out a way to "backup" my Gmail account to my home server (cli only) to have easily readable emails. Alpine seems to fit the bill, but before I go ahead and get it grabbing 17000 odd emails, I have a couple of questions:

1. I have set up alpine with imap and can happily read my GMail. I do not need to send emails using alpine this is purely to read and create a backup.

2. I understand I have to edit the inbox path parameters in order to actually download the emails to my server, like this:
```
 Navigate through: Setup > Config

Highlight &#8216;Inbox Path&#8217;, press enter then enter in the following:

imap.gmail.com/ssl/user=yourusername@gmail.com

and to make sure to navigate to the &#8220;Incoming Startup Rule&#8221; section in the same screen and enable &#8220;first-recent&#8221; so that alpine shows me the most recent emails when I go into my Message Index.
```
**[EDIT] this doesn't physically download the email!**

3. Can I edit the actual inbox path away from ~/.mail to another location on my server?
**[EDIT] YES**

4. Say I deleted all the mail I have in Gmail itself, if i run alpine will it repopulate my gmail account?

Any help greatly appreciated.....

---

### Post by Jose Catre-Vandis on 2012-05-26
bump ?

---

### Post by Jose Catre-Vandis on 2012-05-29
no-one can help?

---

### Post by Jose Catre-Vandis on 2012-06-03
Well I have taken a different approach to this, as have not found a straight forward way to achieve my objective. Alpine will download the mail but I can't see a way of getting it back up.

Googling produced several small projects that with a bit of work meet my needs.

First up is **Imap grab** ([http://sourceforge.net/projects/imapgrab/](http://sourceforge.net/projects/imapgrab/)) which offers  a gui and cli python app choice using getmail to download all mail or by label/folder into either mbox or maildir.Once you have downloaded mail, you can run the same command again to fetch only the new mail.

Second, to do much the same thing is **gmail-backup** ([http://sourceforge.net/projects/gmail-backup/](http://sourceforge.net/projects/gmail-backup/)) which uses a bash script and getmail to either mbox or maildir, but this is an all or nothing job, although you can run a sister script just to grab new mail.

As both of these create mbox files, these are easily readable by alpine

Thirdly, is **Imap Upload** ([http://sourceforge.net/projects/imap-upload/](http://sourceforge.net/projects/imap-upload/)), another python app that will upload your mbox files to gmail, based upon the label.

All three run nicely inside screen on my server, and I should be able to do a small bit of scripting to automate the updating of mailboxes on my server.

[EDIT]

And an additional problem with Alpine is that it doesn't see mailbox files that are larger than 2GB (on 32 bit anyway). If this happens you have to split the mbox file into smaller chunks. You can use "split" for this - example:
```
split --bytes=1000M original.mbox new
``` will split your large mbox file into 1GB chunks named newaa newab etc

Hopefully this is of help to someone else

---

