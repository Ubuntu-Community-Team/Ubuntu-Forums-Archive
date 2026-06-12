---
title: "Win 7 computer doesn't boot at all"
date: 2011-07-27
forum: General Help
---

### Post by lilaliv on 2011-07-27
Hi there,

I know these forums are not about Windows, but I think I'll get better help here than in one of the Windows forums, let me explain, why:

A friend of mine has a computer with Windows 7 on it, now it just doesn't boot anymore. I already changed the boot sequence to CD/DVD, but even with the recovery disc, there is nothing happening at all.

Now, since I use Ubuntu 11.04 personally, I thought 'why not try Ubuntu Live'. There's this one second where the purple screen came up (this only happened once), then it's black again and then, 3 minutes later, this is what comes up:

```
udevadm settle - timeout of 180 seconds reached, the event queue contains:
    /sys/devices/pci0000:00/0000:00:01.0/0.0000:01:05.0 (933)
    /sys/devices/pci0000:00/0000:00:02.0/0.0000:02:00.0 (938)
    /sys/devices/pci0000:00/0000:00:01.0/0.0000:01:05.0/drm/controlD64 (1290)
    /sys/devices/pci0000:00/0000:00:01.0/0.0000:01:05.0/drm/card0 (1291)
udevd[72]: worker [86] unexpectedly returned with status 0x0100

udevd[72]: worker [86] failed while handling '/devices/pci0000:00/0000:00:02.0/0000:02:00.0'

udevd[72]: worker [93] unexpectedly returned with status 0x0100

udevd[72]: worker [93] failed while handling '/devices/pci0000:00/0000:00:01.0/0000:01:05.0'
```Since this is the ONLY sign of life I ever got from this computer - and I really don't understand it - I hope that maybe one of you can help and tell me what I can do to make this computer work again?

Thanks alot!

---

### Post by turtle153 on 2011-07-27
Is there any message from booting Windows?
And a purple screen suggests that it is booting from the Ubuntu CD, but I would suggest you use the 10.04 version (or maybe 10.10) as it is more stable.

---

### Post by lilaliv on 2011-07-27
> **turtle153 said:**
> Is there any message from booting Windows?
And a purple screen suggests that it is booting from the Ubuntu CD, but I would suggest you use the 10.04 version (or maybe 10.10) as it is more stable.

No, there is just a black screen booting Windows, no message at all.

Just tried to boot Ubuntu again, the purple screen came up for a few seconds, the error message I get now is a little shorter and some of the numbers in the brackets changed:

```
udevadm settle - timeout of 180 seconds reached, the event queue contains:
    /sys/devices/pci0000:00/0000:00:01.0/0.0000:01:05.0 (933)
    /sys/devices/pci0000:00/0000:00:01.0/0.0000:01:05.0/drm/controlD64 (1292)
    /sys/devices/pci0000:00/0000:00:01.0/0.0000:01:05.0/drm/card0 (1293)
udevd[72]: worker [159] unexpectedly returned with status 0x0100

udevd[72]: worker [159] failed while handling '/devices/pci0000:00/0000:00:01.0/0000:01:05.0'
```

I'm downloading Ubuntu 10.04 right now, let's see if that helps.

Thanks for your help so far! :)

---

### Post by seawolf167 on 2011-07-27
How sure are you that the CD/DVD drive is working properly? Are you able to boot off a Live USB? (for example, created with [UNetBootin]("http://unetbootin.sourceforge.net/"))

---

### Post by Blasphemist on 2011-07-27
See if this makes sense to you. The boot sector of the cd is loading stage one of the boot process and proceeding to stage 2 from the cd. It seems to me that at least part of that is happening from the error you get. It's not stage one that provides enough to get that far from my understanding. I don't know the sequence of what happens in stage 2 and later but I'm sure at some point the required devices are initialized. It looks to me like that isn't successful though I can't tell any helpful details from the error information. It seems it might be the video card but that is a guess.

