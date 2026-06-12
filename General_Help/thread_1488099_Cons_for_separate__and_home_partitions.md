---
title: "Cons for separate / and /home partitions?"
date: 2010-05-19
forum: General Help
---

### Post by Mud.Knee.Havoc on 2010-05-19
Sorry, I couldn't find a better subforum for this...

I suggested that somebody on identi.ca use separate / and /home partitions to make upgrading from one version of a distro to another easier.  This is something that I've always done, as I just need to format/reinstall the OS, then my favorite programs, and everything is back to normal.  But I got three replies back in short order saying that it is messy and will cause problems - which I can't understand. 

I'm honestly interested why this would be a messy alternative.  I've only seen it mess things up when "upgrading" from one distro to a completely different one (such as Ubuntu to Fedora), as it messes up ownership - can be chowned, though - but when upgrading from one version of Ubuntu to the next, it seems to me to be a fantastic idea.  If I was to run into a problem with a new version of a program not working, I guess I'd just delete the .whatever config file or directory and let the program create a default one.

Any thoughts?  I'm truly interested if people have had problems with keeping a separate /home and /, and how major these problems would be.  I just can't see it, but maybe I'm just a lucky guy! :)

---

### Post by howefield on 2010-05-19
> **Mud.Knee.Havoc said:**
> ...which I can't understand.

Don't worry, the only thing you need to understand is that you are correct, they are wrong.

But you'd be better asking them to explain why they might believe that than asking some third party.

---

### Post by nmaster on 2010-05-19
I'd also like to know if there are any downsides to this.  If its as good as many people say, then I think I'll do it when I install 10.04.

---

### Post by linuxman94 on 2010-05-19
I am currently running a separated home partition and i haven't had any problems.  

Here is a great tutorial for separate home partitions.  [Separate Home]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Mud.Knee.Havoc on 2010-05-19
> **howefield said:**
> Don't worry, the only thing you need to understand is that you are correct, they are wrong.

But you'd be better asking them to explain why they might believe that than asking some third party.

I tried, but the 140 character limit was killing me. :D

[Here's the conversation]("http://identi.ca/conversation/32709725") if you'd like to see.  Maybe I wasn't making myself clear - or I misunderstood something.  I'm "ooboontoo" there, by the way. :)  I tried to be as clear as possible within the limits of so few characters.

---

### Post by mb_webguy on 2010-05-19
I usually use separate / and /home partitions, for basically the same reasons as stated by the OP.  *nix systems were designed to be spread across numerous physical and logical drives, and as long as each of the different volumes recognizes *nix-style ownership and permissions, there's really no problem.  There's absolutely no difference in a PC having /home on a separate partition than a server having /var or /tmp on a separate partition.

---

### Post by Mud.Knee.Havoc on 2010-05-19
> **neal.m.master said:**
> I'd also like to know if there are any downsides to this.  If its as good as many people say, then I think I'll do it when I install 10.04.

In my experience, it's fantastic.  Total upgrades take maybe an hour, since you just have to install the OS into /, log in and install whichever programs you need from the repositories.  All of a sudden, your old taskbar icons will pop up and everything else runs like it should. So easy!

---

### Post by srs5694 on 2010-05-19
I can think of two drawbacks to separating root (/) from /home, and both are conditional rather than universal:


[list]
[*]If the amount of disk space is very small, separating the two partitions can result in running out of disk space on one partition while there's still room on the other. I'd say the minimum to make a split sensible would be about 15-40GB, depending on how big an installation it is (how many programs are to be installed, how much user data). Below that, it might make more sense to keep it all on one partition. Of course, these days, few serious installations have less disk space than this.
[*]If the split is implemented incompetently, it could cause problems. I'm using the word "incompetent" to encompass a large number of possible blunders, such as giving way too much space to root (/) and way too little to /home, putting an unrelated partition between the two (such as a Windows partition), or using the wrong filesystems (such as NTFS for /home). Even some of these might not produce huge problems. For instance, putting a Windows C: partition between root (/) and /home will just cause some performance degradation, not system instability.
[/list]


