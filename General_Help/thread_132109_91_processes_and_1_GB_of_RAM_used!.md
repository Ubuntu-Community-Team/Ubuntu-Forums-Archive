---
title: "91 processes and 1 GB of RAM used!?"
date: 2006-02-17
forum: General Help
---

### Post by flummoxed on 2006-02-17
Is this normal? KSysGuard says I have 91 processes and only 15,744 kb of RAM free on a 1GB ram system. This is a KDE install over Gnome-Ubuntu. This just seems crazy to me! Should KDE be wasting this much RAM? I'm only browsing the internet and listening to mp3's on amaroK... 

Even WINDOWS makes better use of ram than this.

Oh... and the CPU load is at about 100%. This can't be normal.

---

### Post by Lord Illidan on 2006-02-17
Type ```
free
``` in a terminal and post output here.

EDIT : Seeing as you have 1 gig of ram have you installed 686 kernel?

Just do ```
sudo apt-get install linux-686
```

---

### Post by flummoxed on 2006-02-17
Isn't the 686 kernel for 64-bit processors?

I went back into GNOME for a minute, got your reply, and swithced back to KDE again. 
Here's what free gave me when I first started:

Mem:           307856 USED    728792 FREE 

then I opened Kopete:

Mem:          322224 USED    714424 FREE 

then I opened firefox:

Mem:          351644 USED    685004 FREE

then I opened amaroK:

Mem:         484864  USED   551784 FREE

And now my system RAM usage is at 970 mb... It almost doubled from 484 in the amount of time it took me to type this.

---

### Post by z-vet on 2006-02-17
I have 99 running processes and 16 Kb free of 1 Gb of RAM. Linux will try to use all available memory, it is normal behaviour. Do you have some problems like freezing or lock-ups? If not, you have no need to worry, i think.

---

### Post by flummoxed on 2006-02-17
Are you sure it's normal behaviour? I don't get a hundred percent CPU load and all my RAM used up while playing songs in gnome...

And it's going noticeably slower while it's like this in KDE.

---

### Post by YourSurrogateGod on 2006-02-17
I don't think that simply because you 16Kb free, it means that actual programs occupy all of that memory, it could be reserved by the OS for possible uses by any future processes that might start up.

I typed in free and this is what I got:
```
             total       used       free     shared    buffers     cached
Mem:        516128     495480      20648          0      13332     228308
-/+ buffers/cache:     253840     262288
Swap:      1510068      12540    1497528
```
I have 512MB of memory, KDE 3.5 and kernel 686.

Try doing K -> System -> Performance Monitor and see how much of memory is used there, then you'll know the true amount of memory use by all of your processes.

---

### Post by flummoxed on 2006-02-17
Yeah, the performance monitor was the orginal thing that tipped me off as to how much it was using.

BTW, should I use the 686 kernel? What's the difference?

---

