---
title: "Freezing Issues, Hardware Problem"
date: 2010-05-17
forum: General Help
---

### Post by 1awesomeguy on 2010-05-17
Summary: Computer is continuously freezing/locking-up for four years. Help?

My computer freezes about once a day or sometimes more. When it freezes the screen stays the same and I cannot move my mouse or anything else. I also notice that if the activity light (maybe a hard drive activity light) is on or off, it will stay like that after the computer freezes (i.e., if does not change after the computer freezes).

This issue has been happening for four years and have lead to all sorts of problems (usually hard drive sectors becoming bad due to incomplete data transfer). It happens in the latest version of Ubuntu, at least the last three versions of Ubuntu, Windows XP, and Windows 7. The freezing does seem to occur a more often in Ubuntu than it does in Win7.

I would REALLY appreciate it if somebody can help me diagnose this issue and get it solved. I do not mind buying new hardware if something is defective to fix this problem.

Here is what I think:
[LIST]
[*]It is not heating issue with the processor. The processor has a good fan on it and after freezing the temperature is still around 40C.
[*]It is not a power supply or power issue as the computer remains powered on.
[*]I do not think it is a RAM issue as I have memtest-ed the RAM extensively finding no problems.
[*]It is not a software issue as there are problems in multiple OS.
[*]The issue happens when I am actively doing something on the computer. The computer only freezes when I am actively on it. It has never locked-up when I left it on overnight.
[/LIST]

The freezing/lock-up has occurred when I am doing the following: browsing the web, opening a folder, rendering video, composing an email in Gmail, and editing an OpenOffice.org document. Pretty much everything I normally do on the computer...

It could be a problem with my video card. Is there a way to stress test it or my other hardware to find out for sure?

Thoughts?

Thanks in advanced!

---

### Post by 1awesomeguy on 2010-06-03
Is this enough time for a bump...?

---

