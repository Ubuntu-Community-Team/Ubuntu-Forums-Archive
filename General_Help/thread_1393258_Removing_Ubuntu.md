---
title: "Removing Ubuntu"
date: 2010-01-29
forum: General Help
---

### Post by RadicalApex on 2010-01-29
Hello all! I recently decided to install ubuntu to give linux a shot and honestly I absolutely hate it. Installing anything is a huge hassle and I just cant take the lack of technical support. I am currently partitioned to dual boot with xp and I'd like my hard drive space back as well as ubuntu completely removed from my machine I searched google and all I can find is threads of people trying to convince others to just keep linux. Is returning to just windows that difficult? Am I just better off cutting the hard drive space as a loss and lesson learned or is there an easy way to do this?

---

### Post by llawwehttam on 2010-01-29
It is very easy to remove. You do not 'uninstall ' an OS, you simply format the partition or make empty space and enlarge your windows one to fill it.
 
However I have no idea what you mena by ' a huge hassle' to install software. 
 
You go to Applications> ubuntu software cnetre, choose the program you want and press install.. simple.
 
Unless you have been trying to install things manually with debs and been trying to cope with dependancies.............NIGHTMARE!!!

---

### Post by skymera on 2010-01-29
Use a Windows partition tool to wipe Ubuntu and then fill the space with your Windows partition.

Yeah it's hassle.
I hate opening my browser, going to a software website, finding the right software, downloading the software. Running the download and installing the software. Having to check updates manually. Having files left over when i uninstall the software.... oh wait.

Also:
Make sure you have your Windows CD to reinstall your bootloader.

> **RadicalApex said:**
>  lack of technical support.

Made me lol

---

### Post by Ahriman on 2010-01-29
I believe that if you booted off the XP installation CD, went into Recovery mode, and at the console typed the following two commands:
fixmbr
fixboot

then rebooted, it will boot directly into XP for you. You can then use the Disk management tool (located in theComputer Management sectin of Administrative Tools) to re-partition the Ubuntu partition and format it. I believe you will need specialist tools from within Windows to grow your XP partition to fill the hard drive; will be better to leave it partitioned into two drives imo.

---

### Post by Grenage on 2010-01-29
> **RadicalApex said:**
> Is returning to just windows that difficult? Am I just better off cutting the hard drive space as a loss and lesson learned or is there an easy way to do this?

No, it's not very difficult; we can talk you through it.  Could you post your partition table for us?  A screenshot of gparted would do:

```
gksu gparted
```

---

### Post by llawwehttam on 2010-01-29
> **skymera said:**
> Use a Windows partition tool to wipe Ubuntu and then fill the space with your Windows partition.
 
Yeah it's hassle.
I hate opening my browser, going to a software website, finding the right software, downloading the software. Running the download and installing the software. Having to check updates manually. Having files left over when i uninstall the software.... oh wait.

 
Made me lol ( a lot).For the OP have a look at the new to linux link in my signiture.

---

### Post by Paddy Landau on 2010-01-29
I must confess that I'm mystified as to how you find it hard to install a program on Ubuntu. Synaptic Package Manager does it all for you!

However...

The previous posters are correct. Here is how I would do it.

[LIST=1]
[*]Restore your Windows boot loader. Try [Ariman's]("http://ubuntuforums.org/showthread.php?p=8742341#post8742341") method first, if possible. Otherwise, go to [download.com]("http://download.com/") and search for MBR (you'll need to install it in Windows, not Ubuntu). You can ask the Windows forums for a good one; I've used [Easy BCD]("http://neosmart.net/dl.php?id=1") with good results.
[*]Use your Windows partition manager to *delete* the Ubuntu partition (warning: ensure that you delete the right partition!).
[*]Use your Windows partition manager to *grow* your existing Windows partition to the rest of the disk.
[/LIST]
Special warning: Fiddling with your MBR and your partitions runs a (small) risk of data loss. Do a **full backup first**!

Good luck.

---

### Post by RadicalApex on 2010-01-29
> **Grenage said:**
> No, it's not very difficult; we can talk you through it.  Could you post your partition table for us?  A screenshot of gparted would do:

```
gksu gparted
```


This sounds like what I need, access to the partitioner (I dont need to repair my mbr or bootloader cause my copy of windows was factory installed and I didnt receive a cd and can cope with grub.) When I type the code nothing happens in terminal just a newline.

@llawwehttam I checked out the links in your sig and I had not known all that, had I known I would have never tried to install ubuntu it's just not for me, I mean the free software thing is a cool idea and all but I can get free software with windows too.