Is this a laptop or pc? Did anything physical or otherwise happen preceding the start of this? Have you tried re-seating the memory and any cards that can be? Do you have a different gpu that can be tried? What make and model is the machine?

---

### Post by CatKiller on 2011-07-27
Based on nothing more than a hunch, I suspect misbehaving graphics hardware.

---

### Post by lilaliv on 2011-07-27
Wow, so many responses in such a short time :) Sooo...

---

@ seawolf167

Yeah, I'm pretty sure it does. I've tried to boot from a USB device and it doesn't work, either. Well, it works even less, if you consider that the Ubuntu 11-CD worked at least a little bit. What I've tried so far is

CD: Ubuntu 11.04 Live
purple screen, followed by: black screen, followed by: code above

USB: Ubuntu 10.04 Live
black screen

USB: Parted Magic
black screen  with cursor, followed by: black screen

---

@ Blasphemist

Yes, that absolutely makes sense to me!

It's a PC and since it is not mine, I can't tell you anything particular about it... :( It's from a company called "Medion" that is sold by a large supermarket here in Germany, but I doubt that there is any support anymore since they were just taken over by some Chinese company or something...

As far as I know there hasn't been anything happening to the computer, nothing physical, no new programs, etc. Concerning the hardware, I have to admit that I don't have any idea how to check/fix something, I don't even know what all the stuff looks like... :/ so sorry!

---

@ CatKiller

Could be, I don't know... but does it make sense that there is the purple Ubuntu 11 screen showing up then, even if it's just for a few seconds? I can even see these two symbols at the bottom, even though I could never tell what they mean...

---

Thanks for all the answers!

---

### Post by Blasphemist on 2011-07-27
lilaliv- If you can post the make and model of this pc I'll look it up and see what would be involved (in as much detail as I can) in getting to the video board.

---

### Post by turtle153 on 2011-07-27
> **CatKiller said:**
> Based on nothing more than a hunch, I suspect misbehaving graphics hardware.

Seems very likely. I had this problem when installing on an old machine; live just wouldn't run. In the end I chose to install off the server CD then put the ubuntu-desktop package over it.

In hindsight, the alternate CD would have been a better option as it doesn't need fancy graphics during install either. The only downside to this is that you have to install Ubuntu to use it, though it's also going to be faster.

---

### Post by seawolf167 on 2011-07-27
> **lilaliv said:**
> CD: Ubuntu 11.04 Live
purple screen, followed by: black screen, followed by: code above

USB: Ubuntu 10.04 Live
black screen

USB: Parted Magic
black screen  with cursor, followed by: black screen

If you select to enter BIOS during POST, can you read and see the BIOS menu options on your monitor? (to check the video card output and monitor display work)

---

### Post by lilaliv on 2011-07-27
Thanks for your answers again!

---

@ Blasphemist

OK, there is a sticker on the back, this is what it says:

Medion (this is the make)
Model: MED MT 525

Is there anything else you need? I don't know what all the numbers and letters mean...

Thank you so much!

---

@ turtle153

I'm no pro, I don't know what all that means, let alone do it...
What CAN I do, then? Sounds rather complicated.

Thank you, too! :)

---

Thanks for helping me! :) That's really nice of you!

---

### Post by lilaliv on 2011-07-27
> **seawolf167 said:**
> If you select to enter BIOS during POST, can you read and see the BIOS menu options on your monitor? (to check the video card output and monitor display work)

What does POST mean? I AM able to enter the BIOS menu, this is how I changed the boot sequence. How do I check if there are any problems with the video card output or monitor display? (btw, the monitor is mine and works perfectly fine with my own computer...).

---

I do see, why you all think of a video card error, but how is it even possible then that I can see the purple Ubuntu screen, even for just a few seconds, before it turns black? Or do I mix something up here?

---

Thank you, seawolf!

---

