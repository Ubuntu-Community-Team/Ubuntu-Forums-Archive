---
title: "External HD Automatically Unmounting"
date: 2009-10-25
forum: General Help
---

### Post by initiallyM on 2009-10-25
Ever since I upgraded from 9.04 to 9.10 the other day, I've experienced the problem of my external hard drive automatically unmounting.

So here is how the problem seems to be occurring. I attach my external hard drive and it mounts. I can manage files on it and do all the regular things with it. Some time later, right after the hard drive spins down, it immediately and automatically unmounts. Unplugging and replugging the usb cable does mount it again. A short time later however, the external hd spins down and unmounts once again.

Before the upgrade, with 9.04, the external hd would never automatically unmount. It would spin down after some time but it would stay mounted and the icon would stay on my desktop.

Any ideas?

---

### Post by barthel on 2009-10-25
I'm not on 9.10 yet, but as this might be a new safety "feature".

Did you check the "Places" menu? That should allow you to remount without fiddling with the cables, although it will open a new Nautilus window.

---

### Post by initiallyM on 2009-10-26
I checked the Places menu.  When the hd unmounted it disappeared from that list as well.

---

### Post by barthel on 2009-10-29
Sorry for the lag in replying--I work 2 jobs.

That must be a change then, since my USB drives still show up under 'Places' after being unmounted.

Do they at least show up under the 'Computer' view of Nautilus?

Perhaps I can duplicate your issue when I go to Karmic.

---

### Post by Dark_Stang on 2009-10-29
Is this one of the Western Digital "green" drives? This is a very common issue with them, and not just with linux.

---

### Post by initiallyM on 2009-10-29
The external hard drive in question is a Maxtor One Touch 4 Plus.

Also, I have a little clarification on what's happening when it disconnects. When I attach the hard drive, an icon shows up on the desktop. Right clicking on the icon gives me two options for disconnecting it: "unmount" and "safely remove drive." When I unmount it, I can still find it in the "Places" menu and go and remount it. When I choose to safely remove drive, it is no longer in the places menu and there seems to be no indication that the usb cable is still attached. I guess that option fully disconnects it.

So again, my problem is that the external hard drive is automatically disconnecting after it spins down. This disconnection seems to take the same effect as safely removing the drive. The hard drive is no longer listed under the Places menu and there seems to be no indication that the usb cable is still connected.

Anyone else having this problem? Any suggestions?

---

### Post by nrgflux on 2009-10-31
Yep, same problem here. Just upgraded to 9.10 (thus not a fresh install).
Same drive too. Maxtor OneTouch 4 Plus.

If anyone can make sense out of these DMESG messages that would be fantastic!

It looks like this is where the drive connects:
```
[96763.812039] usb 2-4: new high speed USB device using ehci_hcd and address 20
[96763.946133] usb 2-4: configuration #1 chosen from 1 choice
[96763.946774] scsi9 : SCSI emulation for USB Mass Storage devices
[96763.946958] usb-storage: device found at 20
[96763.946961] usb-storage: waiting for device to settle before scanning
[96768.944189] usb-storage: device scan complete
[96768.946056] scsi 9:0:0:0: Direct-Access     Maxtor   OneTouch         0121 PQ: 0 ANSI: 4
[96768.946562] sd 9:0:0:0: Attached scsi generic sg2 type 0
[96768.951531] sd 9:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[96768.952906] sd 9:0:0:0: [sdb] Write Protect is off
[96768.952910] sd 9:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[96768.952913] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[96768.954902] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[96768.954906]  sdb: sdb2 < sdb5 >
[96768.984901] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[96768.984906] sd 9:0:0:0: [sdb] Attached SCSI disk
[96769.735401] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended

```

