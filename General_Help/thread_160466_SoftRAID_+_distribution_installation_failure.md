---
title: "SoftRAID + distribution installation failure"
date: 2006-04-15
forum: General Help
---

### Post by Nachtengel on 2006-04-15
Using the directions found in this wiki article:

[https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

I have successfully partitioned my soft RAID array for the purposes of installing Ubuntu on.  However, I was looking to install Dapper instead of Breezy, but there apparently is no script for Dapper.  (during the command debootstrap 'adjective for version' /target)

Trying Breezy instead, I am faithfully typing in:

ubuntu@ubuntu: debootstrap breezy /target

and I am getting the following:

ubuntu@ubuntu: debootstrap breezy /target
I: Validating Packages
I: Checking component main on [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)...

But here it freezes... no network traffic, no CPU utilization, no nothing.  Are there any suggestions as to what might be going on, and how I could fix this?

---

