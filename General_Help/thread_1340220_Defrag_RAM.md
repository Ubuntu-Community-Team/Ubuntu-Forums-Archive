---
title: "Defrag RAM"
date: 2009-11-28
forum: General Help
---

### Post by Quarkrad on 2009-11-28
I understand partition formats (NTFS / ext4) and why Linux is better than windows re defraging.  However, I'm not sure of the relationship between Linux and RAM defrag.  There are a number of windows utilities that claim to improve performance by defraging RAM. If one has a pc that runs like a dog (winXP) with 1GB RAM would a new install of Ubuntu 9.10 see 'virgin' RAM in terms of performance?

---

### Post by NoaHall on 2009-11-28
RAM doesn't get fragmented. So you don't need to defrag it. If your RAM is getting fragmented, the programs you are running are causing SERIOUS damage to your system. It's VERY, VERY bad programming if your RAM is getting fragmented. Linux doesn't have this problem, as far as I know.

---

### Post by oldos2er on 2009-11-28
Isn't your RAM "defragged" when you shut your computer down?

---

### Post by NoaHall on 2009-11-28
I think the OP means in the sense of bits of code being left behind in the RAM when you close the programs, or programs using up more and more RAM as time goes by. Also known as a memory leak.

---

### Post by mrtomservo on 2009-11-28
I thought most of those WinX ram defraggers weren't so much defragmenting the ram, as they were flushing the ram and writing the data to swap to free ram up.  It's possible they might re-arrange data in ram to make it access faster, but that seems like it's unnecessary.  

Ubuntu doesn't need to defrag your ram, if there really is such a thing.

---

### Post by cascade9 on 2009-11-28
RAM defraging is pure BS. Well, not quite, but near enough. 

From what I remember, what 'RAM defragging' does is find unused libraries (.dlls) in RAM, then unloads them to swap. If your running with _very_minimal_ram, or Win9x with its horrid memory leaks, it might not be pointless, but you would be better off using something like cacheman. Or using a better OS. Or getting more RAM. 

Its more like 'RAM recovery' than defragging, but that wouldnt sell so well LOL

---

### Post by Quarkrad on 2009-11-28
Thank you all for your replies - apologies for my lack of knowledge! From what you say it looks like the term defrag RAM with some of these win utilities is an exercise in poetic licensing. It looks like thy are not defrag'ing the RAM as one would defrag a HD.  Thank you once again.

---

### Post by Krupski on 2009-11-28
> **NoaHall said:**
> RAM doesn't get fragmented. So you don't need to defrag it. If your RAM is getting fragmented, the programs you are running are causing SERIOUS damage to your system. It's VERY, VERY bad programming if your RAM is getting fragmented. Linux doesn't have this problem, as far as I know.

Actually, ram can get fragmented. If a program requests a block of memory, then releases it, then requests another larger or smaller block, the new request can be served from available blocks that are not contiguous.

Fragmentation on a hard drive is "bad" because it causes physical heads to have to seek all over the place to read and assemble the fragments into a file.

The physical motion takes time... so the more fragmented the hard drive is, the slower it's overall response is.

Electronic memory (ram), however, has no "seek time". Data is accessed by placing it's binary address on address lines and reading or writing the data from that address.

If the memory is "fragmented", this only means that different addresses are required to access the data.

If, say, data in ram takes up 5 addresses, it makes no difference if the computer has to address "1, 2, 3, 4, 5" or "98, 13, 43, 54, 12".

Both "sequences" take exactly the same amount of time.

The bottom line? "Fragmented" ram is a non-issue and a non-worry.

-- Roger

---

### Post by shaggy999 on 2009-11-28
That's not entirely true that it takes the 'exact' ammount of time to address different RAM addresses. The computer does have to take time to switch data lines, but the measurement is in nanoseconds compared to milliseconds for a hard drive. If data is sequential in RAM then usually it can all be accessed sequentially without changing the data lines (unless the data overflows across multiple blocks, but still it's doing it sequentially instead of all over the place).

I do agree though that RAM defragging is mostly a joke (at least in Linux).

---

### Post by Krupski on 2009-11-29
> **shaggy999 said:**
> That's not entirely true that it takes the 'exact' ammount of time to address different RAM addresses. The computer does have to take time to switch data lines, but the measurement is in nanoseconds compared to milliseconds for a hard drive. If data is sequential in RAM then usually it can all be accessed sequentially without changing the data lines (unless the data overflows across multiple blocks, but still it's doing it sequentially instead of all over the place).

I do agree though that RAM defragging is mostly a joke (at least in Linux).

Well... if we're going to split nanoseconds... "defragmented" ram might have an advantage over "fragmented" ram when considering caching.

Some cache mechanisms read ahead a certain amount on the assumption that the next addresses will be needed.

If the cache mechanism reads ahead but the ram is fragmented, the cache may be pre-filled with data that doesn't belong to the actual addresses that will soon be accessed.

These "cache misses" will of course be slower than "cache hits".

Then there's row and column address strobes along with setup and hold times for dynamic ram.

Sequential addresses may only need row or column strobes because the other is still valid for a block of addresses.

Having to "jump around" all over fragmented ram could cause extra delays in strobing new addresses into the ram array.

All those nanoseconds add up!  :)

---

### Post by cascade9 on 2009-11-29
Nice theory, but AFAIK, 'defragging' RAM doesnt rearrange the data, its just unloads .dlls.

---

### Post by dcstar on 2009-11-29
> **cascade9 said:**
> Nice theory, but AFAIK, 'defragging' RAM doesnt rearrange the data, its just unloads .dlls.

And the best way to avoid a crappy OS with "fragmanted RAM", the necessity to cripple it with various anti virus/malware protection and the cost of applications and regular expensive upgrades is to stop using it.

---

### Post by cascade9 on 2009-11-29
Not disagreeing with 'stop using it' but I'm always flummoxed about 'the cost of applications' stuff I hear about using you-know-whos OS. 

I never had to pay for anything, other than the OS. Open Office, VLC, foobar, EAC, DVD shrink...hmm..I cant think of a single app I had to steal/pay for with microsoft.

---

### Post by Quarkrad on 2009-11-29
If this not too complicated a question(s) - why is then that Linux is more efficient at using RAM compared to win?  (I assume osx is similar to linux re history of OS).  Also, does Linux have limitation on RAM - thinking of 4GB limit with win.  (If this is complex and there is a wiki/readable site somewhere appreciate a pointer).

---

### Post by ibuclaw on 2009-11-29
> **Quarkrad said:**
> If this not too complicated a question(s) - why is then that Linux is more efficient at using RAM compared to win?  (I assume osx is similar to linux re history of OS).  Also, does Linux have limitation on RAM - thinking of 4GB limit with win.  (If this is complex and there is a wiki/readable site somewhere appreciate a pointer).

Linux is not more efficient... It is just smaller.

Smaller = More room for cache.
More room for cache = faster app **loading** speed

When I say faster, this means not so much the first time you load the app, but all subsequent loads thereafter. Also - this doesn't speed up CPU orientated actions, only Hard Disk **reading** operations.

Regards
Iain

---

### Post by cascade9 on 2009-11-29
> **Quarkrad said:**
> If this not too complicated a question(s) - why is then that Linux is more efficient at using RAM compared to win?  (I assume osx is similar to linux re history of OS).  Also, does Linux have limitation on RAM - thinking of 4GB limit with win.  (If this is complex and there is a wiki/readable site somewhere appreciate a pointer).

The 4GB limit is from 32bit, not windows. 32bit Linux is limited to 4GB as well, unless you start playing with PAE. BTW, PAE also works with some versions of windows. 

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

