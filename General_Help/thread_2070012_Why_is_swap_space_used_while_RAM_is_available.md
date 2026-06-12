---
title: "Why is swap space used while RAM is available?"
date: 2012-10-11
forum: General Help
---

### Post by terminator14 on 2012-10-11
Here's a problem I've been facing for a while: normally, as I understand it, anything that gets cached in RAM should not effect anything that actually needs RAM. This video ([1 - swap.ogv]("https://sites.google.com/site/lstoragelockerl/cabinet/1%20-%20swap.ogv?attredirects=0&d=1")) shows me using dd to copy a file to /dev/null, which also causes it to be cached as this happens. After a while, swap starts being used. What's even stranger is that if swap contained the rest of the file I was copying, it would have used a lot more than the 11MB it did, so I'm not sure what those 11MB are. 

In the video, once the dd command is done, I run './mem'. mem is a simple program which allocates 100MB of memory every second. At first, it starts replacing the cached content in RAM (as expected), but later, it starts filling up swap space as well, despite still having over 2GB of RAM to work with at one point (in the form of cached data that it should be able to overwrite).

I would have expected dd to write as much to cache as it could, but once it filled the RAM, it would stop, and not touch swap. If any other program needed RAM, I would expect that program to overwrite the cached data in RAM (filled with the file I just copied), and not touch swap either. For ./mem, I would expect it to overwrite all cached content in RAM before writing anything to swap. Why is this not what's happening?

In practice, this problem affects me when using programs that use a lot of RAM, like vmware. When I run vmware, if my RAM is mostly full of cache that vmware should be able to overwrite, it overwrites a lot of cached data, but it uses some swap too (despite having plenty of cache left to overwrite). If the cache is empty when I run vmware, swap is never used. I wouldn't mind vmware using swap if not for the fact that as soon as swap space starts being used, the entire system slows down. Applications take several times longer to open, and menus take several times longer to respond. If I run 'sudo swapoff -a && sudo swapon -a' while vmware is running in order to copy everything from swap into RAM, everything starts running fast again. This doesn't last too long however, and vmware starts filling up swap space all over again shortly after. This can be seen in "[2 - full cache.ogv]("https://sites.google.com/site/lstoragelockerl/cabinet/2%20-%20full%20cache.ogv?attredirects=0&d=1")" and "[3 - empty cache.ogv]("https://sites.google.com/site/lstoragelockerl/cabinet/3%20-%20empty%20cache.ogv?attredirects=0&d=1")".

Is this expected behavior? Is there a way around it - like a way to tell the OS not to use swap unless it completely runs out of RAM?

---

### Post by jerrrys on 2012-10-11
Have you tried adjusting swappiness?

