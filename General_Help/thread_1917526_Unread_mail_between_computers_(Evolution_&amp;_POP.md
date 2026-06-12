---
title: "Unread mail between computers (Evolution &amp; POP)"
date: 2012-01-30
forum: General Help
---

### Post by Lovegain on 2012-01-30
I use Evolution for mail on my two computers; a desktop and a netbook. Using POP3 I get all incoming to both machines. The problem is that read mail stays unread on the server (and on the other computer). So I have to "read" every e-mail twice. In my eyes it should download some mail as read, if I've already read it on another computer. Can the read/unread state be synced, or pushed to the server?

Somewhere I read that IMAP would keep the read state on the server. I tried to switch to IMAP  but it didn't make any difference.

---

### Post by SeijiSensei on 2012-01-30
I don't use Evolution, but IMAP should have solved your problem.  I read my mail with Thunderbird, and sometimes Squirrelmail, from a number of different computers.  With IMAP, all the clients present the identical view of the mail.  POP3 is really a difficult protocol to manage if you want to read your mail from varying locations.

---

### Post by ajgreeny on 2012-01-30
> **SeijiSensei said:**
> I don't use Evolution, but IMAP should have solved your problem.  I read my mail with Thunderbird, and sometimes Squirrelmail, from a number of different computers.  With IMAP, all the clients present the identical view of the mail.  POP3 is really a difficult protocol to manage if you want to read your mail from varying locations.
+1
If you use IMAP, and set the server to simply mark mail as read, but not move it to trash after reading messages, all your mail will be readable on all machines, and you will be able to see any new ones straight away.

POP is almost impossible to work with if you are using more than one machine, unless you just have your main machine using POP, with a setting to archive messages, not delete from server, and all the other machines using IMAP.  However, for ease of use, I would recommend using IMAP for all machines. I am not sure if all mail servers allow both POP and IMAP to be used at the same time;  I use gmail and that certainly does, though the settings have to be set up on gmail's webmail server, not on your client application.

---

### Post by SeijiSensei on 2012-01-30
If you run your own MDA server with dovecot you can have it listen for both POP3 and IMAP4 requests.  You do have to take care and tell the POP3 server not to delete mail from the inbox once read. (It might be possible to enforce that on the server side with dovecot, but I've never tried.  I want my POP clients to take their mail and go away!)

---

### Post by Lovegain on 2012-02-26
Yeah, you seem to be right. Don't know what made me think the opposite last time I tried.

By the way, I sometimes get an error something like "Could not retreive message" since I switched to IMAP. Why could that be? There's no problems with connection so that's probably not it.

Also, I use filters to sort mail into folders. Is there some way to synchronise filters between machines? Or do you advise just using filters on one machine?

Thanks, and sorry for the late reply.

---

