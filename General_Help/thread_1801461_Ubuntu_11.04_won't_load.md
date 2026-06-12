---
title: "Ubuntu 11.04 won't load?"
date: 2011-07-10
forum: General Help
---

### Post by iRide113 on 2011-07-10
So it use to work fine but I needed to reinstall the system, but now when I try to install (via USB or CD) it gets to the Splash Screen and just freezes. (64 Bit). I am dual booting with Windows 7.

I tried installing it via "In Windows" but it didn't work so I booted up the CD and tried to install that way. I also redownload it to see if it would work.

This is the screen I get.

[IMG]http://1.bp.blogspot.com/_JSR8IC77Ub4/S6747n_wyWI/AAAAAAAAAVg/rcQ7UyAJluw/s400/ubuntu_boot.jpg[/IMG]


I've deleted the partition and remade them again, and again with no luck.


Help please?! :confused:

---

### Post by iRide113 on 2011-07-10
Bumpity....

---

### Post by Rubi1200 on 2011-07-10
Hi,
please post the specifications for the machine, especially RAM and graphics card.

Also, check that you do not have 4 primary partitions, whether the disks are Dynamic, and if your drives are part of a RAID array let us know that too.

Thanks.

---

### Post by iRide113 on 2011-07-10
> **Rubi1200 said:**
> Hi,
please post the specifications for the machine, especially RAM and graphics card.

Also, check that you do not have 4 primary partitions, whether the disks are Dynamic, and if your drives are part of a RAID array let us know that too.

Thanks.

It's a Dell 17R
Intel i5 CPU 460M @ 2.53GHz
Dual Channel DDR3 (6.0 GB)
Intel(R) HD Graphics (no dedicated graphics card on this computer)
08VFX1 Motherboard

______

> 
Also, check that you do not have 4 primary partitions, whether the disks are Dynamic, and if your drives are part of a RAID array let us know that too.


I am not sure about this part though. I attached a picture of what the partitions look like when I install Ubuntu on a 105GB partition.

The disk drive says it's a WDC WD6400BEVT-75A0RT0.

Thanks for your response!

---

### Post by Blasphemist on 2011-07-10
You do have the maximum of 4 primary partitions in use now. Normally that is not the configuration of a dual boot install. You could delete partitions but before I give you any advise I'd like to know what if anything you need to keep or recover and what if anything can be done away with. What has happened and what is the desired goal?

---

### Post by Rubi1200 on 2011-07-10
The specifications look good to me, so I doubt that is the issue.

The screenshot, however, shows 4 primary partitions. That means you have the maximum allowable amount that most modern drives accept.

You will need to delete one of the primary partitions to then create an extended partition. In the extended partition you would then create as many logical partitions as you like to install Ubuntu.

See here for more details about partitioning:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

This excellent site has great guides for setting up a dual-boot with Windows:
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

From the screenshot, I assume you want to install Ubuntu to the 92.38GB partition?

What is the purpose of the 5.80GB partition?

Most important of all, make backups before you start and plan the partitioning/installing ahead of time to avoid mistakes.

If you don't have the Windows recovery disks, create them using the built-in function in Windows.

---

### Post by iRide113 on 2011-07-10
That's the thing. Ubuntu created both of the 92GB & 5GB one.

The 480GB one is my primary for Windows 7 and the 13GB one is my recovery drive where I keep backups and system restore points.

I did nothing to create those two extras. I just pulled the slider across to make a 105GB partition and boom.

---

### Post by wildmanne39 on 2011-07-10
> **iRide113 said:**
> That's the thing. Ubuntu created both of the 92GB & 5GB one.

The 480GB one is my primary for Windows 7 and the 13GB one is my recovery drive where I keep backups and system restore points.

I did nothing to create those two extras. I just pulled the slider across to make a 105GB partition and boom.Hi, also it is recommended to run defrag about three times before resizing your partitions, and many say it is best to resize from windows, but you do not format the partiton just resize then format from the ubuntu livecd.

