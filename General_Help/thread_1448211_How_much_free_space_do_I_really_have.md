---
title: "How much free space do I really have?"
date: 2010-04-06
forum: General Help
---

### Post by schwabdale on 2010-04-06
I installed Ubuntu 10.04 to a flash drive with a 3gb persistent option by booting from the cd.

Since then, I have installed some programs. How can I tell how much free space I have left
for installing software, or saving data on this persistent drive?

---

### Post by Jguy on 2010-04-06
df -k 

to show free space in kilobytes.

alternatively, You can use:

df -B M/K/G/T

To show in MB/KB/GB/TB respectively.

You can also add switch -a to show all file systems, including dummy ones.

---

### Post by schwabdale on 2010-04-06
Is there any software that will do this with a graphical view?

---

### Post by Jguy on 2010-04-06
If you use System Monitor (System > Administration > System Monitor) and scroll to the tab "File systems" This might give you a good representation.

Alternatively, you should be able to right click on whereever Ubuntu placed the device /media or /mnt and right click on it and go to Proterties.

---

### Post by pickboy87 on 2010-04-06
> **Jguy said:**
> df -k 

to show free space in kilobytes.

alternatively, You can use:

df -B M/K/G/T

To show in MB/KB/GB/TB respectively.

You can also add switch -a to show all file systems, including dummy ones.

Try df -h instead. It essentially shows it in a readable format for **h**umans. As for graphical, it should be somewhere in the system menu for Ubuntu. Haven't used it for a while, so you may have to dig around.

---

