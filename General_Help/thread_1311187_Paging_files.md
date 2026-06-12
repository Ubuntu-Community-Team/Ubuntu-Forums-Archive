---
title: "Paging files"
date: 2009-11-02
forum: General Help
---

### Post by forensics man on 2009-11-02
Hello,
I am doing a forensics research project with many operating systems and am planning to use Ubuntu. If I use a Live CD to surf the web and post to a forum,check email etc....etc.... will a Ubuntu NON-Presistent Live CD session leave paging and swap files on the harddrive that I can later analize, of will the harddrive literally be untouched without any digital artifacts at all? Windows XP created many many artifacts even after the history was cleared and cookies were deleted. 
 
Thanks
:popcorn:

---

### Post by HiImTye on 2009-11-02
if your computer has sufficient memory it is unlikely that the swap partition will have any tracable information on it, however, it is a possibility.

---

### Post by Giblet5 on 2009-11-02
Giblet5 can't read scripts.
**P4** *can* read scripts and also has Mad Perception Skillz.

---

### Post by forensics man on 2009-11-02
Does this mean that even if I limit memory in the system, (To try and force paging) that instead of forcing paging I will just get an insufficient memory message?

---

### Post by Giblet5 on 2009-11-02
Giblet5 can't read scripts.
**P4** *can* read scripts and also has Mad Perception Skillz.

---

### Post by P4man on 2009-11-02
AFAIK a live cd will automatically mount any swap partitions it finds. You can use  swapoff to stop that.

---

### Post by HiImTye on 2009-11-02
I thought that the live CD automagically uses the first available SWAP drive to speed itself up or am I wrong on this one?

---

### Post by Giblet5 on 2009-11-02
Giblet5 can't read scripts.
**P4** *can* read scripts and also has Mad Perception Skillz.

---

### Post by P4man on 2009-11-02
Posting this from a live session (karmic, but I know for fact it was like this on jaunty):
```

ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2013        599       1413          0         73        326
-/+ buffers/cache:        199       1813
Swap:         3718          0       3718


ubuntu@ubuntu:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/sdb5                               partition	3807364	0	-1

```

'nough said :)

---

### Post by Giblet5 on 2009-11-02
Giblet5 can't read scripts.
**P4** *can* read scripts and also has Mad Perception Skillz.

---

### Post by P4man on 2009-11-02
> **Giblet5 said:**
> Is that a non-persistent image eg, LiveCD, or is that a USB Startup Disk?

admittedly, its a USB live stick. I might try again with a cd if I can find any, but I seem to remember ubuntu always doing this, I even once put a drive with a swap partition  in an old machine with just 256 Mb ram just so it could boot the live cd and be somewhat usable.

Anyway, I didnt realize there could be a difference between live sessions from cd or usb in this way so i guess this is not conclusive yet. Will try with a cd later.

---

### Post by Giblet5 on 2009-11-02
Giblet5 can't read scripts.
**P4** *can* read scripts and also has Mad Perception Skillz.

---

### Post by P4man on 2009-11-02
This is from a ubuntu hardy live CD (only cd I could find). Definitely no persistence: 

```
ubuntu@ubuntu:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	3807364	0	-1
ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2026        536       1490          0         74        306
-/+ buffers/cache:        155       1871
Swap:         3718          0       3718
ubuntu@ubuntu:~$ 
```

Boy was that bootup splash HUGE in hardly lol.

---

### Post by P4man on 2009-11-02
> **Giblet5 said:**
> 
**P4** *can* read scripts and also has Mad Perception Skillz."


Eck, no, I never even looked at those scripts. I just noticed it enabled swap.

---

### Post by Giblet5 on 2009-11-02
Bitter dregs aren't so bad...  =D>

---

### Post by P4man on 2009-11-02
shame you edited it all your posts, I was curious about your comment relating to enabling swap being able to mess things up. Im not sure what you meant by it, did you mean if an installed linux hibernated?

Anyway, to get back to the question of the OP, I guess, yes in theory using a live cd could leave information on the harddisk of the computer, provided that
A) it actually has a linux swap partition
B) it has so little ram that swap is even used (not likely if it has 1GB or more)
C) rebooting after the live session doesnt clean the swap (I got no idea if it does)

