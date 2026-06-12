---
title: "How to Solve Firefox “this Connection is Untrusted” Problem"
date: 2011-04-20
forum: General Help
---

### Post by lidengdeng on 2011-04-20
Hi:

I got this error (see the pic from this link [http://support.mozilla.com/en-US/kb/This%20connection%20is%20untrusted](http://support.mozilla.com/en-US/kb/This%20connection%20is%20untrusted)) when opening google account, face book, etc.

Some guys suggested to check the system time and make sure the computer time is same as the local time.

According to this hint, I run the command "sudo tzselect" and choose "Europe -> Dublin" (Im in Dublin), then restart PC.

However, the error still pops up.

Any help is appreciated. Thanks.

---

### Post by An Sanct on 2011-04-20
With https, the connection is "untrusted" if the certificate is not up to date or not in the trusted list.

You can add it to the trusted list, by clicking "I understand the risk" and "Add security exception"

PS. make sure, you "understand the risk", make sure the site you want to visit is trustworthy.

---

### Post by lmarmisa on 2011-04-20
This problem could be due to a bug related to the list of trusted Certification Authorities of your Firefox but you should consider more serious problems of security.

Maybe you are not really connecting to Google or Facebook. So, try to investigate deeply this problem. Do not underestimate the possibility that someone is hacking your internet communications.

For example, you should verify your DNS servers are trusted. The public DNS servers of Google (8.8.8.8 and 8.8.4.4) are really trusted.

[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

---

### Post by lidengdeng on 2011-04-20
Thanks for suggestions.

Just make those websites on the list of trustworthy

---

### Post by lmarmisa on 2011-04-20
I repeat. Be careful and verify that the security of your system has been not broken.

This problem could be a symptom that someone is in the middle of your connections with Google or Facebook trying to steal your passwords.

I strongly recommend do not use your computer for Internet banking or e-commerce until you are completelly sure your security has been not broken.

---

