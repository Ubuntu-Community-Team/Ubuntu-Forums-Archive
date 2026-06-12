---
title: "Deleting incomplete Ubuntu partitions"
date: 2009-11-27
forum: General Help
---

### Post by Agentarrow on 2009-11-27
I tried to install Ubuntu as a dual boot with my Vista-running laptop after being very impressed running it as my primary operating system on my desktop.  However, the installation failed at 69% complete and my computer shut down.  My current problem is that I now have 40 GB of space partitioned to Ubuntu but I cannot boot ubuntu and I am unsure how to approach deleting Ubuntu and restoring the partition to Vista, or leaving it as open space for when I burn a new CD (I believe that the CD was my problem) and reinstall Ubuntu.  I read a thread that I googled about how to remove Ubuntu from a vista system, but this did not completely satisfy my question.  So I ask that if anyone has the knowlege of what I should do in this sensitive situation, I would appreciate your feedback.  I understand little of the OS infrastructure, but I remember reading something about something called grub making the computer unbootable if Ubuntu is simply deleted.

---

### Post by Rx.WDZ on 2009-11-27
If you're going to reinstall Ubuntu you can manually specify the partitions during installation and simply repartition the space that currently has the broken system. That would be the simplest solution. I guess more importantly do you plan on reinstalling Ubuntu?

---

### Post by dcstar on 2009-11-27
> **Agentarrow said:**
> I tried to install Ubuntu as a dual boot with my Vista-running laptop after being very impressed running it as my primary operating system on my desktop.  However, the installation failed at 69% complete and my computer shut down.  My current problem is that I now have 40 GB of space partitioned to Ubuntu but I cannot boot ubuntu and I am unsure how to approach deleting Ubuntu and restoring the partition to Vista, or leaving it as open space for when I burn a new CD (I believe that the CD was my problem) and reinstall Ubuntu.  I read a thread that I googled about how to remove Ubuntu from a vista system, but this did not completely satisfy my question.  So I ask that if anyone has the knowlege of what I should do in this sensitive situation, I would appreciate your feedback.  I understand little of the OS infrastructure, but I remember reading something about something called grub making the computer unbootable if Ubuntu is simply deleted.

Grub is only installed right at the end of the installation process.

You can boot off the install CD and manually delete that partition using the Partition Editor, or do it during the install process as described in the other reply.

---

