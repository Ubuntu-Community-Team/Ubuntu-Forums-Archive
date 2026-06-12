---
title: "How much performance difference is there between Ubuntu and Xubuntu?"
date: 2012-04-09
forum: General Help
---

### Post by Eirreann on 2012-04-09
So I've been using Ubuntu (via wubi) for the last couple of days and it's been running quite well... so far.  However, I'm becoming incredibly irritated by the sluggishness of internet browsers and window dragging, so I am tempted to uninstall Ubuntu and replace it with Xubuntu... so my question is, how much performance difference is there between the two?  My PC is pretty old and thus quite slow...
Also, what features would I have in Ubuntu that I would lose in Xubuntu?

---

### Post by PhantomTurtle on 2012-04-09
You should see a pretty big performance boost, especially on slower computers, if you install xubuntu. If you have enough disk space you should install the package xubuntu-desktop. Also if you wanted something even faster install lubuntu. The package is lubuntu-desktop.
```
sudo apt-get install xubuntu-desktop
```
```
sudo apt-get install lubuntu-desktop
```

---

### Post by Eirreann on 2012-04-09
> **PhantomTurtle said:**
> You should see a pretty big performance boost, especially on slower computers, if you install xubuntu. If you have enough disk space you should install the package xubuntu-desktop. Also if you wanted something even faster install lubuntu. The package is lubuntu-desktop.
```
sudo apt-get install xubuntu-desktop
```
```
sudo apt-get install lubuntu-desktop
```

How much hard disc space would I need?  With Ubuntu installed right now (and word docs and music, etc...) I've only got about 7GB left...
Also, will I loose any features by installing Xubuntu?  Like Workspaces, or Dash home, or anything like that?

---

### Post by abyrne on 2012-04-09
Users almost always see a performance increase if they install Ubuntu directly and avoid using Wubi. Just be careful partitioning if you plan to keep Windows on your system.

I recommend lubuntu-desktop, which runs incredibly well on older and less powerful hardware.

---

### Post by Eirreann on 2012-04-09
> **abyrne said:**
> Users almost always see a performance increase if they install Ubuntu directly and avoid using Wubi. Just be careful partitioning if you plan to keep Windows on your system.

I recommend lubuntu-desktop, which runs incredibly well on older and less powerful hardware.

I wish that I had!  Only problem: when I tried to, it glitched up when it was starting to make the partition, now every time I try to install via the disc it gives me an error message saying that it can't partition on my hard drive...

---

### Post by abyrne on 2012-04-09
> **Eirreann said:**
> I wish that I had!  Only problem: when I tried to, it glitched up when it was starting to make the partition, now every time I try to install via the disc it gives me an error message saying that it can't partition on my hard drive...

Of all the times the live CD can glitch, it has to be during the partitioning phase. Cruel fate. :icon_frown:

But anyway, if you're still interested in installing Ubuntu directly, install the Gparted tool from the Software Center and post a screenshot. We may have a partitioning problem on our hands.

---

### Post by Eirreann on 2012-04-09
> **abyrne said:**
> Of all the times the live CD can glitch, it has to be during the partitioning phase. Cruel fate. :icon_frown:

But anyway, if you're still interested in installing Ubuntu directly, install the Gparted tool from the Software Center and post a screenshot. We may have a partitioning problem on our hands.

Will do right now!  Should I make a new thread for that?

---

### Post by abyrne on 2012-04-09
> Will do right now! Should I make a new thread for that?
Up to you. We can continue investigating the problem here or we could create a new thread if you think it would get more people to help. Just post a link to the new thread if you choose to create one.

---

### Post by Eirreann on 2012-04-09
> **abyrne said:**
> Up to you. We can continue investigating the problem here or we could create a new thread if you think it would get more people to help. Just post a link to the new thread if you choose to create one.

I think I'll make it a new thread if I indeed have a problem.  Anyway here's the screenshot:
[IMG]http://i296.photobucket.com/albums/mm188/Loredaen/Screenshotat2012-04-09221508.png[/IMG]