Then the fun starts when the drive spins down:
```
[99191.116040] usb 2-4: reset high speed USB device using ehci_hcd and address 20
[99191.228036] usb 2-4: device descriptor read/64, error 18
[99191.452046] usb 2-4: device descriptor read/64, error 18
[99191.668042] usb 2-4: reset high speed USB device using ehci_hcd and address 20
[99191.780041] usb 2-4: device descriptor read/64, error 18
[99191.996038] usb 2-4: device descriptor read/64, error 18
[99192.212041] usb 2-4: reset high speed USB device using ehci_hcd and address 20
[99192.233152] usb 2-4: device descriptor read/8, error -61
[99192.352398] usb 2-4: device descriptor read/8, error -61
[99192.568047] usb 2-4: reset high speed USB device using ehci_hcd and address 20
[99192.589151] usb 2-4: device descriptor read/8, error -61
[99192.709152] usb 2-4: device descriptor read/8, error -61
[99192.812897] sd 9:0:0:0: Device offlined - not ready after error recovery
[99192.816245] usb 2-4: USB disconnect, address 20
[99192.940462] usb 2-4: new high speed USB device using ehci_hcd and address 21
[99193.064834] usb 2-4: device descriptor read/64, error 18
[99193.280026] usb 2-4: device descriptor read/64, error 18
[99193.496034] usb 2-4: new high speed USB device using ehci_hcd and address 22
[99193.608039] usb 2-4: device descriptor read/64, error 18
[99193.824034] usb 2-4: device descriptor read/64, error 18
[99194.040041] usb 2-4: new high speed USB device using ehci_hcd and address 23
[99194.061149] usb 2-4: device descriptor read/8, error -61
[99194.181150] usb 2-4: device descriptor read/8, error -61
[99194.396043] usb 2-4: new high speed USB device using ehci_hcd and address 24
[99194.417146] usb 2-4: device descriptor read/8, error -61
[99194.537151] usb 2-4: device descriptor read/8, error -61
[99194.640046] hub 2-0:1.0: unable to enumerate USB device on port 4
[99195.096040] usb 4-4: new full speed USB device using ohci_hcd and address 18
[99195.280039] usb 4-4: device descriptor read/64, error 18
[99195.568042] usb 4-4: device descriptor read/64, error 18
[99195.848040] usb 4-4: new full speed USB device using ohci_hcd and address 19
[99196.032042] usb 4-4: device descriptor read/64, error 18
[99196.316037] usb 4-4: device descriptor read/64, error 18
[99196.596034] usb 4-4: new full speed USB device using ohci_hcd and address 20
[99196.623058] usb 4-4: device descriptor read/8, error -61
[99196.747064] usb 4-4: device descriptor read/8, error -61
[99197.024035] usb 4-4: new full speed USB device using ohci_hcd and address 21
[99197.051061] usb 4-4: device descriptor read/8, error -61
[99197.176068] usb 4-4: device descriptor read/8, error -61
[99197.281049] hub 4-0:1.0: unable to enumerate USB device on port 4

```

I don't mean to hijack your thread, initiallyM, but hopefully we can get to the bottom of this!

---

### Post by barthel on 2009-11-01
To me, the key lines are:

  [99192.812897] sd 9:0:0:0: Device offlined - not ready after error recovery
and 
  [99194.640046] hub 2-0:1.0: unable to enumerate USB device on port 4

This explains why the drive is disappearing from the desktop--it truly is no longer visible to the system.

initiallyM, if your output has the same or similar errors (prior to the "offlined" error), I'd be willing to bet it's a hardware driver issue--especially if the device worked in Jaunty. I'd receommed filing a bug report against USB mass storage.

Good luck!

---

### Post by nrgflux on 2009-11-01
Thanks for replying, barthel.

The HD is indeed completely gone from the system.

And the reverse is true as well it seems: The light on the front of the Maxtor unit is out. Usually it pulsates when in sleep mode, now there is nothing so it looks like the drive does not even detect the PC any more.

One more variable is that I am running on a MAC Mini (March 2009 model).

I'll wait for reply from initiallyM and if the output from DMESG matches up I'll submit a bug report.

Cheers

---

### Post by initiallyM on 2009-11-01
Thanks a lot for your input and the further elaboration, nrgflux.

My own computer is a 2 year old Dell Inspiron. 

