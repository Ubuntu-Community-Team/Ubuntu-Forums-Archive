---
title: "Partition for system files - clean install"
date: 2012-04-21
forum: General Help
---

### Post by razing32 on 2012-04-21
Hi,

I am installing Ubuntu 11.10 on my Laptop.

I have read multiple guides but I still can't get a clue on how much space and partitions I should have.
I've seen options with just / /home and /swap and others with partitions for every system folder /var /tmp /usr and so on.

I have a 500 GB HDD. How would you break it down ? 
How many partitions ? How much space for each ?

I am planning to use my laptop for music , games, and the likes so I will install plenty of programs. I will also download very many as well.

PS : I am planning the install in a few hours. Quick replies would be most appreciated.

---

### Post by PhantomTurtle on 2012-04-21
You might not even want /var, /tmp and /usr since they can all be put into /. I believe there are advantages to this but you probably won't need them. For swap, it's usually about the same size or twice the size of your RAM. You COULD get away with it, but it's better to make one anyway. / can be the rest. No need for a separate /home partition if your only going to use one distribution(Ubuntu) on that computer. Additionally I would just leave to the guided partitioning, which will decide for you(hurray for laziness).

---

### Post by razing32 on 2012-04-21
> **PhantomTurtle said:**
> You might not even want /var, /tmp and /usr since they can all be put into /. I believe there are advantages to this but you probably won't need them. For swap, it's usually about the same size or twice the size of your RAM. You COULD get away with it, but it's better to make one anyway. / can be the rest. No need for a separate /home partition if your only going to use one distribution(Ubuntu) on that computer.

So , just a / directory plus a swap that's double my RAM should be enough ?

---

### Post by PhantomTurtle on 2012-04-21
> **razing32 said:**
> So , just a / directory plus a swap that's double my RAM should be enough ?

You got it.

---

### Post by PhantomTurtle on 2012-04-21
Sorry I made a little edit before and you must have missed it. You can just use guided partitioning which will make your life a whole lot easier.

---

### Post by oldfred on 2012-04-21
I suggest separate /home or data partitions and keep system partition smaller for efficiency.  But everyone has different needs and opinions. I find my own optimal configuration is not so good a couple of years later.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

If you do not have Windows do not create a NTFS partition as you need Windows to run chkdsk occasionally or do other maintenance that Linux cannot do.

I like separate data partitions, but if you do not know size that you may use for data then one larger partition either /home or /mnt/data gives flexibility as resizing when you have lots of data is more difficult.

---

### Post by razing32 on 2012-04-21
> **oldfred said:**
> I suggest separate /home or data partitions and keep system partition smaller for efficiency.  But everyone has different needs and opinions. I find my own optimal configuration is not so good a couple of years later.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

If you do not have Windows do not create a NTFS partition as you need Windows to run chkdsk occasionally or do other maintenance that Linux cannot do.

I like separate data partitions, but if you do not know size that you may use for data then one larger partition either /home or /mnt/data gives flexibility as resizing when you have lots of data is more difficult.

So , let me be clear i got this

About 10-25 GB for / mountpoint. I was thinking of giving it 50 GB just in case.
/home or /data for the majority of the remaining space
And the swap should be double RAM in Gibibytes
Well I have 8192 RAM (according to SiW) so I will make a SWAP of 16384 , right ?

---

### Post by oldfred on 2012-04-21
Swap only needs to be 8GiB if you hibernate. The old double RAM was when RAM was only 256KB or 512KB.

Some other choices.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?")
I prefer sleep and shutdown to hibernate. Boots fast compared to Windows and full boot in Ubuntu is faster than recovery from hibernate in Windows for me.
'Dynamic Swap Space Manager' from the Ubuntu Software Center

---

### Post by razing32 on 2012-04-21
> **oldfred said:**
> Swap only needs to be 8GiB if you hibernate. The old double RAM was when RAM was only 256KB or 512KB.

Some other choices.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?")
I prefer sleep and shutdown to hibernate. Boots fast compared to Windows and full boot in Ubuntu is faster than recovery from hibernate in Windows for me.
'Dynamic Swap Space Manager' from the Ubuntu Software Center

Hmm,

What about installed programs ?
I plan on installing plenty of games.
And I also plan to run one (or more ) virtual machines with Windows games.

Can I choose the install path ? Or are they stored somewhere other than /home ? Because then I would run into space issues fairly soon.

NOTE : I am a beginner in Linux as you;ve probably guessed , so I used to just use a single moutnpoint in virtual machines in the past.

---

### Post by oldfred on 2012-04-21
I do not know about games, some maybe large. I have lots of apps installed and my root is only 7GB.

---

### Post by razing32 on 2012-04-21
Well , I went with 50 GB for / , 8 GB for swap and rest is /home.

Will let you know how it goes.

I plan on buying a gaming PC anyway but I recently managed to brick my laptop , so I am taking the opportunity to play with Linux.

Thx.

---

### Post by dcstar on 2012-04-21
> **razing32 said:**
> Well , I went with 50 GB for / , 8 GB for swap and rest is /home.

Will let you know how it goes.

I plan on buying a gaming PC anyway but I recently managed to brick my laptop , so I am taking the opportunity to play with Linux.

Thx.

20GB is usually more than enough for a root partition. Do yourself a favour and create another spare partition **now** for the next Ubuntu release you may install, then you won't need to resize anything to create space later on.

---

