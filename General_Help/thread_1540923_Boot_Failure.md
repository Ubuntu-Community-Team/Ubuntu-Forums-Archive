---
title: "Boot Failure"
date: 2010-07-28
forum: General Help
---

### Post by Mangey on 2010-07-28
I'm having a bit of a problem with my system, and I was hoping someone here would be able to help.  I'm really stumped, so I might provide a bunch of unnecessary details.

I have an Alienware laptop, with a Pentium M, 1.73 gHz processor, 1 gb of RAM, 80 gb HD, Intel 915 integrated graphics.   I dual-boot Windows XP and Lucid.

It was just a week ago that I installed Lucid.  I messed up the bootloader, so I formatted the drive, reinstalled Windows and then Lucid.  It ran fine for awhile, actually, better than fine.  It was running great.  Yesterday, the system froze up on me a few times.  Without warning, the system would just stop, I couldn't move the cursor, the keyboard was nonresponsive, etc.  Not only was there no warning from the system that there was a problem, but it didn't even begin working hard or anything.  When I would reboot, it would run fine for awhile, then do this again.

One time when I rebooted, it got stuck, and would not load at all.  I tried to shut it down maually, but the power button was inoperative.  I had to physically remove the battery to get the machine to turn off.  I returned home, and used the machine lastnight without incident, it was probably on for a solid 5 hours without a problem.

This morning it was running fine for about 2.5 hours or so, when the internet stopped working.  I tried disconnecting from my wireless and reconnecting, but it repeatedly failed (it would ask for my login, and then try to connect for awhile before repeating).  I was able to connect on another device, so I rebooted the laptop.  It was this point that my recent troubles began. 

Now it will not boot into Ubuntu at all.  If I choose the first option from the boot loader (running kernel 2.6.32-24-generic, it gives me a screen with a blinking cursor in the upper left, which is otherwise blank. It sounds like the hard drive is spinning, but nothing seems to happen (I left it for about 6-7 minutes).  The same thing happens if I boot into the previous version of the kernel.  

I booted into recovery mode, and that loads just fine.  I do get a series of errors about "fw-host0" stating that it has an error receiving SelfID packets.  At which point it informs me that it is an unrecoverable error, and continues booting.  From failsafe mode, I have successfully booted into a command prompt (which is what comes up if I "resume normal boot") and into the reduced graphics mode.  

While in reduced graphics mode, I ran the self-test application, but that did not find any problems.  I then used the disk utility to check the hard drive, and it informed me that while some resource packet allocation (I hope I got that right, I can't recheck it and forgot to write it down) errors were found, it was only a warning.  Otherwise it gave my drive a "green light."

That mode did not have any wireless access, so I attempted to reboot again and go into failsafe mode with networking.  This time, however, failsafe mode failed to load.  It gave me the sequence of fw-host0 errors, and then the following error:

```
[20.152752] yenta_cardbus 0000:01:03.0 No cardbus resource!
```

After displaying this error, it is merely giving me the same blinking cursor as when I try to boot up normally.  This suggests to me that the error is the same, though I'm not sure why failsafe mode loaded 4-5 times before this without a problem.  I tried booting into Windows, and it was able to do so without incident.

I also tried booting using my LiveCD, but I have the same problem, it boots to that blinking cursor.  Perhaps indicative of a hardware problem?

I am open to any suggestions about what the problem might be, or even how to fix it.  I am in a bit over my head here, and would appreciate any help anyone can provide.  Thanks in advance!

---

### Post by oldfred on 2010-07-28
Change to your partition from sda4 shown:

Must be unmounted:
Try "e2fsck -f /dev/sda5". 
Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sda5
if errors:
sudo e2fsck -f -y -v /dev/sda5

or if not root partition you may be able to unmount it with umount:
1) Run a file system check on sda5:
sudo umount /dev/sda5 2>/dev/null
sudo e2fsck -fycv /dev/sda5

---

### Post by Mangey on 2010-07-28
Thank you for the reply oldfred!

I left my computer alone for a couple of hours, and came back to have another crack at it.  I tried to boot into the LiveCD, but it was a failure again.  I tried recovery mode, and was successful.  I then tried a normal boot, and it worked.

Inspired by this, I booted back into the LiveCD, and was successful.  I ran the commands you recommended oldfred, and it reported no errors (other than the date of the last mount being slightly in the future, which I told it to repair).  I am now back in a regular boot, and it seems to be running smoothly.

So this is encouraging, whatever the problem is, it is not a total loss.  Still, I'm just as mystified.  This morning when I posted, I literally could not even load into the LiveCD, booting into my Windows Partition was the only thing that worked.  Now I am back to running fine.  I am, of course, greatly concerned that I will be running into these same problems again in the near future.

---

