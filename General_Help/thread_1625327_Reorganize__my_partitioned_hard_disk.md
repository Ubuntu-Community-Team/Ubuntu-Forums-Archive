---
title: "Reorganize  my partitioned hard disk"
date: 2010-11-18
forum: General Help
---

### Post by Djalmahal on 2010-11-18
I have a 500GB hard drive which over the course of time I partitioned to allow for different distros. Now I want to reorganize it. How do I join different partitions together, i.e. the 2 unallocated partition on /dev/sda3 to form a new partition for Ubuntu?

Thanks for your input.

---

### Post by wilee-nilee on 2010-11-18
> **Djalmahal said:**
> I have a 500GB hard drive which over the course of time I partitioned to allow for different distros. Now I want to reorganize it. How do I join different partitions together, i.e. the 2 unallocated partition on /dev/sda3 to form a new partition for Ubuntu?

Thanks for your input.

I would first investigate that triangle on the ntfs partition, you may need a chkdsk run. Right click on it then information and take a look at what it says. Ask questions if your not familiar with the process of running this if needed.

---

### Post by Djalmahal on 2010-11-18
Attached is the output of the ntfs partition.
This partition (Windows) never gave me problems though

---

### Post by wilee-nilee on 2010-11-18
> **Djalmahal said:**
> Attached is the output of the ntfs partition.
This partition (Windows) never gave me problems though

Problems can appear before they happen, do you know how to set up a chkdsk /r  the r rather then f as indicated is a bit more thorough longer generally used method.

---

### Post by Djalmahal on 2010-11-18
Sure, I can do this, any input on the first question how to join the unallocated partitions in Gparted, or can I do it in the UBuntu install?

---

### Post by psusi on 2010-11-18
To join the free space you have to move the two partitions in the middle ( /home and swap ) to the left or the right.

---

### Post by Djalmahal on 2010-11-19
I don't seem to be able to do it in my normal Ubuntu (probably because / and /home is mounted?), will it work if I boot from USB?

---

### Post by wilee-nilee on 2010-11-19
> **Djalmahal said:**
> I don't seem to be able to do it in my normal Ubuntu (probably because / and /home is mounted?), will it work if I boot from USB?

From a pure system safety point of view do you have everything backed up?

Edit: Can you afford to loose any operating system installed and or any data as well?

---

### Post by oldfred on 2010-11-19
Since the partitions are in the extended partition, any one logical partiton mounted in the extended mounts the entire extended and prevents editing. You have to use a liveCD or USB and even then it may auto mount the swap and you have to do a swapoff to allow editing.

Always have good backups. Depending on how much data you have in the partitions you are moving it can take a very long time. Do not interrupt the process.

---

### Post by Djalmahal on 2010-11-19
Yeah I have it backed up, but now I came a new big problem, posted it here.

[http://ubuntuforums.org/showthread.php?t=1625395](http://ubuntuforums.org/showthread.php?t=1625395)

Thanks for your help

---

