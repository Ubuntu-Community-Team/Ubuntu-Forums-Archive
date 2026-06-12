---
title: "Question regarding Wine"
date: 2010-09-21
forum: General Help
---

### Post by Patrick70 on 2010-09-21
My main problem is that I would like to have a programme similar to Mailwasher (for Windows) for Ubuntu, but so far I have not come across anything that is useful.
So, if I cannot find anything then perhaps I could run it in a Wine environment, which is what this question is about.

Suppose I run Mailwasher in Wine, then no doubt I open the door to vulnerablities which Windows is prone to.
But what I would like to know, is whether any malicious code (be it viruses, malware or whatever) could enter the system only via the programme running in Wine (Mailwasher in this case), or whether it could leave the door open in general for any kind of attack?

Currently I am running a dual boot (Ubuntu - Vista) on my system.

Thanks, looking forward to the replies!

---

### Post by philinux on 2010-09-21
> **Patrick70 said:**
> My main problem is that I would like to have a programme similar to Mailwasher (for Windows) for Ubuntu, but so far I have not come across anything that is useful.
So, if I cannot find anything then perhaps I could run it in a Wine environment, which is what this question is about.

Suppose I run Mailwasher in Wine, then no doubt I open the door to vulnerablities which Windows is prone to.
But what I would like to know, is whether any malicious code (be it viruses, malware or whatever) could enter the system only via the programme running in Wine (Mailwasher in this case), or whether it could leave the door open in general for any kind of attack?

Currently I am running a dual boot (Ubuntu - Vista) on my system.

Thanks, looking forward to the replies!

The default mail client Evolution can use spamassasin or bogofilter. I think thunderbird has something similar for junk filtering.

Both can learn to spot junk.

---

### Post by Patrick70 on 2010-09-21
> **philinux said:**
> The default mail client Evolution can use spamassasin or bogofilter. I think thunderbird has something similar for junk filtering.

Both can learn to spot junk.

Thanks, I knew that, but what I need is the ability to be able to delete mails from the server without actually downloading them, and as far as I know there is no such software for Ubuntu.

---

### Post by blueridgedog on 2010-09-21
> **Patrick70 said:**
> Thanks, I knew that, but what I need is the ability to be able to delete mails from the server without actually downloading them, and as far as I know there is no such software for Ubuntu.

Do you need this or are you simply accustomed to this?  This is a great feature, but other solutions can work.

---

### Post by Patrick70 on 2010-09-21
Well, although this is something I have become accustomed to, it is something I really can't do without.
Mainly because I receive a lot of notifications from our ticketing system (from the company I run), and it would be a hassle to have to download those since I really have no need for them. Now when I receive a notification, I simply delete it right away from the server via Mailwasher and head to the ticketing system to deal with the ticket.

---

### Post by blueridgedog on 2010-09-21
Will your mail server support imap?  You could manage mail with an imap connection without downloading the mail.

---

### Post by anotherbigal on 2010-09-21
Hi

It is a shame that no one has picked up on the Wine part of your question as comments about using that software would be useful.

Has anyone tried Wine. If how successfull was it? Pros and Cons?

Cheers

Alan

---

### Post by Patrick70 on 2010-09-21
My server does support IMAP yes, but then I am still left with the problem of not being able to delete the messages directly from the server, which is exactly what Mailwasher does.

As Alan said, it would be nice to know about how (in)secure Wine actually is and whether I might be able to use that option instead.

---

### Post by Lateralis on 2010-09-21
Wine is perfectly secure. 

Wine is essentially virtualisation software.  Wine makes use of a virtual C: drive and an emulation layer to fool Windows programs into thinking they're installed on a Windows machine.  However, Windows software only ever runs if you tell Wine to run it.  You would actually have to physically tell Wine to run the malicious code which hopefully you won't do!  Even if malicious code does get run accidentally, the only place it can infect is the virtual C: drive, unless the code was specifically written with knowledge of the Linux file system.  And even then, with this remote and highly unlikely possibility, the only place it can really do any damage is your home partition.  No software can make system changes without you supplying your (sudo) password, and you never do that without stopping and thinking, right?  

As for Mailwasher running in Wine, you may want to check out [WineHQ]("http://www.winehq.org/search/?cx=partner-pub-0971840239976722%3Aw9sqbcsxtyf&cof=FORID%3A10&ie=UTF-8&q=mailwasher&siteurl=www.winehq.org%2F#1090") for other user's results of running this software (it seems like it runs very well).  You may also find [this]("http://forum.winehq.org/viewtopic.php?t=6719&sid=a72ed8b35b8f1737cd926903cbc53f39") discussion on a native Linux replacement for Mailwasher useful.

---

### Post by blueridgedog on 2010-09-21
> **anotherbigal said:**
> Hi

It is a shame that no one has picked up on the Wine part of your question as comments about using that software would be useful.

Has anyone tried Wine. If how successfull was it? Pros and Cons?

Cheers

Alan

With wine, you should be able to make it work...the only real way to find out is to try.  I find it very secure.  If you google this group you will find a few instances where people tried to infect their system with a windows virus through wine and posted the results.  The bottom line is you are safe to use it.

---

### Post by blueridgedog on 2010-09-21
> **Patrick70 said:**
> My server does support IMAP yes, but then I am still left with the problem of not being able to delete the messages directly from the server, which is exactly what Mailwasher does.


I think imap works that way...you are viewing headers and can delete them at which point they are deleted from the server.

Try mailwasher in wine and see if it works for you.  Linux is a playground for experimentation.

---

