---
title: "email to printer"
date: 2011-09-09
forum: General Help
---

### Post by SneakyWho_am_i on 2011-09-09
Hi everyone,

We've been checking our yahoo email through imap+thunderbird and it's been brilliant.
but we miss the days of faxes sometimes... it's frustrating when emails come which we MUST print, and which are time critical... and we have to actually log in and print them.

How can I automatically print incoming emails (with attachments)?
i've spent quite some time on google, andd tried configuring fdm (with lpr) for this task, but I just can't work it out :(

I can't get an eprint printer, am not allowed to move emails to maildirs...
I might theoretically be able to use an email to fax gateway (the cost in nz is a bit scary)
...

So how can I get this done in software?

I'd really like to be able to say "if subject contains foo then send email to lpr. If subject contains bar then send attachments to lpr".

Big thanks in advance.

---

### Post by haqking on 2011-09-09
> **SneakyWho_am_i said:**
> Hi everyone,

We've been checking our yahoo email through imap+thunderbird and it's been brilliant.
but we miss the days of faxes sometimes... it's frustrating when emails come which we MUST print, and which are time critical... and we have to actually log in and print them.

How can I automatically print incoming emails (with attachments)?
i've spent quite some time on google, andd tried configuring fdm (with lpr) for this task, but I just can't work it out :(

I can't get an eprint printer, am not allowed to move emails to maildirs...
I might theoretically be able to use an email to fax gateway (the cost in nz is a bit scary)
...

So how can I get this done in software?

I'd really like to be able to say "if subject contains foo then send email to lpr. If subject contains bar then send attachments to lpr".

Big thanks in advance.


i dont use thunderbird but i think autoprint addon will do what you want, i found it for a friend recently with a mac.

[http://mac.softpedia.com/get/Internet-Utilities/autoPrint-for-Thunderbird.shtml](http://mac.softpedia.com/get/Internet-Utilities/autoPrint-for-Thunderbird.shtml)

it is in mac section but cross platform and works on mac, linux and windows

if this helps please mark the thread as solved.

hope this helps

---

### Post by SeijiSensei on 2011-09-09
One possibility would be to build a local mail server that uses [fetchmail](http://www.fetchmail.info/) to download the messages from Yahoo and a set of [procmail](http://www.procmail.org) rules to handle the "if subject=foo, then X" kinds of policies.

Printing attachments is going to be tough to implement, though.  Try opening a message with an attached binary (a PDF, ZIP, etc.) in Thunderbird and using View > Message Source to see the actual text.  You'll see the binary blob encoded with "MIME."  Simply sending the message to lpr will produce a result identical to what you see with View Source.  You'd have to write some filters to detach and decode the attachments.  A procmail rule that passes the message to [uudeview](http://www.fpx.de/fp/Software/UUDeview/) if attachments are detected might be a possible starting point.

All three programs are in the Ubuntu repositories.  Procmail works as the local delivery agent for a mail transfer agent like sendmail or Postfix.  Most sendmail implementations use procmail by default; in Postfix you need to edit main.cf and change "mailbox_command" to read

```
mailbox_command = procmail -a "$EXTENSION"
```

---

### Post by SneakyWho_am_i on 2011-09-25
These are helpful replies and I love this place.

That thunderbird addon is definitely worth a look, I'll get to that this evening.

As for procmail...

Yeah, procmail is brilliant stuff. If fetchmail can leave the messages on the server (preferably leaving them unread) then this could be a winner too.

My last brush with procmail involved what felt like a thousand hours of reading. It has all the power and ease of use of sed... And the coolness and magic of mod_rewrite. (In short, I'm afraid of it!)

But thanks guys, I'm off to check out these options right now.


EDIT:
I know that part of asking good questions on the internet is research and trust me I hammered both google and my brain before asking here...
But armed with the right terminology with autoprint I found this in the moz repos: [https://addons.mozilla.org/en-US/thunderbird/addon/autoprint2/](https://addons.mozilla.org/en-US/thunderbird/addon/autoprint2/)
- Autoprint2 allows printing through message filters.
This seems to be the same extension linked earlier @softpedia, so the moz link is for reference.

I'm not sure that doing it through thunderbird is the right approach in our situation, but I can't make excuses all day and I'll be having a go with autoprint2 later today while I make some stripped down, simple test runs with fetchmail and procmail at home.

(Thanks again guys)

---

### Post by haqking on 2011-09-25
> **SneakyWho_am_i said:**
> These are helpful replies and I love this place.

That thunderbird addon is definitely worth a look, I'll get to that this evening.

As for procmail...

Yeah, procmail is brilliant stuff. If fetchmail can leave the messages on the server (preferably leaving them unread) then this could be a winner too.

My last brush with procmail involved what felt like a thousand hours of reading. It has all the power and ease of use of sed... And the coolness and magic of mod_rewrite. (In short, I'm afraid of it!)

But thanks guys, I'm off to check out these options right now.

no worries, the add on should do just as you asked.

If all good remember to come back and use thread tools to mark as solved.

Cheers

---

