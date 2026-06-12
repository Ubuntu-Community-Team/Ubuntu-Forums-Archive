---
title: "Warning: Remote host identification has changed!"
date: 2012-03-09
forum: General Help
---

### Post by robinasa on 2012-03-09
Hello, I have reinstalled ubuntu on my server but got this problem: WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! when im trying to connect with ssh on port 22.

This is what it looks like:

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.


I have googled it around, but I can not get it fixed.. Im new in linux.

I connect from a Mac



Thanks!

---

### Post by pavi_elex on 2012-03-09
Have you tried this solution.
[click here.]("http://www.cyberciti.biz/faq/warning-remote-host-identification-has-changed-error-and-solution/")

---

### Post by Lars Noodén on 2012-03-09
Before you do anything else, verify that the new key from the server is the correct one.  If it is not, then you have a problem that you system administrator should be made aware of.  To verify the key, download it with [ssh-keyscan](http://manpages.ubuntu.com/manpages/oneiric/en/man1/ssh-keyscan.1.html) and then get the fingerprint with [ssh-keygen](http://manpages.ubuntu.com/manpages/oneiric/en/man1/ssh-keygen.1.html):

```

 ssh-keyscan -t rsa *host.example.org* > /tmp/key
 ssh-keygen -lf /tmp/key

```

The owner of that machine should be able to tell you if that fingerprint is correct.

One other possible cause for the error message might be use of dynamic addresses.  So the last time you logged into that IP number, it was actually a different machine.

---

### Post by wyliecoyoteuk on 2012-03-09
The key has changed because you reinstalled.
A Unique key is generated for the system on install, reinstalling replaces it with a new one!

On  a mac, they are stored in ~/ssh/known_hosts, so deleting the comntents of that folder should allow you to revalidate

---

### Post by robinasa on 2012-04-17
Thanks all! solved my problem! :)

---