### Post by turtle153 on 2011-07-27
POST is Power On Self Test. In the BIOS settings there may be display options.


[http://www.ubuntu.com/download/ubuntu/alternative-download#alternate](http://www.ubuntu.com/download/ubuntu/alternative-download#alternate) I recommend the 10.04.3 downloads again. The installer is text-based but it pretty self-explanatory should you decide to use it.

---

### Post by seawolf167 on 2011-07-27
> **lilaliv said:**
> I do see, why you all think of a video card error, but how is it even  possible then that I can see the purple Ubuntu screen, even for just a  few seconds, before it turns black? Or do I mix something up here?

Since you can see and change items in BIOS, and the purple Ubuntu screen comes on (if only for a second) I don't think the problem is related to your physical graphics card (and definitely not your monitor, though maybe graphics card drivers?).

Do you perhaps receive a message saying something like "signal out of range" indicating the resolution of the boot media is too high?

Do any other LiveCD work? (Debian, even Windows, etc.)?

If you try to boot off the LiveCD holding right-shift do you get a boot prompt?

---

### Post by turtle153 on 2011-07-27
Perhaps it's a long shot, but Windows might not have booted because a problem with the MBR (that tells it what to do at startup). Certainly then installing Ubuntu would fix it  as it rewrites the boot records.

---

### Post by lilaliv on 2011-07-27
Sorry that it takes so long to answer, but I really want to make sure I try all the things you suggest.

---

@ turtle153

OK, maybe that would be an option. I'd prefer Ubuntu 11, though, since Ubuntu 10 didn't work at all and Ubuntu 11 at leats worked a little... how do I know which of the isos I have to download and install?

And what happens if I try to install Ubuntu - doesn't it 'kill' Windows? I know it's possible to run two systems at the same time, but don't I have to partition the hard-disk first?

---

@ seawolf

I do not receive any message and neither Windows nor Ubuntu Live works (I only have a recovery CD for Windows, that's all I got). I do not know Debian, to be honest, does it work the same way Ubuntu does?

Holding right-shift while booting doesn't change anything - what is it that should be happening?

I'm so sorry, maybe I'm doing everything wrong and it's me, not the computer...

---

Thank you for all your support, it must be tiring to give me all your ideas and not see any results...

---

### Post by seawolf167 on 2011-07-27
Just to ensure it isn't something as simple as a corrupted download - can you re-download the Ubuntu LiveCD and [MD5Sum ]("https://help.ubuntu.com/community/HowToMD5SUM")the download to check its integrity, then re-burn it to a cd at the slowest possible setting and try to boot off that cd?

---

### Post by lilaliv on 2011-07-27
> **seawolf167 said:**
> Just to ensure it isn't something as simple as a corrupted download - can you re-download the Ubuntu LiveCD and [MD5Sum ]("https://help.ubuntu.com/community/HowToMD5SUM")the download to check its integrity, then re-burn it to a cd at the slowest possible setting and try to boot off that cd?

Mmh, I used the same CD to install Ubuntu on my own computer. When I still had Windows, I tried the live version (it worked pretty well), and then I decided to uninstall Windows and installed Ubuntu 11 instead. My own computer still works perfectly.

But if you think it helps to re-download Ubuntu 11, I'll do. It'll just take a while since I have to start my own computer again and therefore disconnect all the stuff from the broken Windows computer (I'm typing from my laptop right now and I can't burn CDs with it).

It's funny that you need two computers to make one other work ;)

---

### Post by turtle153 on 2011-07-27
If you're used to using Ubuntu 11 then that alternate CD will be fine then. Before you install you can always do a disk integrity check.

The installer automatically partitions the disk so you don't need to worry about Windows, it will just give Windows slightly less disk space.

If you're really worried about data on the disk and you want to back it up, you should plug the hard drive (as a secondary disk) into a working computer and extract files from there.

---

### Post by lilaliv on 2011-07-27
> **turtle153 said:**
> If you're used to using Ubuntu 11 then that alternate CD will be fine then. Before you install you can always do a disk integrity check.

The installer automatically partitions the disk so you don't need to worry about Windows, it will just give Windows slightly less disk space.

If you're really worried about data on the disk and you want to back it up, you should plug the hard drive (as a secondary disk) into a working computer and extract files from there.

Maybe this question is silly, but which of these isos do I have to download?

>     ubuntu-11.04-alternate-amd64.iso.torrent
    ubuntu-11.04-alternate-i386.iso.torrent
    ubuntu-11.04-desktop-amd64.iso.torrent
    ubuntu-11.04-desktop-i386.iso.torrent
    ubuntu-11.04-server-amd64.iso.torrent
    ubuntu-11.04-server-i386.iso.torrent

One of the alternates, right? Is it OK if I take the second?

---

### Post by seawolf167 on 2011-07-27
> **lilaliv said:**
> Maybe this question is silly, but which of these isos do I have to download?

Hmmm... maybe you are attempting to boot a 32bit machine with a 64bit install. Do you know what architecture the install cd you burned is? If it is x86_64, are you 100% sure the target machine (the one your are having problems with) is a 64bit machine?

---

### Post by turtle153 on 2011-07-27
Could 64bit on a 32bit computer have caused the problems we saw earlier I wonder? I'd have hoped it would have at least said a problem like that :/ If in doubt use 32 anyway.
And use that alternate download, the desktop live CD clearly hasn't worked so far.

---

### Post by piratebill on 2011-07-27
> **lilaliv said:**
> Maybe this question is silly, but which of these isos do I have to download?



One of the alternates, right? Is it OK if I take the second?

Yes.  That is the 32 bit one (will work on any computer).  The other one will only work on 64bit computers (almost anything made in the last few years).  32 is the safe bet ;)

---

### Post by lilaliv on 2011-07-27
Well, the original Windows on that computer is a 32-bit, my own computer is a 32-bit, too, so the CD I used must be a 32-bit, too, otherwise my own computer wouldn't work, would it...?

I just downloaded Ubuntu 11 again, Ubuntu 10 as well, and the second iso of my last post (ubuntu-11.04-alternate-i386.iso). I'm gonna burn all three of them and see if there is anything they can do. I'm curious what the alternate one will do - hope dies last :)

