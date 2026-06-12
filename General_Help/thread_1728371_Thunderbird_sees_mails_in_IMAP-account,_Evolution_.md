---
title: "Thunderbird sees mails in IMAP-account, Evolution doesn't"
date: 2011-04-13
forum: General Help
---

### Post by uhappo on 2011-04-13
Hi there,

As the title says I have an IMAP-account and I want to use it via Evolution. I have the exact same settings on both Evolution and Thunderbird but only Thunderbird sees the mails (new/old), there are 139 messages. Evolution seen none. Nothing. I looked for IMAP-related problems concerning Evolution and one thread suggested something about Inbox-folder and it's location. I don't know if it's the solution, but I didn't find any luck trying different combos in Evolution's options. Here how the working folder is located in Thunderbird's setup:

[[IMG]http://i6.aijaa.com/b/00662/7881395.png[/IMG]](http://aijaa.com/v.php?i=006627881395.png)

Please help me...!

---

### Post by plucky on 2011-04-14
Don't know if this will help but my IMAP account uses different ports which have to be specified in Evolution.

For receiving it is **username@isp.com:993**
and for sending it is **username@isp.com:465**

i.e. change [email]username@isp.com[/email] to your real username and isp.

Check the requirements from your ISP.

Good Luck

---

### Post by uhappo on 2011-04-14
Thanks for your idea, plucky, but that wasn't the case.

Thunderbird defaults to ports (IMAP) 143 and (SMTP) iirc 587, and those ports work (in thunderbird)

---

### Post by plucky on 2011-04-14
> **uhappo said:**
> Thanks for your idea, plucky, but that wasn't the case.

Thunderbird defaults to ports (IMAP) 143 and (SMTP) iirc 587, and those ports work (in thunderbird)

Have you tried those ports in Evolution?

[email]username@imap.isp.com[/email]:143

&

[email]username@smtp.isp.com[/email]:587

---

### Post by uhappo on 2011-04-14
> **plucky said:**
> Have you tried those ports in Evolution?

[email]username@imap.isp.com[/email]:143

&

[email]username@smtp.isp.com[/email]:587

Yes, I've tried, without success. Any more ideas what's wrong?

BTW, my nokia N900-phone didn't see any messages, also. Only thunderbird (plus Outlook Express on windows-side) have seen messages, so far.

---

### Post by plucky on 2011-04-14
> **uhappo said:**
> Yes, I've tried, without success. Any more ideas what's wrong?

BTW, my nokia N900-phone didn't see any messages, also. Only thunderbird (plus Outlook Express on windows-side) have seen messages, so far.

The only other thing I can think of is what security protocol needs to be set for the IMAP server and for the SMTP server.This information should be provided by your email provider.

Good Luck

---

### Post by uhappo on 2011-04-14
> **plucky said:**
> The only other thing I can think of is what security protocol needs to be set for the IMAP server and for the SMTP server.This information should be provided by your email provider.

Good Luck

There are no security protocols, not in IMAP or SMTP, for this mail. I've checked it.

---

### Post by uhappo on 2011-04-17
Anyone?

---

### Post by artaxerxes on 2011-04-17
> **uhappo said:**
> Yes, I've tried, without success. Any more ideas what's wrong?

BTW, my nokia N900-phone didn't see any messages, also. Only thunderbird (plus Outlook Express on windows-side) have seen messages, so far.


The fact that your phone is not seeing the emails leads me to wonder if Thunderbird is deleting the messages from the server after it grabs them.

---

### Post by uhappo on 2011-04-17
It's still IMAP-account and the phone is not deleting anything

---

### Post by dcstar on 2011-04-18
> **uhappo said:**
> It's still IMAP-account and the phone is not deleting anything

You do know that Evolution's IMAP folders are totally separate from the default "On This Computer" folders?

---

### Post by uhappo on 2011-04-18
> **dcstar said:**
> You do know that Evolution's IMAP folders are totally separate from the default "On This Computer" folders?

Yeah, I'm aware of that. I've got 5 IMAP mail accounts and those are working 100%, I'm just amazed that this one reacts this way.

---