if you're worried about this, just run
sudo swapoff
before beginning your browsing session.

---

### Post by forensics man on 2009-11-02
I guess I will just need to try it then this evening. I was under the impression I could physically remove the harddrive and boot from live cd and work NON-Presistently. My forensics system is windows based so i will probally need to format NTFS so I can even look at the thing so I guess I will 
1> Format NTFS
2> Boot using Live CD
3> analize the drive for Ubuntu swap files....

---

### Post by Giblet5 on 2009-11-02
> **P4man said:**
> shame you edited it all your posts, I was curious about your comment relating to enabling swap being able to mess things up. Im not sure what you meant by it, did you mean if an installed linux hibernated?

Anyway, to get back to the question of the OP, I guess, yes in theory using a live cd could leave information on the harddisk of the computer, provided that
A) it actually has a linux swap partition
B) it has so little ram that swap is even used (not likely if it has 1GB or more)
C) rebooting after the live session doesnt clean the swap (I got no idea if it does)

if you're worried about this, just run
sudo swapoff
before beginning your browsing session.


No biggie and the info is useless since it's wrong.

Here's the problem I described:

You boot a LiveCD and it starts using swap because there is inadequate RAM.

You bring up fdisk and delete the swap partition (eg, to move it to a separate drive for performance reasons) and create a new ext3 partition where swap used to be, write out the changes, and run mkfs on it.

The contents of the swap space just changed a wee bit, and the kernel has no code to check to see if you did that or something like it.

I'd call it a bug.

---

### Post by QLee on 2009-11-02
[QUOTE=Giblet5]Here's the problem I described:

You boot a LiveCD and it starts using swap because there is inadequate RAM.

You bring up fdisk and delete the swap partition (eg, to move it to a separate drive for performance reasons) and create a new ext3 partition where swap used to be, write out the changes, and run mkfs on it.

The contents of the swap space just changed a wee bit, and the kernel has no code to check to see if you did that or something like it.

I'd call it a bug.[/QUOTE]

Well, when you make a filesystem on "it" (your new partition) you give it a new UUID so it won't have the UUID of what was previously your swap.

---

### Post by P4man on 2009-11-02
> **Giblet5 said:**
> 
You bring up fdisk and delete the swap partition (eg, to move it to a separate drive for performance reasons) and create a new ext3 partition where swap used to be, write out the changes, and run mkfs on it.


Not sure I understand you correctly, but you can not delete a swap partition that is in use. You have to swapoff first. Its a common problem with posters here who try resizing partitions fron a livecd but find they cannot because there is swap partition inside an extended partition (which is mounted by the livecd) and therefore the entire extended partition is "locked". Swapping off solves that.

---

### Post by P4man on 2009-11-02
> **forensics man said:**
> I guess I will just need to try it then this evening. I was under the impression I could physically remove the harddrive and boot from live cd and work NON-Presistently. My forensics system is windows based so i will probally need to format NTFS so I can even look at the thing so I guess I will 
1> Format NTFS
2> Boot using Live CD
3> analize the drive for Ubuntu swap files....

Ubuntu (and I bet any other linux distro) does not swap to ntfs. Or even Ext (unless you configure it by hand to use a specific swap file). linux by default swaps to a *partition* which is formatted as swap. On a system with only windows installed there will never be such a partition (windows swaps to a swap *file* that resides on its own fat or ntfs partition) and hence a livecd cant and wont swap in that scenario.

its only if you boot a live cd on a machine that already has a linux swap partition on any of its harddrives that this could occur. If there is no such partition a live cd wont leave a trace.

---

### Post by Giblet5 on 2009-11-02
> **QLee said:**
> Well, when you make a filesystem on "it" (your new partition) you give it a new UUID so it won't have the UUID of what was previously your swap.

Kernel paging doesn't use UUID unless it's explicitly declared in /etc/fstab. A LiveCD just has a generic fstab, so the startup includes a search of all partitions followed by a swapon procedure for discovered swap partitions. After that - until swapoff or boot - it uses an open file descriptor for the device.

