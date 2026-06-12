---
title: "Empathy AIM support missing since Karmic upgrade"
date: 2009-11-05
forum: General Help
---

### Post by topdownjimmy on 2009-11-05
I upgraded to Karmic last week, and I just noticed today that my Empathy no longer has AIM support.  My AIM accounts are gone, and I don't have the choice to add a new AIM account.  This might be my fault, as I know I have quite a few non-standard PPAs in my software sources.

What package is responsible for providing Empathy with AIM support?  What might I have done wrong, and how can I fix it?

---

### Post by topdownjimmy on 2009-11-05
Well, I installed telepathy-core and that seems to have fixed the problem.  It didn't restore my previously existing AIM accounts, but AIM now appears in the new account drop-down.

However, when I try to connect, nothing happens.  I'm using the server login.messaging.aol.com, and port 5190.

And where are my account settings stored, anyway?  I'm alarmed that my old AIM account info is still missing.

---

### Post by pkkid on 2009-11-11
I am having a very similar issue to you.  I had AIM accounts on karmic for about 2 weeks.  Last night they stopped connecting.  After a reboot, the accounts didn't even show up in Empathy and I don't have the option to add AIM accounts either.  I wonder if this is caused by some upgraded component or something.

In any event, adding telepathy-core and restarting empathy did *not* give the option to add AIM accounts as it did for you.

---

### Post by bronxbomberz41 on 2009-11-21
> **pkkid said:**
> I am having a very similar issue to you.  I had AIM accounts on karmic for about 2 weeks.  Last night they stopped connecting.  After a reboot, the accounts didn't even show up in Empathy and I don't have the option to add AIM accounts either.  I wonder if this is caused by some upgraded component or something.

In any event, adding telepathy-core and restarting empathy did *not* give the option to add AIM accounts as it did for you.

Same thing for me.  Almost exactly the same thing.  installing telepathy-core actually took away options for me to add.  Before I had IRC, Jabber, Gtalk, and Local People, now I only have Jabber and Gtalk.

---

### Post by swiftsam on 2009-12-08
my AIM accounts have disappeared as well.  For me the problem occurred after a normal update well after I upgraded to Karmic.

if I run apt-get upgrade, it says the empathy package is being held back.  I've currently got 2.28.1.1 installed.

This doesn't do much to quiet the complaints that empathy wasn't ready to be included as default.

---

### Post by nhasian on 2009-12-09
please make sure you have telepathy-haze installed

```
apt-cache policy telepathy-haze
```

mine says:

telepathy-haze:
  Installed: 0.3.2-1
  Candidate: 0.3.2-1
  Version table:
 *** 0.3.2-1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
        100 /var/lib/dpkg/status

---

### Post by swiftsam on 2009-12-10
Thanks for the reply, but no fix yet.  Telepathy-haze was not installed, but installing it didn't change anything.
```

~$ apt-cache policy empathy
empathy:
  Installed: 2.28.1.1-0ubuntu1
  Candidate: 2.28.1.1-0ubuntu1
  Version table:
 *** 2.28.1.1-0ubuntu1 0
        500 http://ubuntu.media.mit.edu karmic-updates/main Packages
        100 /var/lib/dpkg/status
     2.28.1-1ubuntu1 0
        500 http://ubuntu.media.mit.edu karmic/main Packages
~$ apt-cache policy telepathy-haze
telepathy-haze:
  Installed: 0.3.2-1
  Candidate: 0.3.2-1
  Version table:
 *** 0.3.2-1 0
        500 http://ubuntu.media.mit.edu karmic/main Packages
        100 /var/lib/dpkg/status

```

any ideas?

---

### Post by swiftsam on 2009-12-16
My aim account started working today on its own.  I didn't notice an empathy upgrade in my last upgrade, but it may have been in there.  Anyhow, everything is solved here.

---

