---
title: "HELP!! Filesystem check, bad sectors. Yikes!"
date: 2010-03-05
forum: General Help
---

### Post by 2uRcJQ34G1 on 2010-03-05
[FONT="Verdana"][SIZE="3"]Hiya,

I have a partitioned hard disk [LIST]
[*]sda3 = 17 GB home
[*]sda4 = 21 GB usr
[*]sda1 = 49 MB Dell Utility
[*]sda2 = 82 GB Win XP
[/LIST] Now two days ago, out of the blue I get a message saying that **my hard disk has many errors.** Hence, I ran the disk utility and found the fault -**'Reallocated Sector Count warning and 76 sectors bad'**. I did some research and found out that I need a second opinion for this was an issue in beta. Hence, I check it with 'gsmartcontrol' that confirms the previous error. Upon doing some further research I found out that I can ignore the bad sectors by doing > sudo fsck -c /dev/... by running a live disk(I am using USB). However, before I did that I tried these-> sudo fsck /dev/sda1/3/4 {3 doesn't work- NTFS}
&&
sudo e2fsck -n -f /dev/sda1/3/4 {once again, 3 doesn't work- NTFS}

Now that you know the background, my question is: **Why is no error showing up with fsck, but the Palimpsest is still showing an error sign in the taskbar?? And if the fault is in the Windows partition, can I just use checkdisk from winxp??**. P.S. Does Dell Utility do anything similar??

Thank You in advance.
Cheers.[/SIZE][/FONT]

---

### Post by 2uRcJQ34G1 on 2010-03-05
**Correction: I meant sda2 cannot be checked because it is a ntfs partition.**

---

### Post by 2hot6ft2 on 2010-03-05
> **gore_grinder said:**
> **Correction: I meant sda2 cannot be checked because it is a ntfs partition.**
You can check ntfs with windows check disk utility.

Don't feel too bad I have one hard drive with over 655,000 bad sectors and another with about 27. Both are still in use but for non-critical stuff that I can afford to lose.
It's an indication that the drive may be starting to fail. So if it has your operating systems on it then it may be time to start looking for a replacement drive.
Bad sectors can't be fixed. Some will continue for years and not start getting more bad sectors while others will start getting more and more until it fails.

There doesn't seem to be any hard and fast rules to it.

Personally if my OS's were on it I would shop for a new drive and clone my Operating Systems over to it and if it started getting worse I would swap drives.

I have no idea about the Dell utility but some hard drive Mfg.'s like Maxtor have disk check utilities they will have you run before issuing a replacement drive under warranty.

---

### Post by 2uRcJQ34G1 on 2010-03-05
So if I check my windows partition will that ensure that I will not have to see the message? Moreover, I have expensive propriety software on my hard drive that checks the hard disk serial code to run. i.e I am not sure that it will be able to run if I clone and copy.

---

### Post by 2uRcJQ34G1 on 2010-03-05
Does formatting my hard drive work??

---

### Post by 2uRcJQ34G1 on 2010-03-05
My hard drive is 160 GB can I clone this to an external 500 GB?? By partitioning it??

---

### Post by 2hot6ft2 on 2010-03-05
Formatting the drive wont change the sectors.

Might want to look at [xxcopy]("http://www.xxcopy.com") I have used it before with windows and it can copy the drives serial number to the new drive as well as clone it. It worked great. The fee version is what I used.
> **gore_grinder said:**
> My hard drive is 160 GB can I clone this to an external 500 GB?? By partitioning it??
yes

---

### Post by 2uRcJQ34G1 on 2010-03-05
Cheers. I will check my windows disk now and report back to this thread.

---

### Post by 2uRcJQ34G1 on 2010-03-06
Ok so I just completed the windows xp checkdisk(the one with the blue screen at the beginning). And as usual the feedback scrolled off the screen too fast to read. However, after it restarted there was a message that said the filesystem is clean.

I restarted the system and run Ubuntu, but the error message still poped-up and now I think the only viable option to me is to replace my hard drive.

Please feel free to provide me with some other options of how to "fix" this, or "ignore the bad sectors".

Cheers to everyone who replied.

---

### Post by 2uRcJQ34G1 on 2010-03-06
Does formatting the hard drive take care of the Bad Sectors??

---

### Post by 2uRcJQ34G1 on 2010-06-03
The drive eventually crashed and had to be replaced....

---

### Post by erjoalgo on 2010-07-09
damn... life is indeed cruel...
i have a hard drive in this situation myself, haha, I've had it for less than a year, I am replacing it soon, I wonder what I can do to maximize the life of my new hard drive.

I think I dropped my laptop too many times, although there is allegedly a "fall sensor".
Also, I hear there is a bug in ubuntu where some power settings affect the hard drive's performance, making it work harder and die sooner. 

Anyone want to elaborate on this discussion?

---

