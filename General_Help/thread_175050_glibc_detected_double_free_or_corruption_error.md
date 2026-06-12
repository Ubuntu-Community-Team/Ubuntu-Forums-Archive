---
title: "glibc detected double free or corruption error?"
date: 2006-05-12
forum: General Help
---

### Post by jms830 on 2006-05-12
every time I try to run "xbindkeys-config" I get this error

*** glibc detected *** double free or corruption (fasttop): 0x08097c40 ***
Aborted

I've tried apt-get remove xbindkeys xbindkeys-config --PURGE
and then reinstalled them but still get the error. I also logged out and it still happens when I log back in.

---

### Post by RavenOfOdin on 2006-05-12
That's an old Linux C++ error. Not new news.
To fix it so you can run the program just type:

export MALLOC_CHECK_=0

before running the program.

---

### Post by jms830 on 2006-05-12
thanks it worked. If you get a chance, what exactly does that command do?

---

### Post by RavenOfOdin on 2006-05-12
Some programs might try to free a space through delete that has already been unallocated. That command suppresses the error by switching off checks for this activity.

---

### Post by vitorgatti on 2008-06-10
Thanks a lot, this worked for me too, but I'd like to know what happened to occur this error.
I my case, for example, this message was appearing when I ran a big shellscript of billing stuff here in my company.

I also discovered searching the web that this could be cause by downgrading some packages, but this was not done.

If anyone could explain, I will be grateful :)

---

### Post by galilean on 2008-06-23
Hi all,
I had this error too. I tried typing what you suggested, i.e.

export MALLOC_CHECK_=0

before running the program i want to run, IDL, and it told me:

export command not found

I just recently installed Wubi in my windows machine, and any help will be most appreciated.

---

