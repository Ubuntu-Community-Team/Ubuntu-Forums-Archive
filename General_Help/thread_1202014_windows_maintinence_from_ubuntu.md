---
title: "windows maintinence from ubuntu"
date: 2009-07-01
forum: General Help
---

### Post by blur xc on 2009-07-01
I've heard here and there that you can fix windows from inside of linux.  So, what kinds of things can you fix?  I know you can scan your windows partition from inside of linux, but can you defrag ntfs partitions as well?  I ask because I was educating myself about the purpose of the windows page file, and pretty much, because it's being used while you are running windows, can't be defragged from inside of windows.  Of course, there are boot defrag utilities you can buy, but I already have an ubuntu boot usb drive I could pop in and install for those kids of things...
 
thanks,
BM

---

### Post by linuxmagick on 2009-07-01
While I can vouch for Ubuntu being great for mounting NTFS drives and copying data off of them (done this quite a few times to save peoples data), I don't think I have ever heard of a utility to defrag the Windows page file from Linux.  I'm not saying that such a utility doesn't exist, just that I've never heard of it.  Maybe someone else has.  

You may want to look at [Sysinternals]("http://www.sysinternals.com").  They have a free download utility called Pagedefrag that will reboot your Windows PC and defrag the pagefile before Windows completes loading again.  As for regular disk defragmentation, the built in defrag should suffice.  The only thing some people might find as a downside is that Sysinternals is owned by Microsoft now.  But they were making great tools long before MS took an interest in them.

Don't quote me on the exact figure, but I believe you shouldn't see much of a performance impact until you're around 18%+ fragmentation.

And if someone has a Linux only solution for this, please let me know, as I'd much rather recommend that :)

---

### Post by blur xc on 2009-07-01
Yeah, I can't say for sure what percatage of fragmentation I've had in the past that has caused some good system slowdown...  I don't know if it means anything to you, but I use SolidWorks and Pro E...both are serious system hogs...  When you open an assembly in SW, it copies every individual file over to a temp directory under your documents and settings\local settings folder.  In a typical day, that could be hundreds of files being created and deleted, and if the drive starts getting fragmented, the open/close/save times get REALLY long.  I've read that the default windows defragmenter isn't as good as other solutions...  So, it got me wondering...too bad they don't port SW over to linux..  Pro E used to work in linux, but that ship has sailed, in I think the last release.
 
Thanks for the reply.
 
BM

---

### Post by linuxmagick on 2009-07-01
I've never used Solidworks before.  I'm not the most creative person around.  You've heard right that the built-in defragmenter isn't that great.  It's actually a stripped down version of a commercial tool called DiskKeeper (or something like that).  The commercial version allows you to do a defrag at boot time.  As long as your programs free up the files they are using when you exit, it shouldn't be a problem for the built-in defrag, though.  Obviously, files that are locked or in use like certain Windows system files and other open programs can't be defragged.  But once those files aren't being used by any processes, they should defrag fine.  I would at least give it a shot and see how it works for you.

---

### Post by linuxmagick on 2009-07-01
If they don't run natively in Linux, have you ever tried using WINE to see if they will run?

---

### Post by blur xc on 2009-07-02
Nope I haven't tried wine.  Could be an interesting experiment, but I'd be highly skeptical if either program would work.
 
BM

---

### Post by bobince on 2009-07-02
> because it's being used while you are running windows, can't be defragged from inside of windows

You can always turn off the pagefile, reboot, defrag, then turn it back on again. Windows (as with Linux) runs fine without a pagefile, as long as your machine isn't desperately low on memory.

---

### Post by Slim Odds on 2009-07-02
> **bobince said:**
> You can always turn off the pagefile, reboot, defrag, then turn it back on again. Windows (as with Linux) runs fine without a pagefile, as long as your machine isn't desperately low on memory.

Totally agree. Also disable hibernation so that the large space that it also takes gets cleaned up as well.

You can always turn it back on after the defrag.

---

### Post by krackedpress on 2009-08-27
> **blur xc said:**
> Nope I haven't tried wine.  Could be an interesting experiment, but I'd be highly skeptical if either program would work.
 
BM
I tried SmartDefrag under WINE, but it will not run properly.  

I need to defrag two NTFS drives with Linux/Ubuntu since the first
drive is ext3 and drive 2 and 3 were kept NTFS to save all of the 
file there, since the machine is my file server and I changed from
Win2000 to linux without dual boot, since there was not room to do so.

---

