---
title: "Thunderbird loses mail and asks four times for password"
date: 2011-07-27
forum: General Help
---

### Post by ELMIT on 2011-07-27
I got a wired problem with Thunderbird 3.1.11

Maybe I had the problem before, but recently I notice it, that emails are missing. 
I get the email to Thunderbird on my desktop and I get it to my iPhone.
I noticed that I got a reply for an important email and read it on my iPHone. Then I went to my desktop to see/print that email, ... it is not there.

It is not in the junk folder, it is not in the trash, it is in no inbox (I have multiple email accounts).

I found a thread to rebuild Index.msf, did not appear the email. I deleted the file Index.msf and restarted Thunderbird. I searched for the message, but no luck, this email is missing.


What could be wrong, How to fix it?



The second problem is that Thunderbird asks me for a Security device password, I put it in, and it keeps on asking me four times for it, till it finally accept it. It is not typed wrong, there are multiple windows asking for the Security device password.

How to limit it to ask only once (as it did in the past)?

---

### Post by darkfeline on 2011-09-05
Hi!

I'm not sure about your first problem, but I think your second problem is probably [this]("http://forums.mozillazine.org/viewtopic.php?f=31&t=1711565").  Basically, there's a clash between the Lightning/calendar add-on and Thunderbird's password store, so it ends up asking for your master password multiple times.  There's an addon, StartupMaster, which gives one prompt that precedes all the threads requesting passwords at the same time.

---

