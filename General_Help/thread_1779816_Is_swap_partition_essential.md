---
title: "Is swap partition essential"
date: 2011-06-11
forum: General Help
---

### Post by rng on 2011-06-11
If a computer has enough ram, say 2gb, is swap partition necessary? Will ubuntu run if swap partition is deleted?

---

### Post by katykat on 2011-06-11
Ever since its early days, a swap partition has never been *necessary*, just a *very good idea*.   Linux is not Windoze which tries to load memory with as much garbage as possible. The purpose of the Linux swap partition is to dump little used or unnecessary tasks OUT of memory. Since this is a frequent occurance, its good to keep it on a separate file system, as any errors or glitches in the processes will not then screw up the main filesystem.

---

### Post by Rubi1200 on 2011-06-11
I recommend you read the guide here before deciding whether to use a swap file/partition or not:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by kerry_s on 2011-06-11
> is swap partition necessary?

no, i don't use 1. i have 2gb ram.
i do install a dynamic swap as a just in case, should i choose to compile something or whatever.

---

### Post by HermanAB on 2011-06-11
Basically, if you want to use Suspend/Resume, then you must have /swap = 2x RAM.  Also, if you use Firefox with all its memory leaks, then you need /swap.  So it is usually a good idea to have /swap space.

---

### Post by rng on 2011-06-11
Thanks for the info. Swap seems to be not essential but very desirable. 

But I have seen slackware systems running very well without swap. 

Also, if ubuntu is to be installed on usb, there may be a point in avoiding swap. This may reduce the wear and tear on the usb drive and increase its life. Do you agree?

---

### Post by rng on 2011-06-11
> **kerry_s said:**
> no, i don't use 1. i have 2gb ram.
i do install a dynamic swap as a just in case, should i choose to compile something or whatever.

Dynamic swap seems interesting. Can you briefly tell us how to use it. I have ubuntu 10.04 installed on hard disk. So I install swapspace from synaptic and remove my swap partition thru gparted. Or should the sequence be other way round?

---

### Post by rng on 2011-06-11
> **HermanAB said:**
> Basically, if you want to use Suspend/Resume, then you must have /swap = 2x RAM.  Also, if you use Firefox with all its memory leaks, then you need /swap.  So it is usually a good idea to have /swap space.

You mean crashes may occur if we use firefox without swap? Is that true even for the latest version of firefox?

---

### Post by walt.smith1960 on 2011-06-11
> **rng said:**
> Thanks for the info. Swap seems to be not essential but very desirable. 

But I have seen slackware systems running very well without swap. 

Also, if ubuntu is to be installed on usb, there may be a point in avoiding swap. This may reduce the wear and tear on the usb drive and increase its life. Do you agree?

I don't know about reducing wear and tear, swap is only used when needed.  A downside of creating a swap file or swap partition on a USB drive is space designated for swap cannot be used for normal data storage.  This is not typically a consideration of a capacious hard drive but it may be on a USB drive.  The only time I've ever found swap being used was on a 512 MB. machine but i don't have more than 2 or 3 apps open at one time.

---

### Post by rng on 2011-06-11
How can one remove swap partition using gparted while running any linux? Because all linux versions will be mounting and using swap partition, even livecd?

---

### Post by rng on 2011-06-11
Does dynamic swap space manager ("swapspace") uses swap file. Is it same as making a swapfile on the system? But I thought swapfiles were of fixed size.

---

### Post by kerry_s on 2011-06-11
> **rng said:**
> Dynamic swap seems interesting. Can you briefly tell us how to use it. I have ubuntu 10.04 installed on hard disk. So I install swapspace from synaptic and remove my swap partition thru gparted. Or should the sequence be other way round?

you just install it & let it do it's thing, there is a settings file, but i've never found the need to mess with it.
pretty much an automatic thing.

---

### Post by kerry_s on 2011-06-11
> **rng said:**
> Does dynamic swap space manager ("swapspace") uses swap file. Is it same as making a swapfile on the system? But I thought swapfiles were of fixed size.

yes, it creates swap files when needed & deletes them when no longer used.

---

