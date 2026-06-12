---
title: "Piping output to an email...no 'mail' program?"
date: 2006-02-07
forum: General Help
---

### Post by Kadin2048 on 2006-02-07
I'm trying to set up a cron task that runs a script, and emails the output of the script to me.

The trick is that I want it sent to a real internet email address, not to my local user's email (so that I can view the output without logging into the machine). I have done this without any trouble on my MacOS/Darwin machine, by piping the output of the script to the 'mail' program. So the task looks like:

30 4 * * * sh ~/bin/sync.sh 2>&1 | mail -s "Daily Backup Report" [email]myaddress@gmail.com[/email]

This works wonderfully, and I want to get the same thing going on my Ubuntu box. But I've run into a number of problems.

1) There's no 'mail' program. I need something that will take input on stdin (from a pipe) and send it out as an email...but the 'mail' program doesn't seem to exist in the Ubuntu multiverse. I thought it was a totally ubiquitous program? Is there a replacement for it by a different name, perhaps?

2) I'll need to set up a MTA on my Ubuntu box. My mac has postfix installed, set up (I think) by default so that it will only take messages from the local system and deliver them. My ubuntu box has postfix, but it's not set up. So anyone who could point me to how to set up postfix in a really minimal configuration (I just want it to send local mail out -- not relay or do anything else), would be a great help. I would like to avoid dealing with sendmail, if possible.

I'm open to any thoughts/suggestions/ideas people want to share.

Thanks!
Kadin

---

### Post by dcstar on 2006-02-08
[QUOTE=Kadin2048]
.......
This works wonderfully, and I want to get the same thing going on my Ubuntu box. But I've run into a number of problems.

1) There's no 'mail' program. I need something that will take input on stdin (from a pipe) and send it out as an email...but the 'mail' program doesn't seem to exist in the Ubuntu multiverse. I thought it was a totally ubiquitous program? Is there a replacement for it by a different name, perhaps?
.......[/QUOTE]
Install mailx

---

### Post by kabus on 2006-02-08
If you don't need local mail delivery you could use a small smtp client like msmtp, which does deliver mail through an external server and is a very easy to configure.
Otherwise use postfix, which on Ubuntu comes with a kind of "install wizard" which is pretty self-explanatory (and there's a guide in the wiki, too).
To send mail like you want to do I usually pipe it into mutt or nail, which both have the advantage that they can also handle attachments.

---

### Post by Kadin2048 on 2006-02-08
[QUOTE=dcstar]Install mailx[/QUOTE]

Ahhh, so that's where "mail" went. I saw that in the package lists, but I wrongly assumed that "mailx" would be an X-Windows app.

Thanks.

[QUOTE=kabus]If you don't need local mail delivery you could use a small smtp client like msmtp, which does deliver mail through an external server and is a very easy to configure.
Otherwise use postfix, which on Ubuntu comes with a kind of "install wizard" which is pretty self-explanatory (and there's a guide in the wiki, too).
To send mail like you want to do I usually pipe it into mutt or nail, which both have the advantage that they can also handle attachments.[/QUOTE]

I'll look into msmtp, because that IS all I want it to do. I don't want it to act as a mailserver, at least not right now, I just need some way for scripts to send me emails and tell me that they're done. (Basically, cron jobs.) On my Mac, postfix was apparently just set up and running out of the box and when I piped output to the "mail" program that was addressed to an internet email address, it went through. So I have no feelings for postfix one way or the other, I just know it's working on my other system.

---

### Post by lamego on 2006-02-08
You can also use "sendmail", I am refering to the client sendmail not to the service. If I am not mistaken it comes installed as default on Ubuntu.

---

