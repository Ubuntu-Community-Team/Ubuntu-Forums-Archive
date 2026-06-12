---
title: "How many CPU core ?"
date: 2012-04-18
forum: General Help
---

### Post by winzip on 2012-04-18
Whats the command to find how many CPU core the system has ?

OS: Ubuntu 10.04 Server OS ( no GUI)

---

### Post by Cheesemill on 2012-04-18
```
cat /proc/cpuinfo
```

---

### Post by winzip on 2012-04-18
> **Cheesemill said:**
> ```
cat /proc/cpuinfo
```

This prints lots of attributes and corresponding values. Which attribute to look at ?

---

### Post by sudodus on 2012-04-18
> **winzip said:**
> This prints lots of attributes and corresponding values. Which attribute to look at ?
This command line produces one single number.
```
sudo lshw -class processor|grep '*-cpu'|wc -l
```
If you peel it from behind you get gradually more info.
```
sudo lshw -class processor|grep '*-cpu'
```
```
sudo lshw -class processor
```
```
sudo lshw
```
The last one (the complete output of ***lshw*** is so big, that you should write it to a file and view the file, for example
```
sudo lshw > lshw.txt
```
```
less lshw.txt
```
An alternative is the GUI program ***hardinfo***

---

### Post by Cheesemill on 2012-04-18
> **winzip said:**
> This prints lots of attributes and corresponding values. Which attribute to look at ?
Look at the line that says 'cpu cores'

---

### Post by Cheesemill on 2012-04-18
> **sudodus said:**
> This command line produces one single number.
```
sudo lshw -class processor|grep '*-cpu'|wc -l
```****

This gives a result of 1 on my machine, but I have a dual core processor.
I think it may be reporting the number of CPU's instead.

---

### Post by winzip on 2012-04-18
> **Cheesemill said:**
> Look at the line that says 'cpu cores'

I do not find that. Though i find processor =1.
is it the same thing ?

---

### Post by Cheesemill on 2012-04-18
Post the full output of:
```
cat /proc/cpuinfo
```
and I'll have a look.

---

### Post by winzip on 2012-04-18
> **Cheesemill said:**
> This gives a result of 1 on my machine, but I have a dual core processor.
I think it may be reporting the number of CPU's instead.

Then this is a wrong result. You should get 2 because its dual core.

---

### Post by Cheesemill on 2012-04-18
That was my point.
```
cat /proc/cpuinfo
```
Gives a result of 2, but using:
```
sudo lshw -class processor|grep '*-cpu'|wc -l
```
Gives me a result of 1

I was pointing out that my method gave me the expected answer whereas sudodus' method gave an incorrect result.

---

### Post by winzip on 2012-04-18
> **Cheesemill said:**
> Post the full output of:
```
cat /proc/cpuinfo
```
and I'll have a look.

I may not post server config in this public forum. Will it be possible to tell which attribute giving 2 in your machine ? Probably thats the correct attribute i need to check.

---

### Post by Cheesemill on 2012-04-18
> **winzip said:**
> I may not post server config in this public forum. Will it be possible to tell which attribute giving 2 in your machine ? Probably thats the correct attribute i need to check.

There is no harm in posting the result here, the only information it gives is what model of CPU you are using. It doesn't reveal any other information about your system.

---

### Post by winzip on 2012-04-18
Sorry my bad. I find cpu cores =2.
problem solved.

---

### Post by Cheesemill on 2012-04-18
```
rob@precise:~$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 37
model name    : Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz
stepping    : 5
microcode    : 0x2
cpu MHz        : 1197.000
cache size    : 4096 KB
physical id    : 0
siblings    : 2
core id        : 0
**[COLOR=Red]cpu cores    : 2[/COLOR]**
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt lahf_lm arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6133.31
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 37
model name    : Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz
stepping    : 5
microcode    : 0x2
cpu MHz        : 1197.000
cache size    : 4096 KB
physical id    : 0
siblings    : 2
core id        : 2
cpu cores    : 2
apicid        : 4
initial apicid    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt lahf_lm arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6133.13
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

There is the highlighted line above, also I can just google for 'i3-540 specs' to get a result.

---

### Post by sudodus on 2012-04-18
@winzip: What do you want, exactly? I mean, would it be enough to view a list output and manually decide what is the relevant information like in
*Cheesemill*'s original post ```
cat /proc/cpuinfo
``` or mine
```
sudo lshw -class processor
``` or do you want to do some automatic evaluation, that must find a reliable number without human intervention?

@Cheesemill: I'm reading and learning. Obviously, there are computers, where 'my favourite lshw' might give misleading results.

*Edit: But how would you interpret the output of the two commands on my xeon computer? See the attached file*

---

### Post by sj1410 on 2012-04-18
htop can also show you the total cores along with its utilization, you need to install it


sudo apt-get install htop

---

### Post by growingneeds on 2012-04-18
This one line entry might make things easier
```
cat /proc/cpuinfo | grep "cpu cores"

```

---

### Post by 2bob on 2012-04-18
This is the output from my cat /proc/cpuinfo.

---

### Post by winzip on 2012-04-18
Now I'm totally confused ...

I'm doing jboss performance tuning ..

I see  this ...

[I]**JBoss tuning tip 6:  Turn on parallel gc**
If you have multiple proessors you can do your garbage collection with multiple threads.
By default the parallel collector runs a collection thread per processor, **[COLOR=Red]that is if you have an 8 processor box then you'll garbage collect your data with 8 threads.[/COLOR]** In order to turn on the parallel collector use the flag -XX:+UseParallelGC. You can also specify how many threads you want to dedicate to garbage collection using the flag [COLOR=Red]**-XX:ParallelGCThreads=8.**[/COLOR][/I]

[COLOR=DarkRed]**source**[/COLOR]: [http://www.mastertheboss.com/jboss-application-server/113-jboss-performance-tuning-1.html](http://www.mastertheboss.com/jboss-application-server/113-jboss-performance-tuning-1.html)

Please note [COLOR=Red]**red **[/COLOR]markers.

I am worried what should I put for  my case ..

cat /proc/cpuinfo  this  prints

[COLOR=Blue][B]processor = 1
cpu cores = 2[/B][/COLOR]

Now I'm worried what to  write  for  [I][COLOR=Red][B]-XX:ParallelGCThreads.

[/B][/COLOR][/I][COLOR=Black]Should I write [/COLOR][COLOR=Black][COLOR=Red]**-XX:ParallelGCThreads=1 **[/COLOR] or  [/COLOR][COLOR=Red]**-XX:ParallelGCThreads = 2**[/COLOR]

---

### Post by sudodus on 2012-04-18
> **winzip said:**
> Now I'm totally confused ...

I'm doing jboss performance tuning ..

I see  this ...

[I]**JBoss tuning tip 6:  Turn on parallel gc**
If you have multiple proessors you can do your garbage collection with multiple threads.
By default the parallel collector runs a collection thread per processor, **[COLOR=Red]that is if you have an 8 processor box then you'll garbage collect your data with 8 threads.[/COLOR]** In order to turn on the parallel collector use the flag -XX:+UseParallelGC. You can also specify how many threads you want to dedicate to garbage collection using the flag [COLOR=Red]**-XX:ParallelGCThreads=8.**[/COLOR][/I]

[COLOR=DarkRed]**source**[/COLOR]: [http://www.mastertheboss.com/jboss-application-server/113-jboss-performance-tuning-1.html](http://www.mastertheboss.com/jboss-application-server/113-jboss-performance-tuning-1.html)

Please note [COLOR=Red]**red **[/COLOR]markers.

I am worried what should I put for  my case ..

cat /proc/cpuinfo  this  prints

[COLOR=Blue][B]processor = 1
cpu cores = 2[/B][/COLOR]

Now I'm worried what to  write  for  [I][COLOR=Red][B]-XX:ParallelGCThreads.

[/B][/COLOR][/I][COLOR=Black]Should I write [/COLOR][COLOR=Black][COLOR=Red]**-XX:ParallelGCThreads=1 **[/COLOR] or  [/COLOR][COLOR=Red]**-XX:ParallelGCThreads = 2**[/COLOR]
I think you can have one thread per core.

---

### Post by sudodus on 2012-04-18
> **sj1410 said:**
> htop can also show you the total cores along with its utilization, you need to install it


sudo apt-get install htop
I'm using htop too and I like it :KS

htop shows 4 cpus (but is it processors or cores?) on my xeon machine. Check with the attached file in post #15

---

### Post by Cheesemill on 2012-04-18
> **sudodus said:**
> I think you can have one thread per core.

Unless your CPU supports hyperthreading in which case you have 2 execution threads per core.

In the end though I would recommend using htop. It will show the number of execution threads available - 2 in my case (1 CPU, dual core, no hyperthreading).

---

### Post by winzip on 2012-04-18
> **Cheesemill said:**
> Unless your CPU supports hyperthreading in which case you have 2 execution threads per core.

In the end though I would recommend using htop. It will show the number of execution threads available - 2 in my case (1 CPU, dual core, no hyperthreading).

there is no gui . its ubuntu 10.04 server OS

---

### Post by Cheesemill on 2012-04-18
> **winzip said:**
> there is no gui . its ubuntu 10.04 server OS
htop isn't a GUI application, it's a command line app.
Check out my screenshot above and you can see it running in a terminal.

Install it with:
```
sudo apt-get install htop
```

---

### Post by winzip on 2012-04-18
I have checked the attachment  image  --- htop output.


>>>>It will show the number of execution threads available - 2 in my case 

where is that ? I dont see that in your  image .  Could you please mark that part and upload the image again.

---

### Post by Cheesemill on 2012-04-18
In the top left corner you can see usage graphs for 2 cores, if I had hyper-threading enabled on this CPU it would show 4 graphs (one for each execution thread).

---

### Post by sudodus on 2012-04-18
> **winzip said:**
> I have checked the attachment  image  --- htop output.


>>>>It will show the number of execution threads available - 2 in my case 

where is that ? I dont see that in your  image .  Could you please mark that part and upload the image again.
At the top left

```
  [COLOR="Red"]1[/COLOR]  [||||                     11.4%]     Tasks: 216 total, 1 running
  [COLOR="red"]2[/COLOR]  [|||                       7.2%]     Load average: 0.76 0.65 0.47 
  Mem[||||||||||||||||||  498/1886MB]     Uptime: 01:53:17
  Swp[                         0/0MB]

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command

```

---

### Post by CharlesA on 2012-04-18
> **winzip said:**
> I have checked the attachment  image  --- htop output.


>>>>It will show the number of execution threads available - 2 in my case 

where is that ? I dont see that in your  image .  Could you please mark that part and upload the image again.
It's at the top labeled 1 and 2. :)

EDIT: Ninja'd by around 15 mins.. that'll teach me to not refresh a page before replying..

---

### Post by winzip on 2012-04-18
Ok. noted.  those  shows  each core  usage ..right ? As you had 2 cores ..they shows individual usage clearly.

suppose,  had it been 4 cores  there...I guess   htop  would print ...

1 - <usage % >
2 - <usage % >
3- <usage % >
4- <usage % >


Ok.  good . no problem.



But we are  probably deviating from main discussion....

My query was should I  write ...

 -XX  :  ParallelGCThreads=<number of processor in the box >

OR

-XX   :  ParallelGCThreads=<number of cores in a processor >


which one to pick ? Lets clear it  this up first .

---

### Post by Cheesemill on 2012-04-18
Just use the number htop reports for your number of cores.

---

### Post by sudodus on 2012-04-18
Use the number shown by htop

1 ...
2 ...
==> 2

1 ...
2 ...
3 ...
4 ...
==> 4

---

