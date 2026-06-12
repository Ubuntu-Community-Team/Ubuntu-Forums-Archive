---
title: "8 gig of Ram is it being used?"
date: 2010-04-29
forum: General Help
---

### Post by basilwatson on 2010-04-29
Just read somewhere that it is pointless in having over 4 gig of ram as it will not all be used 

couldn't understand the technical side of it , 
could someone put this into layman's terms and can I enable the other 4 gig and would it make a difference 

kind regards 

Stephen

---

### Post by Joe of loath on 2010-04-29
I think it refers to the 32 bit limitation of 4gb of memory. If you're running a 64 bit OS it doesn't apply, and you shouldn't have to worry.

---

### Post by cascade9 on 2010-04-29
> **Joe of loath said:**
> I think it refers to the 32 bit limitation of 4gb of memory. If you're running a 64 bit OS it doesn't apply, and you shouldn't have to worry.

+1. 

Also, you can use a PAE kernel (physical address extension) on a 32bit OS that lets the OS address more than 4GB (its the address limit that 'stops' 32bit from 'seeing' more than 4GB)

---

### Post by dino99 on 2010-04-29
into synaptic choose and install the kernel, image, header with -pae at the end, all your ram will be used smootly

---

### Post by cascade9 on 2010-04-29
> **dino99 said:**
> into synaptic choose and install the kernel, image, header with -pae at the end, all your ram will be used smootly

The OP has this is his sig- 

Ubuntu karmic koala 9.10
GNOME 2.22.3 (Ubuntu 2008-07-09)
Linux 2.6.24-24-generic x86_64

A bit confusing, but if they are using a 64bit kernel (x86_64) then installing a PAE kernel isnt possible (as far as I know anyway).....or needed.

---

### Post by dino99 on 2010-04-29
> **cascade9 said:**
> The OP has this is his sig- 

Ubuntu karmic koala 9.10
GNOME 2.22.3 (Ubuntu 2008-07-09)
Linux 2.6.24-24-generic x86_64

A bit confusing, but if they are using a 64bit kernel (x86_64) then installing a PAE kernel isnt possible (as far as I know anyway).....or needed.

exact: 64 bits have some issues with some apps, thats why kernels with pae are troubleless

---

### Post by cascade9 on 2010-04-29
> **dino99 said:**
> exact: 64 bits have some issues with some apps, thats why kernels with pae are troubleless

I'm yet to have any troubles with any 64bit programs. Its not 2005 anymore, 64bit works very very well these days. 

I'd take 64bit over 32bit PAE just for the speed increase myself.

---

### Post by 3rdalbum on 2010-04-29
> **basilwatson said:**
> Just read somewhere that it is pointless in having over 4 gig of ram as it will not all be used 

couldn't understand the technical side of it , 
could someone put this into layman's terms and can I enable the other 4 gig and would it make a difference 

kind regards 

Stephen

I can put it into layman's terms.

A 32-bit operating system can only "address" 4 GiB of RAM, because it can only use 4 "digits" (32 bits divided by 8 bits in a byte) to refer to memory addresses.

It's like if the post office only let you have street numbers of three digits or less - you'd only be able to have 999 houses on the street, because if there were more you'd never be able to send mail to them.

A 64-bit operating system uses "longer" memory addresses, that is, it can use up to 8 "digits" in its addresses. So you can address more RAM.

Now, on Windows, conventional wisdom says that the more RAM you have, the faster your computer will go... well, it's only true up to a point. Some people seem to think that memory = processing power, and are outraged that their CPU is working at 100% but the program seemingly isn't using much RAM.

Let's say I was to do a history quiz and be able to have a reference book in front of me. If I didn't have much capacity in my brain, it would take me a long time to do the quiz because I'd have to keep referring to the book. The more brain capacity I have, the more answers I'd know without having to look at the book, and the faster I'd complete the quiz. Ideally, I'd have a brain capacity that exceeds the book, so I'd NEVER need to read it.

However, there is no speed difference between me having the brain capacity to match two books, or the brain capacity to match five books, if there's only one book for me to read. I simply can't use the increased brain capacity if there's nothing to fill it with.

The same goes for RAM. More RAM means less need to get data from disk (disk access is slow). But when you reach a certain amount of RAM, the computer already has all the data it needs in RAM. If the operating system needs to use 2 GiB of data, then it doesn't matter if you've got 8 GiB or 64 GiB of RAM, the speed will be the same because either way all relevant data can be cached to RAM.

