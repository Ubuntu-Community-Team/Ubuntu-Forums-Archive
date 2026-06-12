---
title: "logon scripts and best practices"
date: 2010-05-24
forum: General Help
---

### Post by aarong021 on 2010-05-24
Hello everyone,

I had a question about logon scripts, so here's my scenario.  

I want to create a logon script (or somesuch) that creates a file (if it doesn't already exist) and checks the file for some info otherwise.  If it finds a given trigger in that file, it logs into a local database and does some operations.  

Now my problem isn't with creating that file or even getting it to function as a logon script -- it's with permissions.  After the logon script creates the file, I want that user to have read access on it ONLY.  Further, I don't want to give the user any kind of root access so that they could do the database operations in question or chown/chmod the file. 

What's the best practice here?  I'm noticing that whenever the script runs (in .bashrc right now) the script runs with the current user's permissions.  Ideally, I'd like to make it so the login script can run at a higher level of permissions, (higher than the user has).  Is this even possible?  What's the best way to do this?

Thanks for your help.

---

### Post by aarong021 on 2010-05-25
Anyone?

---

