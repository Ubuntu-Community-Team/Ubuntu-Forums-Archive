---
title: "very high RAM usage on startup - 800 MB!"
date: 2010-08-02
forum: General Help
---

### Post by krack3rz on 2010-08-02
I don't understand why I have a 800MB usage at startup. I didn't add any programs to start at startup. I do though have 10 primary partitions that are auto mounted at startup but it shouldn't use up so much, I have 2GB total RAM.

At startup nautilus uses ~400MB of virtual memory in the "system monitor"

Also which is RAM and which is SWAP in resources in system monitor: Virtual Memory && Memory?

-i figure vm is ram but thats not possible sometimes...it exceeds 2GB

---

### Post by Austin25 on 2010-08-02
Do you have very many gnome applets running?

---

### Post by mikewhatever on 2010-08-02
Can you post the output of the **free -m** command.

---

### Post by Maverick_Meerkat on 2010-08-03
Greetings,

800Mb at startup IS excessive! Ubuntu 10.04 requires approx. 103Mb of physical memory (RAM) & zero virtual memory at startup. 

1. Consult this link & disable all unwanted services from loading at boot-time.

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491) 

2. Disable any visual desktop/window effects, such as Compiz. You'd be surprised how much RAM and CPU time visual effects steal.

With 2Gigs of RAM you could easily disable swap memory too. I only have 1 gig and haven't maxed it out. Although, I am not a gamer. Nor do I run CAD or video editing. For those things you probably need swap memory.

BTW - VM should be virtual memory and physical memory should be RAM. Swap memory is hard disk space used as RAM, so it is essentially virtual memory functioning as physical memory. Swap memory is the Linux counterpart to Window's PageFile Memory.

---

### Post by krack3rz on 2010-08-03
~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012       1971         41          0        141        185
-/+ buffers/cache:       1645        367
Swap:         2137       1419        718

this isn't on startup data but still this is too much! All i got open is: 2 pdf, transmission (500-600 KB/s upload), mozilla firefox(32 tabs), google chrome (38 tabs, this inclusive) and 2 nautilus folders(same path)

currently,
Memory: 1.7GB (87.3%) of 2.0GB
Swap: 1.4 GB (68.0%) of 2.1


Highest wasters of resources:

Nautilus:: status:Sleeping Virtualmemory:1.5 GB cpu:10% memory:757.4 MiB
firefox-bin:: status:sleeping Virtualmemory:934.4MiB cpu:2% memory:135.3 MiB

---
I do have "Extra effects" enabled and have dual screen setup, video card is awesome so that should be ok, it is a Nvidia 275 GTX 768 MB (proprietary driver enabled)

also I have the following applets: Invest 2.30.0 (following 3 stocks), Indicator Applet 0.3.7, Clock 2.30.2 (with weather and seconds in time), and 20 shotcuts on panels (because of dual screens i have 2 individual ones - top and bot; cant drag items from one desktop to another though)

multiple icons on desktop, all my partitions there (cant get rid of them, and other random stuff: ~25 items)
no broadcasting stuffs like empathy on

before i completely switched to ubuntu from XP which is still have as a dual - i didnt have it that high, maximum of 500 MB RAM on startup with more than triple the icons i got here - load was of course slower xD

sorry i wrote so much, tryin to lay all on the table...please help!! ](*,)

---------
although i do have a home server running from this comp all the time the comp is on, though almost no1 ever visits so there is no traffic or usage

---

### Post by mcduck on 2010-08-03
So, you have 70 web pages open at the same time, and Transmissions running, and you wonder why you are using a lot of RAM? :D

Almost half of the RAM you are using is being used by Firefox only.

Also Nautilus tends to get a bit heavy if you have much stuff on the desktop. The drive icons aren't a problem but many actual files is. Especially if one or more of the files are changing over time, like a file being downloaded to the desktop etc.

I can't say anything about the memory usage on startup, for that you'll need to run "free -m" on startup, before you open loads of programs, and post the output here.

---

### Post by dcstar on 2010-08-03
> **mcduck said:**
> So, you have 70 web pages open at the same time, and Transmissions running, and you wonder why you are using a lot of RAM? :D
.........

There must come a time for threads like this when people stop treating them seriously.

Aren't there enough real problems posted in this forum to keep people busy?

---

### Post by mcduck on 2010-08-03
> **dcstar said:**
> There must come a time for threads like this when people stop treating them seriously.

Aren't there enough real problems posted in this forum to keep people busy?
Sorry if my answer doesn't please you, but it's still valid (and serious answer). Having a lot of stuff running will definitely mean high RAM usage, and web browsers are pretty famous for eating a lot of RAM when you have loads of pages open at the same time.

The only mistake in my post was that I mixed up the RAM usage of Firefox and Nautilus, which brings me to the other point (already mentioned in my above post), having lost of stuff on the desktop (Nautilus doesn't like that, it causes high RAM usage). And, like I said, Nautilus seems to really dislike it when something is constantly updating on the desktop, it causes Nautilus to try to thumbnail it over and over again.

I'm here to give help, and do my best to give good answers. That doesn't mean the answer is always what you were hoping for.

To get a better picture of the system's RAM usage, instead of all the programs that might be running on top of it, we really need the "free -m" output without loads of additional apps running.

edit: Never mind. I just realized I read your post as well. Probably I should take a break and get some more coffee to wake my brains up again... :D

---

### Post by krack3rz on 2010-08-03
i dont have anything downloading to my desktop, ever! the 2 nautilus folders i was talking about are the same dir and thats where stuff is being DLed but i wasnt downloading anything only uploading wen i posted "free -m".

most of the problems are from -->nautilus (today it was 1.6 GB!)<-- and other weird things,
java eats alot 700 virtual memory and ~400 MB memory - i wasnt using this at all (this java is an environment || its for a browser), also i have crashes in firefox(some random addon that never crashed before) and google chrome(flash plugin: libflashplayer.so ~60MB or RAM)

---

### Post by krack3rz on 2010-08-04
at startup i typed it:
~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012       1284        728          0        182        304
-/+ buffers/cache:        797       1215
Swap:         2137          0       2137

---

### Post by Mr_VeRiTy on 2010-08-04
I don't know about the other problems, but as for Java I think I can help. When I first installed Ubuntu I was using the open source version of Java, which tended to use wayyyy too much memory, even when I wasn't using anything that uses java, so I installed the Sun Microsystems version of Java by enabling the partner repositories (from System>Administration>Software Sources) and then entering 
```
sudo apt-get install sun-java6-jre
``` into the terminal, unless you are already using the Sun Microsystems version.

---

### Post by soldier1st on 2010-08-05
the high memory use would come from firefox and chrome as loading sites that use plugins would cause it to be high. in chrome you can see what pages take alot of memory but firefox not so, also nautilus sometimes like to leak memory but you can simply end it and it will close then reopen and your apps won't be affected and adding the other java is not needed normaly unless your running a java app that won't open in Openjdk.

---

### Post by Mr_VeRiTy on 2010-08-05
> **soldier1st said:**
> the high memory use would come from firefox and chrome as loading sites that use plugins would cause it to be high. in chrome you can see what pages take alot of memory but firefox not so, also nautilus sometimes like to leak memory but you can simply end it and it will close then reopen and your apps won't be affected and adding the other java is not needed normaly unless your running a java app that won't open in Openjdk.
Openjdk runs apps fine, but it uses a lot more memory to do so, at least in my experience, I might have just had a bad install. Once after using Openjdk, the memory usage was 200, and the CPU usage was 102, and that was *after* closing the java app and there was nothing else using it.

---

