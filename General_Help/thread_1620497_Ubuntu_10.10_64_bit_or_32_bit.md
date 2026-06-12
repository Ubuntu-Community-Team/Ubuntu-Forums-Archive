---
title: "Ubuntu 10.10 64 bit or 32 bit"
date: 2010-11-13
forum: General Help
---

### Post by jacob.david on 2010-11-13
I have recently upgraded my PC with a core i7 950. I thought I'll install 64 bit Ubuntu 10.10. But in the download page I see 32 bit as recommended. Is there any issue with 64 bit? Has anyone installed it?
Regards,
- Jacob

---

### Post by sohlinux on 2010-11-13
There can be issues with 64bit, for example driver availability is not as good as 32 bit, maybe your printer is not compatible or maybe a tv card etc, it really depends on your hardware, and it really depends what you are going to use your computer for, for example intensive tasks like encoding video 64 bit will make it faster. a lot of software will not run faster under 32 bit. personally I had a lot of issues with 64 bit so ended up going back to 32 bit. before you install you could checkout to see if your hardware is compatible.

---

### Post by efflandt on 2010-11-13
64-bit Linux has been around for more than 5 years, and with new computers having lots of RAM to accommodate Win7, if an application does not provide a 64-bit version or whatever, they are behind the times. Although, when I first used 64-bit SuSE in 2004 or 2005 they included kernel support and a compatibility mode to run 32-bit binaries.

At this time the only thing that uses 32-bit on a 64-bit system is flashplugin-installer which includes nswrapper to do that.  Although, real 64-bit flash is available from Adobe that should run on anything except my early Athlon64 3200+ on my old PC from 2004 that lacks the lahf_lm istruction.  Someone did come up with a lahf fix plugin that allows real 64-bit flash with Firefox, although, Hulu Desktop did not recognize that extra plugin automatically.

My new PC is an i5 650 3.2 GHz with 8 GB RAM, so there is no question whether to run 64-bit to easily support that much RAM.  And 64-bit runs fine on my personal and work dual core laptops from 2006 (recently bumped from 1 GB to 2.5 GB).  I also run it on that old Athlon64, which works with flashplugin-installer.

The only application that I ran across that does not have a 64-bit version is logmein, but someone mentioned teamview which is similar and does have a 64-bit Linux version.  So I don't require anything that "requires" 32-bit.

At least they toned down the ominous "not recommended" for 64-bit after complaints.

---

### Post by brydonhunter on 2010-11-13
Drivers the only issue that I ran into. My printer only has 32 bit drivers that I forced install and everything works perfectly including scanning and faxing.

I had a problem with the Beta version and the video drivers but all is working perfectly now. Even flash works great.

As mentioned previously, check out your hardware and see if there are drivers available for them.

---

### Post by gordintoronto on 2010-11-13
I've been running 64-bit for more than a year, and I can not identify any issues caused by it. If you have more than 3 GB of memory, 64-bit is superior.

---

### Post by Monotoko on 2010-11-13
I use 64bit and it is fine except for Flash player. However, you can easily find some workarounds for it by just searching for it online.

---

### Post by jacob.david on 2010-11-15
Thanks you all for the replies. I have installed 64 bit and everything looks gr8 and lightning fast, except for sound. I'm yet to work on fixing the sound issue. 
But I have some problem with dual booting into Windows 7 but certainly that can't be a ubuntu/32/64 bit issue. I'll first get that fixed and then look into the sound problem.

---

### Post by gregelder on 2010-12-30
> **efflandt said:**
> 64-bit Linux has been around for more than 5 years, and with new computers having lots of RAM to accommodate Win7, if an application does not provide a 64-bit version or whatever, they are behind the times. Although, when I first used 64-bit SuSE in 2004 or 2005 they included kernel support and a compatibility mode to run 32-bit binaries.

At this time the only thing that uses 32-bit on a 64-bit system is flashplugin-installer which includes nswrapper to do that.  Although, real 64-bit flash is available from Adobe that should run on anything except my early Athlon64 3200+ on my old PC from 2004 that lacks the lahf_lm istruction.  Someone did come up with a lahf fix plugin that allows real 64-bit flash with Firefox, although, Hulu Desktop did not recognize that extra plugin automatically.

My new PC is an i5 650 3.2 GHz with 8 GB RAM, so there is no question whether to run 64-bit to easily support that much RAM.  And 64-bit runs fine on my personal and work dual core laptops from 2006 (recently bumped from 1 GB to 2.5 GB).  I also run it on that old Athlon64, which works with flashplugin-installer.

The only application that I ran across that does not have a 64-bit version is logmein, but someone mentioned teamview which is similar and does have a 64-bit Linux version.  So I don't require anything that "requires" 32-bit.

At least they toned down the ominous "not recommended" for 64-bit after complaints.
hey efflandt

Did you get Ubuntu to run on your i5-650? I just ordered one, and just figured 10.10 would work. I've read some threads where the integrated graphics seemed to cause a problem. (see thread # 10267446).

tia

---

### Post by IWantFroyo on 2010-12-30
I run 64 bit on my laptop. Choosing is a dedication of time. 64 bit makes for a more powerful system, but you have to be willing to fix difficulties. 32 bit is easier, but your system can't do some things as well as a 64 bit. I did have an ACPI problem, but I'm not sure whether that had anything to do with the bits. If you're gonna use Ubuntu a lot though, I'd recommend the 64 bit.

---

