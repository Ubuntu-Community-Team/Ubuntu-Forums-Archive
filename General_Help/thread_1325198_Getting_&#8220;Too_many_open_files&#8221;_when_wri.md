---
title: "Getting &#8220;Too many open files&#8221; when writing to shared folder on Ubuntu 9.10"
date: 2009-11-13
forum: General Help
---

### Post by Brockb on 2009-11-13
Hi All,

I've shared the folder at my local Ubuntu web-server machine, to be able to write directly to it while working at the IDE on my Windows 7 PC.

First time I've got driven mad when Netbeans failed to SVN update (as mentioned files going straight to the shared folder via LAN). The error it showed was Connot create the file .../.svn/lock

So I've tried to re-checkout the project, at Neatbeans all when fine. But update problem remained.

So I've installed Zend Studio, but it even failed on checkout. With similar can't write error message.

Then I've tried doing checkout into Win7 machine local folder, and move the files to the shared, hoping that might be after restoring the project I'll be able to finally update it! Hell no, my Windows gives me the "Too many open files" error.

I've tried setting "soft/hard nofile" at /etc/security/limits.conf - (for my user, for nobody, for *) - nothing helps

Later times when Ubuntu was 9.04 - I've never had this problem.

Please help!

---

### Post by Brockb on 2009-11-14
Anybody? 
Any clues? 
Any guesses?

<Up!>

---

### Post by Brockb on 2009-11-18
Oh my, is it nobody that have a thing to say on the issue?

---

