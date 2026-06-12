---
title: "Cannot get gpg key for ppas on Karmic"
date: 2009-10-30
forum: General Help
---

### Post by crazybilly on 2009-10-30
I just installed Karmic--it's looking really good. I'm particularly excited about the new way to add ppas, namely add-apt-repository.

But when I try, I get the following error:

```

gpg: requesting key 72D340A3 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

I assumed something was wonky, so I tried getting the key the old school way, as per the instructions on Launchpad (ie, ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
```, but I get the same error there as well.

Considering that I can't find any info out there on this one, I'm pretty sure either I'm doing something wrong or there's something a little funky on my end. Any thoughts?

---

### Post by Uncle Spellbinder on 2009-10-30
Happening here as well. Though I've gotten three of 4 gpg keys the past several hours. I'm going to hazard a guess at server overload.

Someone may correct me, but that's my guess.

---

### Post by crazybilly on 2009-10-30
that was my guess too. which is, I suppose, better than Ubuntu being broke

---

### Post by crazybilly on 2009-10-31
I seem to be periodically able to grab the keys, now. Looks like you're right: probably a traffic issue.

---

