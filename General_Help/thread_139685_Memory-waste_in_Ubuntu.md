---
title: "Memory-waste in Ubuntu?"
date: 2006-03-04
forum: General Help
---

### Post by riwa on 2006-03-04
I have 512 mem on this laptop, though 'top' tells me I only have 380. However, Ubuntu is using 288 mb of memory, when I only have 3 terminals, running lynx, vim(for this file) and (of course) top. Considering it I have lynx running a 600 page txt file, which of course would eat some memory but 300? And even worse when i start X. Let's try it. First I reboot since she's been up a couple of hours.

Before X is launched:

Mem:	385812k total,	178516k used,	207296k free,	8700k buffered

Staring at the buffered memory for one minute it's now increased to 8852.
Used mem has also increased to 178888. 300 k on two lines.
(That's probably the two most expensive ascii-lines I've ever seen.)

After X is launched: (mem already at: used: 179260 and buff: 9388)

Mem:	385812k total,	264612k used,	121200k free,	13604k buffered
That's about 80 meg. Starting timer. 
13:12:30 (with the above memory)

13:17:30 (five minutes later)
Mem:	385812k total,	265356k used,	120456k free,	14144k buffered

That's another 5 meg memory used. For just staring at the 'top' program.
In two hours I'll run out of memory! What's happening behind the scenes?

Before i rebooted I checked my free memory after starting X. 
It went down to 35 meg. It'd been up for 3-3.5 hours running a 600+ page txt file in lynx.

Regards
Richard

(Mem is now (13:27:00) used: 266852 free: 118960  buff: 15220
 A lot less in ten minutes than in five... Hmmm...)

---

### Post by pestilence4hr on 2006-03-04
First, you probably have a video card that uses your memory, which explains the  first cut off the top.

Second, top is reporting memory in use by applications and also memory that is cached from things like disk reads.  So it's really not a "in use" gauge, from the standpoint of "what would have to be swapped if I tried to allocate X amount of memory", since the cached stuff would just be written over.

To get a better idea of how much memory is in use, use the command "free".  Look at the -/+ buffers/cache: line especially.  And read this:  [http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by riwa on 2006-03-04
Ok. I'll read through it. However the free did NOT make me happier...

```

~$ free
                       total       used       free     shared    buffers     cached
Mem:        385812     378656       7156          0      17576     227516
-/+ buffers/cache:     133564     252248
Swap:      2048248      12476    2035772
~$

```

7 megs free!!! And what about my videocard? Is it not working properly?

---

### Post by patrickfromspain on 2006-03-04
patrick@ubuntu:~$ free
                 total        used         free     shared     buffers     cached
Mem:        499476     440612      58864          0      16988     169892
-/+ buffers/cache:     253732     245744
Swap:      1004020          0    1004020
patrick@ubuntu:~$

I'm now using firefox and 1 amsn window. Also 512megs ram.

---

### Post by pestilence4hr on 2006-03-04
[QUOTE=riwa]Ok. I'll read through it. However the free did NOT make me happier...

```

~$ free
                       total       used       free     shared    buffers     cached
Mem:        385812     378656       7156          0      17576     227516
-/+ buffers/cache:     133564     252248
Swap:      2048248      12476    2035772
~$

```

7 megs free!!! And what about my videocard? Is it not working properly?[/QUOTE]

You are reading this output wrong, please go back and read my previous reply.  See how it says 252248 free?

---

### Post by towsonu2003 on 2006-03-04
try sudo apt-get install xubuntu-desktop (network connection needed). xfce4 may make you happier with memory usage. I agree that ubuntu uses too much memory, but I also keep reading that linux likes to use free memory as much as it can.

---

### Post by aysiu on 2006-03-04
Does the supposed memory waste actually visible affect performance, or are you just worried about the numbers?

---

### Post by riwa on 2006-03-07
Well I find it kinda slow and when I'm out of memory I'm definetily slower with using cached than free regarding what that gentoo-guide says. But yes it mainly the numbers that worries me....

The latest two days however my Vim seems to hang when it wants to. And I can't even kill it. That terminal instance is dead. I mean i CAN kill it but it's still there... Don't think it has anything to do with the memory though...

---

### Post by kaamos on 2006-03-07
Don't worry about the numbers, memory usage in *nix systems includes the idea that free ram is seen as wasted ram. So the system tries to make use of all the available memory. Google for linux memory management etc. if you wan't more info..

btw, you can use "free -m" for a more readable output.

---