### Post by tankjer on 2010-06-03
> **1awesomeguy said:**
> Is this enough time for a bump...?
Yes, after >24 hours of no response you can bump (though it's only a tip, not a rule).
Is the processor or graphic card overclocked? If you have Windows installed and you have an ATI/AMD graphics card you could try to install ATITool and run a test there. I don't remember how that test is called, I haven't used Windows in a long time... I think that those freezes could be more a cause of CPU though. Run Prime95 in Windows with Torture Mode. You should leave it for about 24 hours. Most of the errors because of CPU will be found in ~20 hours.
EDIT1: found a post about testing for stability with Prime95 [there]("http://www.devhardware.com/forums/showpost.php?p=569870&postcount=11")

---

### Post by 1awesomeguy on 2010-06-03
> **tankjer said:**
> Yes, after >24 hours of no response you can bump (though it's only a tip, not a rule).
Is the processor or graphic card overclocked? If you have Windows installed and you have an ATI/AMD graphics card you could try to install ATITool and run a test there. I don't remember how that test is called, I haven't used Windows in a long time... I think that those freezes could be more a cause of CPU though. Run Prime95 in Windows with Torture Mode. You should leave it for about 24 hours. Most of the errors because of CPU will be found in ~20 hours.
EDIT1: found a post about testing for stability with Prime95 [there]("http://www.devhardware.com/forums/showpost.php?p=569870&postcount=11")

Thanks Tanker.

I will run a test with Prime95 and report my findings here. I hope the computer won't freeze in the middle of the test *crosses fingers*

Here is my computer information which I seem to have left out of the OP:
```
_OS_: Main: Ubuntu 10.04 (lucid) 64-bit, Secondary: Windows 7 64-bit
_Kernel_: 2.6.32-22-generic
_RAM_: 2 x 1.0 GiB
_Processor_: AMD Athlon 64 X2 Dual Core 4400+
_HD_: 1 TB Sata WD drive

_Video card_: GeForce 7900 GS - 256 MB
_Resolution_: 1680 x 1050, 16.7 Million Colors
_Refresh rate_: 59.95 Hz
_Adaptive Clocking_: Enabled
_GPU Clocl_: 525 Mhz
_Memory Clock_: 775 Mhz
_Temp_ (after computer on for many hours): 72 degrees F
```

---

### Post by tankjer on 2010-06-03
> **1awesomeguy said:**
> Thanks Tanker.
It's Tank**j**er, but I forgive you :D.
> **1awesomeguy said:**
>  I hope the computer won't freeze in the middle of the test *crosses fingers*
If it will do, we will know that's the cause of the CPU.
> **1awesomeguy said:**
> 
Processor: AMD Athlon 64 X2 **Dual Core** 4400+
On that post I gave link to it said to have number of running tests corresponding to number of cores. In this case you would need to have two tests running at the same time:
> If you have an Intel processor with **Hyper  Threading** and/or any Dual Core processors, you need to run **two**  instances of Prime95 for complete effectiveness (as a note for dual  core HT processors, you need quad prime95 testing, that means 4  instances, 2 for each core, due to HT per every core). This is proven  fact- in that two instances of Prime95 will catch instability that one  instance won’t, on an Intel machine with HT. In order to run two  instances simultaneously, simply install a second copy of Prime95 in a  different folder, and run it in tandem with your original. Priority ten  should be used for both instances of Prime95 in this case.

---

### Post by 1awesomeguy on 2010-06-03
Ooops sorry Tankjer (too much Matrix-watching recently...)!

Thanks for pointing out the dual-core situation. I may have missed it.

---

### Post by pricetech on 2010-06-03
Another thing you might try is swapping the memory sticks and re running the memory tests.  You might get different results.

Your logic behind excluding a power problem may be flawed.  A power supply can power a computer, but not have sufficient capacity to keep everything "happy" so to speak.  If you mentioned the specs on the power supply, I missed them.

You don't mention if the computer is a white box or brand name either.  That might help.

---

### Post by 1awesomeguy on 2010-06-03
Thankjer: It seems like the latest version of Prime95 does not require two different instances as it has a setting to do two different tests at once. Most of the settings in the document linked are not available anymore (the article is six years old so the program probably has changed some), so I started a two "Small FFTs (maximum FPU stress, data fits in L2 cache, RAM not tested much)" tests with default settings. I think this will test CPU the most.

I can later do the "In-place large FFTs (maximum heat, power consumption, same RAM tested)" and "Blend (tests some of everything, lots of RAM tested)" tests. Hopefully diagnosing these tests will be easy :)

> **pricetech said:**
> Another thing you might try is swapping the memory sticks and re running the memory tests.  You might get different results.

Your logic behind excluding a power problem may be flawed.  A power supply can power a computer, but not have sufficient capacity to keep everything "happy" so to speak.  If you mentioned the specs on the power supply, I missed them.

You don't mention if the computer is a white box or brand name either.  That might help.

I will keep it in mind to swap the memory sticks (or maybe test one at a time). Though when I ran memtest from the Grub screen, no memory tests were found.

You may be right in my power consumption logic. I did not think of that. I assumed power supplies would give out completely if power consumption exceeded their limit (is this not always the case?). I think I have a generic _500 Watt power supply_ (any way to make sure?). The computer was _home-made_ by myself many years ago.

---

### Post by pricetech on 2010-06-04
> **1awesomeguy said:**
> 
You may be right in my power consumption logic. I did not think of that. I assumed power supplies would give out completely if power consumption exceeded their limit (is this not always the case?). I think I have a generic _500 Watt power supply_ (any way to make sure?). The computer was _home-made_ by myself many years ago.

As far as the rating, that should be on a label on the power supply itself.  It not, I'm not aware of any way to rate it.

As far as testing the power supply itself, see the attached image.  It shows the proper voltages for an ATX power supply.

---

### Post by 1awesomeguy on 2010-06-04
> **1awesomeguy said:**
> I started a two "Small FFTs (maximum FPU stress, data fits in L2 cache, RAM not tested much)" tests with default settings. I think this will test CPU the most.

My computer did not freeze, but I got a single error after 22 hours. I am not sure what to make of it. Current CPU temp is 40 C (so overheating CPU probably not an issue).

```

[Jun 4 11:52] Test 4, 75000 Lucas-Lehmer interations of M1300993 using FFT length 64K.
[Jun 4 11:53] FATAL ERROR: Rounding was 0.5, expected less than 0.4
[Jun 4 11:53] Hardware failure detected, consult stress.txt file.
[Jun 4 11:53] Torture Test completed 56 tests in 21 hours, 37 minutes - 1 errors, 0 warnings.
[Jun 4 11:52] Worker stopped.

```

It has been three hours since the failure and the other worker is still going. Currently, it passed all tests through to Self-test 64K and now started the 8K test again. I am going to stop it.

I am not sure if the failure means anything since the computer did not freeze and the stress.txt file says the following:

> In most cases though, it will fail within a few minutes on a flaky machines.

This part also appears to be useful (I am not overclocking, BTW):

> If you are not overclocking, the most likely cause is an overheating CPU or memory DIMMs that are not quite up to spec. Another possibility is you might need a better power supply. 

Not sure what to do next... Might run Prime95 again and see what it says this time...

---

### Post by 1awesomeguy on 2010-06-05
Running the "Blend test (tests some of everything, lots of RAM tested)" failed after just 9 minutes. The computer did _not_ freeze however...

```
[Jun 4 20:42] Test 2, 4000 Lucas-Lehmer interations of M19922943 using FFT length 1024K.
[Jun 4 20:46] FATAL ERROR: Rounding was 0.5, expected less than 0.4
[Jun 4 20:46] Hardware failure detected, consult stress.txt file.
[Jun 4 20:46] Torture Test completed 1 tests in 9 minutes - 1 errors, 0 warnings.
[Jun 4 20:46] Worker stopped.
```

What can we make of all of this?

---

### Post by 1awesomeguy on 2010-06-08
Okay, ran some more "Blend" tests in Prime95. The second one failed within three hours.

I then removed one of my RAM chips. With only 1GB of RAM Windows 7 was really slow to work with. It froze within a few seconds of starting up. I restarted and tried again. I ran the "Blend" test for a full 28 hours and no errors were found.

---

### Post by 1awesomeguy on 2010-06-14
bump...

---

### Post by pricetech on 2010-06-24
> **1awesomeguy said:**
> I then removed one of my RAM chips.I ran the "Blend" test for a full 28 hours and no errors were found.

Sounds like the stick of RAM you removed may be faulty.  Try running the test with only that stick, leaving the other one out.

---

### Post by rg_stephens on 2010-06-24
You might have to substitute some known-good components and re-test to isolate where the error is coming from. 

Sometimes you'll have to let Memtest run a long time to catch a problem. Even one error in 22 hours is enough to cause big problems. 

I was thinking, if a memory chip was bad it could have corrupted some of the files on your disk. Once you isolate which memory stick has the error (or cpu, or ...), you might need to reinstall the whole system to make things start working normally again.

---

### Post by 1awesomeguy on 2010-08-02
Quick update:

I have still not found a solution to this problem. :( Tested both RAM with various programs. Does anyone have any program recommendations which I can use to accurately diagnose specific computer comments?

I noticed, the freezing issue appears to be happening (almost) every time I open up Google Chrome (most of what I do on the computer) on an up-to-date Ubuntu install, though many other programs (even just browsing files with Nautilus) do cause this to happen. The issue does not happen with Windows 7 nearly as much but it appears to be completely random. I tend to only use Windows 7 now so I can get at least some work done. Unfortunately, my favorite OS, Ubuntu, freezes almost every time I am working (though not reliably enough for me to use it to test computer components).

Exception: If I just SSH or FTP to work off the computer (with Ubuntu), the computer will stay on for days. The freezing only occurs whenever I am actively on the computer doing something / moving the mouse.

This is definitely not a heating issue as it sometimes happen right after I boot up the computer. This is also not a software issue as it has been happening on many different OS and different versions of Ubuntu.

Help? :)

---

