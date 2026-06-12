---
title: "Mail synchronization between multiple PCs with 8+ mail accounts"
date: 2010-07-15
forum: General Help
---

### Post by xeross on 2010-07-15
Hey, 

I've recently purchased a laptop so I've been focusing on getting my data synchronized between my laptop and PC, I'm posting this here because this gets the best chance of finding cross-platform applications that will help me with this problem.

The problem is as follows, I have 8+ email accounts and I prefer to have them all in 1 single map tree instead of a separate tree for every one of them.

This means IMAP is out of the question, so I've been thinking about a few things but I'm not too sure if there's anything out there for some of these things.

**Option 1 - Unison Synchronization**
Using Unison to synchronize the Thunderbird profiles, problem is Thunderbird can't be running on both machines

**Option 2 - IMAP mail hub for all accounts**
Somehow turn my server into a mail hub that gets email for all my accounts, and serve them through IMAP somehow, only problem that might be is that reply-to won't send a mail back with the same mail address people mailed to (Don't know that for sure).

**Option 3 - POP3 mail hub**
Same as option 2 but with a central POP3 hub that will keep all mails forever, should be doable.

**Not viable option - Turn off mail deletion on server**
This ain't viable because this will either cause some of the mail servers to clog up, especially if I were to only turn deletion on on 1 pc.

...

So it seems the POP3 hub is best, and then just let that delete everything off of the remote servers, is this possible, I've tried setting up a mail daemon before but failed miserably (But will try again if it will make this possible).

Thanks for your time, Xeross

P.S.: This might not be entirely relevant to purely Ubuntu but this seemed to be the best community to ask this on.

---

### Post by xeross on 2010-07-18
Bump.

---

### Post by Bachstelze on 2010-07-18
Option 2 with fetchmail to get all your mail and then serve it with IMAP.  I don't quite understand the replay-to problem you're talking about, though.

---

### Post by xeross on 2010-07-18
> **Bachstelze said:**
> Option 2 with fetchmail to get all your mail and then serve it with IMAP.  I don't quite understand the replay-to problem you're talking about, though.

What I ment was that if I receive an email on let's say [email]accounta@example.com[/email] and I hit the reply button, will it automatically sent it from [email]accounta@example.com[/email], probably a minor detail though.

---

### Post by roger_1960 on 2010-07-18
Hi

Re your option 1, I read an article (I think on OMG Ubuntu) about saving your Thunderbird profile in a dropbox folder and having a symlink to it from the normal location.  I havn't tried it but it could do what you want by synchronising all the machines?

---

### Post by xeross on 2010-07-19
I solved it with fetchmail now, now I just need to figure out why the daemon doesn't fetch mail but running it normally does.

---