---

### Post by iRide113 on 2011-07-10
> **wildmanne39 said:**
> Hi, also it is recommended to run defrag about three times before resizing your partitions, and many say it is best to resize from windows, but you do not format the partiton just resize then format from the ubuntu livecd.

Will try!

---

### Post by wildmanne39 on 2011-07-10
> **iRide113 said:**
> Will try!
Please also do what Rubi mentioned back up your system before you start, make sure you have recovery cds for windows. If it ask to convert your partitions to dynamic do not let it do it.

---

### Post by iRide113 on 2011-07-11
So I defragmented my drive multiple times and then created 105GB unallocated space. Then booted via the CD and installed. It auto chose the unallocated space, but once again, it won't boot. Just freezes.

So when I went into Windows to check the partitions again, I got the same thing as the last screen shot. But I noticed something.

Look at the red box. It shows 100% of space is available... Strange?

**EDIT**: Also check at the file system table...

---

### Post by Blasphemist on 2011-07-11
What you see there is normal as windows can't see EXTx partitions. Please boot to the live CD and before starting your install, connect to the forum and use GParted to give us the same look. GParted can see both the windows and linux partition details. Also, exactly at what stage of the install does the freeze happen? Please tell us exactly what does happen after choosing to install before the lockup.

---

### Post by Groggster on 2011-07-11
I believe you just have to deactivate your floppy drive in BIOS. I had the same problem even though i do not have a floppy drive. I am not talking about the boot-order, but deactivating the floppy drive completely. You can usually do this with ease, and if you have a floppy drive that you intend to use afterwards, you can activate it again after the install.

---

### Post by wildmanne39 on 2011-07-11
> **iRide113 said:**
> So I defragmented my drive multiple times and then created 105GB unallocated space. Then booted via the CD and installed. It auto chose the unallocated space, but once again, it won't boot. Just freezes.

So when I went into Windows to check the partitions again, I got the same thing as the last screen shot. But I noticed something.

Look at the red box. It shows 100% of space is available... Strange?

**EDIT**: Also check at the file system table...Hi, do you see a screen at boot up that shows several kernels and windows system? Does it boot past that? if so you need to have a look at this link. I just looked at your first post again if you are still getting that screen then look at this first link and do not worry about posting the boot script information.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If you get a grub error  post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by iRide113 on 2011-07-11
> **wildmanne39 said:**
> Hi, do you see a screen at boot up that shows several kernels and windows system? Does it boot past that? if so you need to have a look at this link. I just looked at your first post again if you are still getting that screen then look at this first link and do not worry about posting the boot script information.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If you get a grub error  post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

Yes, it brings me to the choice of what to boot into. Either Widnows 7 or a few other options for Ubuntu. That's how I am still able to use Windows 7.

I also get an error when I delete the Ubuntu partition(s), but I know how to fix it with just entering a bootsect code.

```
GRUB loading.
error: no such partition
grub rescue>
```

Also for the link you provided, it shows for 10.04, should I still try it even though I am on the latest 11.04?

---

### Post by iRide113 on 2011-07-11
> **Blasphemist said:**
> What you see there is normal as windows can't see EXTx partitions. Please boot to the live CD and before starting your install, connect to the forum and use GParted to give us the same look. GParted can see both the windows and linux partition details. Also, exactly at what stage of the install does the freeze happen? Please tell us exactly what does happen after choosing to install before the lockup.

Are you saying to delete those partitions and then go into Ubuntu via the live CD and then show you the details?

And it happens after the installation completes and it boots up for the first time, I choose Ubuntu to boot into and the little dots are starting changing color and then freeze.

---

### Post by iRide113 on 2011-07-11
I took a picture of my kernel options...

It was too big for the thread so [here]("http://oi54.tinypic.com/msfwq1.jpg") it is.

I'm not exactly sure where to edit it or really what to edit it to. I looked at it and the posts. I had a question and posted it on that thread but still waiting for a response.

