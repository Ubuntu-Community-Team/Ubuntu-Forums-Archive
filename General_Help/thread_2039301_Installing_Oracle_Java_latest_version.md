---
title: "Installing Oracle Java latest version?"
date: 2012-08-08
forum: General Help
---

### Post by Hungry Man on 2012-08-08
I'm currently running an out of date Java. I added some PPA and updated it and I'm one patch behind.

Is there a proper PPA with an up to date version?

I used this PPA:
sudo add-apt-repository ppa:upubuntu-com/java


edt:
sudo add-apt-repository ppa:webupd8team/java

This PPA Seems to work. I'll mark this solved if it does.

---

### Post by QIII on 2012-08-08
Please see the Java wiki in my signature.  In the Oracle Java 7 section is a link called "Using webupd8.org's strikingly simple method"

You will probably need to get rid of your current PPA.

---

### Post by Hungry Man on 2012-08-08
Clicking the link in your sig leads to:

> Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, [no address given] and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.

Apache/2.2.14 (Ubuntu) Server at help.ubuntu.com Port 80
Just fyi.

---

### Post by rukiaEnix on 2012-08-08
I've always preferred to install Java from source.

---

### Post by QIII on 2012-08-08
Works for me and I've never had trouble getting to it to make edits.  Nobody else has complained about it.

May have been transient.

---

### Post by Hungry Man on 2012-08-08
IDK. Not working for me. Weird but it isn't.

edit: Reloading it after the error fixes it. Strange.

---

### Post by QIII on 2012-08-08
> **rukiaEnix said:**
> I've always preferred to install Java from source.

That's what the webupd8 installer does.  It downloads and installs from Oracle, which is the only way it can be done now.  Oracle does not authorize anyone to maintain packages in their repos any longer.  It's just automated and puts files in normal Ubuntu directories for consistency.

The PPA also keeps up with Updates, so you don't have to watch for updates and reinstall.

---

### Post by QIII on 2012-08-08
Works for me and I've never had trouble getting to it to make edits.  Nobody else has complained about it.

May have been transient.

^^ OK, now that is weird!  How did this show up a second time an hour after I posted it?

---