[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

---

### Post by CCgirl6690 on 2012-10-11
thanks for the reply jerry , was helpful , i posed here so i can find this topic later

---

### Post by terminator14 on 2012-10-11
> **jerrrys said:**
> Have you tried adjusting swappiness?

[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

Sounded promising, but nope - it didn't help [(4 - swappiness.ogv)]("https://sites.google.com/site/lstoragelockerl/cabinet/4%20-%20swappiness.ogv?attredirects=0&d=1").

Any other ideas?

---

### Post by jerrrys on 2012-10-11
Maybe a little experiment.  Turn swap off.  That can be done with gparted or ..

sudo swapoff -a

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=swapoff&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=swapoff&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by terminator14 on 2012-10-11
> **jerrrys said:**
> Maybe a little experiment.  Turn swap off.  That can be done with gparted or ..

sudo swapoff -a

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=swapoff&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=swapoff&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

Thanks for the advice, but disabling swap proves nothing, except for the fact that I have enough RAM to run the VM without the OS needing swap, which is something I already know. I do not want to turn swap off permanently either - if I run too many VMs at the same time, without swap, I'm likely to crash my linux. With swap, it will make everything run super slow, but at least it will give me a chance to turn off a VM and make the computer run at normal speed again. The problem I'm having is during regular vmware use, where I have plenty of RAM to run the VM without swap, yet it uses swap anyway and slows everything down.

---

### Post by pbrane on 2012-10-11
just curious, what did you set the vm.swappiness value to? a value of zero should cause the kernel to use RAM until it's essentially exhausted, then use swap. did you reboot after changing the value or use 'sysctl -p'? either should work though.

---

### Post by terminator14 on 2012-10-11
> **pbrane said:**
> just curious, what did you set the vm.swappiness value to? a value of zero should cause the kernel to use RAM until it's essentially exhausted, then use swap. did you reboot after changing the value or use 'sysctl -p'? either should work though.

I tried setting it to 10, and 0. Both didn't work as in both cases, the OS started using swap way before it was anywhere near being out of RAM.

And I edited /proc/sys/vm/swappiness directly:

$ echo 0 | sudo tee /proc/sys/vm/swappiness

---

### Post by pbrane on 2012-10-13
After you set the value you need to reload sysctl.conf (sudo sysctl -p), or reboot. I have mine set to 10 and I don't use swap very much with 4G of RAM. I run VirtualBox and openGL java apps. when I had set the value to 0 I didn't notice any swap being used with memory hungry apps. But I haven't done any real testing either.

What kernel version are you running?

---

### Post by terminator14 on 2012-10-13
> **pbrane said:**
> After you set the value you need to reload sysctl.conf (sudo sysctl -p), or reboot.

I'm editing /proc/sys/vm/swappiness directly, which takes effect immediately, but the changes don't survive a reboot, so rebooting would just undo what I did. There's also no point in me running "sudo sysctl -p", which rereads /etc/sysctl.conf, which I did not modify, as that is just the permanent way of doing the same thing, and there's no point of me making this swappiness change permanent if it doesn't help.

> **pbrane said:**
> What kernel version are you running?

2.6.32-279.9.1.el6.x86_64, CentOS 6.3

And yes, I'm aware that this is an Ubuntu forum, but I don't see this as a distro-specific problem.

---

### Post by pbrane on 2012-10-13
I agree, if it doesn't work there is no sense in making a permanent change just to have to undo it. And you're right, this is a kernel issue. However there are differences in some aspects of distribution compiled kernels. Probably not in this case. Also the 3.x series kernels handle swappiness a little differently if I have read the changelogs correctly. Not sure it's better though.

I would have though setting vm.swappiness to zero would have used more RAM and no swap until RAM is almost gone.

---

### Post by terminator14 on 2012-10-13
> **pbrane said:**
> I agree, if it doesn't work there is no sense in making a permanent change just to have to undo it. And you're right, this is a kernel issue. However there are differences in some aspects of distribution compiled kernels. Probably not in this case. Also the 3.x series kernels handle swappiness a little differently if I have read the changelogs correctly. Not sure it's better though.

I would have though setting vm.swappiness to zero would have used more RAM and no swap until RAM is almost gone.

I thought the swappiness changes would work too, but for some reason, it's not. I suppose it could be a bug causing the swappiness to be ignored, but I doubt it. There's gotta be some explanation for what it's doing. I'll see if I can try running the same tests on a 3.x kernel to find out if the results are the same.

---

### Post by pbrane on 2012-10-13
I came across this article for 2.6 kernels...
[2.6 swapping behavior]("http://lwn.net/Articles/83588/")
Not much help but may be of interest, if you haven't already seen this.

---

### Post by terminator14 on 2012-10-13
> **pbrane said:**
> I came across this article for 2.6 kernels...
[2.6 swapping behavior]("http://lwn.net/Articles/83588/")
Not much help but may be of interest, if you haven't already seen this.

I read the article - it breaks down what is used to decide if the OS should use swap or not, and while informative, it too suggests the use of /proc/sys/vm/swappiness to control how frequently swap is used.

I tried to run the same test on Mint 13 (which has a 3.x kernel) but I was only able to try it as a live CD. While the default swappiness settings of 60 started swapping out data way before the RAM was empty, setting swappiness to 0 seemed to work. Sort of. It kept filling up the RAM and overwriting all cache the RAM was holding until RAM was full, at which point, the system froze. I suspect this is because I was running it as a live CD where everything was stored in RAM, and it didn't like the RAM being full. I guess I'll have to keep looking.

---

### Post by terminator14 on 2012-10-13
While initial tests of setting my CentOS swappiness to 0 didn't work, after rebooting and trying it again, it seems to be working now. I'll see if it keeps working, especially with vmware, and if it does, I'll add the swappiness change to sysctl.conf and mark the thread as solved.

Edit - it looks like it's working with mem (a simple program that allocates 100MB of RAM per second), and doesn't use swap until all RAM is gone, but it works differently with vmware - vmware starts using swap when there's still gigabytes of free RAM still available. I think vmware itself requests to use swap instead of RAM. Is that even possible? Can programs request to use swap over RAM?

---

### Post by pbrane on 2012-10-14
I use VirtualBox with a winxp guest. I don't seem to have the swapping issue you have (swappiness set to 10). I ran vbox and the guest and while RAM usage went up swap was never used. I have 4G RAM. I have the winxp host set to use 512M of RAM. Performance seems fine to me.

As for whether a program can request swap, the virtual memory allocated to each process is 4G in a 64 bit OS. Virtual memory uses paging, or swap space. So I would assume it can. 

Can you post the source or a link to the mem program you are using? I'm curious about the allocation process.

---

### Post by terminator14 on 2012-10-14
> **pbrane said:**
> I use VirtualBox with a winxp guest. I don't seem to have the swapping issue you have (swappiness set to 10). I ran vbox and the guest and while RAM usage went up swap was never used. I have 4G RAM. I have the winxp host set to use 512M of RAM. Performance seems fine to me.

My vmware appears to only start using swap when the cache is full. If you have time, try something like:

```
dd if=/dev/urandom of=~/testfile.big bs=10M count=410
dd if=~/testfile.big of=/dev/null bs=10M
```

The first command will create a 4100MB file in your home directory full of randomized data. The second command copies the file into /dev/null, which basically does nothing except for copying the file to cache. The process itself should not cause your swap to be used, but will fill your cache with random data. After running this, try your virtualbox, and see if it starts using swap. You can also delete the testfile.big after you're done.


> **pbrane said:**
> As for whether a program can request swap, the virtual memory allocated to each process is 4G in a 64 bit OS. Virtual memory uses paging, or swap space. So I would assume it can. 

Hmm... Maybe vmware is requesting to use swap for some reason. The thing is - even if it was, shouldn't that only affect vmware? Why does the rest of the OS slow down considerably just because vmware decided to put some of its data into swap? I don't really care if vmware uses swap a little - if the huge number (I assume) of software developers that designed vmware think it should, who am I to argue? I only care that it impacts the rest of the system.

> **pbrane said:**
> Can you post the source or a link to the mem program you are using? I'm curious about the allocation process.

```
#include <malloc.h>
#include <unistd.h>
#include <memory.h>
#define MB 1024 * 1024
int main() {
    while (1) {
        void *p = malloc( 100*MB );
        memset(p,0, 100*MB );
        sleep(1);
    }
}
```

Save as mem.c, then run gcc -o mem mem.c, then ./mem.

Source: [http://superuser.com/questions/278855/a-linux-program-that-uses-memory](http://superuser.com/questions/278855/a-linux-program-that-uses-memory)

---

### Post by terminator14 on 2012-10-14
I just came across a script that can tell what's being swapped out:

```
#!/bin/bash 
# Get current swap usage for all running processes
# Erik Ljungstrom 27/05/2011
# Modified by Mikko Rantalainen 2012-08-09
# Pipe the output to "sort -nk3" to get sorted output
SUM=0
OVERALL=0
for DIR in `find /proc/ -maxdepth 1 -type d -regex "^/proc/[0-9]+"`
do
    PID=`echo $DIR | cut -d / -f 3`
    PROGNAME=`ps -p $PID -o comm --no-headers`
    for SWAP in `grep Swap $DIR/smaps 2>/dev/null | awk '{ print $2 }'`
    do
        let SUM=$SUM+$SWAP
    done
    if (( $SUM > 0 )); then
        echo "PID=$PID swapped $SUM KB ($PROGNAME)"
    fi
    let OVERALL=$OVERALL+$SUM
    SUM=0
done
echo "Overall swap used: $OVERALL KB"

```

Source: [http://stackoverflow.com/questions/479953/how-to-find-out-which-processes-are-swapping-in-linux](http://stackoverflow.com/questions/479953/how-to-find-out-which-processes-are-swapping-in-linux)

and it tells me something like:

```
PID=2967 swapped 12 KB (gnome-keyring-d)
PID=2976 swapped 16 KB (gnome-session)
PID=2985 swapped 8 KB (dbus-daemon)
PID=3029 swapped 80 KB (gnome-settings-)
PID=3035 swapped 16 KB (gvfsd)
PID=3041 swapped 20 KB (metacity)
PID=3046 swapped 16 KB (gnome-panel)
PID=3050 swapped 168 KB (nautilus)
PID=3052 swapped 84 KB (bonobo-activati)
PID=3057 swapped 124 KB (wnck-applet)
PID=3060 swapped 36 KB (trashapplet)
PID=3076 swapped 32 KB (restorecond)
PID=3081 swapped 8 KB (gnome-power-man)
PID=3083 swapped 1136 KB (nm-applet)
PID=3089 swapped 4 KB (gvfs-afc-volume)
PID=3090 swapped 144 KB (python)
PID=3091 swapped 12 KB (polkit-gnome-au)
PID=3093 swapped 1448 KB (gpk-update-icon)
PID=3097 swapped 20 KB (bluetooth-apple)
PID=3098 swapped 64 KB (gnome-volume-co)
PID=3118 swapped 16 KB (notification-ar)
PID=3121 swapped 20 KB (clock-applet)
PID=3122 swapped 48 KB (gdm-user-switch)
PID=3148 swapped 4 KB (gvfsd-burn)
PID=3192 swapped 1396 KB (vmware)
PID=3244 swapped 2072 KB (vmware-tray)
PID=3738 swapped 60 KB (vmware-unity-he)
PID=5659 swapped 8 KB (evince)
PID=6583 swapped 24 KB (bash)
Overall swap used: 7096 KB
```

Despite me having plenty of RAM available. If all of these were vmware related, I'd understand (maybe the developers decided some parts didn't need to be in RAM since keeping them in swap wouldn't effect performance) but things like bash, metacity, gnome-panel, nautilus, etc. are all things I use all the time. Why in the world would it put them, or even parts of them into swap? They only take up 7MB in total, but keeping them in swap slows down the system considerably. And why does this only happen when vmware starts using swap, and in no other situation (as far as I can tell)?

---

