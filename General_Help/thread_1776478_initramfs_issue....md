---
title: "initramfs issue..."
date: 2011-06-06
forum: General Help
---

### Post by Jimcamera on 2011-06-06
Dear All,

After a seemingly normal shutdown, my lap-top will not launch Ubuntu.  I end up with the initramfs prompt.   I've been using Ubuntu happily (10.04) for a good few months now.

The windows part of my laptop still boots up fine.

I've tried booting from my installation cd but it starts off saying "unable to handle kernel paging request at O1FC1000" and proceeds to chunter a lot, but ends up just hanging.  Lots of hacker type text,but no action.  I've left it hanging for half a day to no avail.

Having done some searching on this forum I've tried a few things, but no joy.  This includes going to change the root in the grub menu to each and every one (six) of the possible (hd0,6).  It allows me to do this, but when I go for the loopback part it says either file not found or unknown filesystem...

I've tried doing a chkdsk through windows, but the Ubuntu partition doesn't seem to have a letter assigned to it, so I can't change the drive letter to enable a chkdsk (if this is a viable thing to do).

I'm about to go away for a day, so my response to any help that may be forthcoming may be delayed, but I'm becoming desperate now...

As you may have guessed, I am not at all used to the under the bonnet aspects of computers, though not scared to try.  It's just that you will need to explain where to start all the typing, if we get that far.

Thanks in anticipation...

All the best

Jim

---

### Post by Rubi1200 on 2011-06-08
Hi and welcome to the forums :-)

Please do the following so we can help you troubleshoot this:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Jimcamera on 2011-06-09
Right, back on track with my very own thread.

I have downloaded and am running boot_info.. and have the following 

[I]
"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.
[/I][I]
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information...
Searching sda2 for information...
Searching sad3 for information...
Searching sda4 for information...
Searching sda5 for information...[/I]

And that's where it hangs.  This would seem to echo the issues I discovered with my system testing.

