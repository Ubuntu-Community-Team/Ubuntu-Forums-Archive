---
title: "Questions about dual booting"
date: 2012-02-03
forum: General Help
---

### Post by lou002 on 2012-02-03
I'm not new to Ubuntu (I've been using Wubi for awhile now and I used to have a whole laptop dedicated to Ubuntu until it broke) but I've got a few questions as I've never dual booted before.

So I took the appropriate steps--I created a Windows repair DVD, Put a system image on my external drive and backed up Windows today--but I had a few questions:

What is the optimal hd space for the OS? I was thinking of using 10gbs as I really only want to mess around in Ubuntu and learn it, not use it as a full time OS. It'll be more like a part time OS for when I don't want to play WoW and don't need to sync my iPad.

Is there an easy way to get arid of the OS if I hypothetically need those gigs back? I only ask because I don't want to do something that could potentially destroy the Windows 7 Home Premium (64bit edition) of my desktop as it's the only machine I have and I don't want to do anything to it that I might not be able to fix.

And finally, is there a recommended flavor of Ubuntu that you'd suggest? Just 'normal' Ubuntu? Xubuntu? I have a Dell Inspiron 560 with a Intel(R) Celeron(R) CPU 450 @ 2.20GHz (2.19 GHz is also next to that on the info chart), 2.00 GB RAM (despite being a 64bit machine) Intel(R) G45/G43 Express Chipset for graphics.

Any help/advice/answers are greatly appreciated! That is one thing I love about the open source community, always willing to help someone learn :)

---

### Post by BC59 on 2012-02-03
Some answers:
Appropriate space...10GB for Ubuntu is little space. Only the tmp files produced during copying, burning a CD etc, are covering the free space. The system is using 4-5GB and adding applications needs more. You need a swap partition as well. So all these can be squeezed to no less than 15GBs.
About destroying Windows, playing with partitions is always a risk. As a last resort in case of a disaster you could download a legal Windows 7 .iso and burn a DVD to reinstall everything. There is always solution.
Now if you need to delete Ubuntu, you will need a disk like that, to restore the Windows boot system.
About the most recommended Ubuntu, it's always the "basic Ubuntu" last version. Now is 11.10. In April comes the 12.04.

---

### Post by KingYaba on 2012-02-03
I recommend partitioning 20GB for Ubuntu and I recommend using Ubuntu 10.04 or the latest Xubuntu release (11.10). 10GB is fine, too. You can always delete the Ubuntu partition and merge back into your Windows one. Doing that will require the Ubuntu live CD and the use of GParted. It will also take some time but you're doing the right thing by backing up your data before you begin the Ubuntu install. 

But there's the thing: is there a problem with Wubi?

---

### Post by Paqman on 2012-02-03
> **lou002 said:**
> 
What is the optimal hd space for the OS? I was thinking of using 10gbs

That should be fine. I wouldn't bother with anything over 1GB for swap, unless you want to be able to hibernate, in which case go for a 2GB swap.

> 
Is there an easy way to get arid of the OS if I hypothetically need those gigs back?


Sure, you can use Windows to restore the MBR back to what it was before you installed GRUB, then just delete the Ubuntu partitions and expand your Windows ones.

> 
And finally, is there a recommended flavor of Ubuntu that you'd suggest?

You can use whatever you like. Regular Ubuntu should run fine. With Intel integrated graphics you might find the Unity 2D desktop is snappier than the default 3D one, just log out and click the cog by your user name to switch.

---

### Post by lou002 on 2012-02-03
> **KingYaba said:**
>  But there's the thing: is there a problem with Wubi?

It's slow, especially when running the Ubuntu updates and trying to use the internet. Oh and neither Kubuntu or Xubuntu wants to install (they come as options) Otherwise, absolutely nothing.

---

### Post by lou002 on 2012-02-03
> **Paqman said:**
> That should be fine. I wouldn't bother with anything over 1GB for swap, unless you want to be able to hibernate, in which case go for a 2GB swap.

