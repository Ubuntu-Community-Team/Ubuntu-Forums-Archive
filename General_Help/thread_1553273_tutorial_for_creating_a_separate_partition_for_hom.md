---
title: "tutorial for creating a separate partition for /home/?"
date: 2010-08-14
forum: General Help
---

### Post by princeofnam on 2010-08-14
I'm about to reinstall Ubuntu and one thing I'd like to do is create a separate partition for /home.  does anyone have any good tutorials?

also what are the exact benefits of that?
upgarding ubuntu doesn't necessarily delete your files right?
is it just as a security measure in case the kernel becomes corrupted?

---

### Post by wojox on 2010-08-14
See here [Seperate Partition for home]("http://ubuntuforums.org/showpost.php?p=9718270&postcount=2")

---

### Post by princeofnam on 2010-08-14
i'm still at a lost for how much space I should allocate to swap and root.  i've seen varying amounts and I'm not sure how much is optimal

---

### Post by kyphi on 2010-08-14
The amount of space you make available depends on how much space you have available and on how much RAM you have.

Swap used to be allocated as twice the amount of RAM.  Today's computers are generally well equipped with RAM as well as enormous hard drive capacity so that is no longer necessary.

I run my Ubuntu on an 80 GB partition divided so:  Operating system = 10 GB, Swap = 1.8 GB, Home is what is left = 68 GB

---

### Post by princeofnam on 2010-08-14
did you arbitrarily choose 10gb or was that calculated based on your HD space. is it then 1/8?


you specified 1.8 GB of Swap space, assumably because you have 1 GB of RAM? Why didn't you make it 2 GB out of curiosity?

in my case I have 3 GB of RAM and a 120 GB Harddrive

---

### Post by fast_ian on 2010-08-14
This could easily turn into one of those "there's as many different ways to do it as there are people" threads..... I've gone round and round over the years - 8, maybe 10 partitions, back to one, with and without swap etc - The short answer is "there is no right and wrong way." My 02c, FWIW:

- Hard drives are *huge*, why not use 2x RAM as a swap partition? Even if you've got 16GB, let it know it's got plenty of room to swap if needed - Give it 32 out of your 500 [More likely a TB or two of course nowadays ;-)] It'll probably never get used (although can't you "sleep" to it?) but WTH?

- A separate partition for "the OS" that's *just* big enough (say 1.5x) is a good idea IMHO - *You* don't put anything in there, it has it's own backup strategy, and allows you to get the machine back should "/" get broken without worrying about your other "stuff". [In summary ;-)]

- Do a lot of dev work? I liked a separate /src on occasion.
- Lot of "big" files? - Put 'em on their own partition.
- etc.

Good luck, cheers,
Ian

---

### Post by kyphi on 2010-08-14
Perhaps it will help if I give you a readout of the figures in my partition editor:

/ allocated space 11.18 GiB, used = 5.56 GiB, unused 5.62 GiB
swap = 1.86 GiB
/home allocated space 61.49 GiB, used 13.32 GiB, unused 48.17 GiB

I have 2 GB RAM.

All my backups are stored in another partition on another hard drive.

There is no magic calculation but I do find that my allocation meets all my needs.

The difference in the figures are the result of whether or not you calculate with metric bytes or computer-speak bytes.  Personally I prefer metric, i.e. 1 KB = 1000 bytes.

With your specifications, I would recommend 1.8 GB swap, 10 GB /, and the rest for /home - depending on your computer use (I do not store movies nor do I collect a lot of music files).

The advantage of having a separate /home partition is not difficult to work out - it is based on the principle of not putting all your eggs in one basket.  If you wish, I will elaborate.

---

### Post by princeofnam on 2010-08-14
the thing is. I never used over 200 mb of swap before, why do most people allocate on the order of GB?

furthermore, isn't it known that root folders should have a certain degree of free space? isn't there an accepted amount at which say 1-3 GB of free space, as opposed to 10 GB, results in slowed performance?

---

### Post by Ginsu543 on 2010-08-15
If you have enough RAM (>2GB), you may not need a swap partition at all. The OS needs a swap partition if it runs out of RAM while trying to perform an operation (i.e., it's using the swap file as RAM). With the huge sizes of RAM available these days, swap partitions have become less and less necessary.

On the other hand, if you want to be able to hibernate, than you need to have a swap partition, since the OS saves its status to the swap partition when it goes into hibernation mode. To be able to do this, you obviously need your swap partition to be as big as your RAM capacity. The 2 x RAM rule is no longer essential because of the large RAM sizes we're talking about.

In my experience, setting aside 10 GB for the / partition is plenty for normal desktop use. I can install pretty much all the program I use and have plenty of room left over.

---

