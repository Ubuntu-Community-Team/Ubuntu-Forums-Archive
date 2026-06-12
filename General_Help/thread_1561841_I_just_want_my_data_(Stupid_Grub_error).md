---
title: "I just want my data (Stupid Grub error)"
date: 2010-08-26
forum: General Help
---

### Post by dcsii on 2010-08-26
Well about a week ago my computer acted a bit funny and upon attempting a reboot I hit grub error 17, and really haven't been able to make it past it. The posts I find, haven't  been that helpful, and all I want is to to get at my harddrive that had my original OS on it and get some files off and backed up at least.

Backing up, I've only used a single OS of Hardy Heron. I don't understand why I'm being affected by this error when all I have is two harddrives that are used as unbroken partitions. Best advice I've used is to use a live disk, however the one I've currently got is for Lucid Lynx. I'm not sure whether I need to go and get the old version of a live disc since all I want are my files, I'm content to update to the newer version (though part of me wants to wait for the next one since it's only a few weeks away.) If I could get my system running as it was that'd be great too.

I believe the harddrives are fine since both are recognized in bios, just when running the live disk it asks if it wanted to install it or try it first. When running in the trial of Lucid, I can see the second harddrive and access files as I could on Hardy, but I can't see the main one. 

I really don't know what to do and am considering just starting over and cursing the loss of the data I want to preserve.

---

### Post by quixote on 2010-08-28
Possibly all that's wrong is your Master Boot Record (MBR)  or partition table was somehow corrupted.  Those can be recovered, so don't give up just yet.  You can use a Lucid LiveCD on a Hardy install, except that Lucid uses a different version of grub so you wouldn't want to use grub-specific commands.  If you can get and burn a LiveCD iso of Hardy, that might be even safer.

I'll call your main partition, the one invisible to the Lucid LiveCd, sda1, and the second one sda2.  If your designations are different, substitute the right ones.

Boot with a LiveCD (Lucid is okay for this). Run ```
sudo mke2fs -n /dev/sda1
```That should return a list of superblocks, which are addresses containing backups of the partition table.  Use one of the higher ones, like 229376. (It could be any number.)

Run ```
sudo e2fsck -b 229376 -p /dev/sda1 
```The -p stands for "preen", fix any errors without asking whether to do it, -b specifies the superblock.  If we're lucky, that will fix it.  If it still gives you grief, we'll try the MBR next.

---

### Post by dcsii on 2010-08-28
Ok prior to this I had added a fresh harddrive and installed Lucid Lynx on it. Now, I could "see" the 747 GB and 160 GB harddrives in the places menu. However, when trying to access it output the following error:

[quote="error"]
Unable to mount 747 GB
Error mounting mount: wrong fs type, bad option, bad superblock on /dev/sb1
 
missing codepage or helper program or other error in some cases useful info is found in syslog dmesg | tail or so
[/quote]

I then input the code as follows:
```
sudo mke2fs -n /dev/sdb1
```
It output the following list:
32768
98304
163840
229376
294912
819200
884736
1605632
2654208
4096000
7962624
11239424
20480000
23887872
71663616
78675968
102400000

I then put in the code for each of the number codes as instructed with this code:
```
sudo e2fsck -b 32768 -p /dev/sdb1 
```
Then each number code output the following:

> 
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open sdb1
could this be a zero length partition?


I'm also going to note that the 747 GB harddrive is no longer listed in the places menu. Not really sure what's going on, I'm kinda lost and over my head.

---

### Post by quixote on 2010-08-28
Disk failures are always hugely intimidating.  But they're often recoverable. Don't worry too much about what the nautilus file manager does or doesn't see.  It's flaky as hell when it comes to drives with errors on them.  

The superblock number code to use in the e2fsck command is one of the *higher* ones.  E.g. 294912.  Anything but the first one, which is the one normally used and which is corrupted.  Let's just hope those haven't all been over-written with the wrong partition table.  Try it again with one of the higher numbers.  

If it still does nothing for you, then we can try testdisk to recover a partition table.  If that doesn't work, then it's down to using photorec to get your data off the drive (instructions [here]("http://www.psychocats.net/ubuntucat/recoverdeletedfiles/")), and then reformatting.  We can go through all that in more detail if it becomes necessary.

---

### Post by dcsii on 2010-08-29
Disk errors are also hugely frustrating, but I digress, I had already tried each of the codes including the higher ones, and just about all of them had the same output that I named earlier. 

I understand and know how to use photorec but hadn't had luck with it in the past, but will try that when we come to it. The partition table I don't know anything about or really what one is. Or why I had one since I thought it was pretty simple with just two harddrives that I used each as one complete partition. The only other thing that I guess counts are two flash drives, a large external harddrive, and a camera with an SD card memory that connected via USB.

---

### Post by quixote on 2010-08-29
"Hugely frustrating."  Yeah.  That too.

The partition table is a list at the beginning of each partition that tells the operating system where the filesystem is on the physical sectors on the drive.  Without it, the OS doesn't know where to find anything.  The data are still there until overwritten -- which can happen whenever the system is used since it thinks that's all free space -- which is why something like photorec can recover it.

I think the remaining option, besides diving in with photorec to recover individual files, is to try to use testdisk to recover the partition table.  

Since your first priority is the files, I'd go get those first with photorec.  As I say, every time you access the drive, there's a potential to make the problem worse.  If you can get the first priority files, and then want to try test disk, the steps for that are:

Enable universe repository, reload, and install testdisk.  (You probably already have it since you're familiar with photorec.)  Then follow the steps outlined [here]("http://www.howtoforge.com/data_recovery_with_testdisk"), using the same defaults and the same options.  (Don't get creative.  The wrong options can make the disk unusable.)  Start in Step 2, at the part a little way down that says "Now let's assume we have lost our partition table".  Be nice if that solved it! :?

---

### Post by dcsii on 2010-09-01
Sooooo.....

After tweaking around Testdisk to analyze the drive it hits read errors all around and all the way through. First at the overview of the partition, then when doing an analysis of the 91200 cylinders.

The MBR code won't write to the first sector, doubt any of the changes I see that I can do will help. All just sucks and is frustrating, I think my data is gone, and getting to replace what I don't have readily backed up is going to take some time.

Starting photorec with little hope of anything coming from it, but figure what the hell

---

### Post by quixote on 2010-09-01
Sounds like you hit a major disk failure.  But wasn't that a new hard drive?  That's horrible.  I hope photorec helps some. :(

---

### Post by dcsii on 2010-09-01
No I've had it for at least two years and what I've lost is my own fault for not backing up. Photorec as far as I can tell can't get at anything (though I'll still try to use other things that I can) and I don't think there's anything I can do, short of spending a few hundred which it isn't worth spending over the extra hassle that it is to get what I can get back. 

Unless of course there's something I'm missing and can do.

For future reference, can I reformat the bad drive to re-use it or is it a paperweight at this point?

---

### Post by quixote on 2010-09-04
Well, in the interests of science, once you're sure there's nothing more you can recover off it, you could see whether you could reformat.  If so, then use if for things that are completely temporary, like sandboxing new operating systems or software or something.  (And then, knowing the way the universe works, it'll run flawlessly for years. :-x)

I'm kind of shocked that even photorec can't get much.  As something that does direct disk reads, it should be able to just read sectors, even if all they have in them is zeroes.  I wonder if maybe your disk is okay but the read mechanism failed.  Not that it helps you, since replacing that isn't a do-it-yourself project.  What an all-around bummer.

---

