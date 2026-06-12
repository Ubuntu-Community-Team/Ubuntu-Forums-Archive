---
title: "hard reboots filesystem corrupted Can't boot from anything"
date: 2009-12-01
forum: General Help
---

### Post by modred11 on 2009-12-01
I've tried booting from three LiveCDs (two CDs one DVD), and I've confirmed that at least one of the CDs works on another computer (I didn't check the others).

I've done a ton of hard reboots on Ubuntu (Wubi) on my Laptop. The system got to the point where it froze predictably a few minutes after booting up (long enough for me to backup stuff thankfully). Then I had to do a hard shutdown.

I read that the hard shutdowns corrupt the filesystem.

I tried using the HP/Compaq system restore service four times, windows still can't boot (it goes immediately to installing some HP software so I can't access the windows command line; it freezes during the install).

the LiveCDs come up with a command line and say something about something (a file) being corrupted and startx doesn't work (either says it won't or tries it and freezes; meaning another hard shutdown).

I've been trying to repartition/reformat the hardrive but I can't get to anything that'll do that, I do have access to the command line from the liveCD so IDK if I can use that to do something.

I checked the hash on the .iso file and it matched the wiki page. I couldn't figure out how to check the hash on the CD. I used a different program to burn the last CD, and it has (approximately) the same problem as the other two.

[my laptop's a HP/Compaq Presario CQ50; 2 GHz dual-core 32-bit processor, 2 GB RAM, ~300 GB harddrive (I don't remember the GB exactly)] The wubi that was installed was the old Ubuntu (not 9.10). The LiveCDs were all 9.1.

I'd like to reimage the hard drive, or reformat or whatever. I can't use it right now, I'd be happy if I could get it to a state where I can boot an operating system (it doesn't matter which). What I was going to do was just use the liveCD to reformat and install Ubuntu, but I can't use the LiveCD to do anything as it's in the command line and won't boot X, if someone knows a command line tool for partitioning or reformatting that should do it (I hope).

---

### Post by efflandt on 2009-12-01
You can **md5sum whatever.iso** to check if a download matches the advertised md5sum.

Typically there is md5sum.txt file in the root of the CD.  So cd to the CD and run **md5sum -c md5sum.txt** to see if it burned properly.  And if any files fail, loop mount the iso file and see what answer you get from the same command from the loop mounted iso.  Some people suggest burning an iso at a slower speed, but I have not had any trouble using default 16x of my desktop or 12x of my laptop (but I do not do anything else on the PC at the time).

Sometimes drives just fail.  I tried using an old 60 GB drive from work and I could only put about a 32 GB ext3 partition on it plus swap.  If gparted-live CD tried to make a 40 GB partition, or a partition on the tail end of the drive it would either fail create the partition, or fail to recognize it after it created and formatted it.  So that drive is trash.

My boss' grandsons ended up trashing the hard drive of an old laptop.  WinXP refused to boot in any mode (safe or recovery) it said to avoid further damage.  And with a live CD I could not even copy their WinXP user dir (cp -r * copied some, but failed on My Documents).  Gparted recognized how corrupted it was and would not touch it until Windows fixed it.  In a USB enclosure, Windows USB cannot even mount it to chkdisk it (just makes clickity click sounds repeatedly trying to read).

---

### Post by modred11 on 2009-12-01
I don't really think it's a hardware problem or that the CDs were burned wrong. But I'll try to check them I guess.

I ran some of the compaq/hp tests that they have for the hardware (other then system recovery it was the only thing I could actually do) and they were all fine before (for both memory and hard drive). I'm running the memory test from the Ubuntu CD now.

I've tried booting into the command line with the CD again (both by selecting Install and Use without effect) and both of them took me to a blank black screen (one of them let me use the mouse pointer to -well- do nothing actually). So I'm not actually sure that I can get back to the Linux command line again.

I read that Parted is the command line equivalent of GParted, so I was going to try to use that.

The hard drive is one or two years old now. I sure hope it's not failing.

---

### Post by audiomick on 2009-12-01
You could try a Gparted live CD
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Pesky_Programmer on 2009-12-01
It is possible that Windows may still be on your computer, assuming that it has not been corrupted or reformatted. My copy of windows came with a cd containing the Windows recovery console.

(I am doing this from my memory if I accidentally leave something out let me know)  
If you have this disk try booting from it. It will take a few moments to load and when it does you will have an option to press R to enter the recovery console. 

When you do so it should display all if any partitions that contain the Windows format. Now assuming windows is still intact you should be able to select your C: Drive, there should be a prompt asking you witch drive to log onto. Then it should ask you for your administrative password, this is not the password you use to log on, as most people don't have one just leave it blank and press enter.

 Once you get into your C: drive type the command "FixMBR" without the quotes. This will fix your master boot record for windows deleting/bypassing Grub. Your computer should then load into Windows XP no problem allowing you to retry the install for ubuntu.

I hope this helped and if I was unclear at some point let me know and I will try to explain better.

