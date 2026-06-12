---
title: "Creating a RAMDisk"
date: 2011-02-13
forum: General Help
---

### Post by ShatPank on 2011-02-13
Hi, is there any chance someone could give me a bit of help creating a script to mount a 2gb RAMDisk for session use.

I.e, I just click a script, and my RAMDisk is created, but the next time I
I boot, it is not there, until I run the script again when I need it.

Running Ubuntu 10.10 if that makes any difference

Thanks in advance.
Stu

---

### Post by An Sanct on 2011-02-13
Go to 
System -> Preferences -> Startup Applications

Enable your script there, then it will always be ran at start up.

---

### Post by ShatPank on 2011-02-13
The problem is I only want it to run on certain sessions, and I have no idea to make a clickable script that would just mount a RAMDisk for me.

The other problem I had, is that different tutorials I found on google seemed to do nothing it can be a bit of a bugger being new to Linux, lol

---

### Post by An Sanct on 2011-02-13
```
mkdir -p /tmp/ram
sudo mount -t tmpfs -o size=512M tmpfs /tmp/ram/
```This will make a 512 MiB size ramdrive (**tm**porary **f**ile **s**ystem)

Now, just put that into a bash script and run it :)

---

### Post by ShatPank on 2011-02-13
So basically for a 2gb RAMDisk I'd need to do

#! /bin/bash
mkdir -p /tmp/ram sudo mount -t tmpfs -o size=2048M tmpfs /tmp/ram/
I'm assuming I just save that to a file, say "RAMDisk.bin" ?

sorry for noobish questions, I'm still pretty noob :P

---

### Post by An Sanct on 2011-02-13
Correct :)

put
```
mkdir -p /tmp/ram 
sudo mount -t tmpfs -o size=2048M tmpfs /tmp/ram/
```
into a text file, name it "ramdisk.sh" or something and then execute it whenever needed.

This will create a 2Gb ram drive in /tmp/ram, make sure, to make it small enough, so you don't exceed your actual ram.

---

### Post by ShatPank on 2011-02-13
That's more simple than I was expecting then :)

I should be ok, I've got 8gb.

Possibly a silly question, will that make it display an icon for the drive also, either in the Places menu on my task bar, or an Icon on my desktop like for my external drives?

Thanks for the help by the way, the script should be exactly what I wanted

---

### Post by dino99 on 2011-02-13
totally useless

you still have a swap partition for your needs, and a ram disk (exactly the same as swap is) will confuse the whole system: OLDISH Fat era is died long time ago

---

### Post by An Sanct on 2011-02-13
A ramdisk is never totally useless, if you have to encode a movie, it is nice to do it quick, that's where the ram disk comes into action.

PS. That will create a folder and then mount it as a temporary filesystem, not visible under "my places" or "computer", but you could link it to media
```
sudo ln -s /tmp/ram /media/ramdrive
```

---

### Post by ShatPank on 2011-02-13
The problem with a Swap Partition, is that it doesn't grant me the option to drop any files in that I currently want to access at high speed.

For instance, if I'm doing some video conversion, I'd drop the original file in the RamDisk, and convert from there, granting me performance increases.
A Swap Partition does not allow me to do this, as I cant really access it directly.

However, that script doesn't seem to create a RamDisk like I was hoping, I see no sign of it, no Icon etc to access it, and when accessing /tmp/ramdisk/ in Nautilus, it displays that there is 97gb free?

*Edit*
Should really have refreshed, I shall link it like you said, I'm assuming in that case that Nautilus was just referencing the free space on my home partition rather than the free space in the RamDisk folder?

Your reasoning for RamDisk use was identical to mine by the way, video encoding and conversion is the specific reason I want it.
Thanks again

---

### Post by jocko on 2011-02-13
> **dino99 said:**
> totally useless

you still have a swap partition for your needs, and a ram disk (exactly the same as swap is) will confuse the whole system: OLDISH Fat era is died long time ago
You are totally wrong. A ram disk is NOTHING like a swap partition. Swap is an extension to ram on a physical disk (~1000x slower than ram) which should only be used to store portions of ram that are not currently used to make place for things that need to be in ram.
A ram disk is more like a reserved portion of ram that acts as if it was a hard drive (but still with the speed of ram).

---

### Post by An Sanct on 2011-02-13
Oh yes :) I forgot to mention, you still have 
```
/dev/shm
```
Which is a flexible ramdisk, so if you put 1Gb inside here, 1Gb will go from your available ram, if you delete it, the ram is freed ... this might be even better than a "fixed" ramdisk.

---

### Post by jerrrys on 2011-02-13
if you got enough ram why even have a swap partition (other than sleep)

---

### Post by ShatPank on 2011-02-13
If I had no swap partition I can imagine my computer would probably explode just to spite me :P
But I see you point, doesn't the Swap Partition also help for open task's that aren't really being used, kind of hibernating them? I may have read something wrong though, not to certain about that.

How would I go about implementing / easily accessing said Dynamic RamDrive? it does sound the much better option

---

### Post by An Sanct on 2011-02-14
> **ShatPank said:**
> If I had no swap partition I can imagine my computer would probably explode just to spite me :P
But I see you point, doesn't the Swap Partition also help for open task's that aren't really being used, kind of hibernating them? I may have read something wrong though, not to certain about that.

How would I go about implementing / easily accessing said Dynamic RamDrive? it does sound the much better option

A swap partition is a relict from the past and also a net to catch you, if some software goes ballistic. Memory leaks are everywhere and if the leak is huge or ongoing, if the amount of ram is not big enough to handle it, the system will crash.

so:
ramdrive: fast, actually ram, behaves like a disk
swap: snail slow, actually disk, behaves like ram

---

### Post by ShatPank on 2011-02-14
I did know of swap drives, but for some reason I thought I'd read about them also being used to kind of hibernate program's to help them boot faster? Unless that was maybe window's related? I'm sure I remember something like that, although I may be getting 2 different thing's confused.

How would I go about linking the dynamic RamDisk you mentioned to my Places Menu... Actually, I just bookmarked the folder and that does it.... Didn't know that before :)

Thanks again for the help again :)

---

