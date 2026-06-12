---
title: "Boot repaired but partitionlost.. how to salvage??"
date: 2012-07-21
forum: General Help
---

### Post by Amused2Death on 2012-07-21
Ok,
quick scenario, 640 gig hdd with dual boot Ubuntu and winxp with 2nd 500 gig hdd.

Had to go interstate and take the desktop, all went well going away, but when i came home i had lost the ability to boot into any OS. Grub came up with just tab as my assistance.

So i rebooted to cd with rescatux and followed the default fix. Sweet now i have both OS's available but the 2nd hdd isnt. It shows its there and healthy but when using disk utility is simply shows it as unknown 500 gig, partition hpfs-ntfs, bootable, partitioning = master boot record.

I cant mount it or access it, winxp tells me its not formatted, and it is/was my backup hdd.

How do i save 400 gig of data ??

thanks in advance

---

### Post by varunendra on 2012-07-21
Try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

TestDisk Step By Step: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by oldfred on 2012-07-21
+1 on    	varunendra suggestion of testdisk. 

What format was partition(s) on drive? If NTFS you may want to try chkdsk or if ext3 or ext4 try fsck.

With both the grub & drive issues, did you have an abnormal shutdown, power failure, or perhaps drive is just failing. You can check drive's status in Disk Utility, click on drive and see what Smart Data status is. All I know is green is good.

---

### Post by Amused2Death on 2012-07-21
Thanks,
I will read the TestDisk step by step instructions, and post how i went.

The drive is reported to be healthy both by Ubuntu and Winxp, with Winxp thinking it needs formatting. The file system on it is NTFS so both Ubuntu and Winxp can access it.

For whatever reason, when i reconnected everything and fired up the PC, grub came up telling me for help to use the tab key. For me it may have well been in a foreign language.

I rebooted with the grub rescue cd but it hung on searching. I replaced the grub cd with rescatux and rebooted. I followed the default repair which didn't take long.

I'm guessing that rescatux has rewritten something so both Ubuntu and Winxp think the drive needs formatting. It didn't have time to actually format it but it did have time to delete the partition i suppose. I just can't think of why it would.

It is just 1x500 gig partition.

Again thankyou for the help, now im off to read :o).

---

### Post by oldfred on 2012-07-21
Does Disk Utility still show it as 07 or 0x07? That is partition table. Then all NTFS partitions have to have a NTFS or Windows boot signature  (PBR) even if they are not currently bootable. If partition PBR was corrupted testdisk can restore the backup if not written twice.

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Or:

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

---

### Post by Amused2Death on 2012-07-23
For some reason i was unable to post yesterday, it kept timing out.

Disk Utility showed 0x07.

Thanks again for your prompt assistance, TestDisk saved the day, though being nervous, i spent several hours copying data across as soon as it gave me the ability. Once satisfied i had retrieved all the important stuff, i then let TestDisk rebuild the boot sector.... all returned to normal.

I thanked the makers of TestDisk with a donation, as i was very grateful for the program.

Sadly i then went on to update Ubuntu to 11.10 then to 12.04. I should have known better, 11.10 i lost the ability to find Administration and Preferences, and that continued into 12.04 where i lost my 2nd monitor. 12.04 thinks it is on a laptop for some reason, i am also getting a few failure messages and it has wanted to reboot twice so far to attempt to fix them.

Not to worry, WinXp is a solid as ever (no i'm not joking) and as i am currently half way through Diablo 3 Inferno level with my Wizard, i will probably continue to use XP the majority of the time. That is until i get some extra time to get my head around the new version of Ubuntu and sort out its problems.

Again thankyou for your help.

---

### Post by oldfred on 2012-07-23
I guess I think trying to fix computer issues as the best game around. :)

Were you running Unity or Fallback? I have not made the transition to Unity and run gnome-panel (gnome3) which is almost the same as fall-back (gnome2) which has the old panels & menus.

I upgraded from 6.06 thru 9.04 every version. But had to do a clean install with 9.10 as I converted to 64 bit. I found the clean install so much better I now only use clean installs.

