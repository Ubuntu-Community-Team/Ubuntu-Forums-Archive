---
title: "Keyserver keyserver.ubuntu.com down?"
date: 2010-01-14
forum: General Help
---

### Post by weaver4 on 2010-01-14
Is keyserver.ubuntu.com down?

I try to add the repository:

sudo add-apt-repository ppa:xorg-edgers/ppa

and I get this error:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 165D673674A995B3E64BF0CF4F191A5A8844C542
gpg: requesting key 8844C542 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

---

### Post by pmulgaonkar on 2010-01-14
I had the same problem earlier. There are mirror keyservers that seem to work. See post #14 for a list on this thread: 
```
https://bugs.launchpad.net/ubuntu-website/+bug/435193
```

Good luck.

--prasanna

---

### Post by firebrat75 on 2010-01-20
I am having the same problem, I tried all the keyservers listed in post #14 of the thread that you mentioned, and I still can't get through....  I have checked my firewall logs, and it is not getting blocked there.  

I don't have firestarter or anything installed since we have a perimeter firewall here where I work, so could it be something blocking it from the OS?

---

### Post by neogarfield on 2010-01-23
Hey,
I'm a newbie to Linux, and I've got the same problem. I've tried the alternate keyservers mentioned as well.... Any help would be cool...

---

### Post by quixote on 2010-05-28
I had to turn off the firewall at my router briefly in order for the key process to work.  The perimeter firewall may be what's causing the problem.

Be nice if the fact that a firewall could be an issue were stated right up front in the error message! 

:rolleyes:

---

### Post by neogarfield on 2010-05-28
Hey, actually I found out that that my system administrator was blocking the keyserver port... He opened it, and its working fine for me now!

---

