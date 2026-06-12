---
title: "How to force all cores to work"
date: 2012-03-01
forum: General Help
---

### Post by Trotel on 2012-03-01
Hi,
 
When I work with very big files, all simple commands takes a long time and by default my machine seems to work with only one core (Intel Corel i5 480 2.67Ghz) so I have 2 questions:
 
1. How to force my machine to work with all cores when I use commads or scripts?
 
2. Is there a problem if I force all cores?
 
Thanks.

---

### Post by Tiganjero on 2012-03-01
Are you sure that all of your cores are detected? That's not an uncommon problem.

Cheers,
George

---

### Post by Trotel on 2012-03-03
> **Tiganjero said:**
> Are you sure that all of your cores are detected? That's not an uncommon problem.

Cheers,
George

If all of my cores are detected? sorry but I don't know, when I run a command working with this hard file, I saw for example, core1: 90%, core2-4: ~20-30%, I guess If my machine work with all its cores close to 100%, the work will end faster.

---

### Post by whitethorn on 2012-03-03
That depends on if the programs you use are programmed for parallel processing. Some are, but that depends on what you're doing. Having multiple cores allows a process to run full speed on a core or two while the system still remains responsive. 

It might be possible to use more cores but you'd have to tell us what you're trying to do.

---

### Post by NikTh on 2012-03-03
> **whitethorn said:**
> that depends on if the programs you use are programmed for parallel processing. 

+1

---

### Post by raja.genupula on 2012-03-03
Hi actually you can force applications as up to what limit they have to use by using cpulimit. 

but if much applications are running then more CPU will be used . less Apps Less CPU . whats the use of forcing the CPU to high use even you're not running in that range . 


If you wanna work with all your CPU , play a big sized game . that will take i hope . 

all the best .

---

### Post by hwttdz on 2012-03-03
This is actually a more complicated question for larger files than it is for many small files.  For many small files my general solution is to use xargs or parallel to farm out the smaller jobs.

For example, say I want to find all .gz files that contain the word "ubuntuforums".  

The slow way (this runs zgrep on each .gz file found):
```
find . -name "*.gz" -exec zgrep -l "ubuntuforums" {} \;
```

But since I don't care about the order of the returned list I can use xargs to do things in your case about twice as fast:
```
find . -name "*.gz" | xargs -P 2 -n 10 zgrep -l "ubuntuforums"
```
This splits the list of .gz files into chunks of 10 and starts two different instances of zgrep passing 10 files to each, when an instance of zgrep finishes it starts a new one.  The OS will take care of putting one on each core.

And finally you can use parallel to accomplish the same:
```
parallel zgrep -l "ubuntuforums" -- `find . -name "*.gz"`
```
Parallel is cool in that it determines how many jobs to start.  It processes each argument individually (at least by default).

If you're running a script on a large file you could plausibly split the file in two and run the command on each half and then combine the results.  But that sounds like it's going to involve trading your old problem (slow) for a new one (how to combine results from the two halves of the file run separately).  If you're thinking of something like image processing, the software has to be written in such a way as to take advantage of multiple cores, there's no way to split processes across multiple cores.  So short of getting your hands dirty (as in absolutely filthy, disassembling and reassembling the program) there's no easy way.

And the simple answer to your second question, there's nothing wrong with making all your cores to work.  Your fan might spin up pretty high, but it shouldn't be an issue.

---

### Post by Trotel on 2012-03-05
Well, for example my file has 20 GB, is only text very simple but very hard, so when I use very simple command (grep, cat, wc) the work take a long time. My machine have 4 cores, but the command use only one (seems) and I want to work with 3 cores.

---

### Post by idoitprone on 2012-03-05
sounds like you need a better harddrive

---

### Post by jailbait on 2012-03-05
> **Trotel said:**
> Well, for example my file has 20 GB, is only text very simple but very hard, so when I use very simple command (grep, cat, wc) the work take a long time. My machine have 4 cores, but the command use only one (seems) and I want to work with 3 cores.
Thats not related to the CPU.

Its called having an high IOWAIT. Check something like iotop to see if your maxing your HD throughput.
 If you are, consider getting 10K or SSD drives. with SATA/SAS.

---

