---
title: "Switching from Windows 7 to Ubuntu, and I need a little help."
date: 2012-09-15
forum: General Help
---

### Post by ZombiesAteMyNeighbors on 2012-09-15
Hello. As the title says, I'm considering switching from Windows to Ubuntu. I did this about a month ago when my laptop broke, but my wireless card wasn't detected, and I couldn't for the life of me figure out how to fix it. So, I have some questions before I do this.

1. How do I make my wireless work? I have an HP dv5 1235dx, with a broadcom wireless adapter (Not sure exactly which, I googled it, and googled how to find out, but no luck. I'm sure someone here knows, though)

2. Will I still be able to play Minecraft on Ubuntu? I play with a torrented, cracked version which comes with an .exe installer, and it installs a .minecraft folder in %appdata%. I'm not sure if it would work in Ubuntu?

3. Is it worth downloading the 64-bit version as opposed to the 32-bit? I have a 300gb HDD, 4GB of RAM, and an Intel Core 2 Duo processor.

4. Dual booting. I remember when I was installing Ubuntu before, there was an option to install it alongside Windows. Do I just click that and it does the work for me, or do I need to do something specific to make that option work properly?

5. What exactly is the terminal, and is it absolutely necessary to use it? I automatically assume it's like the windows command prompt, which I never use, but I'm more than likely wrong.

Sorry for the long post. I'll be looking forward to your replies. Thank you.

---

### Post by ZombiesAteMyNeighbors on 2012-09-15
Oh, also. I know some forums have rules against bumping. Is it unnecessary to bump my thread on this forum? Thanks.

---

### Post by Cornova on 2012-09-15
> **ZombiesAteMyNeighbors said:**
> 5. What exactly is the terminal, and is it absolutely necessary to use it? I automatically assume it's like the windows command prompt, which I never use, but I'm more than likely wrong.


I switched to ubuntu about 4 years ago from XP and it is very much like DOS. Some people do all their installing and upgrading using the Terminal but I've found that I rarely have to use it, and when I do, the commands are usually easy to find via Google and if not someone on the forums always has an answer.

---

### Post by ZombiesAteMyNeighbors on 2012-09-15
> **Cornova said:**
> I switched to ubuntu about 4 years ago from XP and it is very much like DOS. Some people do all their installing and upgrading using the Terminal but I've found that I rarely have to use it, and when I do, the commands are usually easy to find via Google and if not someone on the forums always has an answer.

Ah, alright thanks. I was a little worried about that. It seems pretty complicated.

Have any answers to any of my other questions by any chance? I'd appreciate it.

---

### Post by LiamOS on 2012-09-15
> **ZombiesAteMyNeighbors said:**
> [COLOR=Blue]Ah, alright thanks. I was a little worried about that. It seems pretty complicated.

Have any answers to any of my other questions by any chance? I'd appreciate it.[/COLOR] 
Despite the terminal being pretty daunting at first, you can get used to it pretty quickly, and once you do, the majority of what's going on makes a lot more sense. 
When I use linux, everything other than my document viewer and web browser work from a terminal, but the only time my sister uses a terminal is when she's pasting in a command from me or google.

> **ZombiesAteMyNeighbors said:**
> [COLOR=Blue]Hello. As the title says, I'm  considering switching from Windows to Ubuntu. I did this about a month  ago when my laptop broke, but my wireless card wasn't detected, and I  couldn't for the life of me figure out how to fix it. So, I have some  questions before I do this.

1. How do I make my wireless work? I have an HP dv5 1235dx, with a  broadcom wireless adapter (Not sure exactly which, I googled it, and  googled how to find out, but no luck. I'm sure someone here knows,  though)[/COLOR] 
The wireless *should* work out of the box. There are occasional instances where it doesn't, but I also think most(if not all) Broadcom devices should 'just work' under Ubuntu. I know that the linux kernel supports them,
Did you do a full install last time? Also, if you have the Ubuntu liveCD/USB lying around, you could boot it and run 
```
lspci
``` 
in a terminal, and post the output here in code tags; this'll tell us what wireless card you have.
> **ZombiesAteMyNeighbors said:**
> [COLOR=Blue]2. Will I still be able to play Minecraft on Ubuntu? I play with a  torrented, cracked version which comes with an .exe installer, and it  installs a .minecraft folder in %appdata%. I'm not sure if it would work  in Ubuntu?[/COLOR]
 
I'm not sure if Minecraft works on linux, but this version won't. What I'd recommend is using a virtual machine to run Windows XP, which you should have little problem obtaining. This might sound slightly daunting, but it's really easy, and very useful. You merely have to install virtualbox from the Ubuntu software centre, and install Windows within it. Once you've done this, you'll have Ubuntu running with a windows open which has Windows inside it. 
You could also dual boot.
In general, .exe files do not work under linux.
> **ZombiesAteMyNeighbors said:**
> [COLOR=Blue]3. Is it worth downloading the 64-bit version as opposed to the 32-bit? I  have a 300gb HDD, 4GB of RAM, and an Intel Core 2 Duo processor.[/COLOR]
 
I would personally go for the 64-bit release. Unless you have specific requirements in software or anything, it won't make much of a difference, though.
> **ZombiesAteMyNeighbors said:**
> [COLOR=Blue]4. Dual booting. I remember when I was installing Ubuntu before, there  was an option to install it alongside Windows. Do I just click that and  it does the work for me, or do I need to do something specific to make  that option work properly?[/COLOR]
 
It's been well over a year since I went near that option, but it worked perfectly for me then with no configuration. Before doing this, I'd advise defragmenting the Windows partition from inside Windows, and deleting anything useless to free up space.
> **ZombiesAteMyNeighbors said:**
> [COLOR=Blue]5. What exactly is the terminal, and is it absolutely necessary to use  it? I automatically assume it's like the windows command prompt, which I  never use, but I'm more than likely wrong.

 Sorry for the long post. I'll be looking forward to your replies. Thank you.[/COLOR]  
The terminal will either be one of your favourite or least favourite programs. :p
If you like to know what your computer is doing, how things are working, etc., learning to use the terminal won't take long and is pretty informative. Otherwise, it's just like the Windows prompt.

---

### Post by gabriella on 2012-09-15
> **ZombiesAteMyNeighbors said:**
> Ah, alright thanks. I was a little worried about that. It seems pretty complicated.

Have any answers to any of my other questions by any chance? I'd appreciate it.

When you install you have the option to partition and resize the HD to whatever size you want and keep Windows on that. Then Ubuntu will be installed on the new partition. I always use the manual partitioning option and set my sizes. It's quite easy in fact.

as to your wireless card issue I think that would be best in a seperate thread of its own. However, usually difficult Wireless cards can be sorted out. I had the notorious BroadCom 43XX series card and it really wasn't that difficult to do.

I went with 32 bit although technically I could have used 64 bit so as to avoid any glitches. Yours may be different

---

### Post by ZombiesAteMyNeighbors on 2012-09-15
> **LiamOS said:**
> Despite the terminal being pretty daunting at first, you can get used to it pretty quickly, and once you do, the majority of what's going on makes a lot more sense. 
When I use linux, everything other than my document viewer and web browser work from a terminal, but the only time my sister uses a terminal is when she's pasting in a command from me or google.


The wireless *should* work out of the box. There are occasional instances where it doesn't, but I also think most(if not all) Broadcom devices should 'just work' under Ubuntu. I know that the linux kernel supports them,
Did you do a full install last time? Also, if you have the Ubuntu liveCD/USB lying around, you could boot it and run 
```
lspci
``` 
in a terminal, and post the output here in code tags; this'll tell us what wireless card you have.

I'm not sure if Minecraft works on linux, but this version won't. What I'd recommend is using a virtual machine to run Windows XP, which you should have little problem obtaining. This might sound slightly daunting, but it's really easy, and very useful. You merely have to install virtualbox from the Ubuntu software centre, and install Windows within it. Once you've done this, you'll have Ubuntu running with a windows open which has Windows inside it. 
You could also dual boot.
In general, .exe files do not work under linux.

I would personally go for the 64-bit release. Unless you have specific requirements in software or anything, it won't make much of a difference, though.

It's been well over a year since I went near that option, but it worked perfectly for me then with no configuration. Before doing this, I'd advise defragmenting the Windows partition from inside Windows, and deleting anything useless to free up space.

The terminal will either be one of your favourite or least favourite programs. :p
If you like to know what your computer is doing, how things are working, etc., learning to use the terminal won't take long and is pretty informative. Otherwise, it's just like the Windows prompt.

When my wireless wasn't working, I had installed it on the hard drive from a USB stick. I would boot into Ubuntu from my USB thing to do the command you told me to, but I'm a little busy at the moment, so I can't exactly log off of windows.

Are virtual machines slow?

---

### Post by ZombiesAteMyNeighbors on 2012-09-15
> **gabriella said:**
> When you install you have the option to partition and resize the HD to whatever size you want and keep Windows on that. Then Ubuntu will be installed on the new partition. I always use the manual partitioning option and set my sizes. It's quite easy in fact.

as to your wireless card issue I think that would be best in a seperate thread of its own. However, usually difficult Wireless cards can be sorted out. I had the notorious BroadCom 43XX series card and it really wasn't that difficult to do.

I went with 32 bit although technically I could have used 64 bit so as to avoid any glitches. Yours may be different

Well, I'll just go with 32 bit since I already have it on a usb stick. Thanks for your help!

---

### Post by LiamOS on 2012-09-15
> **ZombiesAteMyNeighbors said:**
> When my wireless wasn't working, I had installed it on the hard drive from a USB stick. I would boot into Ubuntu from my USB thing to do the command you told me to, but I'm a little busy at the moment, so I can't exactly log off of windows.

Hmm. That's quite weird.
I'm not quite sure what to do then.
> **ZombiesAteMyNeighbors said:**
> Are virtual machines slow?
It depends. You can alocate them a certain amount of your system resources, which you're not too short of, so a virtual machine would probably work well enough for you.

---

### Post by ZombiesAteMyNeighbors on 2012-09-15
> **LiamOS said:**
> Hmm. That's quite weird.
I'm not quite sure what to do then.

It depends. You can alocate them a certain amount of your system resources, which you're not too short of, so a virtual machine would probably work well enough for you.

Do you think my wireless issues would be avoided if I installed Ubuntu while on a wired connection? Maybe it didn't work last time because it had to download the drivers, but it didn't have the chance to.

---

### Post by oxf on 2012-09-15
> **ZombiesAteMyNeighbors said:**
> Do you think my wireless issues would be avoided if I installed Ubuntu while on a wired connection? Maybe it didn't work last time because it had to download the drivers, but it didn't have the chance to.

I dont think you need to install with a wired connection as such. However, if your WiFi is not detected you will need to use a wired connction to get the drivers etc. Ndiswrapper is one such tool that will get your WiFi "addapted" to Linux. Once you've installed it should automatically search for ndsiwrapper when you have a wired connection.

---

### Post by ZombiesAteMyNeighbors on 2012-09-15
> **oxf said:**
> I dont think you need to install with a wired connection as such. However, if your WiFi is not detected you will need to use a wired connction to get the drivers etc. Ndiswrapper is one such tool that will get your WiFi "addapted" to Linux. Once you've installed it should automatically search for ndsiwrapper when you have a wired connection.


Well, I'm currently installing it on a wired connection, and am using my desktop at the moment.
A bit into the installation, the LED for wifi turned from Red to Blue, indicating that wireless is enabled.

The 'copying files' part of installation is taking kind of long, which is worrying me a bit, but I'm probably just being paranoid.

---

### Post by oldfred on 2012-09-15
The 64 bit version would be better for your system. You end up with PAE which tries to switch processes in and out to use the 4GB.

[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

---

### Post by JKyleOKC on 2012-09-15
A few messages back you asked if virtualization would be slow. With a dual core processor and 4 GB of RAM it should be almost as peppy as your original native Windows system, but its internet response times may be a bit weak for gaming. I'm not a gamer so have no personal experience with that, but do use a number of virtual machines for serious production work and development, with no problem. The general recommendation I see on the forums, though, is that virtual machines aren't recommended for most games.

---

