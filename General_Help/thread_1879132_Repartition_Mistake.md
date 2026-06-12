---
title: "Repartition Mistake"
date: 2011-11-11
forum: General Help
---

### Post by brohan76 on 2011-11-11
Hello, I am a Ubuntu and Linux newbie. I apparently know just enough to get myself in trouble. A few weeks ago I shrank my Vista partition in Vista, and then installed Ubuntu 11.10. Today I removed more unnecessary items from Vista, and then shrunk that partition further leaving me 58GB of unallocated space. I then used a 11.10 live CD and GParted for the first time to try and grow the Linux partition. I was unable to figure out how to use the size option to grow the partition, only shrink it. What I ended up inadvertently doing was moving my original 37GB partition (/dev/sda5) to the unallocated 58GB partition.  Ubuntu rebooted just fine. When I go to properties of the partition I am booted into for Ubuntu it says I have 51GB free space, leading me to believe that I now boot to the 58GB partition (/dev/sda3).

My question is this - Storage Device Manager shows errors for /dev/sda5.  What should I do to /dev/sda5 to rid it of errors, and then what should I do with hit entirely? Is there a way, and if so, should I combine sda3 and sda5, OR do I format sda5 and use it as a separate partition?  What would be the benefits of each? 

I know that was a lot, but thank you for your help and input.

---

### Post by dcstar on 2011-11-11
> **brohan76 said:**
> Hello, I am a Ubuntu and Linux newbie. I apparently know just enough to get myself in trouble. A few weeks ago I shrank my Vista partition in Vista, and then installed Ubuntu 11.10. Today I removed more unnecessary items from Vista, and then shrunk that partition further leaving me 58GB of unallocated space. I then used a 11.10 live CD and GParted for the first time to try and grow the Linux partition. I was unable to figure out how to use the size option to grow the partition, only shrink it. What I ended up inadvertently doing was moving my original 37GB partition (/dev/sda5) to the unallocated 58GB partition.  Ubuntu rebooted just fine. When I go to properties of the partition I am booted into for Ubuntu it says I have 51GB free space, leading me to believe that I now boot to the 58GB partition (/dev/sda3).

My question is this - Storage Device Manager shows errors for /dev/sda5.  What should I do to /dev/sda5 to rid it of errors, and then what should I do with hit entirely? Is there a way, and if so, should I combine sda3 and sda5, OR do I format sda5 and use it as a separate partition?  What would be the benefits of each? 

I know that was a lot, but thank you for your help and input.

You have two partitions with the same UUID being mounted as / (root).

Boot off a Live CD and change the UUID of the partition you **don't** want to boot from (search for detailed instructions).

Reboot into Ubuntu and do:
```
sudo update-grub
```
Once you are satisfied that your Ubuntu system is working correctly, use gparted to delete the unused partition and then repeat the above command.

---