### Post by rng on 2011-06-11
> **kerry_s said:**
> you just install it & let it do it's thing, there is a settings file, but i've never found the need to mess with it.
pretty much an automatic thing.

Just want to confirm once more please. I already have a swap partition. I will not need to delete swap parition manually (thru gparted)?

Thanks for answering and for your patience.

---

### Post by kerry_s on 2011-06-11
> **rng said:**
> Just want to confirm once more please. I already have a swap partition. I will not need to delete swap parition manually (thru gparted)?

Thanks for answering and for your patience.

If you have a swap partition, you don't need swapspace.

---

### Post by walt.smith1960 on 2011-06-11
> **HermanAB said:**
> Basically, **if you want to use Suspend/Resume, then you must have /swap = 2x RAM. ** Also, if you use Firefox with all its memory leaks, then you need /swap.  So it is usually a good idea to have /swap space.

There may to be an issue with terminology. Here is my understanding.  There are two power saving modes. Most if not all *buntu distros use the terms suspend and hibernate.  Hibernate is sometimes referred to as "suspend to disk". This requires no power at all AFAIK.  Suspend on the menu refers to suspending to RAM.  This requires a little bit of power, either from the wall or from a battery because DRAM must be refreshed. If power is lost so are the contents of the suspended machine's RAM.  Suspend to RAM can be done with no swap of any description.  Hibernation, or suspend to disk, requires a separate swap partition somewhat larger than installed RAM because the contents of RAM are written to the swap partition.  A swap file will not work for hibernation, it must be a physical partition. I've not used Hibernation but have read that resuming from Hibernation takes about as long as a cold boot so don't see a benefit for me.

---

### Post by rng on 2011-06-11
Thanks for the info.

---

### Post by l300lvl on 2011-09-24
> **walt.smith1960 said:**
> There may to be an issue with terminology. Here is my understanding.  There are two power saving modes. Most if not all *buntu distros use the terms suspend and hibernate.  Hibernate is sometimes referred to as "suspend to disk". This requires no power at all AFAIK.  Suspend on the menu refers to suspending to RAM.  This requires a little bit of power, either from the wall or from a battery because DRAM must be refreshed. If power is lost so are the contents of the suspended machine's RAM.  Suspend to RAM can be done with no swap of any description.  Hibernation, or suspend to disk, requires a separate swap partition somewhat larger than installed RAM because the contents of RAM are written to the swap partition.  A swap file will not work for hibernation, it must be a physical partition. I've not used Hibernation but have read that resuming from Hibernation takes about as long as a cold boot so don't see a benefit for me.

In case anyone else reading here is curious, in my case with a dual core amd e350(netbook) it actually takes LONGER resuming from hibernation than it does doing a cold boot, and I mean so much longer the point in saving battery life goes right out the window.

---

### Post by ottosykora on 2011-09-24
> **rng said:**
> Thanks for the info. Swap seems to be not essential but very desirable. 

But I have seen slackware systems running very well without swap. 

Also, if ubuntu is to be installed on usb, there may be a point in avoiding swap. This may reduce the wear and tear on the usb drive and increase its life. Do you agree?

well on usb drives it is not of big sense to have swap on the usb drive too.
I mean with it something like flash drives, as usb sticks etc. Writing here takes long time and this will only further make all other tasks running much, much slower. 
The other point is the wear of the flash, it is getting less important today, but still relevant.
However if there is a swap partition on the host computer found, then it can be used by the system running from usb.

---

### Post by l300lvl on 2011-11-04
> **l300lvl said:**
> In case anyone else reading here is curious, in my case with a dual core amd e350(netbook) it actually takes LONGER resuming from hibernation than it does doing a cold boot, and I mean so much longer the point in saving battery life goes right out the window.


after posting this i discovered the tuxonice kernel builds and with their scrips/recommendations hibernation has improved greatly and i can now see hibernation being a viable option for saving battery life, among other things.