---

### Post by modred11 on 2009-12-01
> **Pesky_Programmer said:**
> It is possible that Windows may still be on your computer, assuming that it has not been corrupted or reformatted. My copy of windows came with a cd containing the Windows recovery console...
If you have this disk try booting from it.

I'm afraid I don't have that disc. (even if I did I imagine it'd fail to boot up same as all four of my liveCDs do (yeah I made another one at x8 write speed and it actually works worse then the others)

I had gotten back into the linux command line for a bit and ran sudo parted and using the Help command was able to repartition/format and make a linux partition (ext2). After that everything became much more stable (I was able to boot onto the liveCDs). For a few hours.

I ran the linux install thing from each of the three original liveCDs and they all said the CD was corrupted or some program (different each time) wouldn't work. And while I was in the command line it kept interrupting whatever was going on by outputting like six lines of things saying like "zlib_error" something "corrupt" something, etc...

Anyway, I can't boot into the liveCDs anymore, and now I went back to the command line and whenever I try to use sudo it says
"zlib_error" [stuff] "corrupted" [other stuff]

I really don't know how to get this to a workeable state, it seems to me like the LiveCDs are using the hardrive for something and because it's corrupted whatever they put their gets corrupted. Either that or my hands are like instant corruption to all CD data.

It's particularly odd that the sudo command became corrupted over time, I mean, I wouldn't think the CD would change.

The only things I can think to even try right now are like booting from a USB stick (no idea if that'd make any difference) and somehow reimaging the hardrive (maybe by hooking it up to another computer and having that computer just access it, not depend on it; like a 'write-only' state).

It will be really annoying if I have to throw my laptop away cause've this, I mean, this was all (apparently) caused by my laptop freezing and me having to do a hard shutdown.

@audiomick thanks, I didn't know that was possible. I'll try that.

---

### Post by Mark Phelps on 2009-12-02
You didn't mention what OS you were running or what you were doing when the laptop siezed up.

If you were running Ubuntu 9.10, I'd suspect overheating -- since there have been a bunch of posts from folks about that very problem after installing (or upgrading to) 9.10.

Laptops generally have a temperature probe setup to either throttle down the CPU or to shut down the machine -- to prevent serious damage from overheating.

What OS did it come with?  I suspect Vista (since it's only two years old).

If it did come with Vista, did it run OK (other than s..l..o..w)?

It's most probably out of warranty, and google results show it available today for around $500, so it may not be worth a lot of money for you to have it repaired.  But, you could check with HP to see what they would charge to restore it for you.  And, if you're going to do that, if you want a multi-OS machine, you could also check to see what they would charge to install Windows 7 on it.

---

### Post by mr clark25 on 2009-12-02
you might run memtest if you can get it to boot from the live cd again. I'm not that good at this, but it might be a ram problem?

---

### Post by modred11 on 2009-12-02
> **Mark Phelps said:**
> You didn't mention what OS you were running or what you were doing when the laptop siezed up.

If you were running Ubuntu 9.10, I'd suspect overheating -- since there have been a bunch of posts from folks about that very problem after installing (or upgrading to) 9.10.

Laptops generally have a temperature probe setup to either throttle down the CPU or to shut down the machine -- to prevent serious damage from overheating.

What OS did it come with?  I suspect Vista (since it's only two years old).

If it did come with Vista, did it run OK (other than s..l..o..w)?

It's most probably out of warranty, and google results show it available today for around $500, so it may not be worth a lot of money for you to have it repaired.  But, you could check with HP to see what they would charge to restore it for you.  And, if you're going to do that, if you want a multi-OS machine, you could also check to see what they would charge to install Windows 7 on it.

It's not overheating, it freezes, it doesn't shutdown itself (it ran for a frozen hour trying to install the HP stuff after botting windows after running the system recovery). I believe overheating always causes instant shutdowns.

Sorry, I don't know what the Ubuntu OS was, but realize neither it nor Vista is actually on the machine anymore (at least not usuably, and Gparted said there were no operating systems on it). It's not 9.1 (I couldn't get that to download over the wireless) but it's only a few months old... I think it's the one that was right before 9.1, I think I installed it like a week before 9.1 came out. I had Ubuntu installed through Wubi.

And yeah it was running fine before this started. I'm pretty sure it's out of warranty. I should check with HP, I'll try that. I'm going to go see some computer friends today and see if they can't suggest a way to reimage it or something without having to boot it.

@mr clark25 I ran the memory test from the liveCD before, and I think it said 70% passed, I have no idea how good that is. It didn't display the information after it went through the tests, it just started running through them again so I told it to stop. I'm pretty sure it was 70% when it reached the end of them the first time.

I'll try calling HP tonight and see what they say.

---

### Post by modred11 on 2009-12-09
I've taken the laptop to the Best Buy Geek Squad and they identified that the RAM was failling and that was the problem.

I'm going to replace the RAM and see if that fixes it.

---

