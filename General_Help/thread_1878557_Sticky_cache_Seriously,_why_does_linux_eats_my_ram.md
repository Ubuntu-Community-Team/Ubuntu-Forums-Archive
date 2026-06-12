---
title: "Sticky cache: Seriously, why does linux eats my ram?"
date: 2011-11-10
forum: General Help
---

### Post by ah_mad on 2011-11-10
This guy:

[http://www.linuxatemyram.com/index.html](http://www.linuxatemyram.com/index.html)

tries to convince me that I can get back my memory that is used by cache anytime I need it and he proposes a test here:

[http://www.linuxatemyram.com/play.html](http://www.linuxatemyram.com/play.html)

Well, in my case, the test fails badly:

step 1:

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3015       2901        113          0         15       2282
-/+ buffers/cache:        603       2411
Swap:         2406       2406          0
```

So 2282MB is used by cache and 113MB is free.

Now:

```
$ ./munch
Allocated 1 MB
Allocated 2 MB
Allocated 3 MB
Allocated 4 MB
.
.
.

Allocated 265 MB
Allocated 266 MB
Allocated 267 MB
Allocated 268 MB
Allocated 269 MB
Killed
```

Ok, Linux gave me, generously another 156MB and that's it! But for god sake, I have 3GB of ram.

So, please tell me how I can claim my mem from this ram eater cache when I need it. This my uname:

$uname -a
Linux syd-laptop 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 15:27:15 UTC 2011 i686 GNU/Linux

I really appreciate if somebody shows me how can I tell Linux that my programs are more important than its cache, and when I nicely ask linux for mem, it is very rude of it to kill my program and clings to its cache with both hands.

Thank you very much indeed

---

### Post by dcstar on 2011-11-10
> **ah_mad said:**
> 
........
So, please tell me how I can claim my mem from this ram eater cache when I need it.
........

The Linux kernel automatically manages RAM use and uses **unused** RAM for file caching. When a process needs RAM it is automatically given it, and this function works very well so I don't know why you are complaining.

---

### Post by jocko on 2011-11-10
> **ah_mad said:**
> ```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3015       2901        113          0         15       2282
-/+ buffers/cache:        603       [COLOR=Blue]**2411**[/COLOR]
Swap: **[COLOR=Red]        2406       2406[/COLOR]**          0
```

So 2282MB is used by cache and 113MB is free.

Actually, since the cache is simply overwritten as soon as the operating system or some application actually needs to use more ram, you should ignore cache and instead look at the available memory: You had 2411 Mb free, easily accessible ram, just waiting to be used...

But, your swap is completely filled up, which should never happen in a situation where you still have that much available ram.

Let the kernel handle the memory usage. It is designed to work the way it does for a very good reason: Empty ram is wasted ram.

Did you not read the link you yourself posted? The script you used to "free up" memory is actually designed to FILL UP memory, as part of a demonstration of how trying to circumvent linux's memory and cache management actually is a BAD idea. It also clearly states that you need to inactivate swap, to avoid filling that up too (which will seriously slow your system down and make applications unstable, which I guess is what you mean when you say that rude linux kills your apps...)
The part of that demonstration that actually does what you seem to want is this:
```
$ echo 3 | sudo tee /proc/sys/vm/drop_caches
```
But re-read the page with the tutorial. It clearly shows which effects you would accomplish, and none of them are desirable...

---

### Post by ah_mad on 2011-11-10
Hi dcstar, I'm complaining because Linux is killing my applications, claiming "out of memory error." It sometimes kills chromium and sometimes gnome-power-management. And this is all because although I have 2411Mb free ram, Linux doesn't give it to me and starts killing applications.

This was an example to show the Linux cache  "MISmanagement" that while gives 2GB to cache doesn't give more than 260Mb to an application claiming out of memory.

---

### Post by ah_mad on 2011-11-10
Hi jocko,

Thank you very much for looking into my problem.

My problem is exactly with your very first sentence:
"since the cache is simply overwritten as soon as the operating system or some application actually needs to use more ram"

My problem is that the cache is NOT simply overwritten, as soon as my application "munch" actually needs to use more ram, instead Linux killed my application, claiming "out of memory." after asking for 260Mb of ram while more than 2GB of ram is kept hostage by cache.

I have checked the

echo 3 | sudo tee /proc/sys/vm/drop_caches

thingy. The first time it drops few MG of my 2GB cache and after that it doesn't do anything. This is exactly my problem I have 2GB of sticky cache that doesn't go away in any way.

---

### Post by Devilman13 on 2011-11-10
I have 2 Ubuntu machines (one 10.something other 11.10) running on 1 GB of memory.

One is running 3 or 4 servers 24/7.

The other (I'm on now) has empathy, firefox, thunderbird, xchat, GnomeMUD, X-term, and other things open and everything is fine. 73% of my RAM is in use and 6% of my swap is in use.

This thread doesn't make sense to me...

---

### Post by ah_mad on 2011-11-10
So basically based on what jocko and Devilman13 are saying, the root of the problem is that linux is insanely filling up my swap to suffocation point for no reason while I have so much "free" memory. (probably the strange cache behavior is a byproduct of the "full swap" situation, probably linux looks at the swap and see it's full and concludes that I'm out of memory).

If that is the case, my question is that how can I tell Linux to stop filling up the swap while I have still plenty of ram available.

Something that might shed some light: I have an ext3 ecryptfs partition. I heard that linux decrypts the whole thing at start up, could it be that encryptfs decrypted data somehow occupies the whole swap?

By the way thanks for all of your support.

---

### Post by ah_mad on 2011-11-10
So I thought one way to test the "full swap hypothesis", the jocko's idea

>  It also clearly states that you need to inactivate swap, to avoid filling that up too (which will seriously slow your system down and make applications unstable, which I guess is what you mean when you say that rude linux kills your apps...)

is to turn off and on the swap when it's too full:
```
$ free
             total       used       free     shared    buffers     cached
Mem:       3087664    1332388    1755276          0      45424     632420
-/+ buffers/cache:     654544    2433120
Swap:      2464520    1282628    1181892

# swapoff -a
# free
             total       used       free     shared    buffers     cached
Mem:       3087664    2498624     589040          0      49552    1559396
-/+ buffers/cache:     889676    2197988
Swap:            0          0          0

# swapon -a

```

But now I see something funny, immoderately after turnning the swap off, the size of cache increased from 632MG to 1559MG. This means that linux is storing the cache in the swap which seems to be nonsense at the first glance(if you are going to write the cache on disk, write it in the original place at the first place), but also it could be that because linux wants to minimum the amount of encryption/decryption.

But, this "cache in the swap" is saying something about my problem, the problem I think is that when I ask for memory, instead of dropping the cache, linux tries to write it in the swap and consequently makes such a mess. It could be that linux wants to avoid writing back encrypted data in any cost.

---

### Post by ah_mad on 2011-11-10
Ok, now I can confirm that the problem is the "swap" itself. With 

```
# swapoff -a
```

I was able to run lots of instances of chrome, firefox, opera and thunderbird and munch reached got 827Mb above all of them:

```

Allocated 822 MB
Allocated 823 MB
Allocated 824 MB
Allocated 825 MB
Allocated 826 MB
Allocated 827 MB
Killed

```

So, this is what's happening: 

If I have swap then linux tries to move the cache to the swap and then swap gets full, then linux halts the whole operation instead of dropping the cache. This results in "out of memory". But without swap, Linux knows that it has no hope but dropping the cache in the first place.

So, this is a bug in linux kernel (mine is 2.6.32-35 it might be solved in newer versions), but still I'm wondering why should linux move the cache to the swap in the first place, is because of encryptfs?

Meanwhile, I'm shutting down the swap completely. It's better to have lower performance rather than being deprived of my own RAM.

---

### Post by philinux on 2011-11-10
I only have 2 gig RAM and swap never gets used. Have you tweaked any swap settings at all?

E.g swappiness

---

### Post by stinkeye on 2011-11-10
What's your current swappiness?
I use 10.

This is from the SwapFaq Community info page [**_[COLOR="DarkRed"]What is swappiness and how do I change it?[/COLOR]_**]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F")
To check the swappiness value 
```
cat /proc/sys/vm/swappiness
```

To change the swappiness value A temporary change (lost on reboot) with a swappiness value of 10 can be made with 
```
sudo sysctl vm.swappiness=10
```

To make a change permanent, edit the configuration file with your favorite editor: 
```
gksudo gedit /etc/sysctl.conf
```

Search for vm.swappiness and change its value as desired. If vm.swappiness does not exist, add it to the end of the file like so: 
```
vm.swappiness=10
```

Save the file and reboot.

---

### Post by dcstar on 2011-11-12
> **Devilman13 said:**
> I have 2 Ubuntu machines (one 10.something other 11.10) running on 1 GB of memory.

One is running 3 or 4 servers 24/7.

The other (I'm on now) has empathy, firefox, thunderbird, xchat, GnomeMUD, X-term, and other things open and everything is fine. 73% of my RAM is in use and 6% of my swap is in use.

**This thread doesn't make sense to me.**..

It may make sense if we eventually find out that various non-standard things have been done to the OP's system to "improve" it.

Most people who don't stuff around with their Ubuntu systems have few problems, it is those that decide to alter things (and usually don't reveal these changes until heaps of time has been wasted) that have weird issues like this.

---

### Post by ah_mad on 2011-11-20
Some new "non-updates" on the problem. I thought it might be that the encryptfs doesn't work very well with ext3 file systems (I think I read it somewhere) anyway, I migrated ext4 but I didn't see any visible improvement.

Still I think, the problem is with the encryption, because unlike normal fs, when you deal with encryptfs you need to run AES cipher on all the cache data before they are written to the disk, hence it takes beyond linux estimate to write the data back. I'm going to play with swappiness but if didn't solve the problem, I'll get rid of encryption and see if it solves the problem or not.

---

### Post by ah_mad on 2011-11-20
> **stinkeye said:**
> What's your current swappiness?
I use 10.

This is from the SwapFaq Community info page [**_[COLOR="DarkRed"]What is swappiness and how do I change it?[/COLOR]_**]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F")
To check the swappiness value 
```
cat /proc/sys/vm/swappiness
```

To change the swappiness value A temporary change (lost on reboot) with a swappiness value of 10 can be made with 
```
sudo sysctl vm.swappiness=10
```

To make a change permanent, edit the configuration file with your favorite editor: 
```
gksudo gedit /etc/sysctl.conf
```

Search for vm.swappiness and change its value as desired. If vm.swappiness does not exist, add it to the end of the file like so: 
```
vm.swappiness=10
```

Save the file and reboot.
Stinkeye,

Thank you very much about your advice on swappiness. I don't think I had done any permanent change to it before. This was my first attempt to apply the change it didn't make much different the first time, obviously because swap was already full and even swapoff -a couldn't empty:

> 
$ cat /proc/sys/vm/swappiness 
60
$ ./munch 
Allocated 1 MB
Allocated 2 MB
.
.
.
Allocated 254 MB
Allocated 255 MB
Allocated 256 MB
Killed
$ free
             total       used       free     shared    buffers     cached
Mem:       3087664    2852208     235456          0       5972    2221480
-/+ buffers/cache:     624756    2462908
Swap:      2464520    2464464         56

$ sudo sysctl vm.swappiness=10
vm.swappiness = 10
$ ./munch 
Allocated 1 MB
Allocated 2 MB
.
.
.
Allocated 282 MB
Allocated 283 MB
Allocated 284 MB
Allocated 285 MB
Killed

$ sudo sysctl vm.swappiness=0
vm.swappiness = 0
$ ./munch 
Allocated 1 MB
Allocated 2 MB
.
.
.
Allocated 273 MB
Allocated 274 MB
Allocated 275 MB
Killed
$ free
             total       used       free     shared    buffers     cached
Mem:       3087664    2783152     304512          0        720    2171168
-/+ buffers/cache:     611264    2476400
Swap:      2464520    2464520          0

$sudo swapoff -a
swapoff: /dev/sda5: swapoff failed: Cannot allocate memory



But after restarting it basically stop the swap usage:
> 
$ free
             total       used       free     shared    buffers     cached
Mem:       3087664    2871036     216628          0      48524    1790152
-/+ buffers/cache:    1032360    2055304
Swap:      2464520          0    2464520


I'll update the thread in a week about the result of decreasing swappiness.

---

### Post by ah_mad on 2011-11-25
OK, as I promised, here is the update:

swappiness = 10 (vs original 60) kind of helped. I haven't restarted my machine since I posted last \
post which was four days ago. Eveything was pretty nice but I observed that the swap started to fill\
 up little by little and I think part of the problem is that no matter how many applications I close\
, it doesn't go down. Anyway, just before writing this message, finally it got full and few of my pr\
ograms crashed, for the same old out of memory situation.

So, now I changed my swappiness to 0, to see if I give me a better result or not. Better or not, it \
doesn't change the fact that it's a crappy situation. I mean kernel shouldn't be that dumb. Maybe, I\
'll report it as a bug in near future.

---

### Post by stinkeye on 2011-11-25
Before you start writing up bugs you might want to make sure it's not
your playing around or hardware that has caused the problem.
With 2 Gbs of ram and swappiness of 10 I've never seen the swap partition being used.

---

### Post by dcstar on 2011-11-26
> **stinkeye said:**
> Before you start writing up bugs you might want to make sure it's not
your playing around or hardware that has caused the problem.


You mean like the encrypted partitions and probably more things that the OP hasn't yet mentioned?

As I mentioned previously, we probably have a system that has been "improved" and we most likely haven't been told half the non-standard changes made to this system, so trying to diagnose an issue like this is pretty much a pointless waste of time until the OP admits all the "improvements" that have changed the install from the standard setup.

---

### Post by ah_mad on 2011-11-28
The problem appeared pretty much the first few days I installed Lucid. That was the reason why I went and bought an extra GB of ram in a false hope that it will solve the problem. I pretty much followed the standard installation and didn't install any extra driver. (I used to install hdapsd manually but I think this time it was installed automatically) The installation process itself asked me if I like that my home directory be encrypted. I didn't know much about swappiness, dropcache, etc. I'm using Linux since 2003 and I never touched these stuff till now that the system started killing my apps.

Anyway, it's funny that kernel doesn't give a damn about the fact that "swappiness = 0":

> 
~$ cat /proc/sys/vm/swappiness 
0
~$ free
             total       used       free     shared    buffers     cached
Mem:       3087664    2472920     614744          0     237456    1270224
-/+ buffers/cache:     965240    2122424
Swap:      2464520    2440072      24448


---

### Post by ah_mad on 2011-12-07
I found people having exactly the same problem as mine:

[http://serverfault.com/questions/171164/can-you-set-a-minimum-linux-disk-buffer-size]("http://serverfault.com/questions/171164/can-you-set-a-minimum-linux-disk-buffer-size")

and

[http://askubuntu.com/questions/41778/computer-freezing-on-almost-full-ram-possibly-disk-cache-problem]("http://askubuntu.com/questions/41778/computer-freezing-on-almost-full-ram-possibly-disk-cache-problem")

The second one offers the solution:

> sysctl -w vm.min_free_kbytes=65536

I'm going to give it a shot. It will probably helps with not letting my system freeze but still the stupid sticky behavior of the cache remains unexplained.

---

### Post by ah_mad on 2012-01-05
UPDATE:
Got rid of encryption. I can't say it was cured totally but it got lot better. Without encryption, with addition of all the other cures that stuff that I applied (swapinness, telling the cache to **** off for the last 128MB of ram,...) kept him going for:

> ~$uptime
 11:46:55 up 13 days, 13:26,  2 users,  load average: 1.49, 0.92, 0.62

But I don't say it's prefect. Still I think there's bug there. I'm going to buy another GB.

---

### Post by ah_mad on 2012-01-23
More updates: If I run my "munch" as root, kernel shows more respect and suddenly clear up the whole cache, although it kills few apps on the way including nm-applet, gnome-power-management, my browser,... . So remember to save everything before going for this option.

---