---

### Post by Grenage on 2010-01-29
Ok, something isn't right there.  If you boot from the Ubuntu CD (as a Live CD) you should be able to run Gparted from that.

---

### Post by a2z on 2010-01-29
I don't understand how you thought you could like installing software when your not knowledgeable enough to get rid of it.
I bet you'll like getting rid of Ubuntu less than you enjoyed acquiring it.
Obviously the learning curve isn't for everyone
I find the software and support is well worth it.
Sure linux has it glitches as said before, all os's/software will have them. I can remember some cussing with win98 when I first dabbled in computers. And even xp plucked more than a few graying hairs from my head.
I can say that after 1 year with ubuntu, I'm 100% converted.

a2z

---

### Post by Grenage on 2010-01-29
I don't think we need to preach to the man, he just wants to remove Ubuntu. ;)

---

### Post by RadicalApex on 2010-01-29
> **a2z said:**
> I don't understand how you thought you could like installing software when your not knowledgeable enough to get rid of it.
I bet you'll like getting rid of Ubuntu less than you enjoyed acquiring it.
Obviously the learning curve isn't for everyone
I find the software and support is well worth it.
Sure linux has it glitches as said before, all os's/software will have them. I can remember some cussing with win98 when I first dabbled in computers. And even xp plucked more than a few graying hairs from my head.
I can say that after 1 year with ubuntu, I'm 100% converted.

a2z

Theres no need for condescending comments like this we all have our own preferences and I respect yours as you should mine.

---

### Post by Paddy Landau on 2010-01-29
> **RadicalApex said:**
> ... I dont need to repair my mbr or bootloader...
Yes, you do. The current bootloader expects there to be both Windows and Ubuntu. If you just get rid of Ubuntu, the bootloader will throw its hands in the air and give up.

To access GParted in Ubuntu, go to System > Administration > either Partition Editor or GParted.

In any case, read through [my previous post]("http://ubuntuforums.org/showthread.php?p=8742383#post8742383"), because it's about as straightforward as you'll get.

---

### Post by nothingspecial on 2010-01-29
> **RadicalApex said:**
> This sounds like what I need, access to the partitioner (I dont need to repair my mbr or bootloader cause my copy of windows was factory installed and I didnt receive a cd and can cope with grub.) When I type the code nothing happens in terminal just a newline.




This might be a hassle and I`m sorry for the poor technical support but gparted isn`t installed by default in some versions of Ubuntu. 

```
sudo apt-get install gparted
```

but you won`t be able to alter your ubuntu partition because it will be mounted.

```
sudo fdisk -l
```

will list your partitions.

I know exactly how you feel btw

---

### Post by RadicalApex on 2010-01-29
> **Paddy Landau said:**
> Yes, you do. The current bootloader expects there to be both Windows and Ubuntu. If you just get rid of Ubuntu, the bootloader will throw its hands in the air and give up.

To access GParted in Ubuntu, go to System > Administration > either Partition Editor or GParted.

In any case, read through [my previous post]("http://ubuntuforums.org/showthread.php?p=8742383#post8742383"), because it's about as straightforward as you'll get.

Oh great! hah thanks a bunch, and thanks everybody for all the help. I think I'm gonna put this all on hold for now since I still have dual-boot access to xp for my wireless and honestly I think I've just gotten far too frustrated too soon (4 hours of reading documentation and still no progress will do that to you ;)) I just cant bring myself to give up on a challenge.

---

### Post by nothingspecial on 2010-01-29
What are you having problems with. Looking at your post count, you haven`t asked yet.

---

### Post by Paddy Landau on 2010-01-29
> **RadicalApex said:**
> ... I'm gonna put this all on hold for now...
No problem.

It's actually easy to do (I've done it myself), but it does look daunting from this side.

Let us know on this thread when you're ready to try again, and we'll be happy to help.

---

### Post by RadicalApex on 2010-01-29
> **nothingspecial said:**
> What are you having problems with. Looking at your post count, you haven`t asked yet.

Yeah hah I'm not one to ask for help, I'm used to people on the Internet just telling you to figure it out yourself but I can see you guys are rather helpful. I am having trouble getting my wireless internet working, first off I'm using 9.10 and have a Broadcom BCM4311. I attempted to install ndiswrapper so I can use the windows driver for it (Broadcom a**holes!) and I have the ndiswrapper tar.gz but it refuses to install with make and make install but honestly I have very little clue on what I'm doing cause this is so new to me and I'm just so mentally tired at this point.

---

### Post by Ahriman on 2010-01-29
Well, no wonder! I've been a Linux user for a few years now and I **still** get frustrated with make, make install crap.

---

### Post by nothingspecial on 2010-01-29
get a wired connection, then

```
sudo apt-get install ndisgtk
```

If you can`t get a wired connection get in in windows from [here]("http://packages.ubuntu.com/karmic/ndisgtk")

