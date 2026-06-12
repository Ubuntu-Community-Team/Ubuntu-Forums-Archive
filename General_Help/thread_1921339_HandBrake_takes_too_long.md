---
title: "HandBrake takes too long"
date: 2012-02-06
forum: General Help
---

### Post by KingYaba on 2012-02-06
Sorry to bump an old thread but is there a way to tell Handbrake to use multiple cores? Right now it's only using one of my four and I'd like to use two or three if possible. Thanks. :)

---

### Post by howefield on 2012-02-06
Post moved to its own thread.

---

### Post by satanselbow on 2012-02-06
Are you using the snapshot ppa? Multi-threading jus fine n dandy here ;)

[https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)

ppa:stebbins/handbrake-snapshots

---

### Post by howefield on 2012-02-06
Must say it's been a while since I used Handbrake, but as far as I recall the default was to automatically used multiple processors.

---

### Post by KingYaba on 2012-02-07
> **satanselbow said:**
> Are you using the snapshot ppa? Multi-threading jus fine n dandy here ;)

[https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)

ppa:stebbins/handbrake-snapshots

I didn't realize there was a PPA. And apparently I've been running an old version of Handbrake. Simply upgrading did the trick. I did a test and it used four cores so I'm happy.

---

