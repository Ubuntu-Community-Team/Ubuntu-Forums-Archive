---
title: "Tracker running although it shouldn't"
date: 2011-01-14
forum: General Help
---

### Post by zzarko on 2011-01-14
I have an tracker problem that I know it could be solved by uninstalling it, but I'd like to try otherwise. Tracker is configured to recursevly look at Desktop (few icons), Documents (some OOo documents, about 600MB of PDFs), Music, Pictures and Videos (all empty), and non-recursevly at my home directory (a few archives and documents). None of this directories have any links to other parts of the system. At Indexing tab all options are (currently) turned off.

I have 4 HDs in my system, with about 10 partitions (all mounted in /media), containing various audio/video material and pictures (and very few of actual documents). I have installed a lot of programs and games (~18GB).

Every time I log in, there is a process tracker-store that is sweating my disks (iotop shows 90-100% for that process), and while it's running, I almost can't do anything with the machine. Sometimes, when I select Pause All Indexing from tracker's icon, the searching stops, sometimes not (and when it's not, it's tracker-store that is doing the work).

Now, I have a few questions, if someone know:
1. What is tracker still indexing after almost 3 months since I installed 10.10? The Documents directory is more or less the same since the installation. The File system percentage is always 0%, and Applications is 1% (I turned Indexing options off last week, as I tried to stop it from indexing anymore). The computer is (almost) never turned off.
2. Why is it still working if all options are turned off?
3. Is there a way to disable it without uninstalling?

---

### Post by zzarko on 2011-02-03
After not being able to solve my tracker problems in some other way, I uninstalled tracker - problem solved...

---

