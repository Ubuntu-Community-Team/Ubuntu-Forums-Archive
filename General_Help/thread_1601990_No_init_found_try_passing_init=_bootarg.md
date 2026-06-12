---
title: "No init found try passing init= bootarg"
date: 2010-10-20
forum: General Help
---

### Post by Presence on 2010-10-20
Was attempting to install a dedicated graphics card in an older machine (was using onboard video). When I installed the graphics card, I received an error and had to do a hard reboot. Plugged the onboard video back in and booted it up. The grub screen appeared right after post (normally just boots straight to 10.10). When I booted 10.10, got the error:

> Target filesystem doesn't have requested /sbin/init.
no init found try passing init= bootargI rebooted into a live CD and tried to fsck the partition to see if there were any errors.

The fsck gave this error:
> fsck.ext4: Device or resource busy while trying to open /dev/sda2
Filesystem mounted or opened exclusively by another program?The partition isn't mounted or open in any program.

When I tried to mount the drive through nautilus, I got this error:
> DBus error org.gtk.Private.RemoteVolumeMonitor.Failed operation is already pendingTried to use GParted to see if I could create a new partition on the drive to reinstall and then migrate the files over but it gave the same error when it did it's fsck.

Last thing I tried was to install the hard drive into an enclosure I had laying around. I got the exact same errors. I tried to view the files in windows also, windows failed to give it a drive letter.

Is there any way to rescue this drive? It's a 250GB hard drive I just installed a few days ago, so I hope I didn't lose it. Had no luck so far searching for solutions.

---

### Post by Jebtrix on 2010-10-20
Sounds like the hard drive controller is borked. Only thing to try would be to borrow the hard driver controller board off another same model drive :( If you got it recently and the return policy is favorable, just get another, trade hard drive controller boards, then return it. Or you can be nice and return working drive and RMA the dud after saving your data somewhere else.

---

### Post by Presence on 2010-10-20
No luck there. This was a drive I had lying around. It worked fine until I had to hard reboot the computer.

Doesn't seem like it would be the hard drive controller board anyways. I can still get into GRUB which means it can access the MBR, so it can't be completely dead.

---

### Post by Whik on 2010-10-20
is it like this issue?

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1561735&page=2](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1561735&page=2)

im seeing that alot right now and i myself have gotten the issue. if i could just back up my files id be happy right now...

---

### Post by Presence on 2010-10-20
Yes, same error, though it seems like I should be able to mount the drive from a live CD or view the files in Windows if it's just the boot that's messed up. 

I'll try some of those solutions and see if I can fix it. Thanks for the link.

---

### Post by Whik on 2010-10-20
that same issue has been posted like 6 times right now. the first solution didnt work for me. fyi. so idk if itll work for you. seems to be a big issue right now so hopefully it will be fixed soon

---

### Post by Presence on 2010-10-21
Tried the solutions there with no luck (doubted they would work). 

All of them hung when trying to mount the partition that my 10.10 install is on.

Seems like you have the exact same problem here:
[http://ubuntuforums.org/showthread.php?t=1602013](http://ubuntuforums.org/showthread.php?t=1602013)

Tried running bootinfo script ([http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)) and the script hung while "Searching sda2 for information..." Again, can't seem to access the partition in any way.

Could probably format the hard drive to use it again, however I'd like to get the data off first.

---

### Post by Presence on 2010-10-21
Still haven't found a solution. Ideas anyone?

---

### Post by tk189 on 2010-11-08
I have loads of problems with this same or very similar issue.

Previously using 10.04 and now on 10.10

Boot erros basically resulting in having to run from Live CD then purge and re-install grub using this walkthrough: 

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

It got to the point with 10.04 that I was having to do this several times a day!!!! ridiculous. The thing that seemed to crash my pc was firefox but sometimes just opening an app or the file manager would cause first, the mosue to freeze then the windows to one at a time grey out. Finally nothing would respond including the shut down or reboot forcing a hard reset.

Then, each time the damn thing would not boot. I'd instead get an error about no init found and something about bootarg.

Crap!

Fresh re-install on a new hard drive with 10.10 and everything has run fine for 3 maybe 4 weeks now until today! Suddenly without warning my pc went down, on re-boot... this same grub error.

I am at the minute running from Live CD and just trying to go through the whole damn purge and re-install of Grub.

I have ubuntu 10.04 running on an old machine elsewhere in my home with no problems. The common thing I am starting to see with people suffering the same issues is that my prone to problems PC is pretty new and has a quad core processor.

Could it be that dual or quad core processors have an issue with Grub? I have no idea.

It's a big problem affecting a lot of people but no-one seems to have this fixed yet.

:(

---

### Post by wane.dacha on 2011-01-09
I'm having a similar problem and can't find a fix.

However, if you run a liveUSB/CD you can download testdisk ([link here]("http://www.cgsecurity.org/wiki/TestDisk")), you can plug in an external hard drive and recover your files.

---

