---
title: "Extremely Slow Swap Performance"
date: 2010-06-24
forum: General Help
---

### Post by Nphyx on 2010-06-24
I'm getting horrible (unusable) performance every time swap is accessed. This was compounded by the GEMS leak and a few other memory leaks, but now under normal non-leaky memory usage swapping is still intolerable. For instance swapping out ~300mb when I opened a new program with RAM full resulted in the system nearly freezing up for about 3-5 minutes (however long it took to brew a cup of coffee and come back to the system just finally unfreezing).

Abbreviated System info:

```

System: hp tx2z-1050us (tablet pc)
RAM: 3gb
Swap: 4gb
HDD: 500gb SATA
Video: Radeon HD 3200 (running radeonhd drivers)

Kubuntu Lucid x86_64 / Kernel 2.6.32-22-generic
KDE 4.4.4
Qt 4.6.3

```

Memory (shortly after above example):
```

$free
total       used       free     shared    buffers     cached
Mem:       2698372    2673688      24684          0      11600      97460
-/+ buffers/cache:    2564628     133744
Swap:      3903784     343228    3560556

```

hwinfo attached.

I don't think this is a general HDD problem for two reasons: 1. it's brand new, 2. benchmarks give reasonable results when there is no swap activity, e.g. hdparm:
```

$hdparm -t /dev/sda
/dev/sda:
 Timing buffered disk reads:  222 MB in  3.03 seconds =  73.37 MB/sec

```

I do have /tmp mounted to tmpfs, see fstab below, however I got the same problem with it disabled so I don't think that is the problem either, and in any case use of /tmp does not cause performance problems (e.g. in extracting archives):
```

$cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                                 <mount point>   <type>  <options>               <dump>  <pass>
proc                                            /proc           proc    defaults                0       0
/dev/mapper/sda4_crypt                          /               ext4    errors=remount-ro       0       1
# /boot was on /dev/sda3 during installation
UUID=f7b926eb-4067-46d7-846f-01d67e10ae86       /boot           ext2    defaults                0       2
/dev/scd0                                       /media/cdrom1           udf,iso9660 user,noauto,exec,utf8 0       0

/dev/mapper/swap                                swap            swap    defaults                0       0

# PSP
#/dev/sdd1 /mnt/psp vfat user,shortname=winnt 0 0

# TMP RAM disk
tmpfs /tmp tmpfs defaults,nosuid 0 0

```

Let me know if anything else will help.

---

### Post by ankspo71 on 2010-06-24
Hi,
With 3gb of ram, you have plenty of ram to do most things in Linux without having to even access swap. _[Have you already tried adjusting your swappiness? (link)]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?")_ Generally speaking it isn't needed for the average user, but it might be a good idea if you were experiencing memory leaks and/or incredibly slow performance with swap. What is consuming most of your 3gb of ram? Is it "gems" (the package)? You can see what is using memory if you run "top" in the terminal. Swap is going to be much slower than ram (3 to 4 times slower, I think), but programs should be able to run in swap without stalling. Maybe the problem lies in your swap? Does the problem go away if you disable your swap, then run the applications? Below are the commands to turn swap on and off.
```
sudo swapoff -a
sudo swapon -a 
```

Hope this somehow helps.

---

### Post by Nphyx on 2010-06-24
Thanks for the reply. The memory usage is pretty normal for me - when I'm doing web development I may have my IDE open (500mb), a virtual machine or two, plus plenty of miscellaneous stuff (video running behind my IDE window, amarok, kopete, apache+mysql). I eat the RAM up pretty fast, that's why I got so much in the first place. Typically the top users are Java (my IDE is Java-based), chromium-browser (20+ tabs plus a slow memory leak in the nightlies), and firefox with a ton of development addons. This is not unusual and normally wouldn't cause problems.

Before Lucid swap was not a problem; things would run slower when I was switching between apps a lot, but not to the point that the whole system would freeze. Also, the lag would never last more than a few seconds - nothing like these 30 second - 5 minute swapgasms where the system is so frozen the mouse cursor doesn't move.