---

Haven't seen your reply - thank you, too, piratebill :)

---

### Post by piratebill on 2011-07-27
> **lilaliv said:**
> Well, the original Windows on that computer is a 32-bit, my own computer is a 32-bit, too, so the CD I used must be a 32-bit, too, otherwise my own computer wouldn't work, would it...?


This is correct.

---

### Post by turtle153 on 2011-07-27
Good luck with the installs, I know how much of a pain it is when Linux breaks :p

---

### Post by Mark Phelps on 2011-07-27
Since you're running Win7, do NOT, repeat NOT -- allow the Ubuntu installer to resize your Win7 OS partition to make room for Ubuntu.  Doing so risks filesystem corruption which, if it happens, will render your Win7 unbootable.

Use the Win7 Disk Management utility to do any shrinkage of the Win7 OS partition. And do NOT use it to create any new partitions.  Leave the new unallocated space as is, and allow the Ubuntu installer to format it.

Also, if your PC has an optical drive, BEFORE you do anything else, use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will allow you to repair the Win7 boot loader later -- should it become corrupted.

---

### Post by turtle153 on 2011-07-27
> **Mark Phelps said:**
> Since you're running Win7, do NOT, repeat NOT -- allow the Ubuntu installer to resize your Win7 OS partition to make room for Ubuntu.  Doing so risks filesystem corruption which, if it happens, will render your Win7 unbootable.

Use the Win7 Disk Management utility to do any shrinkage of the Win7 OS partition. And do NOT use it to create any new partitions.  Leave the new unallocated space as is, and allow the Ubuntu installer to format it.