It doesn't look like there are any partitions after my main hard drive (I know, I don't have much space left; I just installed League of Legends on XP).

Does it make a difference if the disc I originally used was formatted on a Windows 7 computer?  I'm thinking of trying again on the XP.

---

### Post by Eirreann on 2012-04-10
*sorry, just trying to keep this on the front page so that abyrne can respond to it*

---

### Post by Peripheral Visionary on 2012-04-10
Wubi probably slows things down alot. I find, on my 8-year-old Dell with it's paltry little Celeron processor and 512 of RAM, **very little difference in speed between Xubuntu and Lubuntu.** The only real difference that I experience is the lack of features in Lubu that I enjoy in Xubu, like the customizable panel and applets and modest compositing and such. Your mileage may vary, of course. I do, however, absolutely love the default file manager in Lubu (PCManFM), and I use it in Xubu in place of Thunar.

---

### Post by PhantomTurtle on 2012-04-10
Dual Booting is definitely a better option than wubi, and also I recommend you start by getting the Xubuntu live cd so that you can save some space and bandwidth when it comes to installing. Also here is a guide on how to dual boot Ubuntu 11.10 and Windows 7: [http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/]("http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/")(well it's 11.04 and windows 7, but it will work the same with 11.10, This is the way I dual boot). Some things to add before you start is that you might not need to make any extra partitions other than /boot, /, and swap partition. You DO NOT need to make a /home partition(I don't, but that's for a different reason, anyway's it is not required).

---

### Post by Eirreann on 2012-04-10
> **PhantomTurtle said:**
> Dual Booting is definitely a better option than wubi, and also I recommend you start by getting the Xubuntu live cd so that you can save some space and bandwidth when it comes to installing. Also here is a guide on how to dual boot Ubuntu 11.10 and Windows 7: [http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/]("http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/")(well it's 11.04 and windows 7, but it will work the same with 11.10, This is the way I dual boot). Some things to add before you start is that you might not need to make any extra partitions other than /boot, /, and swap partition. You DO NOT need to make a /home partition(I don't, but that's for a different reason, anyway's it is not required).  I'm using Windows XP, actually; and apparently if I use a live disc iso downloaded from Ubuntu's website, it'll handle all of the partitioning for me.  (BTW, I'm right now figuring out how to install Ubuntu via a disc and not Wubi; this thread has moved a bit since last you commented, haha!)

---

### Post by Eirreann on 2012-04-10
Okay, I think I've figured out my problem; I only ever get the error when installing when I change the size of the partition (from 11.2GB to 10.0GB [or before I deleted some stuff from 8.9GB to 10.0GB])  So now I'm just going to give it a go with it's "recommended" partition size, and see if that helps...

---

### Post by euphoric_anomaly on 2012-04-10
> **abyrne said:**
> Users almost always see a performance increase if they install Ubuntu directly and avoid using Wubi. Just be careful partitioning if you plan to keep Windows on your system.

I recommend lubuntu-desktop, which runs incredibly well on older and less powerful hardware.

I'm running Lucid Lynx on a Dell Optiplex GX280 with only 768mb of memory and a 2.8Ghz SINGLE CORE intel processor, everything runs great, no lag, no lockups, another reason I'll never go back to Microsoft :)

---

### Post by Eirreann on 2012-04-10
> **euphoric_anomaly said:**
> I'm running Lucid Lynx on a Dell Optiplex GX280 with only 768mb of memory and a 2.8Ghz SINGLE CORE intel processor, everything runs great, no lag, no lockups, another reason I'll never go back to Microsoft :)

Wow, well for me, 2.8GHz is a lot, haha!  I'm stuck w/ 1.5GHz!

Anyway, it may be that my hard drive just is too old to stabely manage multiple partitions... I guess I'll go back to using Wubi and scour my computer to see exactly how many programmes need Windows to run; I am seriously considering just overwriting XP with Ubuntu.
So, what limitations does "Wine" have as far as programme compatibility?

---

### Post by PhantomTurtle on 2012-04-10
> **Eirreann said:**
> Wow, well for me, 2.8GHz is a lot, haha!  I'm stuck w/ 1.5GHz!