Do I have to do all of this manually then? or is there an automatic option?



>  Sure, you can use Windows to restore the MBR back to what it was before you installed GRUB, then just delete the Ubuntu partitions and expand your Windows ones.

MBR? Do you mean the repair disc I burned? I don't have an actual copy of Windows (Dell doesn't package recovery discs in anymore)



> You can use whatever you like. Regular Ubuntu should run fine. With Intel integrated graphics you might find the Unity 2D desktop is snappier than the default 3D one, just log out and click the cog by your user name to switch.

Wouldn't Xubuntu work better since it's less graphics intensive and 'lightweight' or maybe Lubuntu (sorry! I've been reading about this to make sure I do find the right one. I just can't remember if Lubuntu is 'officially' apart of the *Buntu family yet.)

---

### Post by afz12 on 2012-02-03
Hi lu002

I have read that 5 GB is the recommended minimum but for "playing around" 10 GB will be fine. I have one notebook with dual boot XP and Ubuntu 10.10 and another Win7 machine that I may dual boot with Ubuntu 11.10 or 12.04 alpha (as this version actually seems to go quite well!). I have had never ending hassles with Thunderbird on Ubuntu 10.10 but 11.10 works automatically - I suggest this. Also its "Unity" interface isn't as bad as people make out and if you start with this you'll probably be content with it :)

However the issue of "removing" Ubuntu as a partition isn't straightforward. I tried this once and just gave up. Ubuntu lingers as a log on screen etc and is just a nuisance. However partitions remain seperate so it is probably unlikely that anything that "blows up" on your Ubuntu partition will interfer with your Windows partition. If anything goes wrong it will occur during install. Make sure you defrag your hard drive first and be careful not to completely install Ubuntu!

An alternative, and very safe alternative is to use Virtualbox for example and install Ubuntu as a virtual machine. It will run a bit slower than "native' but function much the same. Also you can "dynamically assign" a lot more hard drive space (e.g. 100 GB) and this will only be used if you actually use up the 100 GB. Otherwise Virtualbox will only use hard drive that is immediately used (perhaps only a few GB). Interestingly though, it doesn't seem to "shrink back" if you remove files. Still, you can always delete the Virtual machine (very easy) and start others.

Another limitation is that Virtualbox will only access up to 1/2 your RAM so having 4~8 GB available is a good idea.  Good luck!

---

### Post by Paqman on 2012-02-03
> **lou002 said:**
> Do I have to do all of this manually then? or is there an automatic option?

Yep, there's an automatic option. During install you can tell it how much of the disk you want to devote to Ubuntu. A swap will be set up automatically, but I can't tell you how big it would be.


> 
MBR? Do you mean the repair disc I burned? I don't have an actual copy of Windows (Dell doesn't package recovery discs in anymore)


Sorry. MBR = Master Boot Record.

It's a special section of your hard drive that is used to boot operating systems. Ubuntu uses a bootloader called Grub. If you remove Ubuntu you'll also have to remove Grub and return it to Windows-only settings. Don't worry about that, it's pretty straightforward and we can cross that bridge if we need to.




> 
Wouldn't Xubuntu work better since it's less graphics intensive and 'lightweight' or maybe Lubuntu (sorry! I've been reading about this to make sure I do find the right one. I just can't remember if Lubuntu is 'officially' apart of the *Buntu family yet.)

Define "better"? Choice of desktop environment is very subjective. Regular Ubuntu should work fine, as you've got the 2D option if you need it. Other people like K/X/Lubuntu. You're not stuck with one either, you can install any DE you want at any time, regardless of which one your originally installed.

---

### Post by Paqman on 2012-02-03
> **afz12 said:**
> 
An alternative, and very safe alternative is to use Virtualbox for example and install Ubuntu as a virtual machine.

On a Celeron with 2GB I wouldn't really recommend this. It would work, but it wouldn't be fun to use.