Also, if your PC has an optical drive, BEFORE you do anything else, use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will allow you to repair the Win7 boot loader later -- should it become corrupted.

We've already established that Windows won't boot, therefore there's no access to those tools. I dual-boot with Windows 7 (installed Ubuntu around 5 times and used gParted to resize Window's partition a fair few times too) and there have been no problems at all.

---

### Post by lilaliv on 2011-07-27
@ Mark

Windows 7 doesn't do ANYthing anymore, it doesn't boot, the recovery disc won't help, either,* it's dead. I don't have any option to do anything with it, I cannot create any new space or a repair disc, it's plain dead... :( But thanks for your advice anyway because...

* btw: I really only have a recovery disc, "Medion" never provides a complete Windows installation disc... (so I guess it's not even possible to boot from it, if I think about it)

---

Haha :D - good news:

I've tried the alternate Ubuntu CD first, and a menu showed up. I've looked through several of the options, but always ended up cancelling the installation when Linux asked me how to use the disc... I was afraid, I admit it :( the only option was to use the entire disc and I thought that whatever I would try, it would definitely totally ruin Windows.

So I tried Ubuntu 10 - and what can I say? The Live version works! It works!! I can see the computer, wohoo! :) There is one disc, two partitions, one called BOOT, one called RECOVER, windows is there, all the data is there, so at least I can save all the stuff on it - that's great for now.

So now I'm really keen on working out what the original problem is - there has to be something wrong with the boot manager then, hasn't it? I'm not sure, I've read somewhere else that installing the linux boot manager using the Live CD is possible - the question is whether the Linux boot manager is able to boot Windows 7 if there is no Ubuntu installed...?

---

Thank you all SO MUCH for your help by now! This is the first time for months that this computer shows any sign of life ;) I just really hope I can fix this...

---

### Post by turtle153 on 2011-07-27
The simplest way is to install Ubuntu which will then set up the Grub boot manager. This lets you switch between Windows and Ubuntu at startup.

Once you can get into Windows, (If you can at all) you can then use a program called MbrFix to rewrite the boot manager for Windows alone, and then finally remove the Ubuntu partition to free up disk space.

---

### Post by lilaliv on 2011-07-27
> **turtle153 said:**
> The simplest way is to install Ubuntu which will then set up the Grub boot manager. This lets you switch between Windows and Ubuntu at startup.

Once you can get into Windows, (If you can at all) you can then use a program called MbrFix to rewrite the boot manager for Windows alone, and then finally remove the Ubuntu partition to free up disk space.

But don't I risk that Windows is destroyed completely? When I tried to install Ubuntu (I really wanted), it would always give me four options:

- 3x use complete hard disc (in different ways),
- 1x manual (too scary).

Since we all know that Windows likes to spread all its stuff, like, on the whole hard disc (that's what that defragmenting stuff is all about, isn't it), I'm afraid this will only cause new problems. I don't want to ruin windows any *more*.

---

Well, it's half past midnight here and I can't ask for the owner's opinion on that right now. First I will suggest to save all the private data, then I will see what else I can do. I think I will have to tell him that maybe there's no other solution than trial and error, accepting possible damages, but I just can't do that without permission.

---

But I really have to say that it's great how much support there is within the Linux community. This is so different from everything I know ;) Thank you all! I will probably be back by tomorrow evening :)

---

### Post by turtle153 on 2011-07-27
Is this on the graphical CD? It should have Whole-disk and dual-boot.
You can always plug it into another computer to save data.

Good night now then, I'll check here tomorrow to see if it works :)

---

### Post by piratebill on 2011-07-27
> **lilaliv said:**
> But don't I risk that Windows is destroyed completely? When I tried to install Ubuntu (I really wanted), it would always give me four options:

- 3x use complete hard disc (in different ways),
- 1x manual (too scary).

Since we all know that Windows likes to spread all its stuff, like, on the whole hard disc (that's what that defragmenting stuff is all about, isn't it), I'm afraid this will only cause new problems. I don't want to ruin windows any *more*.

---

Well, it's half past midnight here and I can't ask for the owner's opinion on that right now. First I will suggest to save all the private data, then I will see what else I can do. I think I will have to tell him that maybe there's no other solution than trial and error, accepting possible damages, but I just can't do that without permission.

---

But I really have to say that it's great how much support there is within the Linux community. This is so different from everything I know ;) Thank you all! I will probably be back by tomorrow evening :)

One "risk free" way I can think of is to install ubuntu on an external drive.  that way grub and the new OS go there, and leave the main windows drive untouched.  If you boot off the new drive, grub will come up showing both ubuntu and windows (hopefully).  If you can boot into windows.  Just back up everything first.  

At least you can back the drive up.  Good luck :)