Changing swap while the kernel is running is almost like dd'ing /dev/zero to the current / partition: it will complete successfully and the kernel has no mechanism to detect that this has happened until it attempts to load pages which no longer make sense. I imagine this would result in a kernel panic, but even if it didn't, it would end badly.

It's a bug: one that's unlikely to ever bite anyone, but it's still a bug.

---

### Post by P4man on 2009-11-02
> **Giblet5 said:**
> Kernel paging doesn't use UUID unless it's explicitly declared in /etc/fstab. A LiveCD just has a generic fstab, so the startup includes a search of all partitions followed by a swapon procedure for discovered swap partitions. After that - until swapoff or boot - it uses an open file descriptor for the device.

Changing swap while the kernel is running is almost like dd'ing /dev/zero to the current / partition: it will complete successfully and the kernel has no mechanism to detect that this has happened until it attempts to load pages which no longer make sense. I imagine this would result in a kernel panic, but even if it didn't, it would end badly.

It's a bug: one that's unlikely to ever bite anyone, but it's still a bug.

Ok I take back what I wrote earlier. gparted will not let you delete a swap partition in use, but fdisk will. I just did it (yeah im nuts)

edit: or not. Hmm. Here is my attempt (sdb5 being my swap partition)
```

Command (m for help): d
Partition number (1-5): 5

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: [B]Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)[/B]
Syncing disks.

```
lets see if its gone
```

bob3@bob3-desktop:~$ sudo fdisk -l
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed7ced7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2502    20097283+  83  Linux
/dev/sdb2           38440       38913     3807405    5  Extended
/dev/sdb3            2503       31280   231159285   83  Linux
/dev/sdb4           31281       38439    57504667+  83  Linux

Partition table entries are not in disk order

```

Looks gone. but I cant make a new one there either:
```

Command (m for help): n
No free sectors available

Command (m for help): 
```

swap still seems in use:


```
bob3@bob3-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2013       1140        872          0         42        448
-/+ buffers/cache:        650       1362
Swap:         3718          0       3718

bob3@bob3-desktop:~$ swapon -s
Filename				Type		Size	Used	Priority
**/dev/sdb5 **                              partition	3807364	0	-1
```

---

### Post by QLee on 2009-11-02
Giblet5, Not sure if you missed in the earlier post.

[QUOTE=P4man]Not sure I understand you correctly, but you can not delete a swap partition that is in use. You have to swapoff first. ...[/QUOTE]

You detailed deleting and recreating, therefore you had to swapoff. Or is P4man wrong?

Edit: I see from P4man's post.

---

### Post by QLee on 2009-11-02
> **P4man said:**
> Ok I take back what I wrote earlier. gparted will not let you delete a swap partition in use, but fdisk will. I just did it (yeah im nuts)

If you recreate it with the exact geometry and don't format it all your data will still be there.

---

### Post by P4man on 2009-11-02
> **QLee said:**
> If you recreate it with the exact geometry and don't format it all your data will still be there.

I cant. Neither does it look like I have to. Check my edits above. Looks like the swap stays in use until I reboot. The partition is marked busy and I cant do anything with it now.

---

### Post by QLee on 2009-11-02
I was just telling you that if you had deleted something you wanted to keep, didn't see you were talking about swap until it was already sent. It all good.

---

### Post by P4man on 2009-11-02
Oh ok. I didnt lose any data or something. I was just betting the integrity of my ubuntu install to feed giblet more bitter dregs :D. (or just because Im curious)

---

### Post by Giblet5 on 2009-11-02
> **P4man said:**
> Oh ok. I didnt lose any data or something. I was just betting the integrity of my ubuntu install to feed giblet more bitter dregs :D. (or just because Im curious)

I've developed a liking for dreggy coffee.

So my "bug" gets handled by gparted and fdisk via warnings generated by the partition write calls to ioctl() and the kernel's buffered copy of the partition table gets flagged read-only until the in-use reference count for a block device is cleared via swapoff or reboot.

That's an elegant solution someone came up with.

I learned something interesting. Thank you for all the investigative work, P4.

Interesting how you kinda OCD'ed out on this one. :lolflag:

---

