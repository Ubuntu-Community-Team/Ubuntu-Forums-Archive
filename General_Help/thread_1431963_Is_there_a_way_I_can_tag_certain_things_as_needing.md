---
title: "Is there a way I can tag certain things as needing root access?"
date: 2010-03-17
forum: General Help
---

### Post by Roasted on 2010-03-17
The thought has been lingering to add some Ubuntu machines to our system base here at work. But something kind of had me curious. I was going to set up a generic VNC password on each machine in the remote desktop settings, but this isn't something I want the users to have access to. Can I tag certain items or features as requiring root password so if they click on remote desktop, it comes up requiring the root password to continue?

---

### Post by blueridgedog on 2010-03-17
If you change the ownership of the binary to root (sudo chown root:root /usr/bin/vinagre), then change the permissions to 700 (sudo chmod 700 /usr/bin/vinagre -only the owner can read/write/execute), then you should get the results you are looking for.

---

### Post by Roasted on 2010-03-17
Ah okay. I was thinking maybe there was a way I could have some kind of access control list, and just select certain items to require root authentication before proceeding...

---

### Post by blueridgedog on 2010-03-18
ACL's for Linux have existed for a while:

see [http://www.vanemery.com/Linux/ACL/linux-acl.html](http://www.vanemery.com/Linux/ACL/linux-acl.html) for example.  I have never used them.

---

### Post by HermanAB on 2010-03-18
That is what sudo is for.  Read the man page and the configuration file itself, there are examples in it.

Don't use ACLs.  There is a good reason why nobody uses them - ACLs are unmaintainable in practise.

---

### Post by Roasted on 2010-03-18
> **HermanAB said:**
> That is what sudo is for.  Read the man page and the configuration file itself, there are examples in it.

Don't use ACLs.  There is a good reason why nobody uses them - ACLs are unmaintainable in practise.

We use ACLs... and they work just fine... But when I said ACL in my example above, it was just a generic term I was throwing on the table.

I was just curious if there was some sort of configuration utility that would be able to pick and choose what levels are required to run certain programs...

---