---

### Post by CatKiller on 2011-07-27
> **lilaliv said:**
> 
- 1x manual (too scary). 

It's not that scary. Read what it tells you carefully & if you aren't sure, ask :)

---

### Post by seawolf167 on 2011-07-27
> **lilaliv said:**
> 
I've tried the alternate Ubuntu CD first, and a menu showed up. I've  looked through several of the options, but always ended up cancelling  the installation when Linux asked me how to use the disc... I was  afraid, I admit it :sad:  the only option was to use the entire disc and I thought that whatever I  would try, it would definitely totally ruin Windows.

As long as you:

[LIST=1]
[*]Don't delete the partition
[*]Overwrite the partition
[*]Re-format the partition
[*]Let a *nix tool resize the partition
[/LIST]
You will not have any issues with it ruining Windows!

> **lilaliv said:**
> But don't I risk that Windows is destroyed completely? When I tried to install Ubuntu (I really wanted), it would always give me four options:

- 3x use complete hard disc (in different ways),
- 1x manual (too scary).

Manual partitioning isn't too scary! There is lots of [documentation ]("https://help.ubuntu.com/community/WindowsDualBoot")available and all sorts of people here to answer your questions.

The quick summary is to resize your Windows partition with a Windows disk (since Windows works natively with NTFS and GParted tends to give Windows a hard time with partitions it formats in NTFS). Once resized, boot into your install cd and select to manually partition the drive, then simply create 3 new partitions (minimum IMO).

One for / (root), type ext4, mount point: /
one for /home, type ext4, mount point: /home
one for swap, type swap, mount point: swap

And you'll be good to go.

> **lilaliv said:**
> Well, it's half past midnight here and I can't ask for the owner's opinion on that right now. First I will suggest to save all the private data, then I will see what else I can do.

Backups are always a good idea. I highly suggest full drive images created with the help of [Clonezilla]("http://www.clonezilla.org"), then incremental backups using something like rsync.

---

### Post by seawolf167 on 2011-07-27
Just wanted to add since you were worried about the Windows MBR and partition boot records, they are easy to restore with a Windows disk. Depending if Windows will boot for you at all right not, you may have to boot off a Windows recovery disk (or install cd and enter the recovery mode) and type these commands (assuming Windows 7 or Vista)

```
bootrec.exe /fixmbr
bootrec.exe /fixboot
```

The first (fixmbr) re-writes the drive master boot record, the second (fixboot) re-writes the partition boot record.

There is even a way to recover these with a Linux LiveCD, though I can't seem to find that link at the moment.

---

### Post by piratebill on 2011-07-27
> **seawolf167 said:**
> Backups are always a good idea. I highly suggest full drive images created with the help of [Clonezilla]("http://www.clonezilla.org"), then incremental backups using something like rsync.

If there was a comment rating system here, I'd upvote this twice.

Also seawolf, if you find that link for restoring the windows mbr through linux that would be extremely useful to me.

---