Ubuntu and its programs tend to be fairly efficient with RAM compared to the competition, for various reasons. So to answer your question, with 8 GiB of RAM, it's all usable in a 64-bit operating system - but it probably won't all be used, unless you're running some pretty heavy-duty programs that actually work with a lot of data.

I'm quite proud of this analogy now and I'll put it on my website in case anyone else wants to use it :-)

---

### Post by varunendra on 2010-04-29
> **3rdalbum said:**
> I can put it into layman's terms.

A 32-bit operating system can only "address" 4 GiB of RAM, ......................................... ......................................... .................................... ....................... unless you're running some pretty heavy-duty programs that actually work with a lot of data.
You must be a good teacher ! Hope this is complete & perfect.
I don't have a photographic memory, but I got it all like carved out on my brain. I think I can now explain it very easily to anyone.

I mean a right pick at right place !!

---

### Post by basilwatson on 2010-04-29
I do use some heavy cad and cae on this computer. Just wondering if its worth installing the PAE or the 64 bit system 
Will I notice anything or should I not worry about it 

Thanks for the explanations

IF I was going to get the PAE Kernel What do I look for in Synaptic 

Stephen

---

### Post by gkumar on 2010-04-29
If your current system is as your sig reports it, namely x86_64 architecture, then you definitely don't need a PAE kernel. You already have the ability to address and make use of all the ram you install by default, so don't sweat it!

---

### Post by cascade9 on 2010-04-29
> **basilwatson said:**
> I do use some heavy cad and cae on this computer. Just wondering if its worth installing the PAE or the 64 bit system 
Will I notice anything or should I not worry about it 

For number cruching (which is an important part of CAD IIRC) .....go 64bit, everytime. ;) 64bit enjoys a serious advantage for anything like that over 32bit. I admit that I'll a huge fan of 64bit these days, IMO, if your computer suppports 64bit, in most cases, you should use it. 

Also, and not 100% sure on this, but I beleive that while the PAE kernel will allow the OS to 'see' more than 4GB, it limits any single program to addressing 4GB, so its not the best solution.

---

### Post by jwbrase on 2010-04-29
> **3rdalbum said:**
> I can put it into layman's terms.

A 32-bit operating system can only "address" 4 GiB of RAM, because it can only use 4 "digits" (32 bits divided by 8 bits in a byte) to refer to memory addresses.

It's like if the post office only let you have street numbers of three digits or less - you'd only be able to have 999 houses on the street, because if there were more you'd never be able to send mail to them.

A 64-bit operating system uses "longer" memory addresses, that is, it can use up to 8 "digits" in its addresses. So you can address more RAM.

Now, on Windows, conventional wisdom says that the more RAM you have, the faster your computer will go... well, it's only true up to a point. Some people seem to think that memory = processing power, and are outraged that their CPU is working at 100% but the program seemingly isn't using much RAM.

Let's say I was to do a history quiz and be able to have a reference book in front of me. If I didn't have much capacity in my brain, it would take me a long time to do the quiz because I'd have to keep referring to the book. The more brain capacity I have, the more answers I'd know without having to look at the book, and the faster I'd complete the quiz. Ideally, I'd have a brain capacity that exceeds the book, so I'd NEVER need to read it.

However, there is no speed difference between me having the brain capacity to match two books, or the brain capacity to match five books, if there's only one book for me to read. I simply can't use the increased brain capacity if there's nothing to fill it with.

The same goes for RAM. More RAM means less need to get data from disk (disk access is slow). But when you reach a certain amount of RAM, the computer already has all the data it needs in RAM. If the operating system needs to use 2 GiB of data, then it doesn't matter if you've got 8 GiB or 64 GiB of RAM, the speed will be the same because either way all relevant data can be cached to RAM.

Ubuntu and its programs tend to be fairly efficient with RAM compared to the competition, for various reasons. So to answer your question, with 8 GiB of RAM, it's all usable in a 64-bit operating system - but it probably won't all be used, unless you're running some pretty heavy-duty programs that actually work with a lot of data.

I'm quite proud of this analogy now and I'll put it on my website in case anyone else wants to use it :-)

While all this is true, the speed advantage of the x86_64 platform does not lie in the added memory addressing capability but in certain other features than the bigger address space (such as having more registers available).

---

