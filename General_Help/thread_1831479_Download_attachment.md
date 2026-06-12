---
title: "Download attachment?"
date: 2011-08-23
forum: General Help
---

### Post by U2XS on 2011-08-23
Is it possible to set up a cron job that will download attachments from e-mails & process them in a certain way?  I would want to do it entirely through command line & I don't know which software to start looking at.

---

### Post by sbraz on 2011-08-23
i'm sure it's possible... i don't know how but i'm interested in this topic. :)

try googling "linux download email attachment command line" and click "i'm feeling lucky" :p

a stock ubuntu presents these locations:
```

/etc/cron.daily
/etc/cron.hourly
/etc/cron.monthly
/etc/cron.weekly
```
if you put a script here it'll run (under root account) every day, hour, month, week, depending on which directory you choose.
there are ways of customizing cron and anacron for both user and delays, but i've only gathered epic failures so far trying this. :D

---

### Post by U2XS on 2011-08-23
Ahh, well using cron isn't really difficult.  This one page can show you almost everything you need to know.  [http://adminschoice.com/crontab-quick-reference](http://adminschoice.com/crontab-quick-reference).  The reason that I mentioned it is because I am looking for command line software (that doesn't require a GUI).

---

### Post by sbraz on 2011-08-23
hmm honestly i didn't find much myself but you can try this:

[http://www.troublefixers.com/automatically-download-email-attachments/](http://www.troublefixers.com/automatically-download-email-attachments/)
(dropbox.deb/.rpm 32/64bit, source available)
> **AirDropper is a simple tool developed for all those users who demands files through Emails. The unique feature of this tool is that this tool automatically download files to a particular location in your computer, once it receives any file in your online account.** To use this tool, first you will need to create a free online account on AirDrooper.com and then download a tool name DropBox to automatically download all received files from your online account. Dropbox can be installed on any Computer, Windows, Mac or Linux. Also it can be installed on all popular phones including Dropbox for  iPhone and iPad, you can also install DropBox on your android phones,Blackberry phones or Symbian Phones using web interface of Dropbox.








Can I run Dropbox on a Linux server?
If you use Linux from the command line only, follow the command line interface (CLI) instructions contributed by the Dropbox community. Once you have installed Dropbox for the command line, you can install and use Dropbox's CLI script to view your Dropbox status.

---

### Post by U2XS on 2011-08-24
When I stopped looking for command line, I found a very nice piece of software called MailDrop: **[http://getmaildrop.com/](http://getmaildrop.com/)**.

I can't say that it's exactly what I was looking for, but since it is Linux based, there must be a way to issue these commands without the GUI.  There's also not a lot of this kind of software, so I really can't be choosy.

---

### Post by U2XS on 2011-08-24
> **sbraz said:**
> hmm honestly i didn't find much myself but you can try this:
[http://www.troublefixers.com/automatically-download-email-attachments/](http://www.troublefixers.com/automatically-download-email-attachments/)
(dropbox.deb/.rpm 32/64bit, source available)
I took a look at Airdropper/Dropbox.  It is also a little different but a valuable alternative.  Thanks

---

