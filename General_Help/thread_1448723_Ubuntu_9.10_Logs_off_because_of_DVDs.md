---
title: "Ubuntu 9.10 Logs off because of DVDs?"
date: 2010-04-07
forum: General Help
---

### Post by Doctadrez on 2010-04-07
First and foremost, this is the second post I've ever posted on these forums, the first being a solution to someone else's problem. For the past two years of using Ubuntu, these forums + Google have helped me with everything else I've needed, except this. I'm thoroughly impressed at the help the community gives. Now, on to my problem.

My Ubuntu session logs off "randomly" but only when playing/ripping DVDs on my laptop. It's happened about a dozen times since my upgrade to 9.10 from 9.04, though I haven't used my DVD player exhaustively. On 3 occurrences of it logging me off, I had been playing a DVD (not the same one) and opened a new tab on Firefox, causing immediate log off.

Other times, it's been a simple bump to the laptop while trying to rip a DVD using Handbrake, which makes me think it's an IO issue that forces a log off for some reason? I'm not sure.

System Specs:
Core 2 Duo T7200
ATI X1600
2GB Ram
Ubuntu 9.10 32bit 
Kernel:2.6.31-20

I've attached my /var/logs/messages as of my last log off. I've been using Ubuntu for quite some time, but would not exactly call myself an expert on it. And as such, can't really make heads or tails of this (if at all relevant).

---

### Post by uRock on 2010-04-07
Hello Doctadrez and welcome to the forums,

 I looked through your text file and I see that it says there is no swap partition, if this is true it may be your problem.

Can you run this command in a terminal and copy and paste the results? ```
sudo fdisk -l
``` 
[-l is a lower case L not a 1(one)]

Regards,
Ronnie

---

### Post by Doctadrez on 2010-04-07
ndrs@Ares:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97979797

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4178    33559753+   7  HPFS/NTFS
/dev/sda2            4179        5222     8385930   83  Linux
/dev/sda3            5223       12161    55737517+  83  Linux




Correct, I don't have a swap partition. I was under the impression that swap partitions weren't explicitly needed. I forgot to make such a partition from the start, and have always feared resizing partitions.

---

### Post by uRock on 2010-04-07
> **Doctadrez said:**
> ndrs@Ares:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97979797

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4178    33559753+   7  HPFS/NTFS
/dev/sda2            4179        5222     8385930   83  Linux
/dev/sda3            5223       12161    55737517+  83  Linux

Correct, I don't have a swap partition. I was under the impression that swap partitions weren't explicitly needed. I forgot to make such a partition from the start, and have always feared resizing partitions.

It may be possible that your problem is being caused by filling your RAM. The good news is that you don't have to create a separate partition. You may create a swap file within one of the partitions that your ubuntu can use. 

There is a great tutorial on this [ubuntu page]("https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?") that will walk you through the steps. [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

Let us know if you need any help with this.

Cheers,
Ronnie

---

### Post by Doctadrez on 2010-04-07
well, I added 2GB of swap space, but it seemed to bog down my system pretty hard. I adjusted the swappiness from  60 to 10 to 5 and it still seems to be pretty sluggish.

On a positive note, however, I have yet to be logged off during dvd playback, as was usually expected.

I suppose it's a trade off.

---

### Post by uRock on 2010-04-07
> **Doctadrez said:**
> well, I added 2GB of swap space, but it seemed to bog down my system pretty hard. I adjusted the swappiness from  60 to 10 to 5 and it still seems to be pretty sluggish.

On a positive note, however, I have yet to be logged off during dvd playback, as was usually expected.

I suppose it's a trade off.

I have never used the swap file. I just recently learned that it existed. If it keeps making your system slow, then you may want to make the partition instead of the file.

Cheers,
Ronnie

---

