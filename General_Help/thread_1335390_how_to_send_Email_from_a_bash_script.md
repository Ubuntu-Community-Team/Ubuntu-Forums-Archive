---
title: "how to send Email from a bash script?"
date: 2009-11-23
forum: General Help
---

### Post by y10linux on 2009-11-23
Hi all,

I am trying to write a bash shell script that sends e-mails. It would be nice (although not strictly) necessary if attachments could be added to the e-mail sent.

I have found several things that "should" work, but none of them "really" does... 

My best shot so far is:

/usr/bin/mail -s -p "mail subject" [email]mail@address.com[/email] <<< "message text"

but no e-mail is sent and I get the following message:

"Cannot parse address `mail subject' (while expanding `mail subject'): Format of RFC822 object is bad"

I have also tried mutt, but with little success so far.

I can send and receive e-mail with this computer (using a web browser + gmail or using the evolution mail client).

Any help would be most welcome!

---

### Post by koma77 on 2009-11-23
I can send mail like this:

/usr/bin/mail -s "Subject" [email]address@someisp.com[/email] < textfile_with_mail_contents.txt

---

### Post by y10linux on 2009-11-23
> **koma77 said:**
> I can send mail like this:

/usr/bin/mail -s "Subject" [EMAIL="address@someisp.com"]address@someisp.com[/EMAIL] < textfile_with_mail_contents.txt

First of, all, thanks for answering!

With this command (even if I add the -p option) I do not get any error message, but no e-mail is sent either. I have tried several mail addresses and checked that messages were not filtered as spam.

I'm guessing  /usr/bin/mail is not correctly configures, but I do not know how to configure it...

---

### Post by t0p on 2009-11-23
To be able to send mail from the command line (and therefore also from a script) I had to do the following:

1.  Install the programs **mailx** and **exim4**;

2.  Because I can't actually run a mail server from my computer (ISP restrictions), I had to set exim4 to use a Gmail smtp server; as explained [here]("http://wiki.debian.org/GmailAndExim4").

Now I can send mail by using this syntax:

```
mail whoever@whereever.com
```

I am prompted for subject; cc address(es); body of email.  I end the mail by typing a full stop (".") on its own line.

To do it from a script, you'll need to check out all the options for mail/mailx; run

```
man mail
```

---

### Post by falconindy on 2009-11-23
You need an MTA (mail transfer agent) like Sendmail, Postfix, or Mailx in order to send emails externally.

---

### Post by koenn on 2009-11-23
what t0p says should work to send mail from a command line

to script it, it sort of depends what you're after : a script that e.g. sends an alert to a predefined email-address will be quite different from e.g. a script to send spam through a given smtp server. 
So, what is it you're trying  to do ?

---

### Post by y10linux on 2009-11-23
> **t0p said:**
> To be able to send mail from the command line (and therefore also from a script) I had to do the following:

1.  Install the programs **mailx** and **exim4**;

2.  Because I can't actually run a mail server from my computer (ISP restrictions), I had to set exim4 to use a Gmail smtp server; as explained [here]("http://wiki.debian.org/GmailAndExim4").

Now I can send mail by using this syntax:

```
mail whoever@whereever.com
```I am prompted for subject; cc address(es); body of email.  I end the mail by typing a full stop (".") on its own line.

To do it from a script, you'll need to check out all the options for mail/mailx; run

```
man mail
```


Thanks very much, It works now!

---

### Post by y10linux on 2009-11-23
> **koenn said:**
> what t0p says should work to send mail from a command line

to script it, it sort of depends what you're after : a script that e.g. sends an alert to a predefined email-address will be quite different from e.g. a script to send spam through a given smtp server. 
So, what is it you're trying  to do ?

I want to send alert e-mail every time a point in an already written script is reached. More specifically, the script executes several things in every subdirectory from a given directory (in each case the calculation take from five minutes to a couple of hours). I would like to be able to check how things are going without having to actually come to work at weekends (or having to send someone when I am travelling).

Moreover, since I updated to karmic koala my computer tends to shut down unexpectedly, so receiving emails from the script would also help me avoid losing computation time.

To sum up, just being able to run the line that I am now running from command line in a shell script would probably be enough (being able to attach files would be great too).

---

### Post by t0p on 2009-11-23
> **y10linux said:**
> Thanks very much, It works now!

You're welcome!

Could you mark this thread as [SOLVED]?  You do this through **Thread Tools** at the top of the page.

---

### Post by t0p on 2009-11-23
Ooh, I see you haven't quite finished!

> **y10linux said:**
> 
To sum up, just being able to run the line that I am now running from command line in a shell script would probably be enough (being able to attach files would be great too).

I don't think mailx does attachments.  I would suggest using **mutt**.  If you consult the manpage, you'll see all the options available.

---