I have attached again, the two images I obtained when following the (if I remember correctly {like I didn't your name Rubi1200}) the exit and lbdisk commands from initramfs.  Apologies in general for the waste of bandwidth.

I will shut down and restart the live cd install in case the system testing (which still hangs and cannot be closed down) is impeding the boot_info program.

All the best

Jim

---

### Post by matt_symes on 2011-06-09
Hi

From Rubi's post

> Boot the Ubuntu Live CD/USB.You need to boot into a LiveCD/USB download and run the script.

> "gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.You're trying to run the script when in Busybox, at the busybox prompt ?

That will not work because at the point it's failing it has not found the root filing system and cannot follow the symlinks from awk to gawk.

Unless i am misunderstanding what you have done...

Kind regards

---

### Post by Jimcamera on 2011-06-09
For info, restarting from the live cd with nothing else running still leads to the situation described in my last post: hanging...

Best

Jim

---

### Post by Rubi1200 on 2011-06-09
You mention that Windows was booting normally; is that still the case?

If yes, you need to try another distro called [Slax]("http://distrowatch.com/table.php?distribution=slax"). Download it and burn the image to CD before booting the computer with it. Make sure BIOS is set to boot from the CD drive.

If you get to the Slax live desktop open a terminal from the menu and run the command for the boot script with one exception; you do not need to preface it with sudo since Slax uses a root terminal.

I have to go offline for about 5 hours but will look back in again as soon as I can.

Good luck!

---

### Post by Jimcamera on 2011-06-09
Matt,

You wrote:

[I]You're trying to run the script when in Busybox, at the busybox prompt ?

That will not work because at the point it's failing it has not found  the root filing system and cannot follow the symlinks from awk to gawk.

[/I]No, I'm not trying to run the script from the busybox (initramfs actually, if that's important) prompt.  I'm running it from Terminal through the live cd induced Ubuntu that I can get running on my laptop.

For info, it's still hanging, "searching sda5 for information..."

Thanks

Jim

---

### Post by Jimcamera on 2011-06-09
Rubi1200,

Yes, windows does still boot normally.

I will download Slax and rerun the script *sans* sudo and let you know what happens.

Thank you for your help on this, I will check the thread later.

Best

Jim

---

### Post by jramshu on 2011-06-09
I have read there is a fix for this by running fsck /dev/sd* from a live cd. "*" being your drive name. 

EDIT: You could actually run this against all partitions to check for errors.

---

### Post by Rubi1200 on 2011-06-09
> **Jimcamera said:**
> Rubi1200,

Yes, windows does still boot normally.

I will download Slax and rerun the script *sans* sudo and let you know what happens.

Thank you for your help on this, I will check the thread later.

Best

Jim
I suspect the reason the boot script is not working has to do with possible file-system damage. 

Try and use Slax and report back if you are successful. If so, we can take it from there.

---

### Post by Jimcamera on 2011-06-09
Hello All,

Slax seems to run, I choose graphics mode, and it does all sorts of exciting hacker-text type things but ends up with "Starting up X11 session manager..."

My cursor lies forlorn in the bottom left hand corner.

How do I get a menu to choose Terminal from?

One child put to bed, two more to go, so responses may be disappointingly slow.
Thanks

Jim

---

### Post by Rubi1200 on 2011-06-09
Did you choose the first menu entry for KDE graphics mode?

Try the one further down called VESA mode and see where that gets you.

You could also try the entry called text mode.

---

### Post by Jimcamera on 2011-06-09
Got Slax to work - a whole new interesting world out there...

...but I cannot get it to find my wifi.  It can find it, but how do I get it to log on?

Thanks

Best

Jim

---

### Post by Jimcamera on 2011-06-09
Hi All,

Managed to work around Slax not letting me get to the internet, saved boot_info onto a USB..

..and it works!

Here's the results.txt:

     ```
             Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'ext4'

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0e33ec55

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    29,366,819    29,366,757  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     29,366,820    29,575,664       208,845   7 NTFS / exFAT / HPFS
/dev/sda3          29,575,665   353,190,352   323,614,688   7 NTFS / exFAT / HPFS
/dev/sda4         353,191,934   625,141,759   271,949,826   5 Extended
/dev/sda5         353,191,936   614,012,927   260,820,992  83 Linux
/dev/sda6         614,014,976   625,141,759    11,126,784  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1018 MB, 1018167296 bytes
14 heads, 13 sectors/track, 10926 cylinders, total 1988608 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                 249     1,988,607     1,988,359   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        C0382B19382B0DCA                       ntfs       PQSERVICE
/dev/sda2        44F82B61F82B508A                       ntfs       SYSTEM RESERVED
/dev/sda3        A2742CC5742C9E53                       ntfs       Packard Bell
/dev/sda5        a8f65524-f503-40f0-a151-3658b3cd2ffe   ext4       
/dev/sda6        f7be1b53-50e6-46f9-995e-14d54ed87337   swap       
/dev/sdb1        0123-4567                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /mnt/sda1                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sda2        /mnt/sda2                fuseblk    (rw,noatime,allow_other,blksize=512)
/dev/sda3        /mnt/sda3                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sdb1        /mnt/sdb1                vfat       (rw,noatime,quiet,umask=0,check=s,shortname=mixed)
/dev/sr0         /mnt/sr0                 iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file



```

Hope that's all posted properly.

Thanks.

All the best

Jim

---

### Post by jramshu on 2011-06-09
From a live disk.
```
sudo fsck /dev/sda5
```

---

### Post by Rubi1200 on 2011-06-10
Hi Jimcamera,
nice job getting Slax to run and finding a way to do the boot script :-)

Okay, I suggest you run the following command to try and fix the damage to you Ubuntu install:

```
e2fsck -f -y -v /dev/sda5
```

Note, again, that since Slax uses a root terminal there is no need to use sudo.

