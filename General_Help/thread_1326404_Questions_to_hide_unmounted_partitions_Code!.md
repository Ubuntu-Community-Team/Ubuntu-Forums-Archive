---
title: "Questions to hide unmounted partitions Code!"
date: 2009-11-14
forum: General Help
---

### Post by Kartinka on 2009-11-14
```
# we only care about block devices
ACTION!="add|change", GOTO="hide_partitions_end"
SUBSYSTEM!="block", GOTO="hide_partitions_end"
KERNEL=="loop*|ram*", GOTO="hide_partitions_end"

################################################## ############################

# Floppy Drive which should not display
KERNEL=="fd0", ENV{ID_DRIVE_FLOPPY}="1", ENV{DKD_PRESENTATION_HIDE}="1"

# Partition sda2 that we want to hide from gnome
KERNEL=="sda2", ENV{DKD_PRESENTATION_HIDE}="1"

# Partition sda3 that we want to hide from gnome
KERNEL=="sda3", ENV{DKD_PRESENTATION_HIDE}="1"

################################################## ############################

LABEL="hide_partitions_end"
```Hey Community :wink:,

I'm new here and new by using Ubuntu. in the last days, I tried to install Ubuntu 9.10 and make some settings there. No long time later, i found the first problems for myself...

I have the following partitions on my only hard drive in my Laptop.

[FONT=Times New Roman][FONT=Arial]40 GB Vista Systempartition
20 GB Ubuntu / (root) Partition
2  GB Ubuntu SWAP
10 GB Ubuntu /home Partition
30 GB Filepartition for Vistasystem
70 GB Filepartition for Vistasystem
80 GB Filepartition for Vistasystem[/FONT]
[FONT=Arial]
While i tried to seperate both Systems of each other I found this Thread. Because I will seperate them that 
I will see nothing of Windows in Ubuntu and otherwise.[/FONT]
[/FONT]I tried it with the written things in this Thread and everything happend good, I was able to hide the Partitions.

But now I have some little questions.

First question: Are the partitions hidden from the whole system with that code or only from gnome / nautilus?!

Second question is for understanding the code:

What are the following words do, and where can i find a description or manual with them?!

ACTION!="add|change", GOTO="hide_partitions_end"
SUBSYSTEM!="block", GOTO="hide_partitions_end"
KERNEL=="loop*|ram*", GOTO="hide_partitions_end"

ENV{DKD_PRESENTATION_HIDE}="1"

I searched but nowwhere i found something about that?! But anyway I have to found or? Because how to know something abaut add|change or loop*|ram* to write that code when it's nowwhere to read?!

---

### Post by Kartinka on 2009-11-15
No one any Idea?!

---

