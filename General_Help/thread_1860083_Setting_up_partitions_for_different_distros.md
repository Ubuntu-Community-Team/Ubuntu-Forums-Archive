---
title: "Setting up partitions for different distros"
date: 2011-10-14
forum: General Help
---

### Post by rmcellig on 2011-10-14
I have a HP laptop with a 250GB HD. I was thinking creating a partition for my Dropbox folder (50GB), and separate partitions for lubuntu, xubuntu and maybe mint and ubuntu. This way each distro would be able to access sync to the dropbox partition and each distro would boot in it's own partition.

Any thoughts on how to set this up? Boot from a live CD and create 5 maybe 6 partitions?

I need some guidance on how to set this up. Thanks!!!

---

### Post by wanderingarticfox on 2011-10-14
I'm not into Laptops but I just built a new mid-tower and learned a lot . 1, you can only have 4 primary partitions in Linux. I use sda1 for Swap, sda2 is Kubuntu and sda3 is Ubuntu and sda5 is logical and free space. I utilize the Kubuntu forums to set up a logical partition that allows Kubuntu and Ubuntu to share Documents, Music and Pictures. I am sure someone here can help. Search the Ubuntu Wiki as far as partitions and booting and brush up on some background and terms. I still mess up on terms sometimes but here and the other Forum people are real good about helping you learn. Also search the How-To's and tutorials in this Forum.  Good luck and have fun.:guitar:

---

### Post by WasMeHere on 2011-10-14
Hi Randy,

Yes, use a live system with gparted! Most of the iso files for Ubuntu are set up so that gparted in available when you run it live from a CD or USB drive. 

If you plan to wipe the disk and start from the beginning it is an easy and quick operation (once you have decided how you want to have the partitions).

If you have Windows and want to keep it, but shrink its partition(s) it is also possible but takes several hours. And it is risky, so make a backup image before you start.

Remember that you can only have four primary partitions! I suggest that you let the first partition be primary (if you would like to have Windows, I think it wants a primary partition. Then use the rest of the disk for an extended partition, and create logical partitions in it: data partition, swap partition and system partitions. Today I would recommend the ext4 file system for linux system partitions and ext3 for data unless you want to share it with Windows (then use ntfs).

Have fun :-)
Olle

---

### Post by rmcellig on 2011-10-14
Thanks! I'm just curious about your new tower because I have been toying with the idea of a new customized tower as well. I use my two HP laptops for testing. They were given to me by a friend of mine who was fed up with Windows and decided to buy an iMac.

What price range did your new tower set you back?

Thanks again!!

---

### Post by rmcellig on 2011-10-14
Thanks Olle!

My laptop is my test PC so I have no issues starting from the beginning. I want this to be an all Linux machine. I was thinking of having Linux Mint as the main OS. Could I not for example boot from the Mint live CD, install Mint, then startup from the lubuntu live cd and install side by side with Mint, Then startup from whatever other distro live cd i want to use and do another side by side install. Then with the leftover space I can create a partition for my Dropbox folder so I can share with the other distros I have installed.

Is this method of installing OK?

---

### Post by smurphy_it on 2011-10-14
Any reason why you just don't stick with one of them as your main O/S and run the others through something like virtualbox ?

---

### Post by rmcellig on 2011-10-14
I thought of using Virtualbox. I guess I can try it again and see how it goes. Would be a lot simpler that's for sure. I guess my main concern was giving up speed and performance this way but when you think about it, it is more practical. Right now I have the new Ubuntu 11.10 installed. I still have mixed feelings about it. I was thinking of trying Mint again as my main distro. So many choices out there. 

I was thinking of using this machine to show my PC friends that there are alternatives to Windows and by having a few distros to show them, this might help in their decisions. I am a Mac user (since 1988) primarily but I spend about 80% of my PC time using Linux. Way more choices etc....:)

---

### Post by rmcellig on 2011-10-14
I thought of using Virtualbox. I guess I can try it again and see how it goes. Would be a lot simpler that's for sure. I guess my main concern was giving up speed and performance this way but when you think about it, it is more practical. Right now I have the new Ubuntu 11.10 installed. I still have mixed feelings about it. I was thinking of trying Mint again as my main distro. So many choices out there. 

