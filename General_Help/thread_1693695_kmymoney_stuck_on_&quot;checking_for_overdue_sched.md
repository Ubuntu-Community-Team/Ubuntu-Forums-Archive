---
title: "kmymoney stuck on &quot;checking for overdue scheduled transactions"
date: 2011-02-23
forum: General Help
---

### Post by Phosphoric on 2011-02-23
Help!

kmymoney is freezing on start up with the above message.  Processor running at 100%.  Only way out is to kill the process.
I tried removing the programme and reloading via the software centre but no joy.  If I re-name my date file to a different file type the programme loads normally but of course asks to start a new account.

It would seem that my data file is corrupted in some way?

---

### Post by Phosphoric on 2011-02-23
Think it's sorted now.

Started in terminal ```
kmymoney -n
```

This starts the application with no data file.

Went to settings>configure kmymoney>scheduled transactions.

De-select "check schedules on startup"

This has allowed me back in to my data file thank goodness. :D

I'll now work from there.

Don't know if it was connected but after all the deletions and re-installations I got another error message on start up "could not read network connection list /home ray.DCOPserver_ray-desktop_0

Went to  /home/username > show hidden files and deleted .ICEauthority and rebooted.

Seems OK now.

I'll mark this as solved in that my original problem is now fixed. :D

---

### Post by BertQuat on 2012-01-24
Thank you for this it helped me out no end.

Having done a bit more investigation it seem to be related to a scheduled transaction with an end date that had been passed but the transaction not entered (transaction date 18th en date 20th and date file accessed 24th). I have entered the transaction and reset the automatic checking and all seems okay now. 

Thank you again 
 
:popcorn:

---