Once the command completes, and assuming no errors, reboot taking out the CD and you should be back in Ubuntu.

---

### Post by Jimcamera on 2011-06-10
Hello All,

Continued thanks for your continued help.  We are getting somewhere.  Slax could enable the fsdk, but the live cd Ubuntu could not.

So the fsdk did quite a lot of fixing and eventually finished.

I boot Ubuntu, and it goes much better than before, but I get this message:
[I]

There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256

[/I]Then it flags in the top right of screen "Install problem! The configuration defaults for GNOME Power Manager have not been installed correctly.  Please contact your computer administrator."

Meanwhile I am asked for the password for keyring 'Default'.  I enter this, but that's it, and I'm left hanging.

Which door shall we blast open now?  Or are we cutting the blue wire - or is it the red?

Thanks!

Best

Jim

---

### Post by Rubi1200 on 2011-06-10
Hi,
we are making progress, I think?

Here is what I would ask you to try; try and boot into recovery mode on the Ubuntu install and drop to a command prompt shell.

If it works, post the output of the following command:

```
df -H
```

If you are unable to get that far, then boot again with Slax and mount the Ubuntu partition and run the command from Slax.

---

### Post by Jimcamera on 2011-06-10
Sorry for delay - children, breakfast, school and wife run.  Back now for a short while before having to go off again.

So:  Having to do this via Slax - how do you mount the Ubuntu partition (and what does this mean?).  I now know that it'll be sda5, but, but..

Thanks

Jim

---

### Post by Jimcamera on 2011-06-10
.. I'm trying to mount the Ubuntu partition from the command line in Slax, right?

To this end, I type:

mount /dev/sda5

I get the following response:

*mount: wrong fs type, bad option, bad superblock on /dev/sda5, missing codepage or helper program, or other error.  In some cases useful info is found in syslog - try dmesg  | tail or so*

Hmm..  

Thanks.

Best

Jim

---

### Post by Rubi1200 on 2011-06-10
Okay, I am a bit confused about that because after the fsck finished last time you were able to make some progress.

As to the latest error, I read that one of the causes is a full file-system; in other words, you need to clean things up a bit.

Of course, if you are unable to access the install to do anything...

Please hang in there and I will ask some other users to jump in and offer their perspectives too.

---

### Post by coffeecat on 2011-06-10
Hi, I'm one of Rubi1200's "other perspectives". :)

Trying to get up to speed here in what seems to be a knotty problem.

> **Jimcamera said:**
> Yes, windows does still boot normally.

Can you confirm whether this is still so? I'm surprised because the filesystem on your sda5 Ubuntu root partition is/was corrupted and part of the grub (bootloader) code is in sda5. Were/are you able to see the grub menu OK?

> **Jimcamera said:**
> [I]
There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256

[/I]Then it flags in the top right of screen "Install problem! The configuration defaults for GNOME Power Manager have not been installed correctly.  Please contact your computer administrator."

Meanwhile I am asked for the password for keyring 'Default'.  I enter this, but that's it, and I'm left hanging.

I *believe* this is all caused by problems only in the configuration files in your own account and not in system files. Fingers crossed! I like Rubi1200's idea of running 'df -h' but, of course, you can't because you can't log into your account.

Try this:

At the grub menu, choose recovery mode. At the secondary menu, choose "drop to root shell". It doesn't matter whether you choose networking or not. If you don't have an ethernet cable attached you won't get networking anyway. You should end up in a plain text-only console with a '#' prompt. That's a root prompt, so be careful what you type - you have full root powers. Run:

```
df -h
```... and post the output. You'll have to write it down - sorry. Now, to shutdown gracefully so as not to do any filesystem damage:

```
shutdown -h now
```... or, if you want to reboot into Windows, the code is:

```
reboot
```Sometimes terminal commands **do** make sense! :wink:

