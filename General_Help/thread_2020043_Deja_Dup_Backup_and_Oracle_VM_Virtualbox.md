---
title: "Deja Dup Backup and Oracle VM Virtualbox"
date: 2012-07-07
forum: General Help
---

### Post by Welly Wu on 2012-07-07
I am having a problem with Deja Dup and my Oracle VM Virtualbox virtual machine folder and files. To be specific, Deja Dup seems to stop backing up .VDI files especially when I make changes within my guest virtual machine and I need to backup those changes using Deja Dup. Subsequent incremental and delta backups stop when Deja Dup is trying to access the .VDI files. I have a 53.67 gigabyte .VDI file that contains my Microsoft Windows 7 64 bit Ultimate Edition Service Pack 1 guest virtual machine.

I also subscribe to CrashPlan+ home unlimited service on a monthly basis and it has no problems handling my backups or restores. I am thinking about replacing Deja Dup with CrashPlan+ home unlimited as I am able to make local backups to an external hard disk drive that is attached to my System76 Lemur Ultra notebook PC.

I found this thread which is marked as solved:

[https://answers.launchpad.net/deja-dup/+question/170945](https://answers.launchpad.net/deja-dup/+question/170945)

However, the information does not solve my specific problem.

Why is this happening?

What more information and data do you need for me to be of greater assistance to pinpoint the problem and resolve it?

How do I fix this problem?

---

### Post by Welly Wu on 2012-07-07
I deleted my previous Deja Dup backups and I initiated another full backup. It is now backing up all of my /home directory including my Oracle VM Virtualbox .VDI files. I still don't consider this problem to be resolved because I suspect that future incremental and differential backups will continue to come to a halt when Deja Dup tries to backup any changes to my Oracle VM Virtualbox .VDI folder and files. If I find this to be the case at a later date, then I will switch to CrashPlan+.

Finally, Deja Dup is slow. I only have a Crucial M4 SATA-III 6 GB/s 128.00 GB Solid State Drive and Deja Dup takes forever to backup my data. My /home directory is only 112 GB and I used 82 GB for my data. I have a Western Digital MyPassport 2.00 TB USB 3.0 Portable hard disk drive connected to a Super Speed USB 3.0 port on my System76 Lemur Ultra and Deja Dup takes about one hour to make a backup of my /home directory.

I have no idea what gives with Deja Dup, but I am beginning to think that I should switch to CrashPlan+. It gives me no problems whatsoever.

---

