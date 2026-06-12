---
title: "How to remove swap partition (after installation)"
date: 2009-08-17
forum: General Help
---

### Post by sundar_ima on 2009-08-17
I have installed ubuntu 9.04 with out giving any swap partition. Later on I tried this tutorial  [COLOR="DarkRed"][https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")[/COLOR]to add swap partition from terminal. Only change I made was 3072Mb instead of 512Mb. Now the problem is that I am not able to save anything on ubuntu partition and not able to open any application like openoffice.org. It shows no free space (or free space 0B) though i have lot of space on in the drive. How do I remove swap partition and get my ubuntu work like before. 

Any help is appreciated.

---

### Post by sundar_ima on 2009-08-25
Is there anybody to help me...

---

### Post by nhanquy on 2009-08-25
You can use **swapoff** then delete the swap partition for now but that would not the right answer because you had so little space for your ubuntu system to begin with.

---

### Post by slakkie on 2009-08-25
First of all, we need to details:

please post the output of the following commands:

```

cat /etc/fstab
swapon -s
df -kh

```

The first two are to check what you have defined as swap partitions/files, the third is to see how much space you have on each slice.

---

### Post by DaithiF on 2009-08-25
Hi,
if you followed the guide referenced, then you will have created a swap file, rather than a swap partition.  I mention that only because removing a swap file is a little easier than a swap partition -- no need for tools like gparted.

You can basically follow the steps in the guide but in reverse, so:
1. remove the swap entry that you had added in /etc/fstab
2. turn off the swapfile:
```
sudo swapoff /mnt/yourfilename.swap

```
note the command here is **swapoff**, as opposed to the **swapon** you used to enable swap
3. delete the file
```
sudo rm /mnt/yourfilename.swap

```
thats all, you should then have your 3gb of disk space back.

---

### Post by sundar_ima on 2009-08-25
Thank you for the reply.

It worked partially. These are the steps i followed...

1. I removed the swap file entry from **/etc/fstab**.

2. **sudo swapoff /mnt/3072Mb.swap** gave me this out put "swapoff: /mnt/3072Mb.swap: Invalid argument"

3. But went ahead and removed the swap file using nautilus with root permission (command line gave me error "no such file")

Finally i got at least 2.2Gb free space from 0bytes then cleaned up my system with "**sudo apt-get clean**". Now i have 2.4Gb free space. But still 5Gb is hidden. How do i retrieve it? :(

---

### Post by DaithiF on 2009-08-25
Good.  What do you mean by 5gb is hidden.  How do you determine that ?
thanks

---

### Post by Post Monkeh on 2009-08-25
if you go to system > administration > partition editor
what does the main screen sat about your drives and partitions?

---

### Post by Penguin Guy on 2009-08-25
> **sundar_ima said:**
> But still 5Gb is hidden. How do i retrieve it? :(
A useful tool for finding out where all your disk space is, is Baobab ([COLOR="Green"]Applications -> Accessories -> Disk Usage Analyser[/COLOR]). It will show you a hierarchical pie chart diagram (basically a glorified pie chart) of your disk usage; once you get the hang of it, it proves a useful tool for freeing disk space.

---

### Post by P4man on 2009-08-25
> **sundar_ima said:**
> Thank you for the reply.

It worked partially. These are the steps i followed...

1. I removed the swap file entry from **/etc/fstab**.

2. **sudo swapoff /mnt/3072Mb.swap** gave me this out put "swapoff: /mnt/3072Mb.swap: Invalid argument"

3. But went ahead and removed the swap file using nautilus with root permission (command line gave me error "no such file")

Finally i got at least 2.2Gb free space from 0bytes then cleaned up my system with "**sudo apt-get clean**". Now i have 2.4Gb free space. But still 5Gb is hidden. How do i retrieve it? :(

edit: I misread. You can probably ignore this msg, sorry :blush:


A few things. to see what swap is in use, type ```
swapon -s
```

It seems you didnt make a swap partition, but a swap **file**. "/mnt/3072Mb.swap" is a file, that you mounted as swap. If you want to reclaim that space, make sure the swap on it is not active (swapon -v to check, if you want to swapoff everything, type "sudo swapoff -a"), then delete that file. I bet its 3GB in size ;)

---

### Post by sundar_ima on 2009-08-26
> **DaithiF said:**
> Good.  What do you mean by 5gb is hidden.  How do you determine that ?
thanks

I am extremely sorry. Today i checked each folder in my home folder and found lot of movie files (downloaded by my friend) which i did not took in to account. So the procedure to remove swap file is correct and worked properly.

I think i had less than 3Gb of space before i used that guide (that is why i got 0bytes). <--- Just a guess. 

Thanks for all the help guys i got my (free) space again :P

**@ P4man**

> It seems you didnt make a swap partition, but a swap file.

Ok. Changed the thread title accordingly. 

A good lesson is learned today :)

---

