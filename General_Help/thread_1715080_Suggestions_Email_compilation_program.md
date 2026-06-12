---
title: "Suggestions? Email compilation program"
date: 2011-03-26
forum: General Help
---

### Post by searchfgold6789 on 2011-03-26
Hi,
I am helping out at a computer repair small business, and I would be grateful for help from the Ubuntu Community: We are looking for a program that will take emails from a GMail server or thunderbird storage and list them in one big text file, kind of like a backwards mailing list.
It should be able to run on Windows, but maybe if there is a linux program it will be of interest too.
Thank you so much for your suggestions!
P.S. Is it possible to do this with Thunderbird and a shell script?

---

### Post by SeijiSensei on 2011-03-26
The default "mbox" format for mail places all the messages in a single text file.

One method you might consider is to create a user account on a Linux box and install the "fetchmail" package.  Set up a script that uses fetchmail to retrieve the articles from gmail and deliver them to the local user you created.  Then all the messages will be stored in /var/spool/mail/username.

If you run a POP/IMAP server like Dovecot on the Linux box, a Windows user could read the compiled mailbox with any mail client.  You could also install a webmail client like Squirrelmail so users could read the messages with a web browser.

---

### Post by searchfgold6789 on 2011-03-26
Okay - but I have one question before I do that:
Are the files stored in a human-readable format, all in one text or mbox file?

Also - I found out just now how to save email files as text files using Thunderbird. This is especially convenient, because now I can probably find out how to make a bash script that takes those saved text files and appends them to one huge .txt file.
(it is becoming more apparent as I research this that I will probably be using Linux.)

---

### Post by SeijiSensei on 2011-03-26
> **searchfgold6789 said:**
> Are the files stored in a human-readable format, all in one text or mbox file?

Yes, they will be in plain text, but they'll also include all the headers, and any attachments will be displayed in MIME encoding.  That's why I suggested adding Dovecot/Squirrelmail so you can read the compiled messages in a more friendly format.

> Also - I found out just now how to save email files as text files using Thunderbird. This is especially convenient, because now I can probably find out how to make a bash script that takes those saved text files and appends them to one huge .txt file.

That solution sounds fine if you don't mind the human intervention required.  By the way, TBird's local folders are in mbox format as well, I believe.  I looked at my local Trash folder in Thunderbird, and it looks pretty much like mbox.  So simply setting up TBird to monitor the remote mailbox with POP3 should generate the file you need automatically.

---

### Post by HermanAB on 2011-03-26
Howdy,

Fetchmail and Procmail should be able to do what you want, but it won't be easy.  Procmail is arcane, but it works.

---

### Post by searchfgold6789 on 2011-04-05
What about mailman?

---

