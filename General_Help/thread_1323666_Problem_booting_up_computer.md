---
title: "Problem booting up computer"
date: 2009-11-11
forum: General Help
---

### Post by Old Newville on 2009-11-11
My computer is giving me fits and I wondered if anyone can help. I'm running Ubuntu 8.04 LTS and I've been very pleased with it until now.

I had a power outtage at my house not long ago. Since then, my computer has had a rough time on boot up. 

The check disk function runs and produces a long list of error messages too numerous to write down or even read.

Here is a sample: "dev/sda5 contains a file system with errors." Also this, "Inodes that were part of a corrupt orphan link list found," and "an automatic file system check of the root system failed." I'm no programmer, but these don't sound good!

During bootup, if I go to "recovery mode," I get nowhere and have to restart the box. If I start in the usual mode, I can get my machine to boot up if I hit escape to skip the check disk. The machine boots very, very slowly compared to before the power outtage.

So far, this issue has not slowed down my work, but I'm worried that some morning the computer won't start.

I'd appreciate any suggestions.

---

### Post by phishie on 2009-11-11
> **Old Newville said:**
> My computer is giving me fits and I wondered if anyone can help. I'm running Ubuntu 8.04 LTS and I've been very pleased with it until now.

I had a power outtage at my house not long ago. Since then, my computer has had a rough time on boot up. 

The check disk function runs and produces a long list of error messages too numerous to write down or even read.

Here is a sample: "dev/sda5 contains a file system with errors." Also this, "Inodes that were part of a corrupt orphan link list found," and "an automatic file system check of the root system failed." I'm no programmer, but these don't sound good!

During bootup, if I go to "recovery mode," I get nowhere and have to restart the box. If I start in the usual mode, I can get my machine to boot up if I hit escape to skip the check disk. The machine boots very, very slowly compared to before the power outtage.

So far, this issue has not slowed down my work, but I'm worried that some morning the computer won't start.

I'd appreciate any suggestions.

Well, since you can boot it up for now, first thing first. Back it up somewhere before it really goes bonkers.

---

### Post by 824957q on 2009-11-11
yes definitly back it up and this has happend with me on my ubuntu it is not the programs fault it is actually your hard discs fault for some reason ubuntu wasn't made with a loss of data restore wich means if a power outage occurs it wont even bother looking at your hard drive to resume everything so you should try out kubuntu you can have all the black outs you want and everything will boot up normaly don't forget to mark your thread as solved :)

---

### Post by lidex on 2009-11-12
Backup, backup, backup. Then boot from a LiveCD into a command line. You'll want recover/repair option. Run this command:
```
e2fsck -f -y -v /dev/sda2
```

The reason you boot into live session or just command line is that ***you must not run this check while the partition is mounted***. Replace sda2 with the appropriate entry.

---

### Post by Old Newville on 2009-11-12
Thanks to everyone who posted a suggestion. The solution was so simple I feel stupid for not seeing it earlier.

When the disk scanner was running and the error messages flying, the whole kaboodle ended at a prompt: "root@ubuntu." 

All I had to do was type "fsck" and the file system repaired itself. It took about 10 minutes. When I rebooted the machine, it started up as quick and smooth as before.

Problem solved!

---

### Post by lidex on 2009-11-13
Please mark thread as solved under "thread tools". It helps others who may have that problem.

---

