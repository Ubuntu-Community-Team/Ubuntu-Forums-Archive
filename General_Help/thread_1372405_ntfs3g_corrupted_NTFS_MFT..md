---
title: "ntfs3g corrupted NTFS MFT."
date: 2010-01-04
forum: General Help
---

### Post by stevenvu on 2010-01-04
Hi,

I don't usually post scary post titles, but i'm a little desperate. I apologise for the bad grammar and flow of this message, i'm blaming it on this tiny netbook.

Summary: Linux crashed, corrupting only the NTFS partition, the mft isn't recoverable with CHKDSK and testdisk.

getdataback on windows sees the partition with all of it's files.

Question: If getdataback can see all the files it must be able to see the mft. Is there a way to rebuild the mft?

Long winded version:

So I was running 9.10 64bit and was accessing a NTFS partition made by Vista.

I was extracting a 7z. archive when the computer became unresponsive. Ctrl Alt Backspace didn't work, alt ctrl f1 worked but i couldn't login so couldn't halt the system. I waited 5 min and turned off the computer. 4 seconds on the power button.

When the computer restarted all the partitions were fine except the NTFS partition. 9.10 couldn't mount the partition, saying CHKDSK needed to be run. Booting into Vista, I get a black screen with a cursor flashing on the top left. Booting into recovery I ran CHKDSK /f /r c: which came back with something like "mft corrupt, couldn't recover aborted".

I then got back into 9.10 and tried testdisk. When attempting to do anything with the partition, it crashed with MFTSegmentation fault. 

Getting desperate, I tried to dd the partition onto a nas but at 30 gb the computer got really slow so I aborted that. {I don't have a hdd large enough on the computer}.

I then unplugged the hdd and plugged it into another computer, using sata. Linux doesn't have any advanced recovery tools for ntfs so i used getdataback on vista. This sees all of the files but I can't find a way to recover the MFT.

I haven't lost any files but wouldn't mind restoring the mft. Is there a way of doing this?

Rant:

WTF. Ubuntu 9.10 comes with ntfs3g as default? It should be safe to use. Windows has crashed many times but hasn't taken down the mft. 

Reading more about this, an MFT getting corrupted should never really happen other than if the disk is physically defected.

ntfs3g shouldn't be included as default and should come with a warning.

Please help,
Steven

---

### Post by ajgreeny on 2010-01-04
Have you seen this post?
[http://ubuntuforums.org/showthread.php?t=847922](http://ubuntuforums.org/showthread.php?t=847922)

It may or may not help, but I thought it worth showing you.

I have no experience of the problem to offer you, either, but do wonder if the problem is a result of the ntfs file system not being unmounted (as it crashed) which makes it unmountable in linux unless you do it manually with the -f option (force).  Normally running it again in it's own OS, ie running windows and then shutting down properly, would release the lock on the linux mount, but perhaps there is more to your problem that this will not solve.

---

### Post by bodhi.zazen on 2010-01-04
I understand you are frustrated, but lets try to fix your problem rather then blaming ntfs-3g , you could as easily blame  7z or microsoft :lolflag:

I would agree that the tools to fix ntfs from linux are not as good as the microsoft tools.

If you are having problems from windows, it is possible your HD failed as you suggest ?

I don not know how to fix your problem, but I would suggest you consider posting on a windows forum as you may get a better answer there.

I would pull the data and re-install Windows (because I do not have a better solution). You may require professional assistance if the recovery tools (test disk / photorec) do not work.

I would check the health of your hard drive and if necessary consider replacing it.

---

