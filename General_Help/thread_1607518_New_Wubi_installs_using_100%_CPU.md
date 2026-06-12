---
title: "New Wubi installs using 100% CPU"
date: 2010-10-27
forum: General Help
---

### Post by Sagekilla on 2010-10-27
Hi all,

I recently installed Ubuntu (10.04 LTS) on two of my computers through Wubi.

One machine is a desktop computer running Windows Vista.
The other machine is a laptop (Dell XPS M1530) running Windows 7.

Both were installed just using Wubi through Windows, using a 20 GB partition.

Currently, my laptop has 1 of it's core pegged at 100% and it gets very hot.

My desktop on the other hand has usually 2-3 cores running at 100%.


The only things I did since I installed was run the update manager and configure my wireless on my laptop. Can anyone point me in the direction of what's causing this?

If you need a full list of hardware I have running on the two, just let me know and I'll grab it (I don't remember off hand).

Thank you for your help!

---

### Post by cgroza on 2010-10-27
Install htop and take a look at what is eating all the CPU. Do not use Gnome System Monitor as it consumes a lot of CPU.

---

