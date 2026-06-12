---
title: "Partition questions (Starting Over)"
date: 2006-04-20
forum: General Help
---

### Post by sinfreealex on 2006-04-20
I've decided to remove the infection, known as Windows Xp (I prefer to call it Winblows), from my 160Gb harddrive.  I am looking to create what will hopefully be the permanent setup for my harddrive.  I have been reading that the best setups have things in seperate partitions.  Could someone give me the short answer as to why this is so?  I would also like serious suggestions on how I should part the drive out.  I am looking for a setup along the lines of
/boot
/swap
/
/home

What sizes would you recommend for those?  I also would like to know if I need to run the installer in expert mode to achieve this goal.  I enjoy the fact that now 'sudo' uses the same password as mine, keeps it simple.  Thank you for your time and I look forward to your advice.

Have a good one.

---

### Post by az on 2006-04-20
[QUOTE=sinfreealex]  I have been reading that the best setups have things in seperate partitions.  [/QUOTE]

Best for what?  In general, "the best" partitioning scheme is the default - all on one partition.

You do not run the risk of running out of disk space on one of your partitions that way.  It is less complex to set up and works just fine.  If you want to preserve your whole home folder for a reinstall (is is very rare that you need to reinstall, you can just remove stuff and start over) it is just as simple to back up that data any other way than to make a seperate partitoin for it.

Do you want to dual-boot?  The installer, by default, will also detect your windows installation and offer to shrink that partition down and create some free space for you.  You do not have to boot into expert mode to do partitioning.  

You can pick one of the easy options (shrink existing partition or use entire drive) or set up your partitions manualy using the default install (just hit enter at the boot prompt when you start the cd)

---