---

### Post by lou002 on 2012-02-03
> **Paqman said:**
> Yep, there's an automatic option. During install you can tell it how much of the disk you want to devote to Ubuntu. A swap will be set up automatically, but I can't tell you how big it would be.

Well that's good. I was about to ask about that. I know some distros are command line installs and all that. I barely know sudo apt-get install/remove. :) I am learning though!




> Sorry. MBR = Master Boot Record.

It's a special section of your hard drive that is used to boot operating systems. Ubuntu uses a bootloader called Grub. If you remove Ubuntu you'll also have to remove Grub and return it to Windows-only settings. Don't worry about that, it's pretty straightforward and we can cross that bridge if we need to.

I doubt we'll need to but always good to know.






> Define "better"? Choice of desktop environment is very subjective. Regular Ubuntu should work fine, as you've got the 2D option if you need it. Other people like K/X/Lubuntu. You're not stuck with one either, you can install any DE you want at any time, regardless of which one your originally installed.

Well "better" as in faster, less strain on the graphics card or RAM, etc.

A follow up--my system is 64 bit but would it really matter which one I use?

---

### Post by coldjeanz on 2012-02-03
> **KingYaba said:**
> I recommend partitioning 20GB for Ubuntu and I recommend using Ubuntu 10.04 or the latest Xubuntu release (11.10). 10GB is fine, too. You can always delete the Ubuntu partition and merge back into your Windows one. Doing that will require the Ubuntu live CD and the use of GParted. It will also take some time but you're doing the right thing by backing up your data before you begin the Ubuntu install. 

But there's the thing: is there a problem with Wubi?

I recently switched from Wubi to a dual boot. There is a big difference. Everything takes longer to load using Wubi (when I say everything, I literally mean everything). If you use dropbox with Wubi or are transferring data from an external hard drive, the system basically becomes unusable. You have to wait for whatever it's doing to finish. Not only that but the rate of transfer is also much slower. Worst of all it crashes a lot and forces you to hard reboot. Wubi is definitely not something you want to keep using for a long period of time, I got rid of it after 2 weeks.

---

### Post by lou002 on 2012-02-04
Okay, so I installed Xubuntu....**BUT** Xubuntu says I've got a problem. Installed the OS..but apparently didn't partition enough to install the upgrades (it says that I've only got 3.4gbs on the partition and not enough space or something--the next time I'm on it, I'll take a screen shot)

It's very hard for me to explain because I don't understand. As soon as I get done with something, I'll a screen shot and edit this post.


Here's the screenshots I took. It says I gave / less than 550 mb, and that i have 572.0 mb of free space. I have *NO* clue how that happened as I did my best to partition it. I was trying to give it 10gigs but I had no numeric way of knowing.

What do I do!? How do I fix this without messing up windows? Can I just install over the xubuntu?

Any help is helpful.
What is a simple way to fix this? I'm still a linux newb. 

Oh geez..I am seriously freaking out here!

---

### Post by Paqman on 2012-02-08
> **lou002 said:**
> 
What do I do!? How do I fix this without messing up windows? Can I just install over the xubuntu?

Any help is helpful.
What is a simple way to fix this? I'm still a linux newb. 

Oh geez..I am seriously freaking out here!

Ok, don't worry, it should be pretty simple to fix.

[LIST=1]
[*]Boot up into your LiveCD or USB (the one you used to install)
[*]There will be a program called Gparted or "Partition Editor" on the disk, launch it
[*]Right click on your swap partition and "swapoff"
[*]Adjust the partitions so that your root now has 10GB. Hopefully you have some free space adjacent to it that you can expand into, otherwise you'll need to shift an adjacent partition over, which is very, very slow. If your root partition is inside an extended partition you may need to expand or move that before you can do likewise with the partition(s) contained within it.
[*]Hit "apply" and go make a cuppa, it could take quite a while depending on how much data has to be moved.
[/LIST]

---