I'll voice my line of thought now so that Rubi1200 and others can comment. I'm hoping that the filesystem has been repaired with Rubi1200's fsck command. (not fsdk - be careful what you type in the root shell), but that damage to your own account's configuration files is causing all the problems now. If so, a drastic but effective way of dealing with that is to delete all the hidden personal configuration files so that they are regenerated when you next try to login. The 'df -h' command from the root shell may or may not tell us something useful, but if it works at least it tells us that the underlying non-gui system is functional. And then we can take it from there.

---

### Post by Rubi1200 on 2011-06-10
Hi,
can you also confirm for us that you ran the e2fsck command I posted or the "plain" fsck.

If you can boot into a root shell from the recovery option, we may be able to do more so also confirm this please. And, if you cannot, try and post the exact error message.

Thanks.

And, I also agree with coffeecat's approach :-)

---

### Post by Jimcamera on 2011-06-10
I can confirm that windows still boots normally.

I did run the e2sfsck (though may not have transcribed it properly in this particular mail).

I have booted into recovery mode (which I've not been able to do before).

From the df -h command I get:

Filesystem       Size      Used      Avail  Use       Mounted on
/dev/sd5         123G       35G       83G  30%      /
None               1.4G      320K      1.4G   1%      /dev
none                1.4G         0         1.4G  0%      /dev/shm
none                1.4G        40K      1.4G   1%     /var/run
none                 1.4G       0          1.4G   0%     /var/lock
none                 1.4G       0          1.4G   0%     /lib/init/rw

Thanks.

All the best

Jim

---

### Post by coffeecat on 2011-06-10
> **Jimcamera said:**
> From the df -h command I get:

Filesystem       Size      Used      Avail  Use       Mounted on
/dev/sd5         123G       35G       83G  30%      /
None               1.4G      320K      1.4G   1%      /dev
none                1.4G         0         1.4G  0%      /dev/shm
none                1.4G        40K      1.4G   1%     /var/run
none                 1.4G       0          1.4G   0%     /var/lock
none                 1.4G       0          1.4G   0%     /lib/init/rw

The reason Rubi1200 suggested you run 'df -h' is that a full root disk can result in the gnome power manager error message. That output is useful because we can now exclude that, so we need to return to this:

> **Jimcamera said:**
> [I]
There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256

[/I]Then it flags in the top right of screen "Install problem! The configuration defaults for GNOME Power Manager have not been installed correctly.  Please contact your computer administrator."

Meanwhile I am asked for the password for keyring 'Default'.  I enter this, but that's it, and I'm left hanging.

Previously I thought that all these could be explained by damaged configurations in your home folder. Now I'm not so sure. If there are damaged configurations in the system folders, this could be very difficult to repair, but let's concentrate on your home folder first and see what we can do. One feature of Ubuntu is that if you delete personal configuration files and folders, they get regenerated with defaults when you next try to log in. You lose any personal configurations you have made, but at least you remove corrupted files.

Since I last posted I've been experimenting with a virtual Ubuntu system to see which config folders can be safely removed. I hope I've got this right, but I can't guarantee anything. You may wish to see if anyone else comments before you proceed.

This is what you could do. Boot up in recovery mode as before and choose "drop to root shell". I'm going to suggest renaming some hidden folders instead of deleting them outright. They can always be deleted later. Now:

```
 cd /home/yourusername
```Substitute your login name for "yourusername". Now:

```
mv .cache .cache.back
mv .config .config.back
mv .gconf .gconf.back
mv .gconfd .gconfd.back
mv .gnome2 .gnome2.back
```As before, be careful what you type and don't forget the leading dots in the folder names. Now:

```
reboot
```... and see if you can login. Post any error messages you see.

---

### Post by Jimcamera on 2011-06-10
I typed the quoted code but upon rebooting, I have exactly the same response..
[I]
"There is a problem with the configuration server.."[/I]

The only difference is that this time it doesn't ask me for my default keyring password.

I assume I hit 'Enter' at the end of each one of the quoted lines of code, yes?

Thanks.

All the best

Jim

---

### Post by Jimcamera on 2011-06-10
.. and just so you all know.. I can longer get into the GUI of recovery mode.  

When booting in recovery mode it does all sorts of things, but leaves me hanging with 

[I]*Setting sensors limits
Skip stopping firewall: ufw (not enabled) 


 [/I]and a flashing cursor with nothing in front (to the left) of it.

Thanks

All the best

Jim

---

### Post by coffeecat on 2011-06-11
> **Jimcamera said:**
> I typed the quoted code but upon rebooting, I have exactly the same response..
[I]
"There is a problem with the configuration server.."[/I]

The only difference is that this time it doesn't ask me for my default keyring password.

The commands have seemingly fixed part of the problem which was in your home folder but it sounds as though the damage to the system  is more extensive than just in your home folder - which is what I had  feared.

Just to recap. The filesystem on your Ubuntu partition was corrupted somehow - we can tell that because you had some sort of response to fsck - but after being repaired there is obviously still damage or loss to individual files. I was hoping that the damage was confined to your home folder. But clearly not.

> **Jimcamera said:**
> .. and just so you all know.. I can longer get into the GUI of recovery mode.  

When booting in recovery mode it does all sorts of things, but leaves me hanging with 

[I]*Setting sensors limits
Skip stopping firewall: ufw (not enabled) 


 [/I]and a flashing cursor with nothing in front (to the left) of it.

Thanks

All the best

Jim

There is no GUI with recovery mode - it's a text console - so I'm not quite sure what you mean by that. Those commands that you typed don't affect the ability of the system to  boot into recovery mode so it sounds as though we are trying to hit a moving target. Which makes me wonder now if there is a hardware fault.

Even though you can boot into Windows, you need to exclude the possibility of a failing hard drive. Perhaps only those sectors that the Ubuntu partition is on are failing. That sounds a bit far-fetched, I know, but stranger things happen. At this point I would suggest booting into the live CD to run a SMART test from Disk Utility but you said in your OP that the live CD wouldn't boot. Was this the same CD from which you originally installed Ubuntu to this machine? If so, it must once have been compatible and perhaps the CD itself has deteriorated. Do you still have the downloaded ISO?

---

### Post by Jimcamera on 2011-06-11
At the beginning of this process I could not boot from the live cd of 10.04 that I had.

I can boot from a version of 10.10 that I downloaded, and work within Ubuntu just fine.

I will do this and try and run the SMART test, assuming I can find it.  

When I referred to a GUI of recovery mode, I was talking about the little text screen control panel that no longer appears - but I see what you mean, it is not a GUI.

I will post the results of the SMART test in  a short while, hopefully.

Best,

Jim

---

### Post by coffeecat on 2011-06-11
Good luck with that. This from memory, but in 10.10 you can find Disk Utility in System > Administration. Highlight your drive in the left pane and you will be able to see "View Smart Data" in the right pane. Click on that and you should be able to run self-tests.

---

### Post by Jimcamera on 2011-06-11
As I thought, I'm not clever enough to run a SMART test.  I ran a system test from administration and skipped all except disk test.  The report, though, says nothing of apparent interest - perhaps you could tell me what to look for?

A hint of progress though.  The system recognises the hard drive partition where Ubuntu is normally stored and I can look at files within - but they are system type files, none of my personal files.  The size of the drive is indicated as 133GB, which is as it should be, and it says that 83Gb is free - so it's acknowledging that my files are in there somewhere.  I will look at each and every folder now, to see what I can find.

So, how do I run this test, please?

Best,

Jim

---

### Post by coffeecat on 2011-06-11
OK.

Smart test: did you see my earlier post just before yours? It may be on the previous page depending on your forum view settings. Open Disk Utility, highlight your internal drive in the left pane, and then look for "View SMART data" on the right. Click on that and there will be a "Run self test" button in the Smart DATA window that opens. Unless your HD doesn't support SMART, that is.

Have you opened the /home/yourname folder in your permanent installation from the live CD? Is it that you can see the various folders, but are not allowed to open them? If so, the reason  is that the UID for the live ubuntu account is 99 and your account UID is 1000. Linux permissions are doing their job and preventing you from browsing your own folder.

If this is so, you need to open a root nautilus in the live CD session with 'gksu nautilus'. It can be a bit confusing navigating to your home folder in the labyrinth of the live filesystem, so post back if you have difficulty with that.

---

### Post by Jimcamera on 2011-06-11
Having a had a rootle around amongst the folders on the aforementioned drive, I found a folder call 'Home' that does indeed have all of my stuff in it - though many of the folders have a cross on them.  I tried to open one of these folders and a warning came up indicating that I did not have "the permissions necessary to view the contents of xxx"

Some items, however, are viewable - a few .pngs I had sculling about untidily in the folder are fine - maybe because they're not in a sub-folder.

Is this useful/interesting?  It certainly seems hopeful.

Best,

Jim

---

### Post by Jimcamera on 2011-06-11
Our responses seem to be just out of sync - I did miss your post about the Smart test, sorry.  It is running now.  

You will also note our overlap re the files - how do I invoke the root nautilus (which sounds very exciting)?

For info - I ran a quick test on the drive and it has thrown up 6 bad sectors.  The only warning I got was ID 197 'Current pending sector count' - it refers to 6 sectors (those aforementioned bad ones?)

Thanks!

Best

Jim

---

### Post by Jimcamera on 2011-06-11
Okay, sorry, I ran gksu nautilus in terminal and can now access my files - I tried opening a pdf and it was just fine.

Shall I try and copy the important files I have onto an external drive before we go any further - or is any further really quite easy?

Best

Jim

---

### Post by Jimcamera on 2011-06-11
I am not allowed to copy files across onto another drive.  I tried doing the same from within a program (Openoffice) but upon saving it inferred that the file did not exist.

Hmm..

All the best

Jim

---

### Post by Rubi1200 on 2011-06-11
You should wait for coffeecat to respond with further suggestions on how to fix things.

Meantime, if you can access your files then copy and backup everything important now.

---

### Post by coffeecat on 2011-06-11
Yes, copy the files while you can. Just copy using a root nautilus to get into your home folder. Don't try opening or copying them with an application such as OpenOffice. That just complicates things and there may be some urgency to get the data off, because....

6 bad sectors is not too bad, but there are 6 bad sectors. It's quite common to have a few bad sectors. Modern hard drives automatically remap these, but if the number starts increasing that's when to get worried. Or, on the other hand, the bad sectors may only have just appeared and some files got corrupted before the information in the bad sectors was transferred to the alternative sectors. I don't know - I'm just speculating because it's frustrating when you get an ambiguous result like that.

I would suggest the following:

Backup those personal files as a first priority.

Your Ubuntu system is probably damaged beyond repair. Neither Rubi1200 nor I like to advise a re-install of an operating system, but I think this is one occasion where it is justified.

If you want to install 10.10 from the live CD you have, that's fine. But take care. The install alongside (or words to that effect) option in the partitioning stage of the installer has an appalling design flaw that can potentially lead to loss of your Windows system. You are safe if you choose the advanced/manual option which is not as daunting as it sounds. You need to use that option anyway if you want to re-use your Ubuntu partitions for the replacement installation.

But bear in mind that there is a possibility the drive is starting to fail. Keep backups of all your important files and once you have 10.10 installed, monitor the hard drive regularly with Disk Utility.

If you want to install 10.10 and need help with the partitioning stage, post back and Rubi1200 and I can advise.

@Rubi1200, are you happy with those comments? Feel free to disagree if you need to! :)