### Post by YourSurrogateGod on 2006-02-17
[QUOTE=flummoxed]Yeah, the performance monitor was the orginal thing that tipped me off as to how much it was using.[/quote]
Try fiddling with a couple of settings in order to get rid of certin visual effects in KDE in order to consume fewer resources. I did that and I noticed an improvement in performance (I wouldn't say that it was a very large improvement.)
[quote=flummoxed]BTW, should I use the 686 kernel? What's the difference?[/QUOTE]
Not much. If you have more than 900MB in ram, then it would be best to use the 686 kernel. The 686 kernel is able to recognize more than 900MB (that's the most that the 386 kernel can if I remember correctly.) That's about the only improvement that I know of. But, since you have 1GB of ram, I'd suggest installing it.

Once you install the new kernel, reboot your machine in order to use it. When GRUB will show up in order for you to log into Ubuntu, you'll see several options for you to select, pick the most recent one with the 686 kernel.

---

### Post by flummoxed on 2006-02-17
The 386 kernel seems to recognize 1012 of RAM, which is close to right. Is there any downside to installing the 686 kernel?

---

### Post by YourSurrogateGod on 2006-02-17
[QUOTE=flummoxed]The 386 kernel seems to recognize 1012 of RAM, which is close to right. Is there any downside to installing the 686 kernel?[/QUOTE]
None that I've noticed.

---

### Post by Rizado on 2006-02-18
[QUOTE=flummoxed]The 386 kernel seems to recognize 1012 of RAM, which is close to right. Is there any downside to installing the 686 kernel?[/QUOTE]If you want to you can follow [this guide](http://www.ubuntuforums.org/showthread.php?t=85064) and compile your own kernel. My performance have increased alot by doing it. The ubuntu kernels seem to load many unnecessary modules (Like ethernet cards I don't have). Make sure you use con kolivas patches because they improve performance, and compile the newest vanilla kernel (If you scroll down you'll see what I mean)

---

### Post by z-vet on 2006-02-18
[QUOTE=flummoxed]Are you sure it's normal behaviour? [/QUOTE]
Once ago i asked the very same question and that was an answer i've got: Linux will use as much RAM as possible. Read [this](http://wiki.linuxquestions.org/wiki/FAQ_-_Linux_problems#Q:_Why_is_Linux_using_up_all_my_memory.3F) article, it explains things better than me.
One more thing: i had GeForce4 video card and replaced it by new GeForce 5500. System runs faster now... Maybe, you use some older hardware that is slower than the rest of your machine? Adding a RAM can't help in this situation, i think.

---

### Post by der_joachim on 2006-02-18
[QUOTE=flummoxed]Yeah, the performance monitor was the orginal thing that tipped me off as to how much it was using.

BTW, should I use the 686 kernel? What's the difference?[/QUOTE]

Yes you should. That is, if you have a Pentium IV. If you have an AMD processor, you should probably use linux-k7 or something. Read [this thread]("http://ubuntuforums.org/showthread.php?t=85917") for more information. 

Here's another useful document: [the Kubuntu optimalization guide]("https://wiki.kubuntu.org/KubuntuOptimization").

Good luck.

---

### Post by flummoxed on 2006-02-18
Wow, thanks a lot for the help. I'll give you a low-down of my system specs.

AMD Sempron 2400+
Abit Nf7-S2
2 x 512MB DDR 400 in dual-channel
Radeon 9800 pro
2 WD 80 gb HDD's (one S-ATA, which holds ubuntu, other IDE with windows)

I'll look through those guides you guys posted. :)

Well, I wonder if amaroK is the problem? When I start playing music with it, the CPU usage jumps to 100%. Is it actually at 100%, or is linux lying to me?

I assume the k7 kernel supports semprons as well... does anyone know otherwise?

---

### Post by z-vet on 2006-02-18
Well, your system seems to be well-balanced (i mean, no hardware that can slow it down). For amaroK...it's memory-expensive, but i personally never had 100% CPU usage with it. Which version do you use? I mean, one you get from repos is a generic build, so maybe compiling it from sources on your own machine will help. Ah, and an engine amaroK uses... try to run it with different engines (if you have several) and see if one is  "lighter" than others. Anyway, compiling software on your machine is always a good idea: it will be more optimized than generic builds you get from repos, imho.
Good luck.

---

### Post by flummoxed on 2006-02-18
I'm using the xine engine... I heard it's lighter than others, and it was the first one I got running mp3's. I'll look into that.

---

### Post by lcg on 2006-02-18
Actually, Linux uses as much RAM as possible for caching file system access.

Think about this for a second: Having 1GB of RAM, would you rather have half or more of it free and therefore unused or would you prefer the OS used it to speed things up, releasing it to processes when needed?
Although RAM got pretty cheap over the last years, I still think having half or more of it unused 90% of the time is a waste of money.

If you want to know what's going on with your free RAM, I suggest (like someone else has already) that you have a look at the 'free' command (-m to get the output in MB):
```
lars@eden ~ > free -m
             total       used       free     shared    buffers     cached
Mem:           503        497          5          0          3        411
-/+ buffers/cache:         82        420
Swap:          956          0        956
```
This is the output I get from my little server. As you can see in the "Mem:" line, it has got 512MB of RAM, 5 of them are free. However, in the next line, you see the numbers without counting buffers and cache as used, i.e. the actual amount of RAM used and available to your programs. In the example above, there are only 82MB used and 420MB are free (or, to be more precise, can be freed when needed). The last line lists my 1GB swap which is usually not used at all on that box.

HTH,
Lars

---

### Post by YourSurrogateGod on 2006-02-18
lcg, what desktop environment do you have?

---

### Post by lcg on 2006-02-18
[QUOTE=YourSurrogateGod]lcg, what desktop environment do you have?[/QUOTE]
On that server? None. :) It's running without X, keybord or mouse. Only a network cable and SSH.

Lars

---

### Post by YourSurrogateGod on 2006-02-18
[QUOTE=lcg]On that server? None. :) It's running without X, keybord or mouse. Only a network cable and SSH.

Lars[/QUOTE]
Ahh... well, that explains why your system output is so lean :) .

---

