---
title: "installation without defragging windows"
date: 2009-10-01
forum: General Help
---

### Post by mountainhere on 2009-10-01
Hi folks...

First off I'm new to ubuntu and i'm stoked with it thus far. I have for the last year been using (with frustration) xandros in easy and advanced mode on my eeepc. ubuntu 9.04 is awesome, and i'm excited to learn and be part of this community.

In my enthusiasm in the last few days i tried to install ubuntu on an old dell inspiron 4000 to be used in our house as a basic email/surfing machine for my roommates. I should say i'm really a beginner with computers and what little experience i have, has been in the last year with linux. Anyways i failed to defrag windows before installing and things have ground to a halt. I tried installing regular install and also html. I tried manual partioning and guided aswell as trying system rescue with no real success. I don't have one but would i need a dell formatting disc to get things going again or do I have any other options?

Additionally and perhaps this has more to do with problems, the computer has only a 5g harddrive and 267 or thereabouts of ram. Whether this lies at the heart of the problem or not my thought was that a stripped down linux os that's easy to use and doesn't take up what little space there is would be a good idea. Additionally introducing folks to ubuntu would be nice. At the moment my efforts at the moment in this regard are likely to produce the opposite result if i can't get moving on this problem. 

Thanks in advance for any suggestions folks might have.

---

### Post by trstncmpbll on 2009-10-01
any way you can give me a readoff of what happens. does it fail during partitioning or install. what does it say? you could have a bad cluster or cylinder shape on your hd. also you can live boot the disk and -f disk format it and it will tell you if it is the hd

---

