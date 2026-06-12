---
title: "Impossible to use my PC when speed goes over 15Mb/s !"
date: 2009-07-05
forum: General Help
---

### Post by credobyte on 2009-07-05
Transmission, Deluge, Vuze .. no matter which one is turned on, if speed goes over 15Mb/s, whole system just hangs ( it takes 1min. to open a terminal :o ).
What could be the problem ? Why it takes so much CPU ( 30-60% ) ?

---

### Post by wojox on 2009-07-05
I have similar problems with transmission.
Seeds and Peers?

---

### Post by DeMus on 2009-07-05
> **credobyte said:**
> Transmission, Deluge, Vuze .. no matter which one is turned on, if speed goes over 15Mb/s, whole system just hangs ( it takes 1min. to open a terminal :o ).
What could be the problem ? Why it takes so much CPU ( 30-60% ) ?

I also have these problems, also with a simple copy or move action from one disk to another, either local or in a network.
Also archive manager takes up the complete computer, although top says it does not. The computer does not respond at all.
Why do some things take over the complete computer when it seems to be doing almost nothing?

---

### Post by credobyte on 2009-07-05
> I have similar problems with transmission.
Seeds and Peers?

Even with 5/5 ( seeds/peers ) :(

> I also have these problems, also with a simple copy or move action from one disk to another, either local or in a network.
Also archive manager takes up the complete computer, although top says it does not. The computer does not respond at all.
Why do some things take over the complete computer when it seems to be doing almost nothing?

The same here, tough, only for files larger than 5GB ( haven't seen any problems in moving movies and similar size files ).

---

### Post by credobyte on 2009-07-06
I'm not a big fan of "bump", but .. does anybody know where's the problem ( any help appreciated ) ?

---

### Post by Tipped OuT on 2009-07-06
Wow one minute to open up a terminal? That sounds bad, you probably have a single core CPU...

What is your CPU by the way?

---

### Post by credobyte on 2009-07-06
Yeah, single-core processor, tough, haven't seen such a hang on other OS's ( even 8.10 file transfers were faster ).

```
          description: CPU
          product: AMD Sempron(tm) Processor 2600+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.2
          slot: Socket 940
          size: 1600MHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm

```

---

### Post by credobyte on 2009-07-27
Scream in a dark forest .. Does anybody have an idea on how to fix this problem ? The best part is that, computer is completely locked but CPU and memory usage is quite normal ( I tough Nautilus may cause these problems, but .. it uses less than my web browser ) :-k

---

### Post by moster on 2009-07-27
First of all, get rid of transmission and get some torrent fith file allocation. Or use most newer transmission. Why? Transmission awfully fragments everything you download and you can check this by this command ```
sudo filefrag -v YourFile
```
It will say something like 6 ideal, your 36000!

Next, I have experienced that problem when I install ubuntu without swap file. I thought it was not needed. I do not know if slowness caused by this but I telling you anyway. Everybody recommend at least 512 MB swap.

Next, you could edit ```
sudo gedit /etc/sysctl.conf
```
then at the bottom of the file add the following if you already do not have it:
```
vm.swappiness=0
```
this is only optional because I do not put it myself and I do not know what it do
```
vm.vfs_cache_pressure=1
```
that will make ubuntu use swap less and save you from potential swapping in the middle of copying. It works for me at. But still not 100%

Last trick is more driver trick. Some people said it help them. If you have in bios AHCI, turn it ON. I recommend turning it off if you have problem with them. In any way, it will change driver that Ubuntu use for hdd access. Be aware that this will probably screw your windows if you have dual boot. Not permanently, just till you change that in bios.

Now... I have experiencing this problem and all this works, but not 100% but I can use now computer when coping. I try booting from live cd and when coping from there, everything is fine. So, it is something we all have AFTER installation. Probably some update screw us all.

I am full of tricks like freakin clown, but this is not 100% solution, only help.
If anybody have any anything else to say I am glad to hear.

:)

---

### Post by credobyte on 2009-07-27
[B]@ moster
[/B]
The problem is not because of my torrent client - it's a global problem. Example - if I want to copy a 4Gb file to another folder, system will hang ( Firefox will act weird, music will start to "pause" itself for a while, etc. ). It's something I simply can't understand .. I've been doing all kinds of crazy things with other distros and Ubuntu 8.04, but 9.04 seems to be "broken" ( just referring to my problem - everything else works like a charm ).

Is Bonnie++ worth a try ( benchmarking ) ?

---

### Post by moster on 2009-07-27
@credobyte

I know it is not solution except ATA-AHCI. That help some people for sure. Everything else I mention is only "help".

I never try Bonnie.

---

### Post by credobyte on 2009-07-27
> **moster said:**
> @credobyte

I know it is not solution except ATA-AHCI. That help some people for sure. Everything else I mention is only "help".

I never try Bonnie.

Sure, don't get me wrong - I was just explaining my current situation ;) Anyway, will try your ATA-AHCI trick a bit later on today.

---

### Post by moster on 2009-07-27
I do not get such serious problem like you. But I was experiencing enormous slowdown when copy from my external USB disk at cca 15 MB/s. I could not even surf. Barely write pure text in this forum. BTW, it was peace of cake for most crapped OS in newer history on my system :) So something is wrong. I definately have problem too, now after all this crap I mention is better but still it is not enough.

