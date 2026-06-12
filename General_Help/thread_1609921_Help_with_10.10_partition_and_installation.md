---
title: "Help with 10.10 partition and installation"
date: 2010-10-31
forum: General Help
---

### Post by MaTTech on 2010-10-31
Thought I'd try Ubuntu on my desktop since I use Linux on my phone (Andriod) and have just recently set up a Linux VPS from scratch and thus have been learning Linux commands.

I have two 1-TB harddrives and a 64-GB Solid State Drive in my desktop. The 64-GB SSD is my boot drive and has Windows 7 installed on it. I have Ubuntu 10.10 installed on a USB drive at the moment.

First time I tried installing Ubuntu "next to an operating system" and used the slider to allocate 10-GB for the install, the install failed. I did some research and found that Windows takes up almost all of the space and using GParted would solve this problem.

So, I used GParted to take about 16-GB away from my Windows install to use for my Ubuntu install.

The 16-GB doesn't show up when the "install next to" option is selected, but it also says that there are 2 hidden partitions and the 16-GB partition is one of them.

I have no idea what to do with the utility that pops up next. When I click "add", I also put a "/" and check "beginning". Seems like it partitions okay, but when I click "install", it starts complaining about having no space allocated for virtual memory.

I have no idea how to do any of the above to make that 16-GB partition work so that I can install Ubuntu on it.

Hopefully I was clear and concise enough in explaining what my problem is so that it can be resolved quickly. Kind of excited to try out Ubuntu. From the trial, it seems very fast compared to Windows.

---

### Post by Verbeck on 2010-10-31
here's how the partitioning in usually done manually
[B]
10-15 Gb : [/B]mount point[B] /
[/B]double the ram size as** _SWAP_ ( or 2GB will do  ) **<---------- this is what you missed
for the remaining space, create a partition and set the** mount point as /home **<------------Optional, but if you do this, it'll be easier to install from scratch a later time (your files and application settings will be stored in your home folder)

hope this helps

EDIT: just noticed that you have allocated 16gb. so 10 gb as /, 2gb as swap, and the rest as /home will do fine (but IMO,16 gb is kinda small-/home usually gets a lot bigger than 4gb)

---

### Post by Sef on 2010-10-31
> double the ram size as SWAP ( or 2GB will do ) <---------- this is what you missed

Actually today, it is recommended that your swap be the same amount as your ram.

From Ubuntu Documentation: [Swap FAQ]("https://help.ubuntu.com/community/SwapFaq")

> How much swap do I need?
As a base minimum, it's highly recommended that the swap space should be equal to the amount of physical memory (RAM). Also, it's recommended that the swap space is twice the amount of physical memory (RAM) depending upon the amount of hard disk space available for the system (although this "recommendation" dates back from a time when physical RAM was very expensive and most Unix systems ran with many processes in swap space - a situation that hardly applies in most situations these days, but ancient Unix/Linux myths like this "recommendation" tend to survive well past their "use by" dates). In reality, if you use hibernation you need what was outlined the relevant paragraph above, otherwise you need as much swap space as your system will use - which may be actually be very little in a modern hardware setup. The only downside to having more swap space than you will actually use is the disk space you will be reserving for it.

---

### Post by Verbeck on 2010-10-31
> **Sef said:**
> Actually today, it is recommended that your swap be the same amount as your ram.

From Ubuntu Documentation: [Swap FAQ]("https://help.ubuntu.com/community/SwapFaq")
i didn't see that before :o

---

### Post by efflandt on 2010-10-31
If you have enough RAM, you do not necessarily need swap, unless you want to be able to hibernate (not needed to suspend).  I had swap on my SSD when I first put it in my laptop to install Ubuntu and try it out, but I don't even think my 1 GB laptop used it.  So now that the SSD is on my 8 GB desktop, I removed the swap partition and expanded a partition to use that space.

So if you have 2 GB or more, I would not worry about the warning of not having virtual memory, unless you want to hibernate.  And then it should be at least as large as your RAM (maybe slightly larger, so you do not undercut it if looking at decimal vs. binary MB).

The **free** command can show how much memory you are using and the important number is under **used** on the second line of numbers (used on first line includes buffers and cache).

```
             total       used       free     shared    buffers     cached
Mem:       8121512     871320    7250192          0      57596     326988
-/+ buffers/cache:     486736    7634776
Swap:            0          0          0
```

---

