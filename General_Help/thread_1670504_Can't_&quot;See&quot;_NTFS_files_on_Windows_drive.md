---
title: "Can't &quot;See&quot; NTFS files on Windows drive"
date: 2011-01-19
forum: General Help
---

### Post by Chirality on 2011-01-19
Hi folks, this is a real head-scratcher for me, because despite being relatively new to *NIX systems, this doesn't seem to be as simple as a mount issue or some other more basic issue. 

So I cracked open a malfunctioning external HDD to see what needed to be fixed, and it turned out to the be actual HDD portion, not the part that interfaces with the computer through the USB. The IC part that hooked into the hard drive was fine. Now I had another *completely different* HDD from an old Windows computer (XP) with two partitions, one being the boot partition. I just want to emphasize again this is **not** the malfunctioning drive I'm working with anymore. On this particular drive Windows had corrupted and left me with no functioning operating system on the drive. So I figured I could recover the files by plugging in the external HDD board (Maxtor) and connecting via the USB into my Ubuntu machine.

So I do, and everything mounts just fine in the GUI. The partitions mount as two separate filesystems. So far, so good. There don't seem to be any issues with my using the Maxtor board. I start exploring the drive in the GUI, and I find out that I can see all the folder names laid out in the GUI but can't access any of the actual files in one partition (the boot partition). Here's where it gets weird and inconsistent, I can see some of the files, desktop.ini and a few (less than five total) minor system files like that, nothing I actually want.

Now in the other partition which isn't the boot partition further weirdness ensues. I have political cartoons I had drawn up and stored there in a number of different formats ranging from .xcf to .bmp to .png and I could see all of them laid out in the GUI, despite not having programs installed that could open some of them (I still haven't installed GIMP). Here's the thing, there are gigabytes of other stuff, music, movies, pictures, documents, you name it on both partitions, even in the same folders as the files that are visible. BUT, *I can't see any of them*. Hell, if nothing else, I should be able to see more than a handful of .ini files just by virtue of there being Windows on the thing.

I went into the terminal and tried navigating using BASH instead of the GUI, but the terminal sees what I see in the GUI, which is pretty much what I expected, but I tried anyway.

The disk itself doesn't seem to have any bad sectors, I performed a scan and it came back green across the board, so I'm thinking it has to be a software challenge. 

I never encrypted the contents of the Windows drive. So does anybody know what's going on here? Any help would be really appreciated, since I really want those files, and I don't want to go to a third-party for a costly recovery when there is no apparent reason I can't access them.

Thanks.

---

### Post by anglican on 2011-01-19
> **Chirality said:**
> Hi folks, this is a real head-scratcher for me, because despite being relatively new to *NIX systems, this doesn't seem to be as simple as a mount issue or some other more basic issue. 

So I cracked open a malfunctioning external HDD to see what needed to be fixed, and it turned out to the be actual HDD portion, not the part that interfaces with the computer through the USB. The IC part that hooked into the hard drive was fine. Now I had another *completely different* HDD from an old Windows computer (XP) with two partitions, one being the boot partition. I just want to emphasize again this is **not** the malfunctioning drive I'm working with anymore. On this particular drive Windows had corrupted and left me with no functioning operating system on the drive. So I figured I could recover the files by plugging in the external HDD board (Maxtor) and connecting via the USB into my Ubuntu machine.The fact that Windows was corrupted probably explains why you don't see everything you're expecting on that drive (e.g. a WINDOWS directory!). Don't despair yet.
> **Chirality said:**
> 
So I do, and everything mounts just fine in the GUI. The partitions mount as two separate filesystems. So far, so good. There don't seem to be any issues with my using the Maxtor board. I start exploring the drive in the GUI, and I find out that I can see all the folder names laid out in the GUI but can't access any of the actual files in one partition (the boot partition). Here's where it gets weird and inconsistent, I can see some of the files, desktop.ini and a few (less than five total) minor system files like that, nothing I actually want.

Now in the other partition which isn't the boot partition further weirdness ensues. I have political cartoons I had drawn up and stored there in a number of different formats ranging from .xcf to .bmp to .png and I could see all of them laid out in the GUI, despite not having programs installed that could open some of them (I still haven't installed GIMP). Here's the thing, there are gigabytes of other stuff, music, movies, pictures, documents, you name it on both partitions, even in the same folders as the files that are visible. BUT, *I can't see any of them*. Hell, if nothing else, I should be able to see more than a handful of .ini files just by virtue of there being Windows on the thing.

I went into the terminal and tried navigating using BASH instead of the GUI, but the terminal sees what I see in the GUI, which is pretty much what I expected, but I tried anyway.

The disk itself doesn't seem to have any bad sectors, I performed a scan and it came back green across the board, so I'm thinking it has to be a software challenge. 

I never encrypted the contents of the Windows drive. So does anybody know what's going on here? Any help would be really appreciated, since I really want those files, and I don't want to go to a third-party for a costly recovery when there is no apparent reason I can't access them.

Thanks.This Windows corruption suggests that the files have somehow been deleted. There are file recovery tools in the repos that you can use to recover much of this data. I've successfully used "magicrescue" in the past when my "son and heir" managed to "accidentally" delete all his holiday photos. It found all the pictures and restored them - with one slight problem, all the filenames will be lost and you'll get a lot of new and fairly meaningless filenames (basically just numbers). If the files have been deleted this may be your only option, and hours spent sorting through recovered files is probably preferable to complete loss of data.

H

---

### Post by Chirality on 2011-01-19
> **anglican said:**
> The fact that Windows was corrupted probably explains why you don't see everything you're expecting on that drive (e.g. a WINDOWS directory!). Don't despair yet.
This Windows corruption suggests that the files have somehow been deleted. There are file recovery tools in the repos that you can use to recover much of this data. I've successfully used "magicrescue" in the past when my "son and heir" managed to "accidentally" delete all his holiday photos. It found all the pictures and restored them - with one slight problem, all the filenames will be lost and you'll get a lot of new and fairly meaningless filenames (basically just numbers). If the files have been deleted this may be your only option, and hours spent sorting through recovered files is probably preferable to complete loss of data.

H

I'm thinking you're right. I plugged it into a windows box and have the same problems. Upon inquiry earlier today, I'm getting the impression that my brother (*sigh*) canceled an inadvertent format midway. I can't blame him too much, since Windows Recovery is vague about warning you of an impending format. This is actually good news, since the files are probably recoverable. At least this drive won't be needing a cleanroom.

Thanks for the help. If you have any further recommendations (applications, techniques, etc.) about data recovery, throw em my way. Hell, if you have a good guide to a DIY cleanroom, I'm always game for a project.

I'm going to mark the post solved.

---

