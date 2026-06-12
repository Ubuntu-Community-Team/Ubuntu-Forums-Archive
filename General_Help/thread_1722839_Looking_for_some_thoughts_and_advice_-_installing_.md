---
title: "Looking for some thoughts and advice - installing Ubuntu on a new PC"
date: 2011-04-06
forum: General Help
---

### Post by ursoouindio on 2011-04-06
Hello you all!

Well, I'm getting a new laptop today. It's a very nice piece of hardware with Sandy Bridge Core i7, 8 GB Ram and NVidia GT-540M with Optimus. It's based on Clevo W150HNQ barebone.


I wonder what should I do, regarding Ubuntu. It comes with Windows 7, but I would like to put Ubuntu on it as well.

I actually run Ubuntu 10.04 32-bit. I have a bunch of things that I need  and I think some of then depend on 32-bit only libraries. I can't really say because I've never tried 64-bits.
I haven't followed newer Ubuntu versions because 10.04 was fine for me and I didn't want to risk anything due to incompatibilities.


Since I'm getting a new pc, I could get the newest Ubuntu, it looks good. Would you recommend it?
I really consider going to 64-bits. Is it very stable? (last time I checked up for 64-bits systems, a couple of years ago, it didn't seemed like that.)

If I get the 64-bits, would it be compatible with 32-bit libraries? (Windows has some kind of compatibility thing, but I'm not sure how it works)
If not, what would you recommend, getting a Virtual 32-bit machine? Not going for 64-bit at all?

I also wonder if I should wait for the official release of Natty. Or should I get the Beta for now and then update it? Or should I go for 10.11 and then update it at the end of the month?
Actually, I'm not much comfortable with major releases updates...


So, I would really appreciate any thoughts. I'm kind of slow when it comes to Linux development but I'm really looking forward for a great experience with Ubuntu on my new machine.
What are the main improvements on Natty since 10.04?? (If there are some read on its improvements I would like to know, I looked around but haven't found any objectively).

Best regards! :)

---

### Post by Dupointx on 2011-04-06
> **ursoouindio said:**
> Hello you all!
Since I'm getting a new pc, I could get the newest Ubuntu, it looks good. Would you recommend it?
I really consider going to 64-bits. Is it very stable? (last time I checked up for 64-bits systems, a couple of years ago, it didn't seemed like that.)

If I get the 64-bits, would it be compatible with 32-bit libraries? (Windows has some kind of compatibility thing, but I'm not sure how it works)
If not, what would you recommend, getting a Virtual 32-bit machine? Not going for 64-bit at all?

I also wonder if I should wait for the official release of Natty. Or should I get the Beta for now and then update it? Or should I go for 10.11 and then update it at the end of the month?
Actually, I'm not much comfortable with major releases updates...

The newest Ubuntu (11.04) is going to have Unity, which is a new desktop. It's probably going to have plenty of bugs and other head-ache inducing problems, so i suggest sticking with the LTS (10.04) or using 10.10 unless you like filing bug reports. 10.10 is pretty good I think, it's better than 10.04 in my opinion, but it's not supported as long as 10.04.

I recommend using the 32-bit (i386) version because 64-bit has some strange problems, or at least I had problems using it. First, I think by default the 32-bit lib's are not included, so if you need them you will have to install them. I also had problems with 3rd party applications like Folding@Home, but I didn't use the 32-bit lib's. I didn't notice any notable performance improvements on the 64-bit version either, so I didn't see the point in using it.

I don't recommend using the Beta because it's going to be buggy, even more buggy than usual. For 11.04 I would even wait some time after it is officially released so that the bugs get squashed. Updating the Beta to the release would not be a problem, you just update like normal, but updating 10.10 to 11.04 may brake the install outright. I always burn a new live-cd and install fresh.

---

### Post by ursoouindio on 2011-04-06
Very nice to see your opinnion Dupointx. It seems we share some apprehensiveness on running for the state-of-the-art development and compromising compatibilities.

The major drawback on stinking with 32-bt system is its memory limitation, as I'm my new machine will have 8 GB of RAM.

Sticking with 10.04 (or even 10.10 that I haven't tried) would be ok. I already know it and have managed to customize its looks for a pleasant usage. I think most of my tweaks around there would be useless on a newer Ubuntu, but thats something I would work it around.

Unity looks good for me, I'm not sure if I got what exactly it should do, but as a nicer interface to manage my files it seems very fine. But I wouldn't go for it if its buggy.

Thanks again!

I would like to hear some oppinios from people that disagree fom us as well ;)

Regards!

---

### Post by ursoouindio on 2011-04-06
Anyone else?

I just got my new notebook.
I'm setting up the basics on Windows and got my disk partitioned. 

I'm just waiting to close the deal on the Ubuntu option to install it.
I think there are more people with good opinions on this :)

---

### Post by cek on 2011-04-06
I've been using 64bit since the very earliest stages of its development, I remember running 64bit gentoo circa 2003/2004.

That said, I've run 64bit ubuntu since 6.10 and any problems that were there are long gone by now.  I've got a full 64bit system and I cannot think of anything that has caused me any problems.  Even flash has 64bit support now.

That said, I wouldn't hesitate one second to run 64bit.  As far as picking between 11.04 and 10.10, that's really a matter of personal preference.  10.10 has some issues with wireless drivers in the kernel (that you can fix by getting updated drivers from wireless.kernel.org), so I personally would go with 11.04 beta, and just keep it updating.

---

### Post by perspectoff on 2011-04-06
I haven't had any problems running 64-bit for quite some time.

Yes, I had to manually install ia32-libs a few versions ago (I think it's done automatically now) for some 32-bit applications to run (like some versions of Skype), but I think even that module is now installed automatically in 64-bit versions.

Having said that, I don't notice much difference in speed between 32-bit and 64-bit versions these days anyway (in the past (prior to Karmic) 64-bit versions were much faster for me). Probably RAM and processor speed is the more important factor, anyway, and my computers are all relatively powerful (I don't have any ARM or similar types of computers).

Then again, I don't run multiple virtual machines at the same time and never have more than 6 or 8 programs running at the same time. 

Someone who does that perhaps should weigh in (and if you don't plan to do that, it is a moot point).

I find no differences for gaming. (Networking connections are the more important factor for me when for networked games, anyway).

The same thing goes for servers -- it is the bandwidth and network connections that make the difference, not whether I have 32-bit or 64-bit.

You know, you could set up two Ubuntu partitions and try them out side by side. A new laptop has, what, a 500Gb hard drive? Plenty of room to do that...

In general I recommend doing that anyway. I never do straight updates -- I leapfrog. I duplicate my existing Ubuntu OS to a second Ubuntu partition and work on that one for updates. Only when I'm sure the update is working properly do I migrate away from the first partition.

Here's the method I've used:
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

The computer I am writing this on has a Windows 7 partition and a Windows boot partition, a 2 Gb Linux-swap partition, and 6 Ubuntu/Kubuntu partitions. 

Another computer has Windows XP, Ubuntu/Kubuntu, CentOS, and OpenSuse.

Sooner or later you may get the urge to compare. Setting up your hard drive properly in the beginning lets you do this painlessly in the future.

---

### Post by ursoouindio on 2011-04-06
Thanks cek and perspectoff for your answers!

Yeah, I'm thinking in giving a try on 64-bit. 

Although, I'm afraid for going to 11.04 because I don't see anyone saying like "Go for it, it is awesome and will work fine!". Unity does look interesting to me but I'm not in for free headaches. I'm not sure what kind of wireless troubles are going on, but if I face them I bet I could figure it out much more simply than avoiding bugs in the main system.

At first I thought on installing 2 Linuxes, a 32 and a 64-bit, but that would not be the best solution - to have two independent Linux systems. I rather build up a 32-bit virtual machine, if it could handle my needs.

Thank you guys very much, I'm falling for my 10.04 (or even 10.10) 64-bits.

---

### Post by oldos2er on 2011-04-06
Another vote for 64-bit.

I don't think there is linux support for Optimus yet.

---

### Post by techunit on 2011-04-06
Be sure to partition you harddrive in windows or with a utility garenteed not to corrupt the windows drive if you are going to dual boot.

---

### Post by ursoouindio on 2011-04-06
oldos2er, Optimus still isn't officially supported. But there is already some workaround to take a better advantage of the pair of GPUs. I don't recall exactly what it is, but I've read that some people developed :)

TechUnit, I'm going to use gparted to resize the Windows partitions... I hope it works, I don't want to go through all the Windows set up.

Thanks!

---

### Post by techunit on 2011-04-06
NO! It is common knowledge that Gparted will damage boot configs in Windows Vista & 7 don't do it. If you already did please PM me with the tread for your problem and I will fix it.

---

### Post by madjr on 2011-04-06
@ursoouindio

i would definitely advise to go with ubuntu 11.04 once its out.

I've been using it since a while now and i can definitely say is very good (even tho still a month for final release).

it has the latest kernel, which should work better with most hardware.

also in case you dont like unity too much, it has a "classic desktop" option like the one you are used to.

i think this will be a very good release.

if for any reasons you run into any problems, you can always stay with 10.04 or 10.10 for a while longer.

regarding 64bits, you should try both and see which one feels better for you.

have fun :popcorn:

---

### Post by ursoouindio on 2011-04-06
> **techunit said:**
> NO! It is common knowledge that Gparted will damage boot configs in Windows Vista & 7 don't do it. If you already did please PM me with the tread for your problem and I will fix it.

Techunit, thanks a lot for the concern!

I haven't damaged anything yet, but actually I'm falling for wiping out the Windows partitions and installing it all over again.

This introduces another question for my situation:

What's the best way to use Windows and Ubuntu on the same machine and both sharing the same data (docs, multimedia files, download and temporary folders...)

I plan to keep one NTFS partition to Windows 7, another NTFS for the mutual data and finally EXT4 and a swap for Ubuntu.
Is it ok?

I don't really know the difference between EXT4 and EXT3. I suppose EXT4 would be better since it is newer.

---

### Post by ursoouindio on 2011-04-06
> **madjr said:**
> @ursoouindio

i would definitely advise to go with ubuntu 11.04 once its out.

I've been using it since a while now and i can definitely say is very good (even tho still a month for final release).

it has the latest kernel, which should work better with most hardware.

also in case you dont like unity too much, it has a "classic desktop" option like the one you are used to.

i think this will be a very good release.

if for any reasons you run into any problems, you can always stay with 10.04 or 10.10 for a while longer.

regarding 64bits, you should try both and see which one feels better for you.

have fun :popcorn:

madjr, thanks for your thoughts. Nice to see a different opinion.

I actually like Unity, from what I've seen on screenshots and video demonstrations. I'm only afraid of if it will be buggy or if it would limit my customizing possibilities. I'm the kind of user that's always tweaking around to make everything work the way he wants to.

Your kernel argument is quite valid, as I own a laptop with recent hardware.


About trying, I was looking to avoid having to install Ubuntu all over again, since I have lots of things to set up and get to working. But maybe I could try it out, Ubuntu is much easier to install and set up than Windows.

Hmmm... now you got me wondering on that too.
I guess that's what I asked for :P

Thanks!

---

### Post by madjr on 2011-04-07
> **ursoouindio said:**
> madjr, thanks for your thoughts. Nice to see a different opinion.

I actually like Unity, from what I've seen on screenshots and video demonstrations. I'm only afraid of if it will be buggy or if it would limit my customizing possibilities. I'm the kind of user that's always tweaking around to make everything work the way he wants to.

Your kernel argument is quite valid, as I own a laptop with recent hardware.


About trying, I was looking to avoid having to install Ubuntu all over again, since I have lots of things to set up and get to working. But maybe I could try it out, Ubuntu is much easier to install and set up than Windows.

Hmmm... now you got me wondering on that too.
I guess that's what I asked for :P

Thanks!

dont worry, 11.04 comes with a **classic mode** with the same gnome desktop you are using now, in case you find unity a bit limited at this stage.

i think it was a very good decision to include it, unlike "other" OSs that force an UI change on you from day 1.

---

### Post by ursoouindio on 2011-04-07
I will give it a try on the beta. I'm downloading it right now, its damn slow...


I'm just thinking here, I'll have to compile some scientific projects such as Sundials or Ipopt and I wonder if there will be any trouble on going for 64-bit. Their documentations don't mention any incompatibilities, but also aren't clear of the opposite. Guess I'll have to check myself :P

---

### Post by flynx on 2011-04-24
I just bought the same Clevo you did.  Trying to get Ubuntu installed.  Maybe we can collaborate.  PM me.

---

### Post by flynx on 2011-04-24
I tried this kernel module here for switching between the nvidia and intel card on the W150HNQ and it seems to work.  The little LEDs that indicate which graphics card is running switched on and off.

[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

---

### Post by ursoouindio on 2011-04-25
> **flynx said:**
> I just bought the same Clevo you did.  Trying to get Ubuntu installed.  Maybe we can collaborate.  PM me.

Hey, very nice to get a fellow on this!!

I tried that script, it does work!
But it also made my dGPU unaccessible to my Windows on dual boot. I managed to revert it, but I don't like the idea so far my system is yet unstable. I'm leaving the dGPU alive all the time, while using the iGPU to render everything.

---

### Post by naklinaam on 2011-04-25
> **ursoouindio said:**
> 
I haven't damaged anything yet, but actually I'm falling for wiping out the Windows partitions and installing it all over again.

This introduces another question for my situation:

What's the best way to use Windows and Ubuntu on the same machine and both sharing the same data (docs, multimedia files, download and temporary folders...)

I plan to keep one NTFS partition to Windows 7, another NTFS for the mutual data and finally EXT4 and a swap for Ubuntu.
Is it ok?


probably already too late but since you are talking of reinstalling windows, I must add one step I always do with a new machine... use clonezilla to grab an image of my 'virgin' drive before I do anything else on the machine... gives me an ability to 'factory reset' if I must.
In terms of sharing data between the 2 OSes.. I have it set up exactly like yours.. Windows on 1 partition, Ubuntu on another, and all my data on a separate NTFS partition. I then rename the Documents folder in my home folder and create a simlink pointing to the data in the common NTFS partition, thus my data automagically lands up in the common partition.
Similarly, I move "My Documents" in windows to also point to the same partition.

---

### Post by flynx on 2011-05-11
had my clevo running great on natty 64bit.

rebooted today and no graphics.   "low graphics mode" doesn't even work.

gdm exits with "code 2"

:-(

the only thing i can think i did was add test_off.sh to my startup apps.  removed it but the problem remains.

EDIT:  removal and re-installation of gnome desktop fixed whatever was wrong.

---