### Post by turtle153 on 2011-07-27
> **seawolf167 said:**
> Just wanted to add since you were worried about the Windows MBR and partition boot records, they are easy to restore with a Windows disk. Depending if Windows will boot for you at all right not, you may have to boot off a Windows recovery disk (or install cd and enter the recovery mode) and type these commands (assuming Windows 7 or Vista)

```
bootrec.exe /fixmbr
bootrec.exe /fixboot
```

The first (fixmbr) re-writes the drive master boot record, the second (fixboot) re-writes the partition boot record.

There is even a way to recover these with a Linux LiveCD, though I can't seem to find that link at the moment.

When my Grub broke, I figured it would be easier to use Mbrfix than finding my recovery CDs xD So I used [http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm). Worked perfectly.

I don't think using that with Wine would be smart, but how about [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)?

---

### Post by seawolf167 on 2011-07-28
> **piratebill said:**
> Also seawolf, if you find that link for restoring the windows mbr through linux that would be extremely useful to me.

Well I couldn't find the post from UbuntuForums I had in mind, but here are two alternatives. Note that the Windows MBR only tries to boot whichever harddrive partition is flagged as bootable or active, so there isn't anything special about it.

[Super Grub Disk]("http://www.supergrubdisk.org/")
[MBR ]("http://packages.ubuntu.com/natty/mbr")package (available though repos)

---

### Post by Mark Phelps on 2011-07-28
> **lilaliv said:**
> ... I don't want to ruin windows any more.

This is a long thread and I might have missed this ... but if your PC has an optical drive, when you can get into Win7, use the Backup feature to create and burn a Win7 Repair CD.  That will prove invaluable later should you need to repair the win7 boot loader.

---

### Post by lilaliv on 2011-07-28
Wow, so many responses and I can't even work on that computer until  Saturday... Nevertheless, I just wanted you guys to know that I haven't  forgotten the forums, it's just that I don't know the owner's opinion on  that yet, so I have to wait.

Sooo...

---

@ turtle153

This  is what happened with the alternate CD. I haven't tried to install  Ubuntu 10, I was so excited the Live version was running and so tired at  the same time ;) I've ended up explaining everything via e-mail and now  I'm waiting for the answer.

---

@ piratebill

Yes,  that would be a really good idea! - but I don't have one and I have to  admit that when it comes to hardware, I'm even more scared to break  something since everything looks so fragile inside of a computer... But that definitely is an option I'll keep in mind, thank  you! :)

Btw, is it really helpful to backup the whole system if  it doesn't even work? I was rather thinking of saving private stuff like  documents or photos or whatever. I've heard of Clonezilla, but I'd  rather use it with a working system.

---

@ CatKiller

You  know, if that computer was mine, I'd do it. And yes, I've already  noticed that people in these forums are really, really helpful :) But  nevertheless, I don't trust Windows... I've had enough problems with  Linux so far, but Windows beats everything ;) I have to wait if the  owner of the computer is OK with the possbility of a broken OS, even  though chances are little.

---

@ seawolf167

Well,  I didn't plan to delete, re-format or overwrite anything, and if I knew  that Windows would just logically use disk space, I wouldn't be afraid  to let Linux do whatever it wants to. But I do know that Windows likes  to spread its stuff. It's like a box with confetti - Linux builds a nice  little carpet, Windows totally goes crazy and throws it around ;) The  computer I'm talking about is somewhat older, there's lots of stuff on  it as far as I could see, and the hard disc is already partitioned for  some recovery mode by the maker.

GParted, btw, is a program  someone in a Windows forum recommended to me - isn't it as good then?  I've tried to start it using a USB device, the computer didn't react at  all, so I thought that maybe on Saturday I just burn a regular CD and  try again. Not good?

And no, Windows won't boot :( Thanks for the  code, anyway, might be helpful if I somehow succeed in bringing Windows  to life again!

---

@ turtle and seawolf concerning this MBR fixing thing:

