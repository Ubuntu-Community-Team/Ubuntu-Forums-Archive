---
title: "Oversized .PST file can't export to Thunderbird via Outlook"
date: 2010-11-26
forum: General Help
---

### Post by Melbel76 on 2010-11-26
Hi all,

I am rather new to the linux environment, and have a HUGE problem. A client of mine has a 7.7G .pst file, every time I try and import it into outlook so I can import to Thunderbird, it breaks due to the size, as Outlook can't handle files bigger than 2G. Is there anyway I can import this file into Thunderbird without having to use Outlook?
Please help me!
Eagerly awaiting your replies.
Melbel76

---

### Post by conradin on 2010-11-26
I'm not exactly sure, but a .pst file is just plain text right?
7 gigs will probably be troublesome no mater how you do it so my thought is to try breaking the file up to some more managable sized files. 
 
heres a link to an article describing such a process.
[http://www.howtogeek.com/howto/ubuntu/split-a-text-file-in-half-or-any-percentage-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/split-a-text-file-in-half-or-any-percentage-on-ubuntu-linux/) 
I had a client a few years back with a 5GB error log, 
I didnt want to loose the log but opening it directly was a pain.

vim or vi should also provide good response if you try yo open the file directly. 

There may be other options to break the file up, then concatenate them later.

---

### Post by HermanAB on 2010-11-26
Howdy,

The best way to transfer mail is via an IMAP server.  That way, you copy the mail to the server using Outlook and copy it from the mail server to the desktop using Thunderbird (or whatever).  The result is a perfect transfer, since Outlook knows how to handle it's own mail files.

The trick is to open anew account on an IMAP server (eg Google mail). Set the account up on Outlook and make sure that you select IMAP protocol, not POP.  Outlook will now have two accounts - old and new.  Click on the old inbox and select all mail (all turns blue) then click drag drop the mail to the new account inbox.  

Do not forward the mail, since that will cause all the senders to become yourself.  You have to do a 'copy' operation using click drag drop.  Try it with a few messages at a time till you are satisfied.  The mail in the new account will look exactly the same as in the old account, except that it will all now be on the server.  Once the mail is on the server, you can do the reverse with the new mail client.

This is the perfect way to copy mail, but it will take a looooooong time to copy 7gigs to Google and back.  A faster way is to install your own IMAP mail server, eg Citadel.

---

### Post by dcstar on 2010-11-26
> **Melbel76 said:**
> Hi all,

I am rather new to the linux environment, and have a HUGE problem. A client of mine has a 7.7G .pst file, every time I try and import it into outlook so I can import to Thunderbird, it breaks due to the size, **as Outlook can't handle files bigger than 2G**. 


Wrong:

[http://support.microsoft.com/kb/830336](http://support.microsoft.com/kb/830336)

---

