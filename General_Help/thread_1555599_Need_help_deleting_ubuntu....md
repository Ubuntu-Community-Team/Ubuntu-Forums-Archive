---
title: "Need help deleting ubuntu..."
date: 2010-08-18
forum: General Help
---

### Post by Oppermongo on 2010-08-18
Before you start considering me as insane, let me explain the situation.
 
I bought an acer laptop a year ago, which had windows vista installed.
Ubuntu was required for school so I partitioned my hdd and got ubuntu on a 17gig selfexpanding partition, I believe it was the 9.04 back then.
 
I updated my Ubuntu some months later to 9.10 and also installed it as the main OS on an old desktop, considering the lower sysreq than windows.
 
6 months ago however, I bought a macbook pro and dualbooted it with windows 7, as well as upgrading my acer laptop to windows 7.
 
Since I'm stuck with 2 laptops, I think it's best to get rid of the Acer.
 
Now I don't think many people on ebay will even know what linux is so I decided to delete the partition and leave the choice up to them.
 
However when I try to uninstall Ubuntu form within Windows, the uninstaller crashes and it fails to do so.
 
Can anyone help me on how to get this done, preferably without ruining my laptop?
 
It seems rather not logical that this can be done from within Ubuntu, but I don't want some third party app ruining a piece of my hdd...
 
Any help is welcome :)

---

### Post by Zee5han on 2010-08-18
You say you want to sell the laptop. So I assume that you want to delete all your file and sell it as if it were just bought.

Why  don't you reinstall windows 7.

---

### Post by nbkr on 2010-08-18
What kind of installation did you run? Wubi?

---

### Post by mitsios on 2010-08-18
If I were to sell it on Ebay I would completely format the disk and re-install Windows.

---

### Post by ronnielsen1 on 2010-08-18
I'm assuming you're talking XP and it won't recognize linux partitions. Use a live cd and delete the partitions leaving them unpartitioned and then let the windows installer partition the hard drive

Ebay knows what Ubuntu is

[http://shop.ebay.com/i.html?_trkparms=65%253A12%257C66%253A2%257C39%253A1%257C72%253A3477&rt=nc&_nkw=ubuntu&_sticky=1&_trksid=p3286.c0.m14&_sop=16&_sc=1](http://shop.ebay.com/i.html?_trkparms=65%253A12%257C66%253A2%257C39%253A1%257C72%253A3477&rt=nc&_nkw=ubuntu&_sticky=1&_trksid=p3286.c0.m14&_sop=16&_sc=1)

Does this mean you no longer use linux?

---

### Post by endotherm on 2010-08-18
well, did you install ubuntu from within windows? if so, i'm not terribly familliar with wubi, so sorry. otherwise, the only real steps to uninstalling ubuntu, is to format over the partition it's on, and replace teh bootloader with one native to the system you are keeping. 

here is some info on reinstalling the vista/win7 bootloader (boot sector and mbr)
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
you may find more concise information online.

---

### Post by endotherm on 2010-08-18
> **mitsios said:**
> If I were to sell it on Ebay I would completely format the disk and re-install Windows.
thats a good point. technically an OEM license is not transferable from owner to owner. at the least from a privacy perspective, running the acer restore would fix the boot and make sure you aren't leaking any personal info.

---

### Post by t0p on 2010-08-18
I do hope you will continue using Ubuntu on your macbook.

Right, a solution for you: as you want to sell the Acer, you don't want any personal info or other data to remain on it, right?  Simplest thing is to reinstall Windows, by default it will take the whole hard drive and Ubuntu will be but a fond memory.  It might be an idea to use dd or DBAN before you reinstall Windows, just to make sure nothinh sensitive is left on the box.  Info on dd and DBAN [here]("http://mirror.href.com/thestarman/asm/mbr/WIPE.html#DBAN").

Make sure you install Ubuntu on your macbook somewhere.  You'll only miss it otherwise.

---

### Post by Oppermongo on 2010-08-19
Thanks for the replies.
I installed Ubuntu 9.04 by qinserting the disk while in windows, it required a reboot and pratitioned my hdd leaving a 17gb to ubuntu.
However, when I reformatted my Acer (done this twice already) the partition remains.
I can access the Ubuntu folder as part of my C drive and there is an uninstall there, which crashes every time.
 
I'll try resetting the partition with system restore, hadn't thought of that, thanks.
I'll look for that DBAN to, seems like a good idea :)
 
And don't worry, I am still keeping Ubuntu on my desktop, don't think I'll install it on the Macbook though, three partitions kinda eat up my hdd and I need it for video editing :)
 
The main reason I don't really use it alot is because I got a lot of paid software like adobe photoshop and os specific software I can't really find a good replacement for on Ubuntu and getting recent games to work in Linux isn't all that obvious (at least for me :))
 
I'll come back with an update on the formatting soon ;)

---

### Post by endotherm on 2010-08-19
> **Oppermongo said:**
> Thanks for the replies.
I installed Ubuntu 9.04 by qinserting the disk while in windows, it required a reboot and pratitioned my hdd leaving a 17gb to ubuntu.
However, when I reformatted my Acer (done this twice already) the partition remains.
I can access the Ubuntu folder as part of my C drive and there is an uninstall there, which crashes every time.
 
well, if the partition is still there, but windows has been reinstalled several times since, then all you should have to do, is open the Disk Manager in windows (run compmgmt.msc as admin. diskman is about halfway down the list on the left), or use gparted from a ubuntu live cd to delete the partition. 

I would probably get dban, wipe the entire hdd, and then restore windows prior to sale, or if you are worried about the legalities of transferring the windows license, just leave it blank and sell it as-is.

---

### Post by Oppermongo on 2010-08-19
Thanks alot, will try this this evening.
And maybe my brother is buying it, so wiping it clean might not be a priority :)

---

