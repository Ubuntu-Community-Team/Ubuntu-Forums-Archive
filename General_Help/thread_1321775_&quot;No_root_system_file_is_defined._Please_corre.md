---
title: "&quot;No root system file is defined. Please correct this from the partitioning menu.&quot;"
date: 2009-11-10
forum: General Help
---

### Post by lazyastronomer on 2009-11-10
I'm installing Ubuntu onto an old computer, and all of the installation steps work out correctly until I get to the "Prepare Partitions" step. 

The screen is blank except for "Device", "Type", "Mount Point", etc listed at the top of the screen. The buttons at the bottom are whited out so I can't press them, but the "Quit", "Back", and "Forward" buttons can still be pressed. 

If I try to go forward because I can't really do anything else, it posts an error message: "No root system file is defined. Please correct this from the partitioning menu."

So I got from other threads that I should go to the Virtual try-it-out-without-installing-it thingy, and went under System > Administration > Gparted.

So now I'm sitting here with all the partitions and options in front of me without a clue of what I'm supposed to do now. How would I manually partition the hard drive? 

Oh yeah, and try to make your help as easy for me (a complete noob) to understand. I am still completely unfamiliar with everything to do with this.

Thanks in advance,
Layzastronomer

---

### Post by Onesimus on 2009-11-10
Why not check this out
[http://www.psychocats.net/ubuntu/installseparatehome]("http://www.psychocats.net/ubuntu/installseparatehome")

---

### Post by lazyastronomer on 2009-11-10
> **Onesimus said:**
> Why not check this out
[http://www.psychocats.net/ubuntu/installseparatehome]("http://www.psychocats.net/ubuntu/installseparatehome")
I want the same partitions that I would have if they had been made autonmatically.


Ok, so I have two partitions on my drive that it is showing.

1) /dev/sda1 ntsf 19.15 GiB (boot)
2) unallocated unallocated 7.84 MiB

What do I do with them, and what do I add? How big do the partitions need to be? Also, I don't want to do anything until I'm sure that I know what I'm doing.

---

### Post by Onesimus on 2009-11-10
> **lazyastronomer said:**
> I want the same partitions that I would have if they had been made autonmatically.



If you want the same partitions as if they had been made automatically, then why don't you allow it to do it for you ???

If you only have a 20Gb hard disk, then you could either have :

  System partition (say 6Gb)
  Home partition (say 13Gb)
  Swap partition (say 1Gb)

or 

  System and Home together (19Gb)
  Swap partition (Say 1GB)

Your swap partition needs to be twice the size of your RAM. (e.g. 512MB of RAM, then swap needs to be at least 1024MB).

For me, I would have a separate home partition, because it allows for easier upgrades.

Each partition wants to be formatted in ext4 (but not swap)

All this happens during the installation, not prior to it.  Your original error message is because you need to have the one partition that has a mount point of '/' - this is the system partition.

Hope this all helps.

---

### Post by coffeecat on 2009-11-10
I'll presume you're happy to wipe out Windows from that computer and have Ubuntu only. If so, try this:

Boot up the live CD. In Gparted, mark both those partitions for deletion and then click on the Apply button (in some versions of Gparted that appears as one big green tick). Both partitions will go leaving you with about 19GB of unallocated space. Now quit Gparted, and double-click the installer icon on the desktop to start. When you get to the partitioning stage choose "Guided - use whole disc" - or something like that, I'm going from memory. It *should* automatically set you up with a large root (/) partition (vaguely equivalent to a Windows C: partition) and a small swap partition. Then, continue with the installer, and you should be good.

The separate home partition guide that a previous poster linked is a good one, but as a complete Linux beginner you might want to avoid that complication. Besides, creating a separate home on such a small HD probably isn't a good idea.

By the way - post some more details of the machine. With only 20GB on the HD it is as you say an old one, and we need to see if the amount of RAM can cope with gnome, which is a fairly hefty desktop. And which version of the live CD do have there? 9.10 or 9.04 or earlier.

---

### Post by lazyastronomer on 2009-11-10
> **coffeecat said:**
> By the way - post some more details of the machine. With only 20GB on the HD it is as you say an old one, and we need to see if the amount of RAM can cope with gnome, which is a fairly hefty desktop. And which version of the live CD do have there? 9.10 or 9.04 or earlier.

I'm not sure about the RAM... I think about 129MB? I've done the memory test, and it said that I was ok, though. 
I'm installing the newest version, 9.10.

Update: Okay, I've deleted all the previous partitions, closed Gparted, and double-clicked on the install icon. I'm getting the same error as before.