I read bunch of I/O slowdown people have... Something is going on definitely.

---

### Post by hibliss on 2009-07-27
I have a similar issue while extracting rar archives, and have since 8.04.

I have not experienced any of the other issues while transferring files (are these SATA or IDE drives?), or while using Bittorrent at the max speed of my connection.

---

### Post by diggedy on 2009-07-27
I used to have this problem until i set swappiness to 0. Now everything runs fine

---

### Post by moster on 2009-07-27
Swappiness definitely help but something else is issue here. 

It seems that bonnie++ is key to test it. Install it trough synaptic or apt-get. Now, I never before use it so I use some of examples over net here it is
```
bonnie++ -d /home/moster/tmp -s 4024
```  
that last number is double my RAM, it was recommended

This will generate some files in there. It last 7-10 minutes and in end give some numbers. Trough whole test I experience sluggishness, sound cracking several time, even firefox go grey or I was not able to change tab. Whole time CPU did not exceed 20%. So, it is I/O slowdown. At least I think.

Overall, to get right picture imagine dead snail.

Somebody else try it?

Hardware:
Seagate 250 GB 7200 SATA 8 MB cache
Chipset Intel G31 (ICH6) DMA enabled
CPU 3,4Ghz, 2GB RAM

---

### Post by Bonzai11 on 2009-07-27
Its just the sheer amount of drive usage.
I'd say check drive read and write.
Torrents are known to kill hardrives because most torrents are humongous and cant be cached.
And the parts people want are random unlike other protocols that go from start to finish.

Also could be bottleneck by ram, cpu who knows.
All it is is that if you've tried different programs your system just isn't up to par for torrents, well at insane speeds.
And also thats pretty crazy 15mb/s, me being a teenager can only dream of having such fast internet.

Just throttle your downloads. You wont be able to download so fast but waiting a couple of minutes more for instant gratification will allow you to use your computer.
And just also thought when you using Bt your constantly sending out Yes and no packets and questions whether other end got packet. This can really put a big strain on cpu.
Also if your not using hardware tcip/ip management( I think thats name I forgot can't think to well atm)
All internet nonsense has to be done by cpu which causes strain.

Just enjoy your even able to get 15mb/s :P

---

### Post by moster on 2009-07-27
I thought he made error in writing. Huh, what kind of internet is 15 MB/s?! :D

Ok, never mind. I had similar problem on windows few years ago when I download some stuff on universaty over torrent. Speed was around 3 MB/s. It is not so much, but every torrent is fragmented in pieces of 128 kb-1MB and when downloading from 50 people at once it is significant I/O.

Solution is to just enlarge cache. Default on most torrent progs is only few MB.

---

### Post by hibliss on 2009-07-27
> **Bonzai11 said:**
> 
Torrents are known to kill hardrives because most torrents are humongous and cant be cached.


Just enjoy your even able to get 15mb/s :P

This is a myth. Thrashing your drive is a problem when your cache is set too small depending on how many torrents you are seeding, but there is generally an option to increase the amount of RAM used to cache seeding torrents.

I have been torrenting for 5 years on the same drive, several terabytes transferred each way with no issues.

Also, 15mb/s isn't that fast in today's market (at least not in the US). I have 20 now, and could get 50/50 if I wanted to pay $100/month.

---

### Post by credobyte on 2009-07-27
> **Bonzai11 said:**
> 
And also thats pretty crazy 15mb/s, me being a teenager can only dream of having such fast internet.

It's a standard package - 60mbps download & 40mbps upload. Nothing fancy here - 20$/month :)

---

### Post by miklcct on 2009-07-27
What's the kernel version?

---

### Post by moster on 2009-07-28
> **credobyte said:**
> It's a standard package - 60mbps download & 40mbps upload. Nothing fancy here - 20$/month :)
I understood that you talked about 15 megabyte/second. That would be about 150 megabit/second!!! 
> **miklcct said:**
> What's the kernel version?
Who you ask? We all have similar problems.
Mine is:
```
Linux moster-desktop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

```

---

### Post by hibliss on 2009-07-28
> **moster said:**
> I understood that you talked about 15 megabyte/second. That would be about 150 megabit/second!!! 

[/CODE]


No, it wouldn't. 1 megabyte=8 megabits. It would be 120 megabits per second.

Also, most people know that internet packages are sold in megabits/second.

---

### Post by credobyte on 2009-07-28
Regarding megabits and megabytes - I'll say as it is .. I'm not really sure what's the difference. All I know is that I can download 10-30Mb in 1 second.

System:
```
Linux credobyte 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux
```

---

### Post by moster on 2009-08-02
> **DeMus said:**
> I also have these problems, also with a simple copy or move action from one disk to another, either local or in a network.
Also archive manager takes up the complete computer, although top says it does not. The computer does not respond at all.
Why do some things take over the complete computer when it seems to be doing almost nothing?

I somewhere read that you upgrade kernel. Did that help?

And how you do it btw? If not too long to describe..

---