What should I type to obtain the dmesg for the external hd?

---

### Post by nrgflux on 2009-11-03
I do not know a way of filtering the output for just the drive.
Just reconnect your drive so it spins up again, then type in
```
dmesg | tail -n 20
```

You should see something similar to the first part of the code in my previous post. Next wait till the drive spins down and "disappears". Type in the same command but with some more (last) lines (say 60).

If you code matches up I'll post a bug report. Hopefully that will get us somewhere.

---

### Post by initiallyM on 2009-11-03
Here's the display message after connecting the external hd

```

[66180.924175] usb 2-1: new high speed USB device using ehci_hcd and address 9
[66181.058477] usb 2-1: configuration #1 chosen from 1 choice
[66181.059635] scsi6 : SCSI emulation for USB Mass Storage devices
[66181.059898] usb-storage: device found at 9
[66181.059904] usb-storage: waiting for device to settle before scanning
[66186.056554] usb-storage: device scan complete
[66186.057474] scsi 6:0:0:0: Direct-Access     Maxtor   OneTouch         0121 PQ: 0 ANSI: 4
[66186.058474] sd 6:0:0:0: Attached scsi generic sg2 type 0
[66186.066482] sd 6:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[66186.068121] sd 6:0:0:0: [sdb] Write Protect is off
[66186.068130] sd 6:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[66186.068136] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[66186.071147] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[66186.071159]  sdb: sdb1
[66186.102582] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[66186.102593] sd 6:0:0:0: [sdb] Attached SCSI disk

```Here's the display message after it disconnects

```

[65632.414782] sd 5:0:0:0: [sdb] Attached SCSI disk
[66050.988327] b44: eth0: Link is up at 100 Mbps, full duplex.
[66050.988336] b44: eth0: Flow control is off for TX and off for RX.
[66142.197320] usb 2-1: USB disconnect, address 8
[66180.924175] usb 2-1: new high speed USB device using ehci_hcd and address 9
[66181.058477] usb 2-1: configuration #1 chosen from 1 choice
[66181.059635] scsi6 : SCSI emulation for USB Mass Storage devices
[66181.059898] usb-storage: device found at 9
[66181.059904] usb-storage: waiting for device to settle before scanning
[66186.056554] usb-storage: device scan complete
[66186.057474] scsi 6:0:0:0: Direct-Access     Maxtor   OneTouch         0121 PQ: 0 ANSI: 4
[66186.058474] sd 6:0:0:0: Attached scsi generic sg2 type 0
[66186.066482] sd 6:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[66186.068121] sd 6:0:0:0: [sdb] Write Protect is off
[66186.068130] sd 6:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[66186.068136] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[66186.071147] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[66186.071159]  sdb: sdb1
[66186.102582] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[66186.102593] sd 6:0:0:0: [sdb] Attached SCSI disk
[68463.112287] usb 2-1: reset high speed USB device using ehci_hcd and address 9
[68463.224193] usb 2-1: device descriptor read/64, error 18
[68463.440192] usb 2-1: device descriptor read/64, error 18
[68463.657086] usb 2-1: reset high speed USB device using ehci_hcd and address 9
[68463.768192] usb 2-1: device descriptor read/64, error 18
[68463.984277] usb 2-1: device descriptor read/64, error 18
[68464.200302] usb 2-1: reset high speed USB device using ehci_hcd and address 9
[68464.220982] usb 2-1: device descriptor read/8, error -61
[68464.340531] usb 2-1: device descriptor read/8, error -61
[68464.556300] usb 2-1: reset high speed USB device using ehci_hcd and address 9
[68464.577036] usb 2-1: device descriptor read/8, error -61
[68464.697118] usb 2-1: device descriptor read/8, error -61
[68464.800318] sd 6:0:0:0: Device offlined - not ready after error recovery
[68464.800330] usb 2-1: USB disconnect, address 9
[68464.920172] usb 2-1: new high speed USB device using ehci_hcd and address 10
[68465.032203] usb 2-1: device descriptor read/64, error 18
[68465.248053] usb 2-1: device descriptor read/64, error 18
[68465.464197] usb 2-1: new high speed USB device using ehci_hcd and address 11
[68465.576193] usb 2-1: device descriptor read/64, error 18
[68465.792166] usb 2-1: device descriptor read/64, error 18
[68466.008266] usb 2-1: new high speed USB device using ehci_hcd and address 12
[68466.028909] usb 2-1: device descriptor read/8, error -61
[68466.148916] usb 2-1: device descriptor read/8, error -61
[68466.364315] usb 2-1: new high speed USB device using ehci_hcd and address 13
[68466.384948] usb 2-1: device descriptor read/8, error -61
[68466.504927] usb 2-1: device descriptor read/8, error -61
[68466.608293] hub 2-0:1.0: unable to enumerate USB device on port 1
[68466.876105] usb 5-1: new full speed USB device using uhci_hcd and address 6
[68466.996198] usb 5-1: device descriptor read/64, error 18
[68467.278536] usb 5-1: device descriptor read/64, error 18
[68467.492280] usb 5-1: new full speed USB device using uhci_hcd and address 7
[68467.612294] usb 5-1: device descriptor read/64, error 18
[68467.837163] usb 5-1: device descriptor read/64, error 18
[68468.052193] usb 5-1: new full speed USB device using uhci_hcd and address 8
[68468.083289] usb 5-1: device descriptor read/8, error -61
[68468.211388] usb 5-1: device descriptor read/8, error -61
[68468.424283] usb 5-1: new full speed USB device using uhci_hcd and address 9
[68468.454417] usb 5-1: device descriptor read/8, error -61
[68468.582403] usb 5-1: device descriptor read/8, error -61
[68468.685257] hub 5-0:1.0: unable to enumerate USB device on port 1

```This is most likely as far as my participation in this thread will go. I just received Windows 7 today and I plan to install it over Ubuntu. Maybe I'll look into dual booting one of these days. See you around.

