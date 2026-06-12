---
title: "How to Resize &quot;/&quot; Partition?"
date: 2012-04-23
forum: General Help
---

### Post by DeathByLinux on 2012-04-23
Hello,
      I have allocated WAY too much space to my / partition and want to know how to shrink it.
      I downloaded GParted and when I select the partition, the Resize/Move option is not something I can do. Can someone tell me what I need to in order to resize this partition, short of having to reinstalled the system over again?

-Nav

---

### Post by Paqman on 2012-04-23
You can't modify any partition while it's in use. You'll have to boot up into your LiveCD or USB and run Gparted from there. Right click on any swap partitions on the disk and "swapoff" to unlock them. Gparted is pre-installed on your LiveCD for exactly this sort of thing.

---

### Post by DeathByLinux on 2012-04-23
> **Paqman said:**
> You can't modify any partition while it's in use. You'll have to boot up into your LiveCD or USB and run Gparted from there. Right click on any swap partitions on the disk and "swapoff" to unlock them. Gparted is pre-installed on your LiveCD for exactly this sort of thing.

Haha, I figured that out just as you replied that.

Why do I need to unlock swap partitions? I want to resize my system partition. The "/" partition, that is. Do I need to take swap off for some safety reason?

Thanks for your patience, by the way.

-DeathByLinux

---

### Post by Paqman on 2012-04-23
The reason to swapoff is if the swap is located inside an extended partition. If that's the case it would also lock all the other partitions inside that extended partition, which may include the one you want to modify.

The LiveCD tries to be clever and mounts any swap partitions it finds to improve performance, but if you're modifying partitions it can get in the way.

---

### Post by DeathByLinux on 2012-04-23
Okay, let me explain what I have and what I plan to do with it and you can let me know what you think.

I have three partitions on my computer: home, swap and /. I would like to resize the "/" partition so it is smaller and put that space into the home folder AND I would like to expand the swap to see if it makes a difference on my system performance. 
You are saying that I should FIRST swapoff, THEN resize the / partition, THEN resize the home folder to expand it AND THEN resize the swap and (I am guessing here) to "swapon?" Walk me through here, friend.

-DeathByLinux

---

### Post by audiomick on 2012-04-23
I believe that leaving the swap mounted will speed up the partitioning process, so you might leave the swap mounted until you have the other two sorted.

You should leave about 15 GB for the / partition if you have plenty of disk space. I wouldn't go under about 8 if space is an issue.

If you want the suspend function to work, you need to have a bit more swap than you have RAM. If you never need to suspend, then a GB or so is probably enough, assuming you have a modern amount of RAM. You can get a feel for this by having a look at the system monitor when you have the computer running at that which is a heavy load for you. I never get into my swap at all. The exception would be if you do really intense video editing or something. As I said, have a look at the system monitor.

Other than that, the process you describe is correct.

---

### Post by DeathByLinux on 2012-04-23
> **DeathByLinux said:**
> Okay, let me explain what I have and what I plan to do with it and you can let me know what you think.

I have three partitions on my computer: home, swap and /. I would like to resize the "/" partition so it is smaller and put that space into the home folder AND I would like to expand the swap to see if it makes a difference on my system performance. 
You are saying that I should FIRST swapoff, THEN resize the / partition, THEN resize the home folder to expand it AND THEN resize the swap and (I am guessing here) to "swapon?" Walk me through here, friend.

-DeathByLinux

Okay, let me read to you what the numbers are:
/: 28.2 gigs
/home: 154.3 gigs
swap: 972.6 megs (lol, I know...)

Here is what I would like them to be:
/: 10 gigs
/home: around 160gigs
swap: around 2 gigs

So, I am going to do a couple more comments and then do this and let ya'll know how it worked out.
Step 1: Shrink / to 10 gigs
Step 2: Expand /home to 160ish gigs
Step 3: Expand swap to 2 gigs
ALL IN ONE GO
Step 4: Press Ok and let the computer do its thing while I sit there with fingers crossed. 

When I was doing the test run, the computer warned me that there might be a booting failure when I shrink the / partition. 

Should I go and do this, guys? Am I missing something?

-DeathByLinux

---

### Post by audiomick on 2012-04-23
Sounds good to me. I would probably do the re-sizes one at time, but if Gparted is willing to do it all at once, go for it.

The sizes look good to me.

---

### Post by DeathByLinux on 2012-04-26
Okay guys, it worked. There was a little annoying thing that I did so that on the far left, there is a like 900 megs of unallocated space. Now, I can live with that until I do a fresh install, so I am going to ignore it till then. Anyway, thanks for all of your patience and help. See you guys around!

-DeathByLinux

---

