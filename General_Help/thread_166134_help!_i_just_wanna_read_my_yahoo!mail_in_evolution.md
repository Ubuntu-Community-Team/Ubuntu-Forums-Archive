---
title: "help! i just wanna read my yahoo!mail in evolution"
date: 2006-04-25
forum: General Help
---

### Post by groggyboy on 2006-04-25
so, the title says it.  i've done some searching in google and these forums, but nothing is helping.  i've poked around in fetchyahoo, and i've gotten it to acknowledge that there is email in my yahoo account, but why won't it download it to my computer?  what am i doing wrong?!?  if anyone knows how to use fetchyahoo or any other similar program, i'm all ears.

and btw, i know of the thunderbird extension to check yahoo, and i know that non-american yahoo accounts have free POP3 forwarding - i *don't* wanna use thunderbird and i *do* have an american account!

cheers,
groggyboy

---

### Post by groggyboy on 2006-04-25
if it helps, this is what the terminal outputs:> groggyboy@PantherModern:~$ fetchyahoo
Logging in securely via SSL as [email]mr_ory@yahoo.com[/email] on Tue Apr 25 21:18:44 2006
Running in daemon mode. Will check every 30 minutes.
Forking into the background.
groggyboy@PantherModern:~$ You are using 0% of your 1.0GB limit.
Successfully logged in as [email]mr_ory@yahoo.com[/email].
Country code : us    Folder: Inbox    Version: 2.10.2
Getting Message ID(s) for message(s) 1 - 1.
Got 1 Message IDs
 and then it waits for a bit, and then repeats.  so it knows there is email there.  why isn't it downloading it?!?

oh, and if someone with fetchyahoo expertise could show me how to get it to forward all my yahoomail to gmail, that would be even better (cuz i've already set up evolution to check my gmail account - that was breeze)

cheers!

---

### Post by troyDoogle7 on 2006-04-26
I know that this isn't the ideal solution, but you can setup a filter that will forward emails to another email account in yahoo itself(I use the uk one)

---

### Post by groggyboy on 2006-04-26
How did you do it?  I like the idea - send all my yahoo.com mail to a yahoo.ca account, which then sends it to my gmail.com account, and from there i can read it online or in evolution.  Ya, I really like it.  Only problem is, i can't figure out how to set up yahoo.com to send the mail to yahoo.ca!  You said something about a filter, but i can only get yahoo.com to filter mail to folders in my yahoo.com account!  There's gotta be a way...

cheers, groggyboy

---

### Post by groggyboy on 2006-04-26
well, i finally got something to work: [mrpostman]("http://mrpostman.sourceforge.net/").

it's java-based and runs on my computer, downloading the mail straight to evolution.  oh and it's slow as all get out.  but at least it works, which is more than i can say for freepops, fetchyahoo, or any of the other solutions i tried.

definitely not as elegant as troyDoogle7's suggestion.  i'd still like to get that one to work.  it's just so pretty!  no need to install software on my computer, and i could forward everything to gmail first and evolution second, so if i'm ever away from my computer, I can still read *all* my email in one place!

i'm still open to suggestions if anyone can get troyDoogle's (or any other) method to work!

cheers,
groggyboy

---

### Post by EdThaSlayer on 2006-06-24
i have been trying to find a way to do that! thanks!

---