copy it across and click it.

It might even be on the cd

---

### Post by RadicalApex on 2010-01-29
> **nothingspecial said:**
> get a wired connection, then

```
sudo apt-get install ndisgtk
```If you can`t get a wired connection get in in windows from [here]("http://packages.ubuntu.com/karmic/ndisgtk")

copy it across and click it.

It might even be on the cd

Are you serious? I tried using aptitude earlier and it didn't work for me but I tried your command and it worked maybe I pulled a typo; either way that was much easier than dealing with the tarball. I'll see if I can pull it together now and get this wireless in order.

---

### Post by nothingspecial on 2010-01-29
And - just a thought - if you can get a wired connection, do all your updates first, might take a while.

I don`t have a broadcom wireless card but who knows after updating it might just work.

---

### Post by rahulabc on 2010-01-29
You don't need to do all that.. Just boot in ur windows and type in run command:
diskmgmt.msc and you'll see ur drives there.. 

There'll be a drive named Unknown drive, juz right click and select delete.
Format it with NTFS or FAT32.. 
n u'll have ur drive working agaoin without using any software... 

If u want to delete grub also, then insert ur xp cd and press R to go in revcovery mode and then run command:
fixmbr

It'll just uninstall grub and boot ur windows directly..

---

### Post by nothingspecial on 2010-01-29
> **rahulabc said:**
> You don't need to do all that.. Just boot in ur windows and type in run command:
diskmgmt.msc and you'll see ur drives there.. 

There'll be a drive named Unknown drive, juz right click and select delete.
Format it with NTFS or FAT32.. 
n u'll have ur drive working agaoin without using any software... 

If u want to delete grub also, then insert ur xp cd and press R to go in revcovery mode and then run command:
fixmbr

It'll just uninstall grub and boot ur windows directly..

I think he`s going to give it a second shot now ;)

---

### Post by RadicalApex on 2010-01-29
> **nothingspecial said:**
> And - just a thought - if you can get a wired connection, do all your updates first, might take a while.

I don`t have a broadcom wireless card but who knows after updating it might just work.


Nah I'm up to date and still no luck, I'm gonna have to read up on ndis and see if I can find out whats going wrong. If anybody knows about broadcom chips and using them with 9.10 I'd greatly appreciate any advice or leads.

---

### Post by nothingspecial on 2010-01-29
Post the output of ```
sudo lshw -C network
```

That`ll show exactly which broadcom card Ubuntu is detecting.

---

### Post by audiomick on 2010-01-29
> **RadicalApex said:**
>  If anybody knows about broadcom chips and using them with 9.10 I'd greatly appreciate any advice or leads.

Hi. I don't know about broadcom myself, but I have seen lots of threads about them. Try searching the forum for "broadcom <your model>".

---

### Post by RadicalApex on 2010-01-29
```
 administrator@fortuna:~$ sudo lshw -C network