Is  there a way to restore the boot record with a Linux Live CD then...? I  mean, is there a way to repair that without installing Ubuntu at all? Of  course it could still be something different going on here, but from  what I could see yesterday, I'd say that it IS the MBR that's broken and  maybe that would already fix it.

---

@ Mark

Thank  you for your advice, I've already read about that, too. The only problem  is that I do NOT get into Windows at all, it won't boot. So there's no  chance to create a repair disc.

---

Well, that's it for now - more to be coming soon ;)

Thanks everyone! :)

---

### Post by piratebill on 2011-07-28
> **lilaliv said:**
> 

Btw, is it really helpful to backup the whole system if  it doesn't even work? I was rather thinking of saving private stuff like  documents or photos or whatever. I've heard of Clonezilla, but I'd  rather use it with a working system.



I'd say yes for one reason.  Its not your computer.  I know where I store all my important stuff on my machines (home folder or my docs in windows).  However the owner could have things stored else where (places one wouldn't normally think of when backing up data).  Some programs like firefox for instance, store all their settings in places other than My docs.  Years of bookmarks or other data could be lost if you don't know to look for it.  Full system imaging isn't a bad choice unless you know exactly where the user's important stuff is.  

That being said, you will probably be ok just backing up their my docs folder.  Disk imaging can take a while and it uses more of your space, so really it all comes down to your preference.

---

### Post by turtle153 on 2011-07-29
I would say you have 3 options then:
1. Try to install Linux (which may well be the best option if it's going to work)

2. Use a Live CD to fix the MBR (perhaps [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) this might solve the problem if the MBR is broken)

3. Attach the hard disk to another computer and take the files from there (but this won't fix Windows so you still might want to use another option)

If you do install Ubuntu and find that Windows is still broken then at least you'll have a working system (Ubuntu) instead.

---

### Post by lilaliv on 2011-07-31
Hi there,

it's me again :)

---

@ piratebill

Yes, that's true. Nevertheless, I don't have another disk to save all the stuff, so I asked the owner and backing up the whole disk is not possible for now. It's just too big, so I saved all the documents and stuff he told me to, and I think that's OK.

---

@ turtle153

I just got a Win 7 disc and what can I say? Windows is still alive. I could choose to repair Windows, but it would tell me it cannot find any problems. I even "repaired" the MBR (if it was ever broken at all) manually, so it's there. The disk is active, too. So altogether the computer isn't broken - at least that's what Windows thinks.

What can I do? Seriously, I don't know how to look for problems if it tells me everything's fine. System restore is not possible, since there are no backup points. Installing Ubuntu now seems to be senseless, too, I'd rather break Windows, I guess.

---

Any suggestions? I mean, ANY?
I don't care how simple or far-fetched they are...

Thank you all! :)


**Edit:** Oh, I totally forgot to mention that I just found out that this computer was originally delivered with Windows Vista, Windows 7 was just an upgrade. Nevertheless, Windows 7 worked and the problem is not just there since the upgrade. I've tried to repair Windows with both a Vista and 7 disc, both didn't work.

---

### Post by turtle153 on 2011-07-31
Do you want to have Windows on that computer? If so your best bet probably is to take it to a repair shop or even buy a new copy.

---

### Post by lilaliv on 2011-07-31
> **turtle153 said:**
> Do you want to have Windows on that computer? If so your best bet probably is to take it to a repair shop or even buy a new copy.

It's not mine, and I don't think the owner wants a Linux system... ;)

Well, I think it'll be best to re-install Windows, I'm not sure if it's even possible to repair this system, though I don't know, either, how to uninstall a not-working system... ;)

Nevertheless, thanks again for all your help! :)

---

**Yay, problem solved!** :)

After I got the opportunity to save the whole system on an external hard drive, I formatted the disk and tried to re-install Windows. The error code I got finally gave me a hint: there was something wrong with the internal memory, in my case two of the four RAM modules were broken. After I removed them, everything was fine again.

Thanks everyone for your help!

---

