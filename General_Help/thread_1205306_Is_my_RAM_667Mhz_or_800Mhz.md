---
title: "Is my RAM 667Mhz or 800Mhz???"
date: 2009-07-05
forum: General Help
---

### Post by s3a on 2009-07-05
When I bought my RAM, if I recall correctly it was sold to me as 800Mhz not to mention that the packaging says *2GB PC2-6400 CL5 240 - Pin DIMM* which means 800Mhz right? However, when I do lshw as root (after installing package lswh), it says my RAM is 667 Mhz. Is there an application (if not in Ubuntu, then in Windows Vista, but I would prefer in Ubuntu) that would actually run something to test the actual speed without just relying on what the manufacturer or store says?

Any help would be GREATLY appreciated!
Thanks in advance!

---

### Post by loomsen on 2009-07-05
```
cat /proc/meminfo
```

*edit*

more appropriate:
```
dmidecode
```

You probably want to use | less as its a lot of output

---

### Post by louieb on 2009-07-05
The ram is capable of running at 800mHz. What about your motherboard?  Can it run at 800mHz? The ram you bought is backward compatible with PC5400.

---

### Post by kerry_s on 2009-07-05
+1 you got to check the board, other wise your just using a compatiable ram running at the max the board supports.

---

### Post by s3a on 2009-07-05
[I]GB 800MHz DDR2 Non-ECC CL5 DIMM  	 KVR800D2N5/2G

From:
[http://www.valueram.com/datasheets/default.asp](http://www.valueram.com/datasheets/default.asp)[/I]

I got that from actually taking out RAM module out of the motherboard. dmidecode also says it's 667Mhz.

I guess it is some minor detail with the motherboard. My motherboard is *Gigabyte S-series GA-P31-S3G*. Someone, please tell me what my motherboard has to do with this. I am planning to buy RAM. I'm guessing I'll need 800Mhz RAM to get the best performance with dual channel, etc but I'd still like to know the motherboard details please. I don't think it is a motherboard limitation though since the box says it supports up to DDR2 1066Mhz RAM.

But like I said in my initial post, does someone have a program that actually tests the speed of the RAM (in Linux or Windows preferably in Linux) and doesn't just list what the manufacturer typed?

Thanks!

---

### Post by c0mput3r_n3rD on 2009-07-05
The motherboard could inhibit your memory from running at the full potential because the motherboard is what everything works off of, think of the mother ship with aliens.  It's why you can't put a quad core processor in an old board that only supports up to pentium 4.  Therefore, if the motherboard can only pull information from the memory at 667Mhz or what ever yours is running at, then it doesn't matter if the physical RAM can perform better.  It all revolves around the motherboard.

---

### Post by s3a on 2009-07-05
> **c0mput3r_n3rD said:**
> The motherboard could inhibit your memory from running at the full potential because the motherboard is what everything works off of, think of the mother ship with aliens.  It's why you can't put a quad core processor in an old board that only supports up to pentium 4.  Therefore, if the motherboard can only pull information from the memory at 667Mhz or what ever yours is running at, then it doesn't matter if the physical RAM can perform better.  It all revolves around the motherboard.

Yes but like I said on the box it says it supports up to DDR2 1066Mhz RAM.

---

### Post by c0mput3r_n3rD on 2009-07-05
The RAM could also be bad :-\

---

### Post by 3Miro on 2009-07-05
If on boot you go into the BIOS you will be able to see the speed of the RAM and I would think that more reliable than anything else.

There may be another problem. If you are running two different sticks of RAM from two different manufacturers or even from the same manufacturer and even of they both are 800Mhz, they may not work together.

Try the sticks in separate to see.

The again, did you check if the RAM is compatible with the motherboard. They not always are.

---

### Post by c0mput3r_n3rD on 2009-07-05
I concur with 3miro.  I know my bios actually clocks the RAM, and most should, that would be your best bet, and then if they're the same speed separately, you might just have to deal with the fact that the RAM is not compatible with the motherboard.

---

### Post by s3a on 2009-07-05
It's one stick, I linked to it earlier in this thread. ([http://www.valueram.com/datasheets/default.asp](http://www.valueram.com/datasheets/default.asp))

I have no idea where in my BIOS to check.

**Additional Question:** Let's say it was 667Mhz and I bought a second stick at 800Mhz, would the 800Mhz stick run at 667Mhz _but still have dual-channel enabled_? In which case, I would just buy 800Mhz.

---

### Post by c0mput3r_n3rD on 2009-07-05
It all depends man.  You'd probably be best asking the seller as they would know their product better.

---

### Post by kerry_s on 2009-07-06
> **s3a said:**
> It's one stick, I linked to it earlier in this thread. ([http://www.valueram.com/datasheets/default.asp](http://www.valueram.com/datasheets/default.asp))

I have no idea where in my BIOS to check.

**Additional Question:** Let's say it was 667Mhz and I bought a second stick at 800Mhz, would the 800Mhz stick run at 667Mhz _but still have dual-channel enabled_? In which case, I would just buy 800Mhz.

yes, if you by 800 it will run at 667, which would be the lowest setting that both can use.

you really should look through your bios, the bios could just be set wrong. on my new computer i can set the speed the ram runs at in the bios, so i can set it to the speed of the ram i use.

---

### Post by jocko on 2009-07-06
Check your bios settings. According to the manual for your motherboard ([found here]("http://www.gigabyte.com.tw/Support/Motherboard/Manual_DownloadFile.aspx?FileType=Manual&FileID=18157")), there is a menu called "MB Intelligent Tweaker(M.I.T.)" that has the option "System Memory Multiplier (SPD)".
It can be set to auto, which should detect the correct frequency, but it is also possible to set manually.

I have an old gigabyte motherboard with a similar option in the bios, and to get 400MHz (max for my ram/motherboard) I have to set it manually to "By SPD", because the "auto" option falls back to 333 MHz, which is a multiple of the fsb frequency (166 MHz).

---

