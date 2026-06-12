---
title: "Improve LiveUSB performance"
date: 2010-04-05
forum: General Help
---

### Post by blazemore on 2010-04-05
Hi all,

I'm using Linux Live USB Creator to make a persistent Ubuntu 10.04 flash drive.
However, with persistence, the Live OS takes an age to load (about 5-10 mins).
Without persistence it boots in a very respectable time of about 70-80 seconds.

I've experimented with larger block-sizes, which do seem to make some difference.
It's a 4gb flash drive. I've noticed that the larger I make the persistence file, the greater this performance drain becomes.

Short of buying a faster flash drive, is there anything I can do to make this faster?

---

### Post by dcstar on 2010-04-06
> **blazemore said:**
> Hi all,

I'm using Linux Live USB Creator to make a persistent Ubuntu 10.04 flash drive.
However, with persistence, the Live OS takes an age to load (about 5-10 mins).
Without persistence it boots in a very respectable time of about 70-80 seconds.

I've experimented with larger block-sizes, which do seem to make some difference.
It's a 4gb flash drive. I've noticed that the larger I make the persistence file, the greater this performance drain becomes.

Short of buying a faster flash drive, is there anything I can do to make this faster?

Persistence means you are writing to the Flash drive, and that can be **very** slow depending on the quality of the drive.

I boot persistent flash drives and it isn't that slow (10.04 is a very fast booting release).

---