**EDIT**: just re-read this:

> I am not allowed to copy files across onto another drive.Describe exactly what is happening. If you access your files/folders with a root nautilus and use an automounted USB drive formatted with a Microsoft filesystem such as FAT32 or NTFS to copy to, you should be able to copy by simple drag and drop without any hindrance.

---

### Post by Jimcamera on 2011-06-11
When I try to drag the files across, it says "Error while copying..." and when I click show more details it says:  "Error opening file: Permission denied"

I can't even copy the file across to Desktop...

Continued thanks...

All the best

Jim

---

### Post by Jimcamera on 2011-06-11
.. I can't even copy and paste sections of documents between documents (ie old to new) in OpenOffice - although I can copy and paste within the old document (old to old) no problem.

This feels like some sort of admin thing that Coffeecat referred to earlier.  Could I be doing the nautilus operation wrongly?

Thanks,

Best

Jim

---

### Post by coffeecat on 2011-06-11
OK. Lets go through this step by step. You must have taken a wrong step. I've just simulated what you are trying to do by running the 10.10 ISO live in a VirtualBox Lucid installation, and this works.

In the live CD session, open a nautilus window from the Places menu. It doesn't matter which. In the left pane you will see your sda5 partition listed, probably as its size as it doesn't have a label. Click on it to mount it, and the main pane of nautilus will show you your Ubuntu filesystem. **Now close that nautilus window - it is of no further use.**