---

### Post by canas on 2009-11-03
I have exactly the same problem.  I have a thread from a few days ago [http://ubuntuforums.org/showthread.php?t=1311901](http://ubuntuforums.org/showthread.php?t=1311901)

My guess is that this is a bug.  Sad to say, but I'm not hopeful to see it fixed until the next release :(

---

### Post by nrgflux on 2009-11-06
I reported the bug on launchpad.
Someone had a similar bug already.
I don't have much hope either.

---

### Post by cmcanulty on 2009-11-14
This is a linux issue and makes a complete backup about impossible here  are links to  web pages about issue with western digital and Maxtor. Unfortunately I can't figure out how to do the fix if anyone can please post  step by step beginner directions. I have 2 ext hds western digital and maxtor asnd both do it. This really needs a bug fix. It is very irritating to have to backup over a hundred ror so sessions to get my 64GB backed up.I have posted many threads about this under backup and everyone said bad hardware etc then I found the web pages.I even sent the HD back to factory and new one does exact same thing.I really want this fixed!
[http://www.nslu2-linux.org/wiki/HowTo/SetSpinDownTimeOnMaxtorOneTouch](http://www.nslu2-linux.org/wiki/HowTo/SetSpinDownTimeOnMaxtorOneTouch)
[http://www.nslu2-linux.org/wiki/FAQ/DealWithAutoSpinDownOnSeagateFreeAgent](http://www.nslu2-linux.org/wiki/FAQ/DealWithAutoSpinDownOnSeagateFreeAgent)
[http://alienghic.livejournal.com/382903.html](http://alienghic.livejournal.com/382903.html)
I think a permanent mount point is also needed so fix will work every time ext hd is hooked up but my tries to do that didn't work. I am not an expert with the terminal. O have also tried formatting as ntfs, ext3 fat 32 and ext4r no difference at all.

---

### Post by jens75 on 2009-11-17
I also have a Maxtor One Touch 4 Plus and I am having the same problem as you when using it with ubuntu 9.10. Does the drive work properly in 9.04? If so, I will revert back to that version instead.
 
I have successfully used the same external hard drive on an old Slackware dist before without any problems. But then i used FireWire.

---

### Post by magnus.kson on 2009-11-17
I have the same problem. The output from dmesg is similar to the ones already posted.
It worked in 8.10 but  in 9.10, it unmouts when the disk get to rest.
It's a bit annoying since I use the disk for automated backup, and if it's not mounted, no backup is made.

(Occasionaly the disk was not mounted at startup in 8.10, but after a manual disconnect-connect it worked all day long.)

I read that it's reported as a bug. I'm not familiar with the bug-handling routines, is there any additional information I can give to help solve the problem, or is it just to wait and hope for the best?

---

### Post by cmcanulty on 2009-11-17
I posted above some web sites but I am not good enough to do the fix. Mine unmounts during backups every few minutes. All it needs is a slight pause while the backup is going and it unmounts.

---

### Post by jens75 on 2009-11-17
I installed 8.04 today and also installed the recommended updates (2.6.24-25-generic #1 SMP). I still get the same problem with my USB drive. I however noticed that if I disable high speed USB (sudo modprobe -r ehci_hcd) the drive works as it should. But of course the performance is really crap.

I will buy a firewire card instead, if I can fit one into my mini itx desktop, and use that instead. Or I will downgrade to an even older version of Ubuntu.

---

### Post by redmk2 on 2009-11-17
> **jens75 said:**
> I installed 8.04 today and also installed the recommended updates (2.6.24-25-generic #1 SMP). I still get the same problem with my USB drive. I however noticed that if I disable high speed USB (sudo modprobe -r ehci_hcd) the drive works as it should. But of course the performance is really crap.

I will buy a firewire card instead, if I can fit one into my mini itx desktop, and use that instead. Or I will downgrade to an even older version of Ubuntu.

If you are going to switch from USB, may I suggest looking into eSATA.  I bought a cheap SATA card with eSATA (external connection) for my P3 mobo PCI slot.  I get great performance and it has never failed any large file transfers.  I use Samba which is notorious for having problems with large files.

I bought a raw 3.5 inch drive and external case.  

Fire wire is deprecated at this point.

---

### Post by Excalibre on 2009-11-19
I'm just gonna give this thread a quick bump because I'm experiencing the same frustrating issue with the same model drive. It started in Karmic -- always worked fine in Jaunty.

---

### Post by nrgflux on 2009-11-20
Initially I piggybacked on someone else's launchpad bug but that was not going anywhere.

I've opened a new one:
[https://bugs.launchpad.net/ubuntu/+bug/486140]("https://bugs.launchpad.net/ubuntu/+bug/486140")

If you experience the same issue it might be good to attach your bug report to it.

---

### Post by PRC09 on 2009-11-20
Just a thought,in the manual for Windows operation it mentions power settings and a time settings,to adjust the length of time before the drive goes into power saving mode.Could this be causing the drop out as there appears to be a default but it doesnt say what it is.....

---

### Post by cmcanulty on 2009-11-21
It is a spin down problem in linux but needs a patch when it spins down in linux it unmounts doesn't in windows

---

### Post by PRC09 on 2009-11-21
Thanks...

---

### Post by magnus.kson on 2009-11-22
After re-reading the links supplied in post #15 of this thread, I booted into WinXp and used Maxtor's program to set spin down-time to "Never". Now my disc doesn't unmount. 
(I don't know if there are any drawbacks if the disc never spin down, maybe it will wear out sooner?)

For those of you who don't have the possibility of using windows, or don't have the original software from maxtor, I figured a script that writes to a dummy-file on the disc each minute will prevent it from spinning down.

Of course none of the above is a solution the actual problem. The disc shouldn't unmount on spin down.

---

### Post by cmcanulty on 2009-11-23
can you send details? If i mount it on an xp machine and set it then move to my  laptop would it not spin down? And can you post the script you used on Ubuntu? Thanks

---

### Post by magnus.kson on 2009-11-24
> **cmcanulty said:**
> can you send details? If i mount it on an xp machine and set it then move to my  laptop would it not spin down? And can you post the script you used on Ubuntu? Thanks

I have dual boot on my pc, Win XP and Ubuntu 9.10
Start Win XP, and then launch the Maxtor Manager program, it should have an icon in your status bar. Find the "Adjust Power Setting" and select "never". (Page 16 in the manual [http://www.seagate.com/support/onetouch/OneTouch4_Mini-Plus_Windows.pdf](http://www.seagate.com/support/onetouch/OneTouch4_Mini-Plus_Windows.pdf) )

When I now run Ubuntu the disk never spins down, at least it hasn't so far.

I'm not an advanced script writer and I tried the script for just a short while before I figured out how to chane the settings as described above, so i give no guarantees that it will work.

```
#!/bin/bash
FILE="/media/OneTouch4 Plus/dummy.txt"
TEXT=$(/bin/date)
echo $TEXT > "$FILE"
```

Just so it writes something, I made it write current date and time to a text file on the disk.
I added the script to System Tools -> Scheduled Activities (if that's what it's called in English) and made it run once a minute.

Hope this helps someone.

---

### Post by cmcanulty on 2009-11-25
OK I added scheduled tasks to my ubuntu where exactly do I paste your script into the scheduled tasks boxes? and running every minute is that only when maxtor is plugged in or always, I ask because I wonder if it would slow everything down to run it constantly, thanks

---

### Post by magnus.kson on 2009-11-26
> **cmcanulty said:**
> OK I added scheduled tasks to my ubuntu where exactly do I paste your script into the scheduled tasks boxes? and running every minute is that only when maxtor is plugged in or always, I ask because I wonder if it would slow everything down to run it constantly, thanks

This is how I did, maybe there are better, and more linux-standard ways to do it.

1. Open your texteditor and enter the code.
2. Save the file with the script as *onetouch.sh* in your home directory
3. Make sure the script file is exectuable (Right click the file and select - Properties - Permissions, check the Executable checkbox.)
4. Make a new entry in Scheduled Tasks
5. Enter the path to the script ( */home/username/ontetouch.sh* ) in the text field for Command. (*username* is of course your username)
6. Select it to run Once a minute

I had my OneTouch always plugged in, and didn't notice any slow down. It just writes a very small file.

---

### Post by cmcanulty on 2009-11-27
OK thanks, I will try it today. Mine seems to unmount really often but once a minute hopefully will do it.Now is there a way I have to mount it so the computer knows to associate the script with it

---

### Post by cmcanulty on 2009-12-05
I have done all the steps listed including set up the scheduled task. But I am unsure of how to make sure the scheduled task coordinates with the mount point of my external hard drive as it seems to have many different names when it mounts and I have never understood how to make it always the same with fstab. I have read a lot about fstab but nothing I have tried with it has ever worked for an external drive that is only mounted for backups.

---

### Post by jens75 on 2009-12-08
I found an interesting article regarding this problem:
[http://www.theinquirer.net/inquirer/news/1021483/seagate-issues-workaround-linux](http://www.theinquirer.net/inquirer/news/1021483/seagate-issues-workaround-linux)
 
I guess the best solution then is to set the spindown to 'never'. I am currently using USB 1.1 and the slow speed is driving me mad. I wonder what impact it will have on the hard drive if it never stops spinning? One thing is for sure, it will consume more energy...

---

### Post by felipemaxim on 2009-12-12
I had the same problem after updating to Karmic. Then i realised the problem was that the "udev" and "hal" services weren't running from boot. I corrected this in System> Administration> Boot-up manager and now my HD disk stays connected with no problems. Give it a try. :)

---

### Post by cmcanulty on 2009-12-12
Wow mine weren't either. Now I will try to mount it tomorrow, hope it works!

---

### Post by jens75 on 2009-12-13
But will this also solve the problem with the hard drive not being mounted again properly, after being suspended due to inactivity (e.g. after 30 min)?

---

