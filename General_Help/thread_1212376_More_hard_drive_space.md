---
title: "More hard drive space"
date: 2009-07-13
forum: General Help
---

### Post by deluxnate on 2009-07-13
I installed Ubuntu in a multi-boot (Jaunty Jackelope) and the GNOME partitioned enough mem for the setup, but left me with about 40MB. 
Gnome Partition Editor is actually gone on my system now (not sure if it does that after everything's set up or not) so how can I partition more memory for my Ubuntu? 

Thanks in advance
Nate

---

### Post by drs305 on 2009-07-13
You may be confusing disk space with memory. Gparted allocates disk space into partitions.

You can install gparted with the following commands (Open a terminal with ALT-F2 and enter the command in the window). You can also open a terminal via Applications, Accessories, Terminal. It will ask for your password after you run the command. You won't see it as you type - it's a security measure. Just type your complete password when asked and hit ENTER.
```

sudo apt-get update
sudo apt-get install gparted

```


Or install it via Synaptic: System, Administration, Synaptic Package Manager. Look for "gparted".

Here is the introductory page to the wiki on partitioning:
[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

Added:
These will allow you to boot and use Gparted with the system unmounted for system partitioning (in addition to the UbuntuCD:

[URL="http://www.sysresccd.org/Download"SystemRescueCD[/URL]

[Gparted LiveCd]("http://gparted.sourceforge.net/livecd.php")

---

### Post by CatKiller on 2009-07-13
Installing GParted ("Partition Editor") won't help. You cannot change a partition that's mounted, and the partition necessarily has to be mounted if you're running a program from it. Boot from the live cd and do your re-partitioning there.

---

### Post by AdamShumpisxXx on 2009-07-13
If it's actually HDD space you're talking about use this:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Burn it to a CD (or flash it to a thumb drive) and run it live. You'll have to take space from another partition to add it to the one that is lacking.

If it's RAM you're talking about...buy more? Hahaha.

And if it's Virtual Memory you're talking about still use GParted but increase your Swap Partition instead of your / Partition.

Hope that helps!

---

### Post by deluxnate on 2009-07-14
Yes it does thanks for the help. The live cd did everything I needed.

---

