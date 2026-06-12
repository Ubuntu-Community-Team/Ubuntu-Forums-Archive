---
title: "Tab expansion of tilde (~) behaving strangely"
date: 2011-04-26
forum: General Help
---

### Post by Birion on 2011-04-26
Hi, I'm having some problems with bash (it seems). I'm not entirely sure when it started, but as far as I can tell it was the latest set of updates (language pack, lsb and tzdata for Natty).

Basically, the ~<Tab> sequence does not expand to /home/birion as it should (and as it did up until pretty much just now), but instead gives me a list of various system user home directories, such as 

```

~avahi/
~avahi-autoipd/
~backup/
~bin/
~couchdb
~daemon/

```

and others. However, ~ on its own still refers to /home/birion - cd ~ gets me to my home directory without a problem, but moving files in between directories hits the ~<Tab> muscle memory problem really quickly.

---

### Post by idoitprone on 2011-04-26
opps you actually need to type ~/<tab>

Edit: disregard what i said before i typed opps, if you really want to diagnosis what happened, check /etc/bash_completion. I also have this behavior, but I dont use ubuntu.

---

### Post by Birion on 2011-04-27
~/<Tab> gives me a listing of my home directory, but doesn't expand the ~, e.g. *cd ~/Do<Tab>* gets expanded into *cd ~/Documents/*, not *cd /home/birion/Documents/*. Say I want to move Documents/photo.jpg to Pictures/Photos. I'm used to typing *mv p<Tab>~<Tab>Pi<Tab>Ph<Tab>*, which means that right now, half the time I'd rename the file to ~PiPh instead of moving it.

I did look at bash_completion, but I was like a kindergartener trying to read Stephen Hawking.

---

