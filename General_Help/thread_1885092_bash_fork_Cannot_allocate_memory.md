---
title: "bash: fork: Cannot allocate memory"
date: 2011-11-22
forum: General Help
---

### Post by fabben on 2011-11-22
Hello everybody! :)

Since I upgraded to 11.10 (upgraded when it was beta) I sometimes get this error messages then I using the tab function i bash:

bash: fork: Cannot allocate memory

I have a lot of memory left (626 MB + almost 8 GB i SWAP).

It never happened before I upgraded, and I've been hoping that this should disappear in lates upgrades, but after some month the problem is still here.

$ uname -a
Linux klisterburk 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
$ bash --version
GNU bash, version 4.2.10(1)-release (i686-pc-linux-gnu)

Does somebody know how I can solve this?

---

### Post by fabben on 2011-11-24
Hello again!

I also sometimes get this error then I'm doing others command.

Example:

$ rm -rf some_dir
bash: fork: Cannot allocate memory
$ rm -rf some_dir
$

The second time it worked.

---

### Post by Wayne_V on 2011-11-24
what is the output of 'free -m' ?

---

### Post by fabben on 2011-11-25
> **Wayne_V said:**
> what is the output of 'free -m' ?

$ free -m
             total       used       free     shared    buffers     cached
Mem:          3273       2871        402          0         14        648
-/+ buffers/cache:       2208       1065
Swap:         9624         30       9594
$

---

### Post by fabben on 2011-11-25
Yesterday I upgraded kernel to "3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 i686 i386 GNU/Linux", but today I got this:

$ screen -S alpine
bash: fork: Cannot allocate memory
$ 

(And the second time I run it it was no problem, as usual).

---

### Post by fabben on 2011-12-10
I still has this problems and have no clue how to solve it.

I also has big problem with my graphic drivers. 2 times of 3 when I reboot my machine, it totally crash when I start firefox. (I must press reset button, because X disappear and the screen shows only graphical junk).

Firefox hangs quite often also.

I think this problems are connected, because I didn't had any of it before.

I have run memory check on the machine for several hours, but it says that everything is okey.

---

### Post by fabben on 2011-12-13
No one has a clue how I can solve this? Is there any program/script that can search for broken things in the system? 

Today I found I had a mail.err file i /var/log. It had 3 lines:

Dec 12 10:11:26 fabbes spamc[13282]: fork failed: Cannot allocate memory
Dec 12 16:40:51 fabbes spamc[13725]: fork failed: Cannot allocate memory
Dec 13 22:17:52 fabbes spamc[366]: fork failed: Cannot allocate memory

---

### Post by imblack on 2012-01-29
I am also getting this same friken error sometimes :/

---

### Post by fabben on 2012-02-22
I have now, on a new disk, installed a totally new system from scratch. I tought the problem should be gone, but no!

After a while, maybe after I installed the samba-package(?), the problem returned. I did not had this problem before I installed 11.10. I just did "ls" some times, and this is what happened:

fabbe@fabbe:/media$ ls
filmdisk  old
fabbe@fabbe:/media$ ls
filmdisk  old
fabbe@fabbe:/media$ ls
filmdisk  old
fabbe@fabbe:/media$ ls
bash: fork: Cannot allocate memory
fabbe@fabbe:/media$ ls
filmdisk  old
fabbe@fabbe:/media$ ls
filmdisk  old
fabbe@fabbe:/media$ ls
filmdisk  old
fabbe@fabbe:/media$ ls

---

### Post by BJCV86 on 2012-02-22
> **fabben said:**
> I have now, on a new disk, installed a totally new system from scratch. I tought the problem should be gone, but no!

After a while, maybe after I installed the samba-package(?), the problem returned. I did not had this problem before I installed 11.10. I just did "ls" some times, and this is what happened:

fabbe@fabbe:/media$ ls
filmdisk  old
fabbe@fabbe:/media$ ls
filmdisk  old
fabbe@fabbe:/media$ ls
filmdisk  old
fabbe@fabbe:/media$ ls
bash: fork: Cannot allocate memory
fabbe@fabbe:/media$ ls
filmdisk  old
fabbe@fabbe:/media$ ls
filmdisk  old
fabbe@fabbe:/media$ ls
filmdisk  old
fabbe@fabbe:/media$ ls


Ok what i'm thinking is this question. What is your motherboard? I'm not a professional at all. I am using a socket 468? 3Ghz Dual thing. What is your socket? And RAM Specs? Not the amount, the company brand and speed. I mention this because specific communicative wavelength and light pulses of which I know of physics and different metal materials do actually permission the software, or deny of it. It's weird how I say it. But how they build it, and what 11.10 has included to understand the elemental properties of hardware. yada yada. New system you say? Ok I can think a question to ask about that. The question is: What socket did you use? And what ram? lol BEEECAUSE. I could be full of crap. But I had an issue. And I got rid of it because I had to stop buying mother boards that didn't support the new'polished implementations for specific things that all these things. I dunno. I thought I would ask. All I know, i had an issue with too much wrong ram. and just enough right ram. but if a ubuntu pro knows the computer science language impressively. Than i'm sure they would have an idea to quickly advance the Ubuntu further based on ur experiances. i hit my head too many times, however u say it. oh and how the software on the disk, communicates with the bios. I dunno I tried.

---

### Post by bignellrp on 2012-05-08
Im getting this also, only after upgrade to 11.10.  Any solutions yet?

---

### Post by fabben on 2012-05-29
> **bignellrp said:**
> Im getting this also, only after upgrade to 11.10.  Any solutions yet?

I have lately also got problems with X. Cannot click in windows. Can write in the active window but not change focus. Can use menu, but not anything else.

I'm almost sure now this is a hardware error. I upgraded to Linux Mint instead, and got exactly the same problem there (but very mush rare than before). Both with X and "allocate memory" thing.

My graphic card is without fans (as it should be) and gets VERY hot. I never turn my computer off normally, but if the problem is still there after reboots I let the computer be off to be cooled off and then everything works again. So, I'll buy new graphic card and suppose it will help. However I can't explain the "cannot allocate memory" thing, but maybe the SIMMs work bad because of the heat from memory card some centimetre away.

---

### Post by SwedishWings on 2012-08-06
I run into this problem as well, but found out that i had no swap partition enabled. Adding a swap partition solved the problem.

Hope this helps.

---

### Post by fabben on 2012-08-24
> **SwedishWings said:**
> I run into this problem as well, but found out that i had no swap partition enabled. Adding a swap partition solved the problem.

Hope this helps.

I hade swap partition (3 GB RAM + like 6 GB SWAP).

However, the problem is solved. I bought a new graphic card, a one with fan. It's sound a hell lot of more than the old one without fan, but the problem has not appeard any more.

The old graphic card was always VERY hot, and I think it created problem with the SIMM-memories.

So, however, problem solved. Thanks for the answers I got.

---

