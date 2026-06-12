---
title: "POSTFIX deliver and forward"
date: 2010-11-06
forum: General Help
---

### Post by ambre on 2010-11-06
Hi guys,

I have fetchmail/postfix set up and working well to collect/deliver the family's email from various ISP's.  Outbound mail is relayed via 'myISP.com'.

What I want to do without destroying my existing setup is have postfix send a copy of all mail processed for 'joe' to my Gmail account so that I can keep up-to-date with my mail while I am away from home.  I have tried amending /etc/aliases by adding 'joe: joe [email]joe@gmail.com[/email]' which allows my mail to be delivered locally but myISP is rejecting the redirected mail because the sender is not 'joe@myISP.com'.

I would appreciate any guidance you can offer to enable me to achieve this.

Thanks

---

### Post by ambre on 2011-03-30
Hi,

Well, I still haven't found a way to do this!!

Does anyone think the following is possible?

Could I write a script (with your help) that would monitor my Maildir and upon receiving a new email, 'wrap' the received message in a new email that is sent by me (my ISP would then accept the message) to my Gmail account?

Look forward to hearing from you all.

---

### Post by SeijiSensei on 2011-03-30
What domain is your mail server in?  When you send outbound mail through your ISP, are they addressed from "joe@myisp.com"?

You probably need to read the [rewriting HOWTO](http://www.postfix.org/ADDRESS_REWRITING_README.html), and particularly [this section](http://www.postfix.org/postconf.5.html#append_at_myorigin), to see how to make outbound mail from your server appear to be addressed from [email]joe@myisp.com[/email].

If, after you've done this, aliasing doesn't seem to work you can try forwarding through "procmail," the default mail delivery agent in Ubuntu (and most all other *nix mail systems).  To do so, you'll need to put the forwarding rule in /home/joe/.procmailrc.  Procmail's syntax is rather arcane, but it is a very powerful piece of software.  Create a file called .procmailrc (note the initial dot) in /home/joe like this:

```

:0c
! someone@example.com

```

The "0: defines the start of a rule, and the "c" switch tells procmail to make a copy of the message and apply the rules that follow to the copy.  The "bang" ("!") is the forwarding operator.  See "man procmailrc" and, especially, "man procmailex" for details.  The forwarded message will be addressed from "joe" modified with whatever domain you've set up in Postfix.

---

### Post by ambre on 2011-03-31
Thank you for your suggestions.  Have have been trying them out and feel that I have made some progress, but unfortunately I am not there yet.  This is really stretching the boundaries for an old duffer like me and the adage 'the more you know, the more you realise what you don't know' is very true.

I looked at Postfix rewriting addresses and have to say that it was a bit too technical for me to understand, but I think that is where the answer lies.  Procmail, on the other hand, seemed to make more sense so this is what I have done and the results I have seen.

Installed [procmail] and entered your code into /home/joe/.procmailrc.
Amended /etc/postfix/main.cf to include [mailbox_command = procmail -a "$EXTENSION"] (found it on the net).
Amended /etc/fetchmailrc to include [mda '/usr/bin/procmail -d %s'] in one of joe's polls (Joe has 3 different email accounts, no idea what it does, found it on the net).
Sent a message to joe at the address of the poll that had been amended and awaited the results.  Evolution is set up to show the sender as [joe@myISP.com]

The results were: the message was picked up by fetchmail, it failed to get delivered to joe's Maildir (why?), a copy message was generated and posted to joe's Gmail account but it was rejected by joe's ISP.

What I now realise is: 1. Joe's local domain is [xyz.lan]. 2. The copy message was sent by [joe@xyz.lan]. 3. Joe's ISP account is [joe123@myISP.com] hence it is being rejected.

I think I just need a little nudge to get this working so any further suggestions will be greatly appreciated. In the meantime I am still surfing the net and reading as much as I can and waiting for the penny to drop.

Thanks

---

### Post by SeijiSensei on 2011-03-31
> **ambre said:**
> This is really stretching the boundaries for an old duffer like me and the adage 'the more you know, the more you realise what you don't know' is very true.

Well I'm a fellow duffer (61), but I've been at this for over fifteen years now.  Every time I scan this board I see how many areas I know nothing about despite having that much experience with Linux.

Sounds like you made some great progress with procmail.  Try adding the lines

```

VERBOSE=yes
LOGFILE=/home/joe/procmaillog

```

to the top of the .procmailrc.  This will write a log that should provide some additional insight into what procmail is doing.

> I looked at Postfix rewriting addresses and have to say that it was a bit too technical for me to understand, but I think that is where the answer lies.

Yes.  In fact I don't think procmail alone can solve this problem because the messages will still be coming, as you say, from [email]joe@xyz.lan[/email] and rejected by your ISP.  

If this is the only machine in xyz.lan, you could try setting its hostname to simply "myisp.com" and see if that fixes things.  

I can't really help with Postfix because I don't use it.  I've run sendmail since I started in this business and know how to do various arcane things with it.  Postfix is generally considered easier to learn and configure than sendmail, and from what I've seen that's probably true.  All I can say is, "don't give up," because it sounds to me like you'll figure this out quite soon.

---