Thanks!

---

### Post by wildmanne39 on 2011-07-11
Hi, yes use the link I gave you it will be fine.

---

### Post by iRide113 on 2011-07-11
> **wildmanne39 said:**
> Hi, yes use the link I gave you it will be fine.

Okay thanks, I was giving it a shot but ran into a question as you can see above. ^^^^^

---

### Post by wildmanne39 on 2011-07-11
Hi, scroll further down the page and it will say How to temporarily set kernel boot options on an installed OS (not wubi)
 
and follow the instructions and there is a picture to help you.

---

### Post by iRide113 on 2011-07-11
> **wildmanne39 said:**
> Hi, scroll further down the page and it will say How to temporarily set kernel boot options on an installed OS (not wubi)
 
and follow the instructions and there is a picture to help you.

Yes I saw that. I will just quote my question I posted there to here.

> **iRide113 said:**
> 
[QUOTE=P4man;10069997] 

Now you can type in additional kernel options like nomodeset (**please dont make the same typing error I made for this screenshot** :D ):

[IMG]http://img26.imageshack.us/img26/3509/dgfdgrunningoraclevmvir.png[/IMG]

press control+X to boot the modified grub entry.

**Important:** setting boot options this way only applies to a single boot. If you reboot the machine, those settings will be lost, unless you make them permanent (see below)



I guess I am missing something... What did you mess up on? :confused:
[/QUOTE]

---

### Post by wildmanne39 on 2011-07-11
Hi, yes that is confusing when he typed nomodeset, he typed nomodest, he left out the t.

---

### Post by iRide113 on 2011-07-11
> **wildmanne39 said:**
> Hi, yes that is confusing when he typed nomodeset, he typed nomodest, he left out the t.

I think you mean E. :P

I will try to do that right now.

Thanks!

---

### Post by wildmanne39 on 2011-07-11
> **iRide113 said:**
> I think you mean E. :P

I will try to do that right now.

Thanks!
Hi, yes I meant e, I am helping a lot of people and I got distracted for a second.

---

### Post by iRide113 on 2011-07-11
> **wildmanne39 said:**
> Hi, yes I meant e, I am helping a lot of people and I got distracted for a second.

Okay, no worries you are extremely helpful!

But now here is the thing. Ubuntu has started working?


I entered nomodeset and booted up. It went into some weird start up and said a line failed but I couldn't see which line because it changed screens too fast. It loaded up in a weird splash screen (looked old) but it got me to the log on page.

I entered my password and it entered me into classic mode - saying I didn't have the right drivers. So I restarted the computer, picked Ubuntu and what do you know... It worked!

I am typing this from Ubuntu as we speak. The only thing is the splash screen is slightly different then normal. The dots don't move.

I made a video of it and uploaded it to youtube to show you. It seems to work, but [here]("http://www.youtube.com/watch?v=oyXOZW-Ew9M") you go if you want to see. 

As of now it works and I have rebooted a few times and still works. Only the brightness setting doesn't work still....

If you think you could help me out there too, [here]("http://ubuntuforums.org/showthread.php?t=1798761") you go :P

---

### Post by wildmanne39 on 2011-07-11
Hi, I am not sure as for the dots not changing, if you are using nomodeset permanently it may have something to do with that. Anyway I think this thread can be marked as solved. I do not know about the the brightness issues either, but I am glad you got it to boot again.

---

### Post by iRide113 on 2011-07-11
> **wildmanne39 said:**
> Hi, I am not sure as for the dots not changing, if you are using nomodeset permanently it may have something to do with that. Anyway I think this thread can be marked as solved. I do not know about the the brightness issues either, but I am glad you got it to boot again.

All I did was the temporary first boot nomodeset. Not the permanent one.

But I will mark it as solved. Thanks a lot!

---

### Post by wildmanne39 on 2011-07-12
Hi, your very welcome! glad to help anytime.

---