---

### Post by varunendra on 2012-07-24
> **Amused2Death said:**
> I thanked the makers of TestDisk with a donation, as i was very grateful for the program.
I applaud you for this.=D>
However, I have found several times that although the partition table 'rebuilt' by testdisk is usable, but is often not compatible with gparted. In such cases, gparted still 'sees' the partition (or entire drive) as 'unknown' or 'unformatted'. So in my opinion, as soon as the data is recovered and copied to another disk, the partition(s) should be recreated with gparted to ensure full compatibility.

> **oldfred said:**
> I have not made the transition to Unity and run gnome-panel (gnome3) which is almost the same as fall-back (gnome2) which has the old panels & menus.I also used to stay away from Unity and stick with Gnome2 as long as possible (thus sticking with 10.04LTS), but as soon as I started using 12.04 due to its much improved hardware compatibility, I started liking Unity too. In fact now I sometimes miss some of its unique functions & features whenever I'm on a different desktop environment. Although it still has a long way to go, IMHO, it has matured enough to satisfy the majority of the new and even existing users.

Yes I do need sometimes the old interface and menu style to do some specific tasks - mainly some one-time configuration types, (because I still can't find a way to do them in unity). For that purpose, I install 'Cairo-Dock' in parallel which now also gives the option to completely boot into 'cairo-dock' desktop environment which is not only good-looking, but also has the old style menus system.

My only grief with Unity - it still feels very restrictive and far less customizable than Gnome2 used to be. But I hope that would go away with time when Unity get more stable and mature.

---

### Post by Amused2Death on 2012-07-26
Apologies for the delayed response:

I have had no issues with Testdisk and Ubuntu (fingers crossed) so far, all seems well.

Change for the sake of it isn't necessarily a good thing, i was more than happy with 11.04.

Once my addiction to Diablo 3 has been satisfied, i will look into Unity more, find out where they hid all the things i want, or use gnome-panel.

The worrying thing is i get an error message everytime i boot into 12.04 and try to use a program, say this time it was Ubuntu software centre. Tells me Ubuntu had a problem, and did i wish to send a report. Never had any issues like this with any previous version...

25 euro = $30 aust, which is a very small price to pay for saving 400 gig of data accumulated over 10 years.

Well the wifes away for a few days, so i'm off to feed my gaming addiction,... again thanks.

Cheers
Steve

---

### Post by hal8000 on 2012-07-26
I would post the error messages that you see with Ubuntu 12.04 to the forum
(but start a new thread) as you have resolved partition problems.

You have the best of both worlds, windows for gaming and Ubuntu for everything else. I'm also a gamer and keep a small windows partition just for gaming. Anything mission critical is done on linux.

About upgrading Ubuntu, I always keep all of my work, bash scripts, images, docs etc, on a USB stick and when a new version of Ubuntu comes out, do a clean install.

Personally I always find a clean install much faster, an upgrade takes about 3x longer as all files have to resolve dependencies, etc.

---

### Post by varunendra on 2012-07-29
> **Amused2Death said:**
> The worrying thing is i get an error message everytime i boot into 12.04 and try to use a program, say this time it was Ubuntu software centre. Tells me Ubuntu had a problem, and did i wish to send a report. Never had any issues like this with any previous version...
I'm also getting the same error message at random times and occasions (sometimes multiple times in one session). In my case, it is related with "bluetoothd" . You can see it in the 'details'  of the generated error report to be sent. Bluetooth isn't working in my laptop (Asus X54C-SX261D), while it's fine in Win7 which I'm dual booting.

I haven't tried connecting to a wireless network yet, but it seems to be okay since it can detect available networks.

Apart from the bluetooth, everything else (including a variety of 3G USB modems and other peripherals) is working so wonderfully that has made the BT a non-issue for me. The error message and its reasons (bluetoothd and related stuff) don't seem to be affecting any other functionality.

I haven't yet got enough time to go after the BT issue, maybe it'll get fixed by itself with some relevant update :).

---

