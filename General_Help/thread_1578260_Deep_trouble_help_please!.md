---
title: "Deep trouble help please!"
date: 2010-09-20
forum: General Help
---

### Post by Opperkip on 2010-09-20
People I have a really big problem. I hop you can help me. I'll explain.

Yesterday i wanted to install ubunty on my Laptop which had all its disk space formatted for windows 7 64bit.
Because i wanted a dual boot configuration i decided to decrease the windows 7 partition and leave the empty space to install ubuntu on.
So I booted the linux live disk and installed ubuntu on my laptop no problems there.
After rebooting however there was a great problem waiting for me.
When i selected my windows 7 to boot it started loading and then gave me a bluescreen.
I put in my windows 7 disk and used startup repair. (This is where the problem comes)
Windows did not see any windows 7 installations on the hard disk. I used startup repair anyways but it said it could not fix the problem. After many hours of googling i decided that i could just reinstall windows. But when i want to do that the windows intallation cant find any hard disk to install on.

Is there anyone out there that does have a solution for me? The best way for me would be to keep the windows that is still on my laptop but which cannot be started.

---

### Post by robsoles on 2010-09-20
Windows 7 (I don't have a copy, I am just going by other posts in this forum and a little personal experience helping local 'sweeties' with it) seems to do some weird stuff with it's file-space and I fear your only resolution may be to use a LiveCD to copy files you simply must keep to a USB stick so as to format your HDD completely.

If you insist on dual booting then, in my opinion at least, you will be best off to partition the drive in the first place to sizes you want for each OS and then install each OS - Windows first, then Ubuntu if you really want to be able to boot both.

Here's a couple of questions that may highlight why it is not so easily recoverable:

Did you use a Windows 7 native partition-resizer to resize the Windows 7 partition in the first place? (Even if the partition-resizer was by MS themselves it wouldn't be the first time they dropped someone's 'ball')

Did you try booting off the Windows 7 partition after it was resized before installing Ubuntu? (If we know it booted and functioned fine then someone among us may be inspired to try harder to help you recover it.)

---

### Post by Opperkip on 2010-09-20
Thank you for the reply. To answer you questions.
1. Yes i used microsofts build in partition resiser. 
2. Yes i rebooted my windows 7 partition succesfully after resising it. 
If anyone else has any other visions or questions go ahead.

---

### Post by Quackers on 2010-09-20
Using the W7 system disc go into repair options. It may not matter that it doesn't find any Windows OS, you still may be able to repair the boot process.
Go into the command prompt from the repair disc and 
type diskpart and hit enter
type select disk 0 and hit enter
type select partition 1 and hit enter (if W7 is on the first partition)
type active and hit enter
type exit and hit enter
type bootrec /rebuildbcd and hit enter  ***NOTE the space between bootrec and /rebuildbcd

It should then say something to the effect that it ran ok.
Reboot the system and hopefully W7 will then boot.
If it boots into the recovery environment (but it probably won't) then you probably have a recovery partition as partition 1. If so, redo the above instructions cahnging partition 1 to partition 2.
Good luck.

---

### Post by Opperkip on 2010-09-20
I would like to thank you for the solution but however it did not work.
Every time i let bootrec /rebuildbcd run It says it found  0 installed windows installations and then quits. This happen voor every partition i choose.
Any other hints?

---

### Post by Aurawin on 2010-09-20
I would boot into Ubuntu, grab all our personal data on USB stick, then re-build entire computer in the following order.

1.) LiveCD boot.
2.) Partition with 50% windows 49% ext4 and the rest for swap
3.) Live Install (Manually partition accepting what you did in #2
4.) After Ubuntu is up and running restart with Widows Disk.  Windows install or even factory reset disk should honor the changed partitions.  Keep in mind your laptop may have a hidden partition with the Windows information inside (DO NOT ERASE).  The restore software will need that data (unless you know otherwise).

There's no recovery of the old Windows data.  IMO Windows / NTFS is too primitive to regain stability from that point.  It's just easier to re-install or forget Windows all together and make the entire drive ext4 :-)

---

### Post by gradysghost on 2010-09-20
It's pretty awesome that an Ubuntu help forum will help solve problems with Windows.  Still, I'm not sure there's anything that can be done.

When you get the BSOD, can you get the stop code (something like 0x0000007B or similar)?  I've seen cases where the BSOD flashes away too quickly to get anything useful out of it, but try if you can.  This may help shed light on why it's blue screening.

Another thing is that you mentioned it actually starts to boot, but blue screens shortly afterward.  This suggests that the Windows boot process is actually capable of seeing the Windows partition and the data on it.  Perhaps this is a case of missing/corrupted system files or bad drivers or something.

