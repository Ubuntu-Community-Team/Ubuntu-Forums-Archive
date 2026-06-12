---
title: "cloning issue"
date: 2012-01-22
forum: General Help
---

### Post by associates on 2012-01-22
Hi,

I have a machine running smoothly on Ubuntu Server 10.04. What I'd like to try to do is to clone it so that I can run the same settings on another machines.

So what I have done is 
1. I plugged in an external HD of 1TB to the running machine
2. using gparted program to format it to FAT32 before use. Note: my local drive (sda6) is based on ext4.
3. Next, run the command "dd if=/dev/sda6 of=/dev/sdb1" and left it running until it's finished

After that, I run gparted to check on the external HD's used size to see if there is something different there. I found the used size was 899G and the unused size was 43G. I do not know if this sounds all right but I personally found it very strange that it took so much data space on the external HD.

Now since this is my first time I have done the cloning. I need some advice.

Any help would be greatly appreciated.

Thank you

---

### Post by dcstar on 2012-01-23
> **associates said:**
> Hi,

I have a machine running smoothly on Ubuntu Server 10.04. What I'd like to try to do is to clone it so that I can run the same settings on another machines.
..........
Now since this is my first time I have done the cloning. I need some advice.


[LIST=1]
[*]Install new drive - do not waste time making partitions etc.
[*]Use **ddrescue** to clone entire drive - not just partitions - including bootloader; or
[*]Use gparted "cut and paste" to copy individual partitions into free space.
[/LIST]
There are already hundreds of forum posts on this sort of thing.

---

