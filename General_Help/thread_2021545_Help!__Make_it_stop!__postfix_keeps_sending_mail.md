---
title: "Help!  Make it stop!  postfix keeps sending mail"
date: 2012-07-09
forum: General Help
---

### Post by AlexBooton on 2012-07-09
I had a problem where mail was not being delivered.  It was queued instead.

Now that the problem is resolved it is sending hundreds of old messages and I can't stop them!

I've tried all of these commands to no avail:
```
# postfix flush
# postfix -f (gives an error message)
# mailq  (queue seems to be empty. Nothing shows up.)
# postsuper -d ALL
# postsuper -d ALL deferred
```
Yet the mail keeps being sent!

How do I kill this???

This is U12.04.

Thanks

---

### Post by HermanAB on 2012-07-09
Well, you can always stop a process with 'ps -e' and 'kill -9 PID'.  Then you can 'cd' to /var/mail/whatever, look for the mail and delete it.

---

### Post by AlexBooton on 2012-07-09
> **HermanAB said:**
> Well, you can always stop a process with 'ps -e' and 'kill -9 PID'.  Then you can 'cd' to /var/mail/whatever, look for the mail and delete it.

Thanks Herman,

I should have said this is outbound mail; not to a local user. /var/mail... seems to only have users queues.  Nothing for outsiders.

At least that's what I'm seeing now.  It may not always be true.

AB

---

### Post by SeijiSensei on 2012-07-09
Look in /var/spool/postfix.

---

### Post by AlexBooton on 2012-07-09
OK, found the problem.

We use fetchmail to retrieve messages from a remote system.

There was an oversize message at the remote server.  

Postfix kept rejecting it and sending out a bounce message.  

But fetchmail never deleted it from the remote server so the cycle repeated every time fetchmail ran.

Even though I had emptied the queue it didn't have any thing to do with new bounces.

Thanks both for your suggestions,

AB

---