[http://tuxonice.net/](http://tuxonice.net/)

---

### Post by rng on 2011-11-05
Thanks for the info and the link. What are the steps to install it? Synaptic only has a user interface for it.

---

### Post by dcstar on 2011-11-05
> **rng said:**
> Thanks for the info and the link. What are the steps to install it? Synaptic only has a user interface for it.

Did you even bother to read the PPA?:

[https://launchpad.net/~tuxonice/+archive/ppa](https://launchpad.net/~tuxonice/+archive/ppa)

---

### Post by rng on 2011-11-05
Thanks for guiding me. Things look very simple once you have a lot of experience but not to the newcomers.

---

### Post by killermist on 2011-11-05
> **rng said:**
> How can one remove swap partition using gparted while running any linux? Because all linux versions will be mounting and using swap partition, even livecd?

From terminal:
```
sudo swapoff /dev/devicewithswap
```
then partition is deleteable via gparted/cfdisk/whatever

---

### Post by sgage on 2011-11-05
> **HermanAB said:**
> Basically, if you want to use Suspend/Resume, then you must have /swap = 2x RAM.  Also, if you use Firefox with all its memory leaks, then you need /swap.  So it is usually a good idea to have /swap space.

That may be true for Hibernate, but not for Suspend. You do need swap = 1x RAM, but not 2x.

As far as "Firefox with all its memory leaks", I've never seen anything remotely that extreme, even after days of active use. In any case, I have 4 G of RAM, 4 G of swap, and never see swap being used at all. I hardly ever even exceed 1 G of RAM usage.

---

### Post by l300lvl on 2011-11-05
> **rng said:**
> Thanks for guiding me. Things look very simple once you have a lot of experience but not to the newcomers.

Open a termianl and paste and run:

sudo add-apt-repository **ppa:tuxonice/ppa**

next run

sudo apt update

now finally run

sudo apt install tuxonice-userui linux-generic-tuxonice linux-headers-generic-tuxonice

now you should be good to go! if everything installs ok, for testing you might want to reboot first and then try to suspend/resume

on my default maverick install that was about all i needed to do to get suspend/resume and hibernate working, but if you need more help afterwards post your results here...

---

### Post by rng on 2011-11-05
Thanks.

---

### Post by deserthowler on 2011-11-05
> **rng said:**
> If a computer has enough ram, say 2gb, is swap partition necessary? Will ubuntu run if swap partition is deleted?

NO!  Not necessary.  On the other hand, is there a reason not to have swap?  Probably not.

Go to /etc/fstab and comment out the swap partition.  Run your computer as you normally run it and keep an eye on memory usage.  Or if it crashes, you need swap.  

I often run my computer, 2GB memory, for 12-16 hours/day without using swap.

If you want to get rid of swap to make extra disk space, you probably need to clean out a bunch of junk or get a bigger disk.

Of course any of my suggestions might cause an unrecoverable system crash ... but that's how we learn. :D

Earl

---

### Post by l300lvl on 2011-11-06
> **deserthowler said:**
> NO!  Not necessary.  On the other hand, is there a reason not to have swap?  Probably not.

Go to /etc/fstab and comment out the swap partition.  Run your computer as you normally run it and keep an eye on memory usage.  Or if it crashes, you need swap.  

I often run my computer, 2GB memory, for 12-16 hours/day without using swap.

If you want to get rid of swap to make extra disk space, you probably need to clean out a bunch of junk or get a bigger disk.

Of course any of my suggestions might cause an unrecoverable system crash ... but that's how we learn. :D

Earl


Just for history's sakes, I can verify that it does work as I ran completely without swap, I actually deleted my swap partition set swapiness to 0 and made the changes in fstab, I dont know if swapiness correlates but I did everything I could find online to get rid of swap, and then once I found out about tuxonice I had to go through the process of learning how to recreate the partition and do swapon etc... but the choice remains, you can indeed run without swap.

My main goal was to increase boot time as I only use a laptop and at the time it was a slower one which took 45 seconds average to boot and it was becoming increasingly annoying, so in regards to swap it always mounts or something on boot and that led me to believe disabling and removing it could indeed increase my boot time, but in the end I don't think it ever made over ~0.5 seconds difference. Results may vary.

 This was all done with a minimum of 4gb ram though, so that may be a deciding factor, my system on average runs over 1200mb according to top/system monitor. I start to feel it lagging when I hit about 2gb but by that time I'll start closing some tabs in my browser lol.

---