Overall, I think splitting these partitions makes a lot of sense for most installations.

---

### Post by drs305 on 2010-05-19
I'll provide some input but make the disclaimer that I often use a separate /home and think it's a great idea for most users. 

I have a separate partition for all my data files, so I often do not have a separate /home until just before I do an upgrade. Then I make a separate /home, which takes me less than 5 minutes since my data files are elsewhere, do the upgrade, and eventually combine them back (sometimes I don't).

Again, IMO the following don't outweigh the benefits, but they are considerations:

1. You need an extra partition. 
a. This may or may not be a big issue. If the system setup is such that partitions must be combined, split, moved, etc, there is always the risk something bad might happen. I know it's rare, and I've done this hundreds of times without problems. However, if my /home partition contains irreplaceable data that couldn't be backed up for some reason, it should be a consideration.
b. It invariably leads to the "is what I'm looking for on sda1 or sda5" moments.  :-)

2. It makes backups a bit more difficult (for me).
I frequently back up my system, and having a separate /home requires I back up both / and /home. 
The counterargument: if you only want to back up your personal files and they are in /home, the backup wouldn't be nearly as large.

3. The default is to have /home within Ubuntu. It requires effort to put it elsewhere, and it provides an opportunity to mess up a working system. ;-)

Having stated the above, the advantages still outweigh the drawbacks, especially once you have created it.

---

### Post by srs5694 on 2010-05-19
> **Mud.Knee.Havoc said:**
> I tried, but the 140 character limit was killing me. :D

[Here's the conversation]("http://identi.ca/conversation/32709725") if you'd like to see.  Maybe I wasn't making myself clear - or I misunderstood something.  I'm "ooboontoo" there, by the way. :)  I tried to be as clear as possible within the limits of so few characters.

This post came in after I made my initial reply. The alternative that's being advocated by some in that conversation is to use a separate data partition in lieu of a separate /home partition. In other words, you'd have a /home directory on the root (/) partition and then store all your documents on another partition, which could be mounted at some unspecified location (/home/yourusername/data, /home/data, /data, /mnt/data, /mnt/fizzbin, whatever). This approach has many of the same advantages of a separate /home partition, and its advocates say it helps keep configuration files from separate installations from interfering with one another. IMHO, though, it reveals a Windows mindset rather than an understanding of the Unix (and hence Linux) mindset. With a few exceptions, such as mail queues, Unix/Linux tends to try to keep each user's data files in a single directory, which helps in locating those files. Windows, by contrast, uses a much less rigorous system in which users could drop their files anywhere. Going back further, it was even common in DOS for users to store their data files in the same directories as the programs that created them. The [Filesystem Hierarchy Standard (FHS)](http://www.pathname.com/fhs/) spells out where stuff is to go in a Linux system, and it says user files go in /home. Granted, that's not ironclad in the FHS, but it is where user files go as a general rule. It's where other Linux administrators (and a home Linux user *is* a Linux administrator) will expect to find user files, so if you need help with something, keeping your user files in /home will expedite communications. Likewise if you need to use find, grep, or some other utility to locate a specific file; if everything is in /home, it's easily located. As to the objection that a separate non-/home data partition helps keep configuration files from interfering with one another, the same thing is easily accomplished by using different user subdirectories under /home for each installation. For instance, you might use /home/fred on your first installation (let's say it's Ubuntu 9.04). Then you decide to try out Fedora, so you might use /home/ffred for it. Then you want to install Ubuntu 10.04 but keep your 9.04 installation, so you can then use /home/fred10. You can do this by varying the username you use for each system or by setting a home directory name that differs from the username. This approach works to separate the accounts on different distributions and keeps everything in /home.

---

### Post by Nythain on 2010-05-19
there really arent any con's that haven't been mentioned.
but a lot of us do distro swap a lot, or change versions of regularly. i dont keep a seperate /home partition because personally, i love a clean slate every time i reformat for whatever reason. i do back up some of my more complex rc's and .confs though.

---

### Post by Mud.Knee.Havoc on 2010-05-19
Thanks for your input, everybody.  I thought I was either going crazy or had missed something there. :)

---