[sudo] password for administrator: 
  *-network:0             
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0204000-c0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:fc:5f:c6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.10 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:22 ioport:a000(size=256) memory:c020a400-c020a4ff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:7d:90:62
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
```

---

### Post by nothingspecial on 2010-01-29
You`re not trying to follow this [[COLOR="Magenta"]load of gobbldygook[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29") are you?

No wonder you are having a hard time. 

Try ```
sudo apt-get install b43-fwcutter
```

Then reboot

I got to go, you will get this fixed. Hang in there.

---

### Post by RadicalApex on 2010-01-29
> **nothingspecial said:**
> You`re not trying to follow this [[COLOR=Magenta]load of gobbldygook[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29") are you?

No wonder you are having a hard time. 

Try ```
sudo apt-get install b43-fwcutter
```Then reboot

I got to go, you will get this fixed. Hang in there.

Yes I was trying to follow that gobbldygook among much other gobbldygook can you see my frustration haha? but yea I found that code and just rebooted and when I came back to post it you had it posted too, it finally works! Thank you so much for all your help and thanks to everybody else who helped me get through this madness. I can finally get my much needed sleep now knowing this is taken care of haha.

And just a re-cap if anybody is ever looking over this for help with a stubborn broadcom wireless card just go with the code nothingspecial posted and thats pretty much the easiest way to go about this don't try to do it the hard way like I did.

---

### Post by Paddy Landau on 2010-01-29
> **RadicalApex said:**
> ... much easier than dealing with the tarball.
Unless you're a super-nerd, **never** deal with tarballs. Don't even download the program from the Internet. Not necessary! Just go to System > Administration > Synaptic Package Manager and install your programs from there. It does everything for you.

There are *occasional* exceptions where *you* have to download the package from the Internet, but again you don't install it yourself; you get Synaptic to install it for you.

> **RadicalApex said:**
> ... it finally works!
I'm glad to hear that.

If you need any more help, post a new thread. This is a friendly forum (mostly).

---

### Post by zipperback on 2010-01-29
> **RadicalApex said:**
> 
Installing anything is a huge hassle and I just cant take the lack of technical support. 


Installing software on modern Linux distributions such as Ubuntu is a very painless process. I don't understand how it can be a hassle.

All you need to do for example is click Applications and then select Ubuntu Software Center. Or if you want you can use Synaptic by going to System -> Administration -> Synaptic Package Manager.

It's a painless and very simple process.


> **RadicalApex said:**
> 
I am currently partitioned to dual boot with xp and I'd like my hard drive space back as well as ubuntu completely removed from my machine I searched google and all I can find is threads of people trying to convince others to just keep linux. Is returning to just windows that difficult? Am I just better off cutting the hard drive space as a loss and lesson learned or is there an easy way to do this?

No one is forcing you to use Linux. 

As for how to remove it, a search of google turns up numerous pages on how to remove it.

Check this link for more information.
[http://tinyurl.com/y9reen9](http://tinyurl.com/y9reen9)

- zipperback
:popcorn:

---

### Post by llawwehttam on 2010-01-29
> **Paddy Landau said:**
> Unless you're a super-nerd, **never** deal with tarballs. Don't even download the program from the Internet. Not necessary! Just go to System > Administration > Synaptic Package Manager and install your programs from there. It does everything for you.

There are *occasional* exceptions where *you* have to download the package from the Internet, but again you don't install it yourself; you get Synaptic to install it for you.


I feel insulted. I use tarballs quite a lot .......... I prefer the word geek though LOL.

(*whisper jumping up and down in glee at being called a nerd)

---

### Post by Paddy Landau on 2010-01-29
> **llawwehttam said:**
> I feel insulted... I prefer the word geek though
:D -- and Sorry!

I meant 'nerd' in a complimentary way. We wouldn't even have computers or mobile phones -- or electric lights for that matter -- if it weren't for the nerds! Oops, I mean geeks!

---

### Post by nothingspecial on 2010-01-29
Yay, anymore questions just ask on here!

I take it you`re going to persevere with Ubuntu now :D

> **RadicalApex said:**
> Yes I was trying to follow that gobbldygook among much other gobbldygook can you see my frustration haha?

You`re much braver than me. I gave up on windows for the third time a couple of weeks ago. My son wanted I tunes so I rescued an old windows pc from work, brought it home and plugged it all in.

Then I put in my trusty wireless dongle - the one that just works when you plug it into ubuntu. "Windows has detected new hardware, shall I download some drivers" which of course it can`t. So I unplugged it all and moved it to the kitchen, plugged it into the router and proceeded to download iTunes - 

Which took about 40 minutes - not one like rhythmbox or banshee. Then I had to accept all the lisences and what have you, and when I finally launched it, it said something about an administrator and it couldn`t find the music folder.

So I went to google and followed some instructions on editing the registry and it didn`t work and messed stuff up even more, until after about 3 hours I just thought sod this, nuked windows and installed linux.

That`s why I said I can understand your frustration.

---

### Post by Ahriman on 2010-01-29
> **llawwehttam said:**
> I prefer the word geek though LOL.
Although the definition of a geek used to mean: a wild man who, as part of a carnival show, would bite the heads off live chickens, mice, snakes, etc.

I prefer 'nerd' myself.

---

### Post by Robster2 on 2010-02-17
> **RadicalApex said:**
>  I am having trouble getting my wireless internet working, first off I'm using 9.10 and have a Broadcom BCM4311. I attempted to install ndiswrapper so I can use the windows driver for it (Broadcom a**holes!).

Hold the phone! 
There is a Broadcom a Linux driver for the BCM4311. 

No wrapper no mucking about just download and install!

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

