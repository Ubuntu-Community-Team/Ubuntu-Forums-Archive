---
title: "Not enough disk space?"
date: 2009-09-22
forum: General Help
---

### Post by zking on 2009-09-22
I tried to download Java.. Some download error popped up and said that I didn't have enough disk space. Why not? I just recently download Ubuntu, dual-booted it with Vista, and I had so much free space before. Did I download it wrong? In the installation process, I had selected "use continuous free disk space". Did this mess me up? 

What can I do?

---

### Post by drs305 on 2009-09-22
Please post the results of this:
```

df -h

```

Look for your Ubuntu install and see if it is 2.5GB and almost full.

There is a bug in the install process (Step 4). If you choose "side by side" as the partitioning option, you must also manually move a slider at the bottom of the page. This is not obvious, but if you don't, you will end up with a 2.5GB partition. This is not large enough.

You have two options if this is the case: reinstall or expand your / partition. I've written guides for both:

If it is full and it only 2.3-2.5GB following a new installation side by side with Windows and want to reinstall:
[2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

If your / is full, you might look at this guide to resizing a / partition if you know why you are out of space:
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

If you don't know why it is full but it is on a large partition:
[Disk Space Problems & Solutions]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by zking on 2009-09-22
Here are the results: 

[FONT=monospace][IMG]http://img180.imageshack.us/img180/4846/screenshotg.png[/IMG]

I don't know what to do =X
[/FONT]

---

### Post by drs305 on 2009-09-22
Unfortunately, what I mentioned has happened. It's a bit bigger than most of the problem installs but not nearly enough to support an Ubuntu install. The install put Ubuntu in a 2.7 GB partition and has run out of room.

You can either try to expand your / system by taking space from your Windows installation, or reinstall. Both would probably take about the same amount of time unless your server is slow.

I would recommend reinstalling. In Step 4 (Partitioning), make sure you move the slider to the left. The *minimum* recommended size is 8GB. If you plan on keeping a lot of data in your HOME partition, you would need to keep that in mind.

Here again is the link, and also a pic of the specific action you would need to take if you decide to reinstall:
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

[Screenshot of Step 4]("http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874")

If you would prefer to try expanding your / partition, here is the guide that will help you:
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

Note: The developers are aware of this bug and are taking steps to fix it. Unfortunately it is taking a while to get it into the ISOs in Jaunty and Karmic.

---

### Post by zking on 2009-09-22
> **drs305 said:**
> Unfortunately, what I mentioned has happened. It's a bit bigger than most of the problem installs but not nearly enough to support an Ubuntu install. The install put Ubuntu in a 2.7 GB partition and has run out of room.

You can either try to expand your / system by taking space from your Windows installation, or reinstall. Both would probably take about the same amount of time unless your server is slow.

I would recommend reinstalling. In Step 4 (Partitioning), make sure you move the slider to the left. The *minimum* recommended size is 8GB. If you plan on keeping a lot of data in your HOME partition, you would need to keep that in mind.

Here again is the link, and also a pic of the specific action you would need to take if you decide to reinstall:
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

[Screenshot of Step 4]("http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874")

If you would prefer to try expanding your / partition, here is the guide that will help you:
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

Alright, thanks for your help man. :KS

But how exactly would I reinstall? Delete it, then install again? Or override it?..

---