My swappiness is already at 10, I've set it lower and higher with no major impact - but it's been that way since Jaunty for me. I definitely don't have the GEMS leak, I have a patched Xorg and I've also run the suggested checks to make sure. Disabling swap does solve the problem, but I run out of memory and things crash so it's not a good solution for me.

My guess is that either something in Lucid or something in the 2.6.32+ kernels has changed the way swap is managed so as to make it go into massive read/write spasms under certain circumstances. I am not able to test 2.6.33+ right now as they break too many things, but a test run under 2.6.34 did seem to mitigate the problem significantly so it may not be Ubuntu's fault specifically.

---

### Post by ankspo71 on 2010-06-25
> **Nphyx said:**
> 
My guess is that either something in Lucid or something in the 2.6.32+ kernels has changed the way swap is managed so as to make it go into massive read/write spasms under certain circumstances.

You might be right about that. After reading about what you said about possible swap management changes, I decided to see if I could get my computer to use up some swap. I changed my swappiness to 98 and used up my memory up to 800mb (out of 2gb) and my 4gb swap still doesn't get used. I ran into high cpu usage so I decided to stop.

I'm wondering you could benefit from a separate drive for swap (I think your computer is a laptop type though so that's probably not possible) or benefit from having a second swap on the same drive. Sometimes the system itself needs the memory and swap as much as the running applications do, which can cause delays in read and write access to memory and swap, which might be the problem you are experiencing. 