Now open a terminal, and:

```
gksu nautilus /media
```A root nautilus window will open in your live filesystem /media directory. You will see one or more folders, one of which will probably be called "a8f65524-f503-40f0-a151-3658b3cd2ffe". Open it and you will see your Ubuntu filesystem. If, by chance, there is no folder of that name, open the others to see which is the mountpoint.

Once you have your Ubuntu filesystem showing in the root nautilus window, browse to /home/yourname and now copy your files. At this point in my simulation I had no problem copying to the desktop, but there's no point copying to the desktop because you are simply copying into RAM memory. In fact it is a bad idea to copy more than a few files to the dektop because you are copying to RAM, which could be insufficient.

Now plug in your external USB drive and copy over your files to the nautilus window that opens by drag and drop.

**EDIT**. **Don't** use OpenOffice!

---

### Post by Jimcamera on 2011-06-11
I think the last trick worked.  I managed to copy some files over to a small thumb drive.  Now going through a minor Hell of broken power supplies and external drives that don't want to be recognised.  This lack of recognition nothing at all, I'm certain, to do with the current problem.

A small aside - how do you force a system to reassess its complement of drives?

Thanks

Jim

---

### Post by coffeecat on 2011-06-11
> **Jimcamera said:**
> A small aside - how do you force a system to reassess its complement of drives?