I was thinking of using this machine to show my PC friends that there are alternatives to Windows and by having a few distros to show them, this might help in their decisions. I am a Mac user since 1988 primarily but I spend about 80% of my PC time using Linux. Way more choices etc....:)

---

### Post by WasMeHere on 2011-10-14
Well I think that you specify at least 50GB for [Dropbox] data, maybe 32 GB for your main system (Mint?), 2xRAM for swap and the rest as fairly small system partitions, 16 GB each is definitely enough to test various operating systems thoroughly.

*Nota Bene:* It is a different experience to test/show a system on hard metal compared to a virtual machine.

---

### Post by aeronutt on 2011-10-14
I typically keep 3 partitions for various distro's/versions of Linux, 2 partitions for Windows (one recovery), and a data partition. Because I keep my data partition seperate, it's easy to keep the Linux partitions to well under 20G.

---

### Post by rmcellig on 2011-10-14
Thanks Olle!!

I think setting up the separate partitions like you mention in your post may be the way to go to really show off the distros to my possible Linux converts. So, I can do a side by side install for each of the distros?

---

### Post by WasMeHere on 2011-10-14
Another and more convenient alternative to run various operating systems, is to run them live directly from iso files on your hard drive. The following method works at least for newer versions of Ubuntu and Linux Mint.

[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11227153&postcount=349_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11227153&postcount=349")

Have a try!
Olle

*Edit: And yes, you can install them side by side, many of us do that. They may 'steal' grub from each other, to put themselves on top in the grub menu, but you can fix that later on.*

---

### Post by rmcellig on 2011-10-14
Man, there are so many options in Linux!! I am a Mac user since 1988 and I am amazed at how flexible you can get with Linux!

I'm a bit confused by the method you suggested with iso files. It looks like a really neat way of doing it. I would just need some help in getting the procedure and steps involved coding wise.

Le's say I have the following iso files:

xubuntu 11.10
mint 11.10
ubuntu 10.04
lubuntu 11.10

How could I set these up from the iso files so they show up in Grub and I can choose which one to boot from? This is a fun learning experience for me!! :)

---

### Post by WasMeHere on 2011-10-14
You can do it two ways

1. Do as I did: make/change a hard link from one of the iso files to a pre-defined name and then boot

2. Make multiple entries for the grub menu, one for each one of your iso files

Of course you can combine all these variations:

Several installed systems
Several entries dedicated for iso files
One entry to link any (new) iso file

Your fantasy is the limit
Olle

---

### Post by rmcellig on 2011-10-14
How do I create a data partition that I can use to keep dropbox on as well as a centralized home folder that I can point all of my startup distros to?

Could I use Ubuntu tweak to point my home directory to the new data partition?

---

### Post by WasMeHere on 2011-10-14
I am not sure if it would be a good idea to use the same home partition for all the startup distros. What if they might change things incompletely, so that the other systems will be corrupted? If all systems except one (Mint) are experimental, you would not need to save your settings globally anyway.

But I don't know, so you need the advice from someone else to answer the question about home partitions.

---

### Post by rmcellig on 2011-10-15
Thanks for the advice Olle about home folders. Makes a lot of sense. Regarding Dropbox, what is the best way to set this up so that all of my distros point to it. Thanks again for your input Olle!

---

### Post by WasMeHere on 2011-10-15
I'm happy to have helped you :-)

I think you know more than I about Dropbox. I only have a small free account, that I have tested, but I don't use it regularly. I hope someone else can help you unless you can find out yourself browsing the Dropbox web site and other information about it on the internet. If necessary start a new thread: How to use Dropbox in Ubuntu!

Have fun and when you know what to do, please mark this thread SOLVED
Olle

---

### Post by rmcellig on 2011-10-15
Thanks Olle,

I started a new Dropbox thread. I will mark this thread as solved once I get an answer from my new thread.

---

