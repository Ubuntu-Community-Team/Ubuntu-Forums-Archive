---
title: "Help with setting up a mail server!"
date: 2010-06-18
forum: General Help
---

### Post by tsuujin on 2010-06-18
Ok, first off I realize this seems like kind of an advanced topic. I've looked through about fifty web sites with partial answers and I still haven't managed to get this working properly.

What I want to do is allow mediawiki to send emails for email/password confirmation. I was told that sendmail could do this, and tried to get it working, but I couldn't seem to get it to function properly.

Someone then told me to go to postfix, and I also can't seem to get it to work properly.

I have a domain registered (akujin.com) with dyndns.org and would like to be able to send mail through it if possible, but if there's a simple say to just send mail without needing a fully qualified server that'd be good too.

What I'd really like is a step by step (assuming no knowledge at all) on how to get sendmail/postfix/whatever to actually send mail, from start to finish. If I need to configure my DNS to do this I'd need to know what's needed there as well.

Can someone help me with this, please?

---

### Post by dcstar on 2010-06-19
> **tsuujin said:**
> Ok, first off I realize this seems like kind of an advanced topic. I've looked through about fifty web sites with partial answers and I still haven't managed to get this working properly.

What I want to do is allow mediawiki to send emails for email/password confirmation. I was told that sendmail could do this, and tried to get it working, but I couldn't seem to get it to function properly.
........
Can someone help me with this, please?

Sending outgoing mail with Postfix basically "works out of the box", with only "I can't get it to work" as a description of your problems there is no way anyone can help you.

---

### Post by tsuujin on 2010-06-19
> **dcstar said:**
> Sending outgoing mail with Postfix basically "works out of the box", with only "I can't get it to work" as a description of your problems there is no way anyone can help you.

I have no idea where to start looking for the problem, so I have no idea of what information I should be providing (which is why I asked for a step by step).

Basically I try something like 
echo "Subject: test" | /usr/lib/sendmail -v [email]me@something.com[/email]
and I get no errors, but the email never actually comes through.

---

