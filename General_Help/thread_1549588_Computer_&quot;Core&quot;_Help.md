---
title: "Computer &quot;Core&quot; Help"
date: 2010-08-10
forum: General Help
---

### Post by Will1 on 2010-08-10
Hi.

Could someone do me a favor and explain briefly how the base of a computer (prior to the OS, prior to the BIOS but still in cyberspace [I believe is the word]) works. For example, your computer consists, generally, of a BIOS and one or more partitions depending on the user. But is that it? Or is it a little more complicated, or just that simple?

I will explain in a diagram.

Is it (the computer structure, or the way it is) more like:[INDENT]Partition2
[/INDENT]BIOS[INDENT]Partition1
[/INDENT]Then when I remove a partition or two:

BIOS

Or more like:

BIOS[INDENT]BIOS Settings

[/INDENT]Partion1

Information for Patrtion1 (data)

Then when you remove a partition:

BIOS

BIOS Settings

Partition1 Information.

And can therefore become cluttered. Or is it even completely different to both of them. And if so could someone explain to me briefly how it is.

Thank you. I hope I explained OK.

---

### Post by pastalavista on 2010-08-10
The BIOS is software which exists indepentently, hardwired, on a CMOS chip on the motherboard and is what co-ordinates all the periferal devices for use with various compatible CPUs, GPUs, etc. Be very careful upgrading the BIOS because it can brick your machine.

I'm curious about what you're trying to do. If you need to clear/reset the settings, take the motherboard battery out for a few hours.

---

### Post by lisati on 2010-08-10
A computer is an orchestrated symphony of many different parts working together.

BIOS is "**B**asic **I**nput-**O**utput **S**ystem". Another way of looking at it is "**B**uilt-**i**n **O**perating **S**marts", and, like pastalavista says, it's used to give the computer enough "know-how" about peripherals and other hardware to get things started.

Feel free to ask questions.

---

### Post by HPD2 on 2010-08-10
Think of the bios as the hardware loader. Its a hardwired piece of software that controls the hardware at the lowest level. Up from the bios you have the Operating System.

A partition is just a digital separator on a hard drive that tells the operating system that X amount of space is grouped together. 
example: 300gb hard drive, 2 partitions 150gb each = 2 drives of 150gb each to the operating system even though they reside on the same physical disk.

---

### Post by DeadlyOats on 2010-08-10
Here's the Wikipedia answer to what a [[COLOR="Red"]BIOS[/COLOR]]("http://en.wikipedia.org/wiki/BIOS") is and how it works.  And here's wiki's answer to what an [[COLOR="Red"]Operating System[/COLOR]]("http://en.wikipedia.org/wiki/Operating_system") is.  Finally, here's wiki's take on [[COLOR="Red"]Hard Drive Partitions[/COLOR]]("http://en.wikipedia.org/wiki/Disk_partitioning").

I hope these links help you understand a little bit about the differences between a BIOS and an OS, and how partitioning works.

---

### Post by Will1 on 2010-08-10
Oh. I know what they are, to a certain level, although I thought the explanations were very good. What I was interested in is how they operate in the hard drive. For instance, with the BIOS, you say that it is independent so it is not on the hard drive or uses the hard drive apart from loading it, reading it, etc. It doesn't store data on it, at all? It stores it in its chip? Bit like RAM?

And then, if that is so, is the only thing on the hard drive the partitions you make and then store data on? I.e. OS's, a storage partition, etc, etc. Then in theory if you have no partitions on the drive, you have nothing on the drive, and the drive will be 100% empty? Did I get that right? Or is there again more to it? I hope you can see where I am going with this.

I know when you format a drive, it isn't necessarily empty because what you used to format it can leave behind information about the drive, or the format or something like that. What I am interested in, and what my question would be, is what is the toll on the hard drive over time of installing OS's and partitioning, and reinstalling, so on so forth. Is there any? Does it leave behind data, information or scraps or what does it do?

What happens when you have one partition, remove it somehow, is the hard drive empty 100%? Or if you reinstall over that one partition is that new partition 100% new and no data left behind by old or previous partitions or use? Excluding the way on a computer if you delete a file it can still exist until you overwrite the 0 1 0 it acquired (i.e no full format, quick format.)

---

### Post by DeadlyOats on 2010-08-10
BIOS has nothing to do with hard drives, except to set the order in which to start.

For example:  In my BIOS settings, I set the the BIOS to search for a boot record in my CD ROM first, then to search my RAID array second, and my IDE drive third.

Partitions, formats, reading, writing have nothing to do with BIOS.  When it comes to hard drives and partitioning and formatting, forget BIOS.  Get that out of your mind.

Yes.  Even if you repartition, even if you reformat a hard drive.  Data can still be recovered from it.  There are special software that are specially written to do a complete, low level, erasure of hard drives.  The really good ones take many hours to complete even one pass.

For regular users, one pass may be enough, but for critically sensitive data, like from financial institutions, or the military, the minimum is four passes.  That could take days.

There's one software in particular that meets military requirements for erasing data at such a low level, but I can't remember what it's called.  The one I use is DBAN - Darik's Boot And Nuke.  Read everything about this program before you use it.  It will wipe not just one hard drive, but if you're not careful about the settings, it will nuke all of the hard drives it detects.

You can look [[COLOR="Red"]here[/COLOR]]("http://www.majorgeeks.com/Dariks_Boot_and_Nuke_d4596.html") for it.  It's freeware.

---

