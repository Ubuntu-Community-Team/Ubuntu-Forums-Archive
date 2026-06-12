---
title: "Can't resize root partition with GParted"
date: 2010-05-23
forum: General Help
---

### Post by Axilus on 2010-05-23
Hey guys,

I just installed ubuntu on my laptop and I was recommended to create separate partitions for root, home and swap. I was told that 15GB would be enough for a  root partition but I am actually running out of that space very quickly after installing a few programs.

I wanted to resize it so I loaded up my live cd with Gparted and It won't let me resize it by more than 1MB. I also have at least 30GB of unallocated space on my hard drive so I don't know why I can't use it.

Here's some screenshots of GParted:

---

### Post by jeremyswalker on 2010-05-23
You can't resize the root partition, because there is no room next to it. Your extended partition is in the way. If you look, all of your unallocated space is located after the extended partition. You would have to move it to expand your root partition.

---

### Post by Axilus on 2010-05-23
> **jeremyswalker said:**
> You can't resize the root partition, because there is no room next to it. Your extended partition is in the way. If you look, all of your unallocated space is located after the extended partition. You would have to move it to expand your root partition.

How exactly do I move it, when I right click on it the only option that is available is 'new'

---

### Post by Axilus on 2010-05-23
I found [this thread]("http://ubuntuforums.org/showthread.php?t=543646") and I'm going to try and do it with the GParted Live CD.

---

### Post by jeremyswalker on 2010-05-23
You can't move it, because swap is turned on. If you look, you will see the little padlock next to your swap partition and the extended partition. If you right click the swap partition, there should be an option to turn swap off. This should allow for movement of all your partitions.

What you would probably do after disabling swap, is expand your extended partition to fill the remaining unallocated space. After that, move the logical partitions within the extended partition to the end. Then you should be able to shrink the extended partition at it's beginning, thus allowing you to expand your root partition.

Of course, before starting...  Backup.. Backup.. Backup..

---

### Post by oldfred on 2010-05-23
IF you have 15GB why are you running out of room. I have many programs installed and have used only 6GB. Are you perhaps running backups that write into root or some process that is generating large error messages?

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by Axilus on 2010-05-23
Well, I have installed pretty much every program that I have on my home ubuntu desktop, and I have used half of the alloted space. I figured if I knock up the size of the partition a little bit more then I won't ever have to worry about it.

This is just and OCD thing of mine thats all lol. I'm not going to run out of space soon, I would just rather not run out of space unexpectedly in the future.

---

### Post by Axilus on 2010-05-23
> **jeremyswalker said:**
> You can't move it, because swap is turned on. If you look, you will see the little padlock next to your swap partition and the extended partition. If you right click the swap partition, there should be an option to turn swap off. This should allow for movement of all your partitions.

What you would probably do after disabling swap, is expand your extended partition to fill the remaining unallocated space. After that, move the logical partitions within the extended partition to the end. Then you should be able to shrink the extended partition at it's beginning, thus allowing you to expand your root partition.

Of course, before starting...  Backup.. Backup.. Backup..

It took a while but it worked. Thank you very much.

Btw, why did it take like 5 hours to just to move around unallocated space. It seems so horribly inefficient.

---

### Post by jerome1232 on 2010-05-23
Because it's actually cloning your partitions and the data from one spot to another, it probably copies all of the free space too.

Your weren't just moving around unallocated space, you were moving everything, including free space around.

---

