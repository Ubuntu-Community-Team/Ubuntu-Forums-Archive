---
title: "Swap file size limit"
date: 2010-10-20
forum: General Help
---

### Post by superdan111 on 2010-10-20
Ok, a possibly preposterous question. I am aware that you can designate a swap file or swap partition on your hard drive that linux uses as "memory". Suggested sizes for the swap file that I've seen range up to about 1024MB. Is there a limit to the swap file size that you can set?

Basically I am running a perl script that processes a massive (6GB) file (DNA sequence data), etc, and requires around 48 GB of memory to run, maybe a bit less. So, would it be possible to set a swap file to a massive, ridiculous size (~60GB or whatever) and successfully run such a script on a desktop?

Yes, I am aware that it would massively slow down the process. The thing is, if the perl script normally completes in about half an hour, and I can get it working on a desktop, I don't mind if it takes days or weeks to complete. I really don't. That's because it takes days or weeks to get access to a computer with the required grunt to do it.

So, is this a stupid idea? Is it even possible? If so, given a perl script that normally completes in a half hour on a 48G system, if you do this, would it take days? weeks? decades? 

Cheers

---

### Post by dcstar on 2010-10-20
> **superdan111 said:**
> Ok, a possibly preposterous question. I am aware that you can designate a swap file or swap partition on your hard drive that linux uses as "memory". Suggested sizes for the swap file that I've seen range up to about 1024MB. Is there a limit to the swap file size that you can set?

Basically I am running a perl script that processes a massive (6GB) file (DNA sequence data), etc, and requires around 48 GB of memory to run, maybe a bit less. So, would it be possible to set a swap file to a massive, ridiculous size (~60GB or whatever) and successfully run such a script on a desktop?
...........
"Desktop" has nothing whatsoever to do with swap size, swap space is slow virtual memory, RAM is fast virtual memory. The less a process uses the slow memory the faster it will run.

Search out the Ubuntu Swap FAQ.

---

### Post by lavinog on 2010-10-20
You should be using a 64bit desktop or a 32bit with PAE enabled (server kernel has this)
You might still have an issue with PAE since I don't know if it would allow an application to use more than 4g of mem.

Other than that it should work.

Is the script anything that you can share?  Maybe it can be rewritten to not use so much memory, and use the disk instead.

---

### Post by Bob65536 on 2010-10-20
This thread might be of interest [http://www.linuxquestions.org/questions/linux-newbie-8/max-swap-size-use-to-be-2gb-on-ia32-has-this-changed-and-on-x86_64-a-609577/](http://www.linuxquestions.org/questions/linux-newbie-8/max-swap-size-use-to-be-2gb-on-ia32-has-this-changed-and-on-x86_64-a-609577/)

So it looks like it should work as long as you are using a 64bit kernel.

Honestly though, I would modify the script so that it doesn't require the entire file to be in memory at once.

---

### Post by superdan111 on 2010-10-20
Thanks all. 

By "Desktop" I mean desktop computer, i.e. a pretty standard computer you get from the shop, not the actual desktop on your screen.

As for rewriting the script, possibly a good idea. It basically takes DNA sequence data with quality information, and chucks out bad DNA sequences, but it's a bit irrelevant since it is only the first step of the process and further programs (the genome assembly step) require that much memory and, there's really no getting around it at that stage, at least not by me. Bear in mind that it's a program that compares literally forty million DNA sequences to each other.

So, if I do this, how much slower can I expect the process to run? Is hard-disk read-write ten,a hundred, a thousand times slower? If the read-write is X slower, does that translate to the program running X times slower?

---

### Post by lavinog on 2010-10-20
How are the sequences stored in memory?
Are they stored using characters, or are they using a binary equivalent?
Are the arrays compressed?
How big is the datafile if you compress it?

If you are storing the data in CHAR arrays, something like ACGT would consume 4 bytes of data.  If you assume that there can only be 4 states, you can combine 4 characters into one since 4^4=256 and a CHAR has 256 possible values.

As for speed issues with swap, I believe you can use multiple disks for swap.
Having a swap partition on 2 different drives could possibly cut the time in half.

You might also be able to use multiple flash drives since flash drives have quicker seek times than rotational disks, but since most of the information would likely be sequential data, I don't know if this would be much help.

---

### Post by superdan111 on 2010-10-20
Alright thanks all, heaps of info to go on with :popcorn:

---

### Post by superdan111 on 2010-10-20
As for this

How are the sequences stored in memory?
Are they stored using characters, or are they using a binary equivalent?
Are the arrays compressed?
How big is the datafile if you compress it?

I'm not really expert enough to answer, and I'm using scripts and programs designed by others. Probably the issue is that for the script I mentioned that uses lots of memory (that does prefiltering of data), the output is pure sequence (= 5 states, A C G T or N) but the input includes data on the quality of the read (which as I understand is in ASCII), so lots of info in there. The program that does the assembly probably uses lots of memory because it has to compare so many reads with so many other reads, and sometimes you have 100+ reads that partially or completely overlap. Sorry I am a not a bioinformatician, just an amateur who is too cheap to hire one :)

---