### Post by kestrel1 on 2009-10-01
Personally I wouldn't try running Ubuntu on a system that is not going to do it justice. Use something like Xubuntu or even Puppy Linux.
Are you trying to keep Windows on this drive (don't do it) :-)
Use Gparted from the live CD & repartition the drive.

---

### Post by mountainhere on 2009-10-01
Hi there thanks for getting back to me...
I'm not at home with the computer but I can tell you that it does sort of install. It takes about 2 hours but it does install but it's so slow as to be unworkable. I mean really slow.

---

### Post by mountainhere on 2009-10-01
Thanks Kestrel1. I do have xubuntu on a disc but know very little about it. I can try this but i wonder if there is a problem with the harddisc that will effect an install.

---

### Post by DeMus on 2009-10-01
> **mountainhere said:**
> Hi there thanks for getting back to me...
I'm not at home with the computer but I can tell you that it does sort of install. It takes about 2 hours but it does install but it's so slow as to be unworkable. I mean really slow.

When you're home try the following:

Boot from the Ubuntu disk
Choose install
Continue till step 4: partitioning
Choose manual
Now you get a list of all partitions on your hard disk
Delete them all, one by one (FAT, NTFS, EXT2, EXT3, all of them)
Then return to the previous step and choose automatic partitioning.
Continue till the end.
It is not the most sophisticated way of partitioning the disk but it works and since you only want to surf and do some e-mailing it is good enough.
During installation the program asks you for a name and password. Since you install Ubuntu use your name and choose a good password.
With that password you can log in AND become root (administrator) when needed. So only you can perform root tasks.

---

### Post by mountainhere on 2009-10-01
hey trstncmpll, thanks for your suggestions. i'm interested to try -f disk. excuse my ignorance but is this a terminal command, can you tell me what to do or should i check wiki for info...
cheers

---

### Post by mountainhere on 2009-10-01
Thanks DeMus... I will try this though I'm thinking this is one of the things i tried a couple of nights ago. I'll def. give it a whirl. The password suggestion i'll definitely take up, makes sense for me to take that role.
cheers

---

### Post by jmszr on 2009-10-01
mountainhere,

+1 - kestrel1's post: 

The recommended minimum system requirements for Ubuntu: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) (as you've noticed) won't allow Ubuntu to run properly on your system.
Either Xubuntu: [http://www.xubuntu.org/get](http://www.xubuntu.org/get) or Puppy Linux: [http://www.puppylinux.org/](http://www.puppylinux.org/) would be more appropriate for your system.

You also might wish to try Crunchbang Linux: [http://crunchbanglinux.org/](http://crunchbanglinux.org/) .

---

### Post by kestrel1 on 2009-10-01
> **jmszr said:**
> mountainhere,

The recommended minimum system requirements for Ubuntu: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) (as you've noticed) won't allow Ubuntu to run properly on your system.
Either Xubuntu: [http://www.xubuntu.org/get](http://www.xubuntu.org/get) or Puppy Linux: [http://www.puppylinux.org/](http://www.puppylinux.org/) would be more appropriate for your system.

You also might wish to try Crunchbang Linux: [http://crunchbanglinux.org/](http://crunchbanglinux.org/) .

I tried out crunchbang but didn't think much to it personally. With a 5gb HDD I would also be looking at a slightly larger drive. You may be able to an old 20gb if you are lucky, but obviously it would bepend wether the machine is able to use a larger drive.

---

### Post by mountainhere on 2009-10-01
Thanks all for the help and suggestions i'll have another bash at this tonight. I'm going to try xubuntu and see what happens after using gparted.
cheers

---

### Post by ram2500 on 2009-10-01
You can pick up a really zippy IBM ThinkCentre or Intellistation (I've seen several Intellistations with 3GHz Pentium 4 hyperthreading CPUs, and even a couple of dual AMD Opteron CPUs.) These machines are only a couple of years old and are dirt cheap--they only cost around $80-200, so it won't break the bank. They usually come out of a corporate environment, so they are usually well cared for.I bought a couple to use as servers and set up a small network in my classroom, and all it needed was a RAID card, 2-3 hard drives and I was good to go! You might want to consider replacing your machine, as a computer with a 5GB hard drive is really, really old and I can only imagine what the processor is (probably Pentium II at best). When I built my Athlon x2 machine that I'm using right now, I thought, well, I only need a 160GB hard drive. Well, when it comes to files, I tend to hold onto them. 160GB wasn't enough at all, in fact, I ended up taking that drive out and putting in a 500GB Seagate, so I know you can never have enough storage. 

These Intellistations and ThinkCentres are comparable to a new computer (I think). I was wondering if I really needed to spend $600 om my computer build when could have bought two or three ThinkCentres or Intellistations for my personal use. Bet Vista would run like a top! I have Fedora on them with server software (Samba) and network the Macs and Dell PCs in my classroom to the two Intellistations. My students store all their files on it, and I share space with the multimedia class down the hall from me. It is set up in a RAID mirroring configuration, and uses a couple of SATA drives I had lying around. All I needed to buy was the RAID cards, an extra hard drive or two, and I was in business! But, I'm sure you won't need all that for your use--I'm using these as servers.

If you decide to go this route, avoid the NetVista models...they usually have pathetic Celerons and are older models.

If you want a laptop, a ThinkPad or HP/Compaq Evo can be had for around $150-250 with a Pentium 4 or Celeron derivative and about 512megs of RAM.

---

### Post by mountainhere on 2009-10-01
Thanks ram2500. The plan is to try and make use of this computer without spending money, so i'm going to try with it as is.

I do have a new problem though. I used gparted to delete current partitions and then have attempted to boot from xubuntu disc. When trying to boot it tells me ' grub loading... please wait'
then i get 'error 22'

anyone out there know what this would mean and a possible solution.
thanks in advance!

---

### Post by jmszr on 2009-10-01
mountainhere,

You have a Grub error, this is the information I was able to find: [http://members.iinet.net.au/~herman546/p15.html#22](http://members.iinet.net.au/~herman546/p15.html#22) and: [http://ubuntuforums.org/showthread.php?t=1203368](http://ubuntuforums.org/showthread.php?t=1203368) and: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I don't know how much help that will be to you; if not enough, I would suggest that you start a new thread with a concise explanation of your problem and a link to this thread  (copy this thread's URL and Go Advanced with the message box and you can insert the link). Please use a descriptive title.

Wish I could be of more help , but I've never encountered this problem.

---

