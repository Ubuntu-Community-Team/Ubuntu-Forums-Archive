---
title: "Very odd problem in ubuntu 11.04, natty,my 3gb ram can not be detected"
date: 2012-08-12
forum: General Help
---

### Post by hshi on 2012-08-12
hi folks, so far, ubuntu can only report 766MiB out of  my 3gb ram after issuing the free -m command? why is this happening? 
any solution? 
 I've already installed PAE and rebooted many times, no luck still..
 
  help please!

Hui

---

### Post by sanderj on 2012-08-12
If you run these command, you'll see all details about your memory:

```
wget http://www.appelboor.com/dump/check-my-memory.py
python check-my-memory.py 
sudo python check-my-memory.py

```

You can post the output here.

---

### Post by hshi on 2012-08-12
OK, you're root
ANALYSIS:
Total of physical memory modules found 1024 MB in 1 memory module(s)
BIOS offers 761 MB as usable
Memory seen by OS 743 MB
BIOS version 09/02/2010
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is 32-bit with PAE

SUMMARY:
Memory difference between DIMM hardware and BIOS offering 263 MB
Memory difference between BIOS offering and memory seen by OS 18 MB
Memory difference between DIMM hardware and memory seen by OS 281 MB

ADVICE:
Your physical memory is less than 3200 MB, and your system does not need special memory treatment

Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 1GiB
          description: DIMM DDR3 [empty]
          description: DIMM DDR3 Synchronous 1066 MHz (0.9 ns)
          size: 1GiB

Finished

---

### Post by sanderj on 2012-08-12
So: "Total of physical memory modules found 1024 MB in 1 memory module(s)". Only 1 SIMM, and only 1GB RAM.

You say you have 3GB installed. How do you know? How many SIMM-modules: 1, or 2, or 3, or ... ?

If you boot and go into the BIOS, what does your BIOS say about your memory?

---

### Post by hshi on 2012-08-12
hi sanderj, I opened my laptop last night and there are two slots,
one is 1gb and the other is 2gb

---

### Post by sanderj on 2012-08-12
> **hshi said:**
> hi sanderj, I opened my laptop last night and there are two slots,
one is 1gb and the other is 2gb

Well, apparently your system does not recognize that. You could play with plugging in/out modules to see what happens.

---

### Post by hshi on 2012-08-12
thanks sanderj. I just opend the laptop again and plug out ram and plug in . After that, it all works and now I can see my 3G (well actually only 2.7 G) in ubuntu now. Very happy, thanks for the help

Hui

---

### Post by sienile on 2012-08-12
It sounds like you have your memory set up in dual channel mode. This limits you to the size of the smallest memory chip. Many people think dual channel just speeds things up without changing the size of the available memory, this is not the case. It halves the memory, but doubles the speed. That's why most people running dual channel use matched chips, and usually 2GB chips.

My advice, since you have unmatched chips, is to go into your BIOS and turn off dual channel. You'll get the full size of your memory, but drop a bit in speed. Chances are you don't even take full advantage of the speed you have now anyway.

--------------------------------------

Well, it seems I was wrong. Didn't refresh after having this and other tabs open for over an hour. :P

You must've dropped your laptop and jiggled the RAM chip loose a bit. Anyway, I'll leave my post there in case someone having a similar issue actually has dual channel turned on.

---