Not quite sure what you mean by this. A system will detect all internal drive partitions when it boots up but not mount them unless it is configured to do so (in /etc/fstab - but this is not applicable to a live CD session) or if you click on the partition in the Places menu when the automouting function deals with it.

For external drives, they should simply be recognised and automounted when you plug them in. The problems you are having certainly could be caused by bad power supplies. Just occasionally you encounter a USB firmware that interferes with automounting in Ubuntu - I've experienced this - but practically all external drives should automount so long as they are functioning properly and the filesystem is undamaged. Yes, corrupted filesystems and inadequate power supples are the two commonest problems. Speaking of which, are any of the external drives 2½ inch ones? They rely on the power being drawn from the USB port which can sometimes be inadequate. If so, try another USB port.

Not wanting to preach, but if you have external drives with dodgy power supplies, it's time to take stock. Your personal data is more valuable than the cost of the physical media it's stored on.

---

### Post by Jimcamera on 2011-06-11
I was whining about my laptop taking an age to realise that a drive has been plugged in, and I was hoping there was some routine you could do to make the computer look around itself to check each and every possible drive.

Not to worry.

I have taken your advice - and it wasn't preaching, and in any case, comparing our relative positions of knowledge you have every right to preach.  So, following your advice, I have purchased a new 1tb drive and I'm backing up windows (when the machine goes "Oooh look, I've got a new drive!") and I will then salvage all I can from the wrecked spaceship that is my sda5 partition and try to re-install Ubuntu.  I assume I should install the latest version?