---

### Post by Onesimus on 2009-11-10
Isn't there an option to use the entire disk ?  If there is, use that.

---

### Post by Onesimus on 2009-11-10
> **lazyastronomer said:**
> I'm not sure about the RAM... I think about 129MB? I've done the memory test, and it said that I was ok

The memory test only checks that the RAM is working properly, not that there is sufficient RAM to run the system.  You can check how much RAM you have by looking in the BIOS as it begins to boot up.

You have to press either F2 or delete, it tells you as it begins to boot.

---

### Post by lazyastronomer on 2009-11-10
> **Onesimus said:**
> Isn't there an option to use the entire disk ?  If there is, use that.

I don't think you understand. There are no options. 

Here's what it looks like:
[img]http://img23.imageshack.us/img23/9172/errorau0.png[/img]
From a google image search.

---

### Post by coffeecat on 2009-11-10
> **lazyastronomer said:**
> I'm not sure about the RAM... I think about 129MB?

Even if you mean 192MB, Ubuntu will struggle with that amount of RAM. The live CD needs even more RAM - because much more of the system has to be held in memory - so I'm now wondering if that message is nothing to do with what it's talking about. The installer has run out of memory and unpredictable things are happening. There is no way you can install Ubuntu/gnome with the live CD unless you add more memory.

You have two options:

Use the alternate installer. This is a text-based installer - not pretty - but it doesn't need as much memory. Look at this page:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Click on the "complete list of download locations" link, choose your mirror and download the ubuntu-9.10-alternate-i386.iso ISO file.

The second option is to install Xubuntu instead, which uses the lighter Xfce desktop. Have a look here:

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

You can see that your system only just meets the minimum RAM requirements for the Xubuntu live CD (if indeed you have 192, not 129MB). The Ubuntu live CD needs more.

---

### Post by lazyastronomer on 2009-11-10
Oh, I'm sorry, I made a mistake. I meant to say that it's about 229MB of RAM. I've already deleted the Windows partitions, how can I check exactly how much RAM I have from the Live CD?
Thanks again.

---

### Post by coffeecat on 2009-11-10
> **lazyastronomer said:**
> I meant to say that it's about 229MB of RAM. I've already deleted the Windows partitions, how can I check exactly how much RAM I have from the Live CD?

System > Administration > System Monitor > System Tab.

That will be enough (just) to run Ubuntu/gnome, but I'm fairly sure you need 512MB for the live CD. The live CD needs so much more than a hard disc installation. I'll have a dig around and see if I can find something.

**Edit:** found it:

[http://www.ubuntu.com/products/whatisubuntu/desktopedition](http://www.ubuntu.com/products/whatisubuntu/desktopedition)

> 
**System requirements **

 [LEFT] Ubuntu is available for PC, 64-Bit PC and Intel-based Mac architectures. At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer). Install requires at least 4 GB of disk space.[/LEFT]
[LEFT]


That looks like the Hardy Heron (8.04), but system requirements won't have changed that much.
[/LEFT]

---

### Post by lazyastronomer on 2009-11-10
> **coffeecat said:**
> System > Administration > System Monitor > System Tab.

That will be enough (just) to run Ubuntu/gnome, but I'm fairly sure you need 512MB for the live CD. The live CD needs so much more. I'll have a dig around and see if I can find something.

Thanks. Here are my system details:
Memory: 213.2MB
Processor: Intel(R) Pentium(R) 4 CPU 1.60GHz

---

### Post by Onesimus on 2009-11-10
Ditto, what coffeecat says about system requirements.

But you might want to check that your CD has burnt correctly - can't remember if there is an option on the Hardy Heron installation to do that.

As Karmic Koala has just been released, I would recommend installing that.

---

### Post by coffeecat on 2009-11-10
> **lazyastronomer said:**
> Thanks. Here are my system details:
Memory: 213.2MB
Processor: Intel(R) Pentium(R) 4 CPU 1.60GHz

Ok - not enough for the live Ubuntu CD. You'll have to go with the alternate CD or the Xubuntu live CD - see my earlier post for where to get them.