Have you tried booting to Windows in safe mode?  Right after you select the Widows option from GRUB, start tapping the F8 key.  Choose Safe Mode from the list of Windows boot options and see if it will boot.  During the Safe Mode boot, I think Windows will start listing out filenames on the screen.  If things crash, maybe note what the last file loaded was.  Don't know if that will help, but it might.

Good luck.

---

### Post by Opperkip on 2010-09-20
I figured it would be best to post here since ubuntu is the only thing my laptop is currently running :)

I filmed the booting of my PC in safe mode and found out when it gave the Blue screen and what the blue screen says. (I filmed it because the blue screen flashes so fast i can't read it)

It give me the blue screen when the file \windows\system32\DRIVERS\CLASSPNP.sys is supposed to load.
The error the blue screen gives is STOP: 0x0000007B

i hope this will help someone solving the problem.

---

### Post by Quackers on 2010-09-20
Opperkip what laptop are you using? It is likely to have a hidden recovery partition, do you know how to access it? Did you make a system recovery disc?

A 7b stop error can be caused by many things - but faulty ram is one of them.

---

### Post by gradysghost on 2010-09-20
That's a really common stop code, and one that can be attributed to probably dozens of problems.  One of those problems that I'm seeing in forums for Win7 seems to be related to the MBR.  (classpnp.sys failures seem to be related to write caching on the HDD, so that's somewhat related.)  Of course, at this point, Windows has nothing in the MBR.  GRUB is there instead.

Ideally, GRUB should remain your bootloader, but you may need to repair the Windows bootloader first, then repair GRUB afterward.

Please note that I can't guarantee this solution will work, and it may end up screwing your system more completely than it currently is.  I strongly suggest backing up any files you are afraid of losing before trying anything further, as has been suggested earlier in this thread.

I don't know how to fix the MBR for Windows in Win7.  In XP, it used to be a matter of booting to the installation disk, going to the recovery console, and running `fixmbr` there.  It may be similar in Win7, though I haven't had a chance to do this myself.

After doing this, you can test to see if Windows boots again.  If it still doesn't, then I'd recommend just scrapping it all and reinstalling Windows **and** Ubuntu, being sure to properly size the Windows partition during its install process.  Otherwise, if Windows does boot, you can try repairing and reinstalling GRUB.

Again, I'm not entirely sure how to do this in GRUB 2, since I haven't had to do it since GRUB 1.something (and I never had much luck with it there, anyway).  Someone else will have to help with that.

But once more, please do not take my word for this.  I'm not an expert on the underpinnings of Windows 7, and clearly I'm not an expert on Linux bootloaders.  Try these things at your own risk, and **always keep a backup of your data**!

---

### Post by Opperkip on 2010-09-20
I have a HP dv7 4040ed Laptop.
I do have a Windows recovery disk but i don't have anything from HP.
I know there is a recovery partition but i can't acces it.

That blue screen appeared since i installed Ubuntu so i'm guessing its not hardware problems.
I found out that it might be a BIOS problem (Which i strongly doubt) so im gonna try updating that.
In the mean time anything that might be of help is appreciated.

---

### Post by Quackers on 2010-09-20
If you have a manual there will be instructions to access the recovery partition (it will be something like pressing the del key or F11 during boot). If you don't have one you could downlkoad one from HP I'm sure. The problem with using the recovery partition is that it may insist on using the original disc format (using the whole disc for re-installation). If you had made a recovery disc you would get more options.
Where did you get the W7 disc from? Or shouldn't I ask?

---

### Post by Quackers on 2010-09-20
From what I've been reading it seems that to access the recovery partition on a HP laptop you need to tap the F11 key during boot.

---

### Post by Opperkip on 2010-09-20
I did not make a recovery disk because I installed ubuntu a ton of times before and nothing ever went wrong.
I got the windows 7 disk from a "friend" just for this problem.
Im gonna try finding the manual.

---

### Post by Quackers on 2010-09-20
Try tapping F11 during boot. If you get the system back I would really recommend you make the recovery disc. It's worth it's weight in gold.

---

### Post by Opperkip on 2010-09-20
Sadly for me. pressing F11 during boot doesnt do anything :S

---

### Post by Quackers on 2010-09-20
As a last resort you could try contacting HP and telling them that your recovery partition doesn't work and ask them for a disc (but they may want to charge you for that).
I would still have a look at their website and confirm that F11 is the correct button to press. There are others that are commonly used. If it turns out that F11 is the correct key and tapping it during boot does nothing, then I would guess that the recovery partition is now gone.

---

### Post by Opperkip on 2010-09-20
Since no other thing helped i tried to use the fixmbr command. sadly this made my Laptop even more of a brick. The linux bootGrub is also gone now and im really stuck again :S

---

### Post by Quackers on 2010-09-20
That shouldn't affect anything but the Windows mbr, unless you have made a mistake with the partition number. That could also have happened causing your first problem - and your lack of a recovery partition now. If you have a GPartED live cd fire it up and have a look at the current partitions listed. Maybe post a screenshot here, if you can make one.

---

### Post by Opperkip on 2010-09-20
Here is the screenshot i made with my linux booted from CD

---

### Post by Quackers on 2010-09-20
Having a look at the above I would say that your recovery partition is gone (even though there is a partition there, it is less than 1MB).
I would suggest redoing the instructions I posted earlier using partition 3 as the active partition. See if you can get back into Windows with that.

---

### Post by Opperkip on 2010-09-20
Because my linux didnt work now anyways i decided to delete that partition already. Now when i get back to my windows install disk it suddenly recognizes my Windows system on my Harddisk. 
However startup repair still cant fix it and your steps also did not help.
First they finished instantly telling me my volume is corrupt.
Now they finish instantly telling me to wait a while, but nothing happens after that :S

Any other ideas now that my OS is suddenly visible?

---

### Post by Quackers on 2010-09-20
It now fails instantly on entering bootrec /rebuildbcd?
I don't know why it should suddenly start to recognise the installation after not doing so before.

---

### Post by Opperkip on 2010-09-20
When startup repair stops working now i can get this from the log:

Root cause found:
No OS files found on disk

Repair action: Partition table repair
Result: Failed. Error code=0x2715

The bootrec thing goes like.

X:\Sources\bootrec /rebuildbcd
Scanning all disks for windows installations

Please wait, since this may take a while....

X:\Sources

And then i can just type again and use commands. I am thinking that when i can type in that console its not doing anything or am i just being stupid here?

---

### Post by Quackers on 2010-09-20
I don't understand, what's the X:\Sources from?

---

### Post by Opperkip on 2010-09-20
Thats the console i have from my windows recovery disk. it starts with X:\sources
Also might me worth noticing that my windows 7 install doesnt detect the new free unallocated space on my harddisk or anything else. it still says my harddisk does not exist

---

### Post by Quackers on 2010-09-20
Ah, don't remember that. 
When you tried those instructions earlier, did you try partition 2?

---

### Post by Opperkip on 2010-09-20
Yes i tried all partitions Diskpart would accept but nothing happened.

---

### Post by Quackers on 2010-09-20
I think we're in trouble :-(
It may be that the Windows files or boot sector have become corrupt.
The only suggestion I can come up with is to re-install Ubuntu choosing to format all drives except the Windows one and, whilst doing so choose to install Grub2 to the mbr of the disc (not the Ubuntu partition). I hope I'm not mis-informing you (although, I don't think things can get much worse).  If you want to wait for somebody else's views/suggestions I wouldn't blame you (I would :-) )
Maybe you could still try to get a recovery disc out of HP in the meantime!
Good luck.