Is there a guide to reinstalling in the custom mode so that I don't risk damaging the Windows install?

Finally, is there a way of copying my emails over from whichever file they were/are saved in before I re-install?  I was using Thunderbird.

Sorry I've been away most of the day, I've had to garden and do family things, which is only right, but may have left you wondering whether the ungrateful..

There will be another hiatus, but after bedtime, I should be able to start the re-install.

Thanks

All the best

Jim

---

### Post by coffeecat on 2011-06-11
Don't worry about the delays. We're used to enormous gaps sometimes on this forum when people are communicating across different time zones.

Thunderbird questions I'll have to defer to others. I've only ever tried it out as I always rely on the website client of my email provider.

**Custom install from the 10.10 live CD.** At the partitioning stage select "Manual/Advanced" It'll be the last choice on that page. After a brief delay while it scans your drive, it will present you with a table showing your partition layout. Select sda5, your current Ubuntu root partition, and click on edit or change (I can't remember which) or you may have to right-click to choose this. I'm going from memory here. In the small edit/change window you need to select ext4 in "Use as...", tick the format box and for mountpoint choose the first dropdown option which is '/' - that's shorthand for your root partition. OK that and you're done on that page. Don't worry about the swap partition - the installer will pick that up automatically. Apart from that you can safely go with defaults for it will automatically detect your Windows installation and install a fresh instance of grub with a dual-boot menu. 

Wait till Rubi1200 has posted, so that he can double-check that I haven't left anything out from that.

The routine for getting the system to check for plugged in drives would be a terminal command such as 'sudo fdisk -lu' or 'sudo parted -l', but that would only list what it already knows about, not rescan everything. If a drive is not detected when first plugged in, there's usually something wrong with the drive or partition filesystem - unfortunately.

---

### Post by Rubi1200 on 2011-06-11
Your Thunderbird email and profiles should be in a hidden folder in the home directory:
 ~/.mozilla-thunderbird

Make a backup of this and then copy it over on the fresh install.

As for the rest of the instructions given by coffeecat; seems right to me, though I haven't played around with installing 10.10 for some time now. Whatever you do, make sure to use the manual partitioning option and pick the right partition as mentioned above.

Good luck and let us know how it goes.

---

### Post by Jimcamera on 2011-06-12
Epilogue:

I am typing this to you from within Ubuntu.  My life is back to normal.  Thank you very much for all your help.

Apart from doing regular disk checks and back-ups, is there anything else I can do to prevent this happening again?

Finally, is there a way of trying to learn all this that really starts at basics?  Every tutorial I've ever tried assumes some sort of knowledge and I really need to start from way back.

Thank you for your time and patience.  I'd love to know who you are, and how you manage to generate enough time to be able to do all this.  And if you ever need any advice about aerial filming, I'll share my expertise with you - it's all I can offer I'm afraid...

Thanks again!

I hopefully won't trouble you too soon, all the best

Jim

---

### Post by coffeecat on 2011-06-12
First: you're welcome! :)

I'm glad to hear you're up and running again. What do you need to do? We never did really consider why this happened in the first place. It's unusual to get a major filesystem corruption spontaneously with no apparent cause. There must have been a cause. Which is why I advise number 1 is to open Disk Utility regularly and check the bad sector count. If it starts rising, backup all your data and think about needing to replace the drive. Drives fail. The only question is when.

You've already mentioned backups. Yes, backup and backup.

Learning from basics? This is a good starting point:

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

Although it's written for 10.04 rather than 10.10, it's still worth reading.

Apart from that: good luck!

---

### Post by Rubi1200 on 2011-06-13
Excellent! I am also really pleased you managed to get up and running again.

Enjoy :)

---

