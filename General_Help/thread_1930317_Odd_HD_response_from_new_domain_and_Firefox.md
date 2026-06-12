---
title: "Odd HD response from new domain and Firefox"
date: 2012-02-23
forum: General Help
---

### Post by Roving Sign on 2012-02-23
I launched a domain yesterday - with a CPanel/Fantastico WordPress install...

Im familiar with DNS propogation -  but this one is odd...

It  has been winking in and out - over the past 24 hours. Might resolve for 5 minnutes, then its gone. That might not be so odd...

The wierd part is - when it tries to resolve, my HD just FREAKS OUT and starts getting very busy, churning away at...something.

Another observation - the Firefox stautus bar says "Looked up aaaaaa.com..."

I've never seen "Looked Up" before - I only ever see "Looking Up..."

Any insight? Im still going to give it another day to clear...but the HD freak out is wierd.

---

### Post by efflandt on 2012-02-23
Is your hostname in **/etc/hostname**, and do hostname and FQDN for the computer (either as alias) point to an IP on your computer (an alternate loopback or nic IP) in **/etc/hosts**? Or is any server app configured for a different name that none of the above points to you?

Maybe your system or an app is having a difficult time finding itself.

---