> Optimizing Swap performance Because swap space uses a disk device, this can cause performance issues in any system that uses swap space significantly because the system itself may also be using the same disk device at the same time that it is required for swap operations. One way to reduce this problem is to have swap space on a different physical drive so that the competition for that resource is either reduced or eliminated.  borrowed from [https://help.ubuntu.com/community/SwapFaq#Why%20do%20I%20need%20swap?](https://help.ubuntu.com/community/SwapFaq#Why%20do%20I%20need%20swap?)

If you are interested in experimenting with a second swap, there are instructions for creating a swap 'file' on the page below, which would eliminate the need for creating a second swap partition. There are also instructions on how to make it permanent and also removal instructions further down in the link. [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

Here is a link that shows a performance hack for multiple swaps.
[http://www.cyberciti.biz/tips/performance-tuning-for-linux-swap-partition.html](http://www.cyberciti.biz/tips/performance-tuning-for-linux-swap-partition.html)
I don't know if this could apply to Ubuntu/Kubuntu, or how well it might work though.

Hope something here helps.

---

### Post by Nphyx on 2010-06-25
That's an interesting thought - I could use a thumb drive for swap. I don't quite understand how breaking up the swap partition on a single drive will help, but it's easy enough to try it.

---

### Post by Chame_Wizard on 2010-06-25
6 GiB for your SWAP can be nice.

---

### Post by dabl on 2010-06-25
More:  [https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?](https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?)

[http://ubuntuforums.org/showthread.php?t=1517153](http://ubuntuforums.org/showthread.php?t=1517153)

---

### Post by hangfire on 2010-06-25
> **Nphyx said:**
> 
I don't think this is a general HDD problem for two reasons: 1. it's brand new, 2. benchmarks give reasonable results when there is no swap activity, e.g. hdparm:
```

$hdparm -t /dev/sda
/dev/sda:
 Timing buffered disk reads:  222 MB in  3.03 seconds =  73.37 MB/sec

```


Don't rule out h/w until you can prove it. I have received new disks that were nearly unusable. If there is a cluster of bad sectors in your swap area, but no where else (or no where else being used yet), you can get retry issues that can slow things down. These may or may not get logged as the h/w will try very hard before reporting an error, and may eventually succeed, albeit slowly.

I suggest installing package **smartmontools** and run some SMART long tests. At least rule it out.

---

### Post by 3Miro on 2010-06-25
How do you get to the point where you need to swap. I have always had problems with swap under Linux, but this is because I use sparse matrices under MATLAB and if I mess up my code, I get s sharp conversion from sparse to dense which means that MATLAB would instantly request a few GB of memory and that hits the swap hard. The system becomes close to unresponsive and I often have to kill MATLAB.

If you have leaks in your program, then the problem may not be the swap itself, but the fact that you are hitting too hard too quickly.

---

### Post by pallair on 2010-07-22
> **Nphyx said:**
>  [...] Before Lucid swap was not a problem; things would run slower when I was switching between apps a lot, but not to the point that the whole system would freeze. Also, the lag would never last more than a few seconds - nothing like these 30 second - 5 minute swapgasms where the system is so frozen the mouse cursor doesn't move.

My guess is that either something in Lucid or something in the 2.6.32+ kernels has changed the way swap is managed so as to make it go into massive read/write spasms under certain circumstances. I am not able to test 2.6.33+ right now as they break too many things, but a test run under 2.6.34 did seem to mitigate the problem significantly so it may not be Ubuntu's fault specifically.

I had exactly the same issue - on Fedora 12! I noticed mass swap-outs (200-300MB at once) when I ran Netbeans (~500MB RSS), 2pcs of Win7 in KVM (2x512MB), firefox, rhythmbox and KDE. I always  had 1500MB free+cached RAM reported by 'free'. Sometimes the mouse cursor was stopped for a minute when the swapping began. I googled a half day but I didn't find reports except yours, so I think it's a KVM-related issue. "vm.swappiness=0" did not help.

After I upgraded to 2.6.33.6 (from Fedora 13) the problem vanished.

---

### Post by ankspo71 on 2010-07-22
Hi,
I'm just checking in again to let you that when I said:

> You might be right about that. After reading about what you said about possible swap management changes, I decided to see if I could get my computer to use up some swap. I changed my swappiness to 98 and used up my memory up to 800mb (out of 2gb) and my 4gb swap still doesn't get used. I ran into high cpu usage so I decided to stop.

My swap wasn't noticeably working at that time. Well since then I did manage to get it to work by changing my swappiness to 100. It was using only a small amount of swap after that, but it was actually working. The test I used this time was with letting googleeaarth run for 5 or 10 minutes with the globe spinning freely (continuously).

---

### Post by Nphyx on 2010-07-23
Well, it may be only a couple anecdotes so far, but I am willing to pin this on the 2.6.32 kernel at this point. I'm still running it and still getting this problem, although I've learned to live with it. Thanks for the reply, at least we know we are not alone! Hopefully I'll have a chance to update to 2.6.33 soon, but I have to wait on driver & software support.

---

### Post by jlaki on 2010-11-27
Does anyone know how will it affect the system if you had your swap off? What are the consequences?

I'm having very similar issue, but I have really slow hard drive and I think that's it.
I realize it might be good to use flash disk as a swap partition, but I don't have any.

---

### Post by vanadium on 2011-09-11
Just stumbled on this old thread, because I have the same experience. Where old machines running Windows 95 would swap like hell, but still be somewhat responsive, the sytem tends to freeze sometimes for many minutes at once when swap is accessed.

I am running now Ubuntu 11.04 with a kernel 2.6.38-11-generic. I have a 1 GB Ram machine, so swap is effectively needed now and then.

- With low swapiness values, the system would run smoothly. However, if swap is needed anyway, the system would freeze for perhaps 10 to 15 minutes.
- I hoped that with high swapiness, 100, the system would, although less snappy, remain more responsive as smaller chuncks of memory are earlier swapped back and forth. Yet I sometimes see the system freeze for more than one minute as, shortly after startup, some 100 megabyte are swapped to disk.

I just wanted to add my observation.

As a reply to the last post: do never disable swap memory. The consequences are that the system will crash when it needs to allocate memory, and it cannot rely on swap to make the memory needed available. Instead of turning of swap, reduce swappiness. Swap will not be used unless absolutely necessary.

---