---

### Post by wilee-nilee on 2010-09-20
OP boot W7 pump the f8 key go to the command line in the safe mode and run ckdsk /f/r. This will have W7 start a chkdsk at startup.

If you can't get to the safe mode this way down load this recovery cd and burn it and boot it and run the commands here is a link on getting to that command line as well.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

If you just want to restore the MS bootloader the command you would run from that booted cd is.
```
BootRec.exe /fixmbr 
```

If you removed sda1 that probably was the firmware for you computer from the manufacturer, hope the chkdsk works.

OP never ever let the ubuntu installer resize your MS partitions as part of the install. W7 has a virtual disk manager that will resize in a virtual environment. You could of used gparted with the round to cylinders off and you would of been okay.

Reloading the MBR is easy so don't worry about this part.

You also can run the bootscript in my signature, and post it in code tags as described. This will give us a better picture of the whole HD and the MBR.

For all in this thread the autorepair for W7 generally does not work when you have put grub in the mbr you have to go to the cli.

---

### Post by Opperkip on 2010-09-20
I would like to thank everyone for their help in getting my laptop back in working order.
I finally miraculously succeeded in making my laptop work again with all my windows files still there.
I downloaded a partition recovery disk and i miraculously made my PC boot back up.
Now im working on restoring the boot files.
One thing is sure next time ill try ubuntu ill backup first :P

Thx again people

---

### Post by Quackers on 2010-09-21
Ah, good news, well done!

---

