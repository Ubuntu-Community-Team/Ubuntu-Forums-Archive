---
title: "Installation question"
date: 2011-08-14
forum: General Help
---

### Post by LinuxSavedMyComputer on 2011-08-14
I am installing ubuntu on another computer. Since my uncle did the install, i wish to get some details.does the option "Install alongside Vista" create a root and swap partion. and if so, what space does it assign to them

-Sorry if this a dumb question

---

### Post by raja.genupula on 2011-08-14
yes it will create but the size of the swap will be depends on the size you're giving for ubuntu in WUBI .

---

### Post by varunendra on 2011-08-15
I think "Alongside Vista" means the OP is making a native installation (using Live CD), not a wubi setup.

@LinuxSavedMyComputer,
This is not a dumb question, rather quite an important one as the partitioning step is perhaps the most critical step while installing any OS, not just Ubuntu.

Since I don't remember when was the last time I let Ubuntu automatically choose partition sizes, I also don't remember whether or not it creates a separate swap partition.

If my guess is correct that you are using a Live CD to install Ubuntu natively, I'd suggest you to choose the manual partitioning option. Although even in the automatic configuration mode, you'll be presented with the chosen partition plan to confirm it before applying to the hard drive.

My preferred layout is:

[LIST]
[*]one 20-30 GB partition as root (/)
[*]one swap partition of 2GB (regardless of the amount of RAM, as I don't use hibernation)
[*]rest of the partitions as NTFS so that I can access them from windows also.
[/LIST]

---

### Post by grahammechanical on 2011-08-15
When you choose Install Alongside (which ever operating system) then the install process divides the hard disk into two parts (not necessarily equal parts), one for Windows and one for Ubuntu. In the Ubuntu part of the hard disk the install process creates two partitions, one for the OS (root or /) and one for swap. There will always be two at least two partitions created, one for the OS and one for swap.

If you want something different then the best advice that I have seen on this forum is to.

1) Defrag the hard disk from Windows using a Windows utility
2) Use a Windows utility to shrink the Windows partitions to create unused space.
3) In the unused space install Ubuntu as Varundendra is suggesting using the Do Something Else option.

By the way if you install alongside another Ubuntu installation you will end up with two swap partitions. So, we use Do Something Else to assign the original swap partition to both Versions of Ubuntu.

Regards.

---

### Post by Mark Phelps on 2011-08-15
It's best NOT to use the alongside option -- which then allows the Ubuntu installer to shrink your Vista OS partition.  That has resulted in some corrupted Vista installs in the past.  And, when they did get corrupted, they would not boot anymore.

Better approach is to use the Vista Disk Management utility to shrink the Vista partition to leave room for Ubuntu.  Then, use manual partitioning in the Ubuntu installer to format the unused space.

---

