---
title: "email filter/conduit using thunderbird"
date: 2012-09-02
forum: General Help
---

### Post by astrand on 2012-09-02
Hi All,
My main email source (exchange server) has ceased providing POP.  I had been using POP to forward email to gmail and was using gmail as my main email client which I like a lot.  

Now I have set up a thunderbird instance on my ubuntu (12.04) box that downloads email via IMAP from my main exchange server and based on thunderbird filter rules, assigns gmail labels by using IMAP to upload the mail to gmail.  This is a kludgy solution at best:

1) requires my box to be online continuously.  
2) requires thunderbird client to run continuously on that box
3) requires GUI to modify filters on box running thunderbird.

My main problem is 2.  Thunderbird periodically crashes or goes into a state where it no longer moves email via IMAP (which requires restarting the application).

So my question(s):
1) is there an online email client that can perform the task I lay out above _or_
2) is there a more stable approach to running a client on my own box.  Preferably as a daemon that can be remotely managed.

thanks

---

