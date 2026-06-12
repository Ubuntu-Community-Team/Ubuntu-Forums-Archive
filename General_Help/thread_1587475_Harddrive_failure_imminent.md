---
title: "Harddrive failure imminent"
date: 2010-10-03
forum: General Help
---

### Post by Oxyris on 2010-10-03
Okay, so I was testing out Ubuntu 10.04 on both the a desktop and a laptop (both HP...I don't remember the particular models but if asked I will find out). It worked fine on the desktop. When I booted the laptop with Ubuntu it worked fine. When I tried to connect it to the internet it seemed to go okay. I mean it asked for the network password and everything. But as soon as the signal was recognized I got a warning that said "Hard drive failure is imminent."

Now this laptop has gone through problems before. I don't know the extents because it's a family laptop and I rarely use it (it's super slow. It used to run Vista but now it runs XP and it's slow regardless). I think the hard drive may have been replaced at one point of another and it has had to be re installed numerous times before. And the way it is used leads me to believe that there is not a lot of space left in that hard drive. So that may have been the issue.

But I want to make sure it is a hardware problem and not something that will happen on the device I eventually decide to install Ubuntu on. So if someone can ease my worries that'd be really helpful. (And also help me understand why the hard drive would fail when the live CD doesn't actively use the hard drive, at least not the way it would if it had been installed in the hard drive.)

---

### Post by coffeecat on 2010-10-03
> **Oxyris said:**
> And also help me understand why the hard drive would fail when the live CD doesn't actively use the hard drive, at least not the way it would if it had been installed in the hard drive.

You're right that the live CD doesn't actively use the internal hard drive - unless you mount one of the partitions from the Places menu. But the live session does probe hardware during the boot sequence and I guess what was happening was that it was picking up the SMART data from the drive.

If you want to investigate this further, boot up with the live CD again and go to System > Administration > Disk Utility. Click on the entry for the hard drive and you should see the SMART status in the right pane - that is if the drive has not already failed. Mine is saying "Disk is Healthy". If you click on "View Smart Data..." you can do just that and run self-tests, but if the drive is truly about to fail then a self-test might be the last straw.

---