Unless you could find a spare 256MB RAM stick and put it in. That machine is not very old. A Pentium 4 1.6GHz will run Ubuntu fairly well. If you did manage to put in another 256MB stick (you've probably got one 256 or 2x128 in already - the missing bit is for video), you'd have nearly 512 and Ubuntu would be fine.

> **Onesimus said:**
> can't remember if there is an option on the Hardy Heron installation to do that.

Sorry - that was probably me confusing things. The link in my edit in my last post was showing a Hardy desktop - you can't mistake the big bird on the wallpaper! The OP hasn't told us what release number he's trying.

---

### Post by lazyastronomer on 2009-11-10
> **coffeecat said:**
> Sorry - that was probably me confusing things. The link in my edit in my last post was showing a Hardy desktop - you can't mistake the big bird on the wallpaper! The OP hasn't told us what release number he's trying.

Right here...

> **lazyastronomer said:**
> I'm not sure about the RAM... I think about 129MB? I've done the memory test, and it said that I was ok, though. 
** I'm installing the newest version, 9.10.**

And about those RAM sticks... can you just plug them into a USB port and be done with it, or do you have to take the machine apart and install it? Off to Google.

Edit: is this what you were talking about? [http://ubuntuforums.org/showthread.php?t=486870](http://ubuntuforums.org/showthread.php?t=486870)

---

### Post by coffeecat on 2009-11-10
Apologies for not noticing the 9.10. Getting late here....

> **lazyastronomer said:**
> And about those RAM sticks... can you just plug them into a USB port and be done with it, or do you have to take the machine apart and install it? Off to Google.

It's a simple job, but you have to take the side of the case off. The slots for the RAM sticks are fairly distinctive and a bit of googling should find you a picture of a typical motherboard. If you take the case side off, there might be a label on the motherboard telling you what make and model it is. Then a further bit of googling will reveal exactly which RAM sticks you need - there are a bewildering variety of types. Don't touch anything inside until you've earthed yourself against a radiator to discharge any static.

Or, with your motherboard or computer make and model, you could look it up at:

[http://www.crucial.com/](http://www.crucial.com/)

By the way, I suggested putting another RAM stick in hoping that, like me, you've got boxes containing bits from old disassembled computers. Unfortunately, to buy new, the sticks you'll need for that vintage of computer (probably DDR DIMM if a desktop) will work out more expensive MB for MB than the newer DDR2 and DDR3 sticks. Something to think about.

---

### Post by lazyastronomer on 2009-11-10
> **coffeecat said:**
> 
By the way, I suggested putting another RAM stick in hoping that, like me, you've got boxes containing bits from old disassembled computers. Unfortunately, to buy new, the sticks you'll need for that vintage of computer (probably DDR DIMM if a desktop) will work out more expensive MB for MB than the newer DDR2 and DDR3 sticks. Something to think about.

[http://www.google.com/products?q=DDR+ram+price&aq=f](http://www.google.com/products?q=DDR+ram+price&aq=f)
[http://www.google.com/products?q=DIMM+ram+price&aq=f](http://www.google.com/products?q=DIMM+ram+price&aq=f)

Crap, that's expensive! I don't have this kind of money, I'm just a kid!

Ah, well, I'll see what I can do... maybe I can find someone who's got an old computer that I can have. If not, what was that about the Alternate Install you mentioned? It looked a bit complicated to me, though, I'll have to see if I'll be able to figure it out. Will I be able to make it by with slightly less than the required RAM?

---

### Post by krakenfury on 2009-11-10
Look at this page.  If you use the Xubuntu alternate installer, you should be able to get your motor going.  :)

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by Onesimus on 2009-11-11
> **lazyastronomer said:**
> [http://www.google.com/products?q=DDR+ram+price&aq=f](http://www.google.com/products?q=DDR+ram+price&aq=f)
[http://www.google.com/products?q=DIMM+ram+price&aq=f](http://www.google.com/products?q=DIMM+ram+price&aq=f)

Crap, that's expensive! I don't have this kind of money, I'm just a kid!



If you are a kid, and have no knowledge (or even limited knowledge) of the workings of a PC, then it would be extremely inadvisable to be removing the cover of the PC and inserting RAM.  It is not a simple process, and not all RAM is the same - and needs to be bought to be compatible with the machine.

This is not meant to be patronising, but well intended.

---

### Post by lazyastronomer on 2009-11-12
> **Onesimus said:**
> If you are a kid, and have no knowledge (or even limited knowledge) of the workings of a PC, then it would be extremely inadvisable to be removing the cover of the PC and inserting RAM.  It is not a simple process, and not all RAM is the same - and needs to be bought to be compatible with the machine.

This is not meant to be patronising, but well intended.

I'm 15, and have a pretty good knowledge of how a PC works. I'm not an expert, but am definitely capable of swapping out RAM.

Not that I intend to. I'm off to check out the "Alternate Install."

---