Anyway, it may be that my hard drive just is too old to stabely manage multiple partitions... I guess I'll go back to using Wubi and scour my computer to see exactly how many programmes need Windows to run; I am seriously considering just overwriting XP with Ubuntu.
So, what limitations does "Wine" have as far as programme compatibility?

With wine you could run into a bit of trouble. It cannot run everything. Before you install shrink your partition, and on Ubuntu choose the option to install on the free space. Also you could shrink it using gparted on the live cd, but this is not recommended because it could cause problems with your Windows partition.

---

### Post by abyrne on 2012-04-10
Hi Eirreann,

Sorry about the delay. Damn time zones :p

Anyway...
> and apparently if I use a live disc iso downloaded from Ubuntu's website, it'll handle all of the partitioning for me. 
Yeah, I've never trusted the auto-partitioning in the installer, but that's because of a borked Vista install about a year back. XP is a lot less finicky than Vista or 7 when it comes to partitions, so I guess its OK to let the installer do its auto-magic.

> Anyway, it may be that my hard drive just is too old to stabely manage multiple partitions
I don't think your problem is old hardware, rather just something being corrupted along the way. If you've ever used that GParted tool before, I would use that to partition manually. If you don't know what your doing, don't just start clicking buttons in that tool. It's pretty powerful, and using it without a backup of your files can leave you a bit unhappy.

> I am seriously considering just overwriting XP with Ubuntu.
So, what limitations does "Wine" have as far as programme compatibility?
Wine is a project that its developers have made tremendous progress with over time, but it's just not 100% there yet. It works flawlessly with some apps, and less so with others. In other words, it might be better to look for native Ubuntu alternatives. Also, when ditching Windows for Ubuntu (or any alternate OS), you have to consider what programs you need beyond a web browser and office suite: things like CAD, MP3 player syncing, etc. There are a lot of Ubuntu alternatives for most of them, but you want to make sure you don't leave yourself without a software tool that may be critical to you for some reason.

---

### Post by Eirreann on 2012-04-10
> **abyrne said:**
> Hi Eirreann,

Sorry about the delay. Damn time zones :p

Anyway...

Yeah, I've never trusted the auto-partitioning in the installer, but that's because of a borked Vista install about a year back. XP is a lot less finicky than Vista or 7 when it comes to partitions, so I guess its OK to let the installer do its auto-magic.


I don't think your problem is old hardware, rather just something being corrupted along the way. If you've ever used that GParted tool before, I would use that to partition manually. If you don't know what your doing, don't just start clicking buttons in that tool. It's pretty powerful, and using it without a backup of your files can leave you a bit unhappy.


Wine is a project that its developers have made tremendous progress with over time, but it's just not 100% there yet. It works flawlessly with some apps, and less so with others. In other words, it might be better to look for native Ubuntu alternatives. Also, when ditching Windows for Ubuntu (or any alternate OS), you have to consider what programs you need beyond a web browser and office suite: things like CAD, MP3 player syncing, etc. There are a lot of Ubuntu alternatives for most of them, but you want to make sure you don't leave yourself without a software tool that may be critical to you for some reason.

Thanks for the response!  Better late than never, haha!
Well, I kinda had everything solved for me, in a way; although it isn't a way that I especially like, but oh well:  my hard drive failed this morning.  I turned the PC on (Windows XP) but nothing I clicked would open, so I tried rebooting at which point it just wouldn't boot; the motherboard didn't acknowledge the hard drive as being there at all.  So I pulled it out and found it to be searing hot (I burnt my fingers a bit) so now I have effectively lost Windows XP.  Luckily we had this other old laptop that had stopped working ages ago for some reason or other, so I popped the hard drive out of that one and put it into this laptop.  We had long ago wiped that hard drive so it was completely empty, so I installed Ubuntu on it and now I am happily using Ubuntu on a 60GB hard drive and I"m experiencing little (almost no) lag of any kind!  Admittedly I kind of miss my games, but that was about the only thing that I used on Windows that I can't get on Ubuntu; everything else for the most part has a good Ubuntu alternative...

