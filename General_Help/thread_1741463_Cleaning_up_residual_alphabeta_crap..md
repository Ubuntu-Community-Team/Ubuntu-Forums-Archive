---
title: "Cleaning up residual alpha/beta crap."
date: 2011-04-28
forum: General Help
---

### Post by c@ssie on 2011-04-28
I've been using Natty since alpha, and along the way several thing became broken. I would like to  get my system to be as stable as if I did a clean install, but without haveing to do all the work it would take, to get everything back the way I want it.  Is there a way to clean up all the leftover obsolete files and bad configurations, created by buggy beta builds?

---

### Post by KegHead on 2011-04-28
Hi!

I've installed bleachbit and Ubuntu tweak.

Also from terminal;

sudo apt-get autoclean

sudo apt-get autoremove

KegHead

---

### Post by c@ssie on 2011-04-29
> **KegHead said:**
> Hi!

I've installed bleachbit and Ubuntu tweak.

Also from terminal;

sudo apt-get autoclean

sudo apt-get autoremove

KegHead

I think you misunderstood my question. All of those things are useful for freeing up disk space,but thats not what i'm concerned with.  I'm with the stability of my system.

---

### Post by KegHead on 2011-04-29
Hi!

Update your system.

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

KegHead

---

### Post by c@ssie on 2011-04-30
> **KegHead said:**
> Hi!

Update your system.

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

KegHead


so that should clean up everything?

---

### Post by KegHead on 2011-04-30
Hi!

And update/upgrade your machine.

KegHead

---

