---
title: "Too much swap being used"
date: 2010-05-09
forum: General Help
---

### Post by nitstorm on 2010-05-09
Hi all,

(Note: I've already checked the forums and google but nothing seems to work hence this new thread)[I]

Problem:[/I]
Way too much swap is being used although most of the RAM is free.

*What I've Tried:*
1. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
    - Tried changing the vm.swappiness(the temporary solution that is lost on reboot),no use
    - The swap2ram.sh didn't work (gives the "not enough RAM" error although there is enough memory)

*Stats:*
[B]uname -a:
[/B]```

Linux nits-desktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

```
[B]
free -m:
[/B]```

nits@nits-desktop:/usr/sbin$ free -m
             total       used       free     shared    buffers     cached
Mem:          2003       1941         61          0         25       1476
-/+ buffers/cache:        439       1563
Swap:         2548       1033       1514

```

[B]cat /proc/sys/vm/swappiness
[/B]```

nits@nits-desktop:/usr/sbin$ cat /proc/sys/vm/swappiness
10

```

**cat /proc/swaps**
```

nits@nits-desktop:/usr/sbin$ cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/ramzswap0                          partition    512792    488768    100
/dev/sda6                               partition    2096440    569832    -1

```

[B]error while executing swap2ram.sh:
[/B]```

nits@nits-desktop:/usr/sbin$ sudo swap2ram.sh
-e not enough RAM to write swap back, nothing done

```
More than happy to provide you with whatever more info required. Please do help. Thanks. Cheers!

---

### Post by nitstorm on 2010-05-09
Sorry folks, just got my head outta my a** and noticed that a lot of memory was being cached. but still isn't this high swap usage???

---

### Post by ibuclaw on 2010-05-09
How long have you been logged in / system uptime?
```
date; who; uptime
```
Does dropping caches help?
```

free -m
sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
free -m

```
free -m will take a note of memory usage before and after the command.

Regards
Iain

---

### Post by nitstorm on 2010-05-09
> **ibuclaw said:**
> How long have you been logged in / system uptime?

```
date; who; uptime
```

```

Sun May  9 19:11:02 IST 2010
nits     tty7         2010-05-09 08:45 (:0)
nits     pts/0        2010-05-09 12:38 (:0.0)
nits     pts/1        2010-05-09 19:10 (:0.0)
 19:11:02 up 10:25,  3 users,  load average: 0.07, 0.02, 0.00

```I have run the system for 4 days and all earlier( that was the longest before there was a power-cut) but it was running pretty ok with just very very little swap being used.

> 
Does dropping caches help?
 	Code:
 	free -m
sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
free -m 


I don't think so...
```

nits@nits-desktop:~$ free -m 
             total       used       free     shared    buffers     cached
Mem:          2003       1937         66          0         27       1435
-/+ buffers/cache:        473       1529
Swap:         2548       1033       1514
nits@nits-desktop:~$ sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
[sudo] password for nits: 
3
nits@nits-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2003        728       1274          0          1        265
-/+ buffers/cache:        461       1541
Swap:         2548       1033       1514

```

---

### Post by john newbuntu on 2010-05-09
Turn off swapping on ramzswap0 device (swapoff /dev/ramzwap0) and see if it is any better since you already have a 2GB RAM.

---

### Post by nitstorm on 2010-05-09
> **john newbuntu said:**
> Turn off swapping on ramzswap0 device (swapoff /dev/ramzwap0) and see if it is any better since you already have a 2GB RAM.
```

nits@nits-desktop:~$ sudo swapoff /dev/ramzwap0
[sudo] password for nits: 
swapoff: /dev/ramzwap0: swapoff failed: No such file or directory

```

---

### Post by ibuclaw on 2010-05-09
> **nitstorm said:**
> 
i don't think so...
```

nits@nits-desktop:~$ free -m 
             total       used       free     shared    buffers     cached
mem:          2003       [COLOR="red"]1937[/COLOR]         [COLOR="Red"]66[/COLOR]          0         27       [COLOR="red"]1435[/COLOR]
-/+ buffers/cache:        473       1529
swap:         2548       1033       1514
nits@nits-desktop:~$ sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
[sudo] password for nits: 
3
nits@nits-desktop:~$ free -m
             total       used       free     shared    buffers     cached
mem:          2003        [COLOR="Red"]728[/COLOR]       [COLOR="red"]1274[/COLOR]          0          1        [COLOR="red"]265[/COLOR]
-/+ buffers/cache:        461       1541
swap:         2548       1033       1514

```

Highlighted important bits.

Looks like it free'd up caches successfully.
You should now be able to turn swap off and back on again to move it back into memory.

```

sudo swapoff -a
sudo swapon -a

```
Now that is the workaround sorted.

As for the real questions... What applications do you use most?
*Something* is eating your system cache significantly for you to run that low on memory...

---

### Post by nitstorm on 2010-05-09
Thanks ibuclaw , that worked :D  

I somehow expected it to magically move the applications from swap to RAM once the cache was cleared, LOL. Also gonna run it for around 12 or so hours just in case the swap starts acting funny again. If the problem doesn't arise will mark the thread solved then. Hope that's ok..

My frequently used programs are :
1. Firefox( I keep watching videos freaking most of the time)
2. quodlibet
3. vlc
4. rtorrent
5. conky
6. cairo-dock

here is a top just in case:
```

top - 22:21:32 up 13:36,  3 users,  load average: 0.01, 0.31, 0.42
Tasks: 155 total,   2 running, 153 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.9%us,  2.5%sy,  0.0%ni, 88.7%id,  0.8%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2051192k total,  1982556k used,    68636k free,     9612k buffers
Swap:  2096440k total,     1152k used,  2095288k free,  1404180k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7617 nits      20   0  484m 126m  37m S   39  6.3  17:44.29 firefox ##(watching a video )           
  995 root      20   0 75284  21m  10m S    6  1.1  17:18.97 Xorg               
 1624 nits      20   0 14476 2084 1092 S    2  0.1   4:22.27 conky              
10449 nits      20   0  2468 1068  784 R    2  0.1   0:00.01 top                
    1 root      20   0  2508 1148  788 S    0  0.1   0:00.87 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.28 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.51 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.20 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.46 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 netns        

```

---

### Post by itsjareds on 2010-05-09
Have you been using Lucid since the betas? I had the same issue which turned out to be an Xorg memory leak. I had to add the Xboot PPA to my sources and run `apt-get dist-upgrade` which installed a testing version that fixed the issue.

I believe this was the bug report:

[Bug #565981]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/565981")

---

### Post by nitstorm on 2010-05-09
> **itsjareds said:**
> Have you been using Lucid since the betas? I had the same issue which turned out to be an Xorg memory leak. I had to add the Xboot PPA to my sources and run `apt-get dist-upgrade` which installed a testing version that fixed the issue.

I believe this was the bug report:

[Bug #565981]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/565981")

Nope. Using Karmic. I dual boot with a Lucid Beta 2 though, but I don't think that's the problem right? Also I never saw Xorg in my top this often before a couple of days, that's when this started. Today it just grew too big and so I decided to post here.

---

### Post by dino99 on 2010-05-09
seems to me that your swap is installed into a file, not a partition

---

### Post by nitstorm on 2010-05-09
> **dino99 said:**
> seems to me that your swap is installed into a file, not a partition

I do have a swap partition. I didn't have this problem until a few days back. 
```

[B]sudo fdisk -l | grep swap:
[/B]/dev/sda6           10445       10705     2096451   82  Linux swap / Solaris

```

---

### Post by ibuclaw on 2010-05-09
> **dino99 said:**
> seems to me that your swap is installed into a file, not a partition
I did not notice that before... good catch. ;)
> **nitstorm said:**
> **cat /proc/swaps**
```

nits@nits-desktop:/usr/sbin$ cat /proc/swaps
Filename                Type        Size      Used     Priority
/dev/ramzswap0          partition   512792    488768   100
/dev/sda6               partition   2096440   569832   -1

```


@nitstorm, What does your /etc/fstab file look like?

---

### Post by dino99 on 2010-05-09
> **nitstorm said:**
> I do have a swap partition. I didn't have this problem until a few days back. 
```

[B]sudo fdisk -l | grep swap:
[/B]/dev/sda6           10445       10705     2096451   82  Linux swap / Solaris

```

ok you have a swap partition, but what about this one: 

/dev/ramzswap0          partition   512792    488768   100

of course ubuntu will always use this one before the swap partition, so remove it and i think your trouble will desappear ( take care to look into that "ramzwap0" before removing it in case

---

### Post by nitstorm on 2010-05-09
> @nitstorm, What does your /etc/fstab file look like? 	

```

nits@nits-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=98959f16-78fc-45bd-980e-81490bed30c7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=0dc51ee0-9432-44a6-9ca3-b9cacf5c9769 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sda10
UUID=343af808-9da1-4cb4-a39d-433bb9d8bbaa /media/Storage ext4 defaults 0 2
#/dev/sda9
UUID=f61c5279-aae5-47b1-b7ee-24bc53a34036 /media/Vault ext4 defaults 0 2

```
Checked the UUID of the swap. Looks good to me so far. Also had to reboot the system. Been running for 2hours so far and none of the swap is being used. Will post back on how things go.

---

### Post by nitstorm on 2010-05-10
Have my  comp running for just 2 hours this morning and this is my [I]free -m:
[/I]```

             total       used       free     shared    buffers     cached
Mem:          2003       1929         73          0         19       1534
-/+ buffers/cache:        375       1627
Swap:         2548        406       2141

```

and how do i disable the ramzswap0???

---

### Post by dino99 on 2010-05-10
> **nitstorm said:**
> Have my  comp running for just 2 hours this morning and this is my [I]free -m:
[/I]```

             total       used       free     shared    buffers     cached
Mem:          2003       1929         73          0         19       1534
-/+ buffers/cache:        375       1627
Swap:         2548        406       2141

```

and how do i disable the ramzswap0???

a better question is: how have you created it ? in any case this have not been created by a genuine ubuntu process, so its your job i guess, no need to complaint and whine :mad:

check the good path and wording, then tweak if necessary: sudo rm -rf /dev/ramzswap0

sudo dpkg --configure -a
sudo update-initramfs -u

---

### Post by nitstorm on 2010-05-10
> **dino99 said:**
> a better question is: how have you created it ? in any case this have not been created by a genuine ubuntu process, so its your job i guess, no need to complaint and whine :mad:

I have no idea how that got created. Looking into google and other threads for a solution.

---

### Post by lavinog on 2010-05-10
[How to remove Compcache](http://ubuntuforums.org/showthread.php?p=7268741)

---

### Post by lavinog on 2010-05-10
> **dino99 said:**
> a better question is: how have you created it ? in any case this have not been created by a genuine ubuntu process, so its your job i guess, no need to complaint and whine :mad:


[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/328437/](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/328437/)
It looks like installing remastersys might be causing this issue.

---

### Post by dino99 on 2010-05-10
> **lavinog said:**
> [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/328437/](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/328437/)
It looks like installing remastersys might be causing this issue.

good point :P

new uptodated remastersys:

echo "deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install remastersys

---

### Post by john newbuntu on 2010-05-10
ramzswap appears to be "A RAM based block device which acts as a swap disk.  Pages swapped to this disk are compressed and stored in memory itself." (Thanks to Google).  Here's a link from another forum on how it can be removed(see post 13):
[http://crunchbanglinux.org/forums/topic/477/solved-location-of-swap-file/](http://crunchbanglinux.org/forums/topic/477/solved-location-of-swap-file/)

---

### Post by nitstorm on 2010-05-10
> **lavinog said:**
> [How to remove Compcache]("http://ubuntuforums.org/showthread.php?p=7268741")

I was looking at that exact thread actually :D Post #9 solved it so for future reference i am posting the link to that single post here. [http://ubuntuforums.org/showpost.php?p=8966639&postcount=9](http://ubuntuforums.org/showpost.php?p=8966639&postcount=9) 
So, that removed ramzswap0 after the reboot.

> It looks like installing remastersys might be causing this issue. 	
Dang!!! I do have remastersys installed!!! 

Thanks a lot everyone, but still gonna wait a while before I mark the thread solved. Cheers!

---

### Post by dino99 on 2010-05-10
look back to post #17 (updated) before reboot :P

---

### Post by nitstorm on 2010-05-10
> 
look back to post #17 (updated) before reboot :razz:


Shoot I missed that then I guess, but ramzswap0 is gone. Already ran the *update-initramfs -u -k 'uname -r'  *so should I run the *dpkg --configure -a  *now?? I am confused. 

Also after the reboot everything was fine for a few minutes and then the swap started filling up like crazy. And I thought I'd let the system run for a while, see if that sorted the problem out, but it hasn't. The swap usage has pretty much been the same since it spiked suddenly.( if this is important there was some program called *collector *that was on the top of the chart in *top* when the swap usage was spiking, i ran *which collector  *returned nothing, ran *locate collector *which returned */lib/bootchart/collector, *got three other returns but they had the word collector in them, this was the only thing that had just the word collector in it)

here are my stats now:
[B]sudo swapon -s:
[/B]```
Filename                Type        Size    Used    Priority
/dev/sda6                               partition    2096440    636240    -1

```
**free -m:**
```

             total       used       free     shared    buffers     cached
Mem:          2003       1941         61          0         27       1681
-/+ buffers/cache:        232       1770
Swap:         2047        621       1425

```
Wondering if I should keep clearing the cache everytime swap usage spikes? Would that be the proper solution to this? Or is a re-install the ultimate answer? 

Damn!! Talking way too much, gonna shut up now :P and thanks for the help guys(for uptil now and in advance...)

---

### Post by lavinog on 2010-05-10
you can use this to show the full path names
```

ps auxf|less

```

---

### Post by nitstorm on 2010-05-29
Just updated to Lucid Lynx yesterday and I don't seem to have the memory leak problem so far, I've just let the machine run for a few hours like 4 or 5 hours at a stretch due to the very frequent power outages we have here but during that time no mem leaks. I still do ***sudo sysctl vm.swappiness=0  ***every time I boot,just in case. lolz

Anyways thanks a lot for the help guys. Gonna mark this thread solved I guess. Cheers!

---

### Post by crazy ivan on 2011-03-12
Hi there, I have a somewhat related problem:

I have 4GB ram installed, due to onboard graphic card I do not have it all available:

```

free -m
             total       used       free     shared    buffers     cached
Mem:          3388       2789        599          0         54        853
-/+ buffers/cache:       1881       1507
Swap:         5857          0       5857

```.

Anyhow, no matter how much RAM i put inside, I always end up swapping, since I really use that device ;)

So I thought about an automation to write back swap.. I thought about wirting a modification of swap2ram from [https://help.ubuntu.com/community/SwapFaq#Empty%20Swap]("https://help.ubuntu.com/community/SwapFaq#Empty%20Swap") and making it repetetive via "sudo crontab -e"

```

#!/bin/sh
err="not enough RAM to write swap back, nothing done"
mem=`free|grep Mem:|awk '{print $4}'`
swap=`free|grep Swap:|awk '{print $3}'`
log="/home/user/.custom.log"
echo "`date`"" : Checking swap state" >> $log
test $mem -lt $swap && sync
sleep 1
test $mem -lt $swap && echo -e $err >> $log; touch /home/user/.swap_warning && exit 1
swapoff -a && swapon -a && rm /home/user/.swap_warning; exit 0 

```

I thought it would be nice to keep a history in "/home/user/.custom.log" and a warning file in "/.swap_warning", that i could monitor lets say via another cron job that notifies me when I reached the limit ("notify-send 'Close those windows!'" :).

So what do you think: is there an easier / existing solution??

---

### Post by lithopsian on 2011-03-12
Having a swap file is not a problem.  No reason not to, and several reasons why it might be a good idea.  Don't just disable a swap file because some google jockey read an article from the last century and thinks it is a bad idea.  The only really good reason I can think of for having a swap partition these days is to share it between different Linux installations on the same machine rather than having a 2GB file sitting on every one of them.  Swap files are much more flexible and perform just as well.

Same with compcache (ramzswap).  It is generally quite a useful form of swap even if you don't understand exactly what it does.  Exactly what it does is compress pages that would otherwise be swapped out to your hard drive and then writes them into memory.  This means that when you need to read pages back from swap they are available relatively quickly instead of extremely slowly from a hard drive.  Any significant number of reads from swap on a hard drive absolutely kills your system, while compcache allows it to continue at usable speeds.   This allows you to run with a quite aggressive swappiness setting without the risk of over-swapping and killing your system.  Overall performance should improve in most situations.  The downside is that by definition your memory is full when pages are being written to swap, so writing even more stuff into memory tends to increase the amount of swap used quite quickly.  The default settings of compcache at 15% of your RAM means that less than 10% of RAM will ever be used for those compressed pages.  Compcache reports the uncompressed swap size which can look quite scary of you think it is taking that much memory, but the compression ratio is typically near 4:1.  In practice this means a gradual decrease in performance as swap is used rather than hitting a brick wall.   I suggest you enable it again, and with 2GB of memory perhaps even increase the size to 30% or 40%.  And try not to be scared when your system is always showing 100MB of swap or more, it is a good thing.

---

### Post by lithopsian on 2011-03-12
> Anyhow, no matter how much RAM i put inside, I always end up swappingIt's intentional!  Don't try to rewrite Linux because you think swap is a bad idea.  Linux will always use all your RAM after a certain amount of time.  It is designed to cache all your disk activity and sooner or later that means all your memory will be in use.  Then it will start to swap out pages it thinks are unused and it is quite heavily slanted towards swapping out application memory.  Within reason this works well because most applications have a chunk of memory that they never use or only use once at startup, so you just don't need that.  The disk cache pages will be clawed back whenever an application needs more memory so they never hurt you.  The only pain comes when so many pages get swapped out that you actually need some of them.  Getting them back from disk is deathly slow and you will know when it happens.  Only then should you worry.

I very much doubt that your memory card has anything to do with this.  Graphics memory use for normal 2D desktop activities is maybe 4MB.  Maybe you have a huge virtual desktop or several wokspaces?  I'll give you 20MB.  Maybe you are using a brand new browser with hardware acceleration, so perhaps doublt that.  It is nothing compared to your 4GB.  Only major 3D gaming will use big chunks of memory and typically graphics cards sharing system memory are just too slow for you to want to use hundreds of MB of it.

---

### Post by crazy ivan on 2011-03-13
> **lithopsian said:**
> It's intentional!  Don't try to rewrite Linux because you think swap is a bad idea.  Linux will always use all your RAM after a certain amount of time.  It is designed to cache all your disk activity and sooner or later that means all your memory will be in use.  Then it will start to swap out pages it thinks are unused and it is quite heavily slanted towards swapping out application memory.

Thank you very much for this enlightening post, lithopsian! We never went into detail about swap in UNIX class, so I learned nothing about cache. Only "swap is slow" got stuck in my head. 

However, with 3 GB Ram running Eclipse, firefox and some other apps and no hardware video acceleration the system was virtually unusable. Now with for 4GB it runs smoothly even though swap gets populated after a while (as you said it should).. Only problem: If I now start something resource intensive (compilation, apt..) system gets unusable again, except if I run "swap2ram" prior to that. So I guess I'm stuck in a dilemma:
Dropping the caches periodically will result in a poorer average performance, while saving me from running into freezing windows, when I do some really necessary hard work..

> **lithopsian said:**
> 
I very much doubt that your memory card has anything to do with this.  Graphics memory use for normal 2D desktop activities is maybe 4MB.  Maybe you have a huge virtual desktop or several wokspaces?  I'll give you 20MB.  Maybe you are using a brand new browser with hardware acceleration, so perhaps doublt that.  It is nothing compared to your 4GB.  Only major 3D gaming will use big chunks of memory and typically graphics cards sharing system memory are just too slow for you to want to use hundreds of MB of it.


When I had 3GB installed the system showed me 2,9 GiB, now with 4 installed it shows 3,3 GiB.. Seems really weired to me.. I might have to reboot and check BIOS. Anyhow I use two viewports (workspaces) at 2704x1050, which is more than my on-bord card can handle (no compositing), so the entire graphics is running on CPU and RAM, I guess. Also I use firefox with foxtab.

---

### Post by lithopsian on 2011-03-13
Depending on configuration, some video cards will grab a bunch of memory in advance.  Look in your BIOS for the memory reserved to the video card and also look in Xorg.0.log to confirm the "stolen" memory.  100MB or so is a believable chunk but I can't imagine it would take 700MB.  Don't be afraid to reduce the size to maybe 16MB or 8MB, which is plenty for a typical desktop.  The card will then take more if it needs it.  If you reduce it too far your X won't start and you'll have to reboot and tweak the BIOS setting a little higher.

Interesting that you say your displays are running in RAM and on CPU.  Obviously they are going through the graphics card at some stage to reach the monitor.  Even that size of display should, off the top of my head, only need about 16MB.  Certainly no more than 32MB.  Your card can surely address that much space, although obviously it will be main memory.  Just because it is main memory doesn't mean the CPU is doing the donkey work.  The whole point of the integrated graphics cards is that they can directly address main memory for video purposes.  Does your card have any onboard RAM at all?  Again, check the X log to see how much memory it is grabbing up front.  Also take a look at the memory use of X itself which may be quite large with those displays.

Do you still have your compcache disabled?  It should allow a more graceful recovery from having some swapped pages that you need to get back.  Instead of having to read 100MB from disk, which takes seconds, you just have to decompress 30MB from memory which takes milliseconds.  You can also adjust the swappiness kernel parameter if you absolutely feel that your system is just swapping out too many useful pages.  It can be set for the current session by editing the /proc/sys/vm/swappiness file, and you can set it permanently in /etc/sysctl.conf or in a file in /etc/sysctl.d.  The default is 60 which really is quite aggressive, but usually works OK with some compressed swap.  0 means don't swap out application pages at all when you can get rid of cache buffers instead.  Lower values will give you a desktop which is less likely to suffer serious delays from retrieving swapped pages but overall will perform slightly less well due to fewer disk cache hits.

Lastly, take a careful look through dmesg output and make sure that your system is correctly addressing all the 4GB that you have.  You may be able to see where some of it is going missing.  Programs, and Firefox in particular, will use more RAM when it is available.  You might find that you get better results by running fewer applications at a time, and certainly fewer at the same time as your browser.  You may also try to restrict the amount of RAM that Firefox is allowed  to grab if it isn't going to be the only application running.

---

### Post by SeijiSensei on 2011-03-13
> **crazy ivan said:**
> When I had 3GB installed the system showed me 2,9 GiB, now with 4 installed it shows 3,3 GiB.. Seems really weired to me.

You need to be running a 64-bit kernel to use RAM above 3 GB efficiently.  There's a workaround called "[PAE]("https://help.ubuntu.com/community/EnablingPAE")" for 32-bit systems.  If you have 4 GB RAM on a 32bit system, you should be using a "-pae" kernel.  What does "uname -a" report?  If you have a 64-bit processor, you should consider installing a 64-bit version of Ubuntu instead.

---

### Post by crazy ivan on 2011-03-13
Sure I have 64bit
```

uname -a
Linux ~ 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 GNU/Linux

```
The whole point of installing it was too be able to use 4GB and get out of the swap business. (Was thinking its kind of safe now, but I already ran into some thunderbird plug-ins not yet providing 64bit executables..).

All the advices by lithopsian seem very reasonable.. But concerning using less apps at a time: I have some knowledge of keyboard shortcuts / mouse gestures and very multitasking habits, always working on other stuff while an app is loading / compiling, so a normal Win XP, Vista or 7 just crashes after some minutes, regardless of hardware, if I try to work with it. I think, 

* self-conditioning by issuing warning messages once swap+RAM is starting to fill up 
* a lower swappiness value 
* auto-executing killing of "pure display" apps (evince,  etc..) and swap2ram once the swap file is bigger than, lets say, 500 Mb, 

should solve my problems of RAM hunger :twisted: Also I really consider limiting firefox and using compcache, as a further improvement..

Concerning memory "loss": I think I have to go to BIOS again, but too many windows open and configured to reboot at the moment ;)  I found these lines in /var/log/Xorg.0.log. D

```

...
[    19.002] (--) PCI:*(0:0:2:0) 8086:27a2:103c:30b1 rev 3, Mem @ 0xf4600000/524288, 0xe0000000/268435456, 0xf4680000/262144, I/O @ 0x00004000/8
[    19.002] (--) PCI: (0:0:2:1) 8086:27a6:103c:30b1 rev 3, Mem @ 0xf4700000/524288
...
[    19.630] (==) intel(0): VideoRam: 262144 KB
...

```

Seems like the 200 Mb that were "missing", with 3GB installed.. I also did "memtest" at the last boot up and found the puzzling number of 3,5 GB RAM installed. Looks like 0.5 GB of my RAM is either broken or not recognized by BIOS. Together with the 200 for the graphic card one can explain the 700 missing..

Now for hardware acceleration: I have an Intel 945 mobile with only shared memory and you're right: I don't know exactly, what happens, when metacity runs without hardware acceleration, i.e. w/o compositing in my case. Only thing I realize is that things (window-movements,videos..) run much smoother with "metacity -c" (on smaller screens or stronger graphic cards). So I guess some more work is really passed over to the GPU in that case.

---

### Post by lithopsian on 2011-03-13
The VideoRam line is not necessarily meaningful.  It probably just corresponds to your AGP aperture and will effectively be a limit on the amount of RAM you card can use.

The relevant line would be something like:
```
(II) intel(0): detected 3964 kB stolen memory.
```This is from an Intel 865G card very similar to use, but with the BIOS specially adjusted to grab as little memory as possible up front (for a single 1280x1024 display).  You would probably need more to support your displays.

Make sure you have newish drivers (say x_x_video_intel 2.90 or higher) because the older ones use a memory mapping method that has to grab a lot more memory because it is too inefficient at reallocating memory on the fly.

---

### Post by crazy ivan on 2011-03-13
Let me explain why I still haven't given up at rewriting linux:

Let's say I compile a large project or call rsync to run a backup. What happens is a lot of harddisk activity that is cached until it fills the RAM. So now linux decides what to put into swap: Since evidently I can't keep all my open application as busy as the "rsync" command is on its own, the kernel will start to think, that my applications are not as important and hence start putting their new data into swap instead of reducing the cache.. Hence all my other programs start to hang. 

I see that this kernel setting is good for making the resource-consuming program run as fast as possible (although in the case of rsync I doubt that this caching is good for anything!) but that is more important for a server or a work-station. For me on a single-user machine the most important thing is to keep the load down and ensure a fluent desktop experience, because I don't want to sit and wait before the compilation finishes, and on the other hand I usually don't care if it takes 5 or 6 minutes.  

So I rewrote swap2ram into this version
```

#!/bin/sh
mem=`free|grep Mem:|awk '{print $4}'`
cached=`free|grep Mem:|awk '{print $7}'`
swap=`free|grep Swap:|awk '{print $3}'`
log="/home/user/.custom.log"
load=`cat /proc/loadavg | awk '{print $1}'`
err="ERROR : not enough RAM to write swap back, nothing done"
cache_warning="WARNING : Excessive caching. Dropping caches"
swap_warning="WARNING : Excessive swapping. Suggesting to close  applications"
swap_note="WARNING : Excessive swapping. Closing read-only applications and writing back swap"
good_swap=100000
warn_swap=200000
bad_swap=300000
limit_cache=500000
critical_load=1.0
loaded=`echo "$load > $critical_load" | bc` #bc: true=1, false=0

test $loaded -eq 0 && exit 0
test $swap -lt $good_swap && exit 0
test $swap -lt $warn_swap && exit 0
echo "`date` "$swap_warning >> $log 
test $cached -gt $limit_cache && echo "`date` "$cache_warning >> $log && sync; echo 3 > /proc/sys/vm/drop_caches
test $swap -gt $bad_swap && test $mem -lt $swap && echo $err >> $log && exit 1
test $swap -gt $bad_swap && echo "`date` "$swap_note >> $log && killall okular eog evince acroread ; swapoff -a && swapon -a && exit 0

```
and added it to cron to run every minute. Its kind of brute force, but for the first time I can have a back-in-time backup without massive system freeze, since it is dropping the caches every minute.
 
I think it would be more correct to replace the "drop caches" part by a mapping of system load to swappiness, but this works for the moment.

---
No "stolen memory" entry to be found in /var/log/Xorg.0.log.

---

### Post by lavinog on 2011-03-14
> **crazy ivan said:**
> Hi there, I have a somewhat related problem:

I have 4GB ram installed, due to onboard graphic card I do not have it all available:

```

free -m
             total       used       free     shared    buffers     cached
Mem:          3388       2789        599          0         54        853
-/+ buffers/cache:       1881       1507
Swap:         5857          0       5857

```.

Anyhow, no matter how much RAM i put inside, I always end up swapping, since I really use that device ;)


How much swap is used when you are "swapping"
If something gets moved to swap space, it probably doesn't get accessed enough to matter.

As for your 3g limit issue, are you running 64bit or 32?

What kind of video card do you have?  There was an issue with the proprietary ATI drivers in the past that caused a memory leak.

---

### Post by crazy ivan on 2011-03-14
> How much swap is used when you are "swapping"
If something gets moved to swap space, it probably doesn't get accessed enough to matter.

As I've written: In my script, when system load is larger than 1 and when swap is larger than 200M , I drop the caches, so swap does not grow that fast and does not take my application data. At swap > 500 Mb and system load > 1, swap gets written back.

At the moment I'm just browsing and have load zero, running happily with 250 MB swap and 75%r RAM usage. So the concept of swap DOES make sense, but only when there is no big hard disk activity going on at the same time, since then my desktop application data gets written to swap. As
>  it probably doesn't get accessed enough to matter

But fluent desktop experience does matter to me! Once again my lamento.. I really think this should be handled better by the kernel. E.g., a mapping of hard disk activity to swappiness factor!!

> Since evidently I can't keep all my open application as busy as the "rsync" command is on its own, the kernel will start to think, that my applications are not as important and hence start putting their new data into swap instead of reducing the cache.. Hence all my IMPORTANT programs start to hang.

I see that this kernel setting is good for making the resource-consuming program run as fast as possible (although in the case of rsync I doubt that this caching is good for anything!) but that is more important for a server or a work-station. For me on a single-user machine the most important thing is to keep the load down and ensure a fluent desktop experience, because I don't want to sit and wait before the compilation finishes, and on the other hand I usually don't care if it takes 5 or 6 minutes. 

Concerning the RAM: I rund 64 bit wit intel 945 mobile onboard. Strangely enough in BIOS the 4Gb are well recognized. Only in memtest I see 3447M:

[http://ubuntuone.com/p/hhI/]("http://ubuntuone.com/p/hhI/")

---

### Post by lithopsian on 2011-03-14
Whether or not to cache file read or written should primarily be an application decision.  The kernel supports this and allows the use of "once-only" file operations.  rsync does not officially support this but patches have been produced so that large file transfers can be done without swamping cache.

There are also a whole host of vm tuning options.  swappiness is the one described most often, but cache pressure can also be useful.

You can examine the read and write activity of swap using the rzscontrol utility with compcache.

---

### Post by crazy ivan on 2011-03-20
Hey lithopsian,
thanks a lot for the many useful tips concerning system performance optimization.. I'll implement them one by one on my system. Anyhow my urgent goal: to stop GNOME from crashing during rsync and other hard disk intensive procedures, was achieved by this brute force script above.

Anyhow: I have a last question concerning swap: Why do they not write it back after hibernation? This filled swap makes the system very slow at the beginning and you get funny stats like "200 mb" RAM, "400 Mb" swap, even though the system went to hibernation in a completely fine state. Before I run

```
sudo swapoff -a && sudo swapon -a
```

I can't really work with it.. Also it leads to some issues with sound:
[http://ubuntuforums.org/showthread.php?p=10580059]("http://ubuntuforums.org/showthread.php?p=10580059")

---