---

### Post by abyrne on 2012-04-10
Ahh.... Hard Drive Failure: The sneaky root of most unsolvable problems.

Well, sorry to hear that it conked out on you. Luckily, a 320GB drive will only set you back about $70USD or less, in case you need more than 60GB of storage.

Glad that you got Ubuntu working well on the new drive, though. Don't forget about installing Xubuntu or Lubuntu if you want to squeeze just a bit more speed out of that machine.  

I guess every cloud has a silver lining, right?

---

### Post by Eirreann on 2012-04-10
> **abyrne said:**
> Ahh.... Hard Drive Failure: The sneaky root of most unsolvable problems.

Well, sorry to hear that it conked out on you. Luckily, a 320GB drive will only set you back about $70USD or less, in case you need more than 60GB of storage.

Glad that you got Ubuntu working well on the new drive, though. Don't forget about installing Xubuntu or Lubuntu if you want to squeeze just a bit more speed out of that machine.  

I guess every cloud has a silver lining, right?
Indeed!
I'm installing Xubuntu via the terminal right now, so that I can compare it to Ubuntu and see which one I like better...

---

### Post by Max Blyss on 2012-04-10
Sorry to intrude on your thread, but it gives me a chance to talk up Xubuntu!  I've found that Xubuntu seems to not only outperform, but also to be a bit more stable than the Unity - Based standard Ubuntu, at least for me (Unity HAS come a long way, tho.).

Also, if you have a laptop, you may want to consider adding the Jupiter applet for some power - saving options...  The WebUpD8 team has a version in their repos that is tweaked for Unity 2D and Xubuntu.

sudo apt-add-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter

Should work right away, but you might just have to log in / out one little time to make it work.

Hope you enjoy Xubuntu...  It is categorically my favorite of all the distros I've tried.

---

### Post by Eirreann on 2012-04-10
> **Max Blyss said:**
> Sorry to intrude on your thread, but it gives me a chance to talk up Xubuntu!  I've found that Xubuntu seems to not only outperform, but also to be a bit more stable than the Unity - Based standard Ubuntu, at least for me (Unity HAS come a long way, tho.).

Also, if you have a laptop, you may want to consider adding the Jupiter applet for some power - saving options...  The WebUpD8 team has a version in their repos that is tweaked for Unity 2D and Xubuntu.

sudo apt-add-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter

Should work right away, but you might just have to log in / out one little time to make it work.

Hope you enjoy Xubuntu...  It is categorically my favorite of all the distros I've tried.
It is indeed very smooth!  Definitely the one to use when performance takes priority!  It runs some of the games that I've tried quite a bit more smoothly than Ubuntu.  I'll have to play around with it more, though, before I conclude if I like it more than Ubuntu or not; I absolutely love the layout of Ubuntu as-is, haha!

---

### Post by nonedrinkwater on 2012-04-10
> **Eirreann said:**
> So I've been using Ubuntu (via wubi) for the last couple of days and it's been running quite well... so far.  However, I'm becoming incredibly irritated by the sluggishness of internet browsers and window dragging, so I am tempted to uninstall Ubuntu and replace it with Xubuntu... so my question is, how much performance difference is there between the two?  My PC is pretty old and thus quite slow...
Also, what features would I have in Ubuntu that I would lose in Xubuntu?


on ubuntu 8 and 9, i had some serious problems with a stable installation when i used wubi, so from now on, i use the partition manager and create it's own space on my hard drive, never again have i ever had a crashing problem with ubuntu. 

if you really have an old computer, you might wanna check out fluxbox, it's light, and it's fast.

---

### Post by kurt18947 on 2012-04-11
A 60 GB. drive is likely big enough unless you have lots of music/vids etc.  You could do something like 15 for *buntu, 15 or 20 or XP and the remainder formatted to NTFS to use as a shared data partition. Actually, with a shared data partition you could likely go smaller with the OS partitions.  Hopefully hard drive prices will decrease once pent up demand is fulfilled.

---

