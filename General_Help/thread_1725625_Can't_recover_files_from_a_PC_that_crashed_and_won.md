---
title: "Can't recover files from a PC that crashed and wont shut down."
date: 2011-04-10
forum: General Help
---

### Post by phil_pick on 2011-04-10
Hey guys, I know that this is a long post and I apologise for it but I am at a loss and any information you can give me would help immensely. Also, I am sorry if this question has been asked but I couldn't find one answering it. 
First off, I am a complete novice when it comes to computers and Ubuntu. 
Here is my problem. My wife's Windows Vista laptop crashed and now will not boot. It is a Compaq and when we turn it on it loads into the HP recovery program. The only option is to format the drive and reinstall windows. 
We can't do this however because we need to extract the files for my wife's college classes. I was told that you can use an Ubuntu Live CD to access these files so I burned a CD with 10.10 on it. It access's the computer and it appears to access the folders from the hard drive but all the folders are empty. Also the partition appears empty as well. 
I found a thread on here that mentioned that the file system needs to be closed for it to be mounted but the computer had to be forced shut down so that isnt an option. Also i read something about chkdsk /f. 

Again, any info would be amazing. Thanks in advance.

Phil

---

### Post by Rubi1200 on 2011-04-10
Hi and welcome to the forums :)

Whilst this is not strictly speaking an Ubuntu issue, I will try and offer some help anyway.

Boot the computer with the LiveCD and do the following so we can try and see what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Do you have the Windows installation/recovery disk or only the recovery partition on the computer in question?

---

### Post by dragonfly41 on 2011-04-10
This adds to the above advice on boot_info_script  ... based on my own recent experience recovering from a Vista crash ...

Unfortunately I had to retrieve my crashed Windows files into an external USB drive and then go through a fresh installation of Vista .. so I now have Vista in primary partition and ubuntu and ntfs in two logical partitions.  

There is a RECOVERY partition which restores Vista OS to factory settings (scrubs all your data so I didn't use that).

I use as my toolkit Parted Magic which comes with an array of tools.

burn the iso onto a bootable CD

[http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)

then boot up and inspect your partitions and file system.

Testdisk is also Parted Magic.

You have Internet access from Parted Magic.

.....................................................

But before all this .. can you get into Vista in "safe mode"?

Keep clicking F8 on booting up and then select safe mode or safe mode plus networking (which gives you internet access).

---

### Post by phil_pick on 2011-04-10
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
127 heads, 63 sectors/track, 61042 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   465,487,871   465,485,824   7 HPFS/NTFS
/dev/sda2    *    465,487,872   488,390,655    22,902,784   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        E68893E08893AE15                       ntfs                                     
/dev/sda2        868E28C98E28B419                       ntfs       RECOVERY                      
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

Here is the results.txt. I no not have a vista boot disk because there is a "recovery" partition. As dragonfly points out though it will format the drive. I have no problem formatting the drive but only after I extract the files that are on there. 

I haven't tried a recovery program yet just because I am a novice and I don't want to screw up the drive worse than it is. I will try the Parted Magic if it wont mess things up worse. Also I knw that this isn't an Ubuntu problem. It's a Windows problem, but I was told that I can find the files and back them up using Ubuntu.

One last bit of info, my wife had a login password. I don't know if that makes a difference but I thought I would let you know. Thanks for the replies.

---

### Post by Rubi1200 on 2011-04-10
Thanks for the results.

I am not a Windows expert and definitely recommend you also post this question and information on a Windows support forum. 

I have heard that sevenforums is one of the best:
[http://www.sevenforums.com/](http://www.sevenforums.com/)

That said, the results indicate that you are missing essential boot files for Windows and I suspect you actually had 3 not 2 partitions as the results show.

There is a program called Testdisk which can be used from the Ubuntu CD to recover data and partitions, but in your situation I would not advise it as the first line of action.

I will ask some other users to also take a look and offer their perspectives, so please be patient.

---

### Post by Quackers on 2011-04-10
Do you have access to another computer with either Vista or Windows 7 of the same architecture installed (ie 32 bit or 64 bit, whichever the damaged computer is using)?

---

### Post by phil_pick on 2011-04-10
I will post this in a few other forums and see what others say.

Yes, I am on another laptop that is running windows 7. The crashed one was Vista though so I am not sure if that matters. 

I loaded Parted Magic and it appears to find folders just like Ubuntu but the folders are generic and are empty, also like what Ubuntu found. The folders and files seem intact on the Recovery partition though.

---

### Post by dragonfly41 on 2011-04-10
Going back to my earlier post .. have you tried starting in windows "safe mode" .. F8 at boot?

You might be able to REPAIR or go back to a windows restore point.


Note that the RECOVERY partition is last resort and restores windows to factory OEM default (sans data files just basic OS as when you bought the PC).   

Try a Recovery disk first.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)


click on "Windows Vista 32-bit (x86) Recovery Disc Torrent"

and burn the downloaded iso (120 MB) onto a bootable CD.

You can do this through Parted Magic (after Parted Magic is loaded into RAM and CD ejected).


[EDIT] This old forum thread gave me a useful reference point ..

[http://ubuntuforums.org/archive/index.php/t-940076.html](http://ubuntuforums.org/archive/index.php/t-940076.html)



...

When I first installed ubuntu in wubi / demo mode (try it first) I found all my windows files in a ubuntu folder .. 

/isodevice

luckily I did not go for a full ubuntu installation until _after_ I had learned how to create the logical partition to keep ubuntu partition separate from windows Vista partition.   

Parted Magic helped me (just like LiveCD but with a set of rescue tools).

---

### Post by Quackers on 2011-04-10
> **phil_pick said:**
> I will post this in a few other forums and see what others say.

Yes, I am on another laptop that is running windows 7. The crashed one was Vista though so I am not sure if that matters. 

I loaded Parted Magic and it appears to find folders just like Ubuntu but the folders are generic and are empty, also like what Ubuntu found. The folders and files seem intact on the Recovery partition though.

You can make a repair disc from the Windows 7 system you are on now if it's the same architecture (32 bit or 64 bit). I think Vista and Windows 7 repair discs are the same.
If you go to Control Panel then Backup & Restore Centre then in the left pane click on "make a recovery cd". Pop a blank cd into the drive and you'll have a repair disc.
I think you may be able to run sfc /scannow from the command prompt in the recovery console of that repair disc, which is a utility that repairs damaged system files. The only thing is that it may ask for an installation disc to repair them.
This is a long shot and I suspect that someone at a Windows 7 forum will come up with something better.
Good luck to you.

---

### Post by phil_pick on 2011-04-10
Dragonfly, yes I tried to enter safe mode but even in safe mode windows takes me to the HP recovery partition. It wont start windows it just loads the recovery program and won't give me an option to go anywhere else or do anything else. This even occurs in safe mode. 

I have a Windows 7 upgrade disk that I thought I could use to upgrade and keep my files but it wont let me upgrade if I am not already in windows. I also tried to restore to a previous point but it said that there are no restore points. As if they have been erased. I am looking for an actual Vista instal disk and see if I can do a repair job but I don't have access to one yet.

Also in a setup menu (F8 maybe) I ran the memory test and it passed and then I ran the hard drive test and it failed. It is weird though because I ran chckdsk and it passed.

---

### Post by dragonfly41 on 2011-04-10
I've just noticed from output of boot info script that it is 

/dev/sda2   (size 22,902,784 - label RECOVERY) which has the boot flag set **on**

whereas 

/dev/sda1 (size 465,485,824) seems to contain Vista OS and data files?


This seems to tie up with you booting into RECOVERY partition.

Have you tried going into GPartEd (in Parted Magic) to change the bootable flag to be **on** in /dev/sda1

and **off** in /dev/sda2 ?


then reboot.


You can check disk integrity in Parted Magic.

---

### Post by phil_pick on 2011-04-10
I checked the health of the disk and it says healthy. How do I open GPartEd? I have Parted magic loaded but I don't see anything by that name in the tools or accessories. I think I might be able to restore to an earlier point if I can get it to boot with the Vista partition.

---

### Post by dragonfly41 on 2011-04-10
I'm in Vista OS at the moment so writing from memory .. Parted Magic is quite intuitive there is  an icon Partition Editor to the left .. and hover over the icons in the lower task bar to launch various tools.

Partition Editor is identical to GParted in ubuntu.

[EDIT] p.s. here are the screenshots ..

[http://partedmagic.com/doku.php?id=screenshots](http://partedmagic.com/doku.php?id=screenshots)

It is Partition Editor icon you click on.

Mount Devices icon shows all the disks (sda1, sda2 etc) and other devices.

You can also launch Firefox.

---

### Post by phil_pick on 2011-04-10
Ok I changed the flags and I am now able to boot using the correct partition. However I am now getting a Boot Manager error. It says that it failed to start and a hardware or software change might be the cause. It is asking for an instalation disk for a repair. Can I use a Vista repair disk ir a Windows 7 upgrade or do you think I would need to call HP to get a full Vista disk? 

Also thanks for all the help. I (and my wife) really appreciate it.

---

### Post by dragonfly41 on 2011-04-10
Go back to my post #8

> Try a Recovery disk first.

[http://neosmart.net/blog/2008/window...disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")


click on "Windows Vista 32-bit (x86) Recovery Disc Torrent"

and burn the downloaded iso (120 MB) onto a bootable CD.

You can do this through Parted Magic (after Parted Magic is loaded into RAM and CD ejected
In Parted Magic burn the iso into a CD and use that as your Vista Recovery Disk when you boot into Vista for a repair.

Alternatively have you tried F10 (or it might be F11) for a repair option?


there is some more advice here ..

[http://www.pctechbytes.com/windows/windows-failed-to-start-error](http://www.pctechbytes.com/windows/windows-failed-to-start-error)

[http://answers.microsoft.com/en-us/windows/forum/windows_7-system/windows-failed-to-starta-recent-hardware-or/8dad59b9-a08d-4cb8-8ddf-1c164b7caf65](http://answers.microsoft.com/en-us/windows/forum/windows_7-system/windows-failed-to-starta-recent-hardware-or/8dad59b9-a08d-4cb8-8ddf-1c164b7caf65)


> 
If you have an actual Windows Vista or Windows 7 disk (depending which  is installed), try booting to the disk. You will see an option to  perform a startup repair. Run that and see if Windows finds a problem.  If it does, allow it to fix the problem, then reboot the machine. If you  get a boot options screen following the reboot, choose &#8220;Start Windows  Normally.&#8221;


Try a System Restore. When booting, select Safe Mode Command Prompt.  Select the Administrator account and type in the password (if there is  one). At the prompt, type *cd \windows\system32\restore *and hit enter. This takes you to the system restore directory. Next, type *rstrui *and  hit enter again. When the system restore screen appears, follow the  instructions and go back a few days prior to the problem.Can you now get in through safe mode and try a repair?

---

### Post by phil_pick on 2011-04-10
Ok, I created a Vista Recovery disk and ran the automatic repair but it failed. It said that it can not automatically repair the operating system. It gives me the error log but I don't know what they mean. 

F8 and F11 menus are not accessible because I get the "windows failed to start" screen before the menus can load.

I can not get to "safe mode command prompt" but I can get to the regular prompt inside of the repair menu from the recovery disk. I tried the *cd \windows\system32\restore [I]prompt *[/I]but it says that there are no restore points on the disk.

Are there any other ideas either for repairing / reinstalling windows or of possibly accessing the files in Ubuntu and just copying them so I can reformat the drive?

---

### Post by Quackers on 2011-04-10
Did the automatic repair screen actually find the Vista OS? Often it does not.
Also, sometimes it is necessary to run the automatic repair 3 times, as it can only repair one thing at a time.
However, in your case, as the files can be seen, but appear to be empty, I'm afraid I fear the worst.

---

### Post by phil_pick on 2011-04-10
Yes, the repair does find the OS. It attempts to repair but than says that it cannot fix it. I ran it four times with a restart in between each and still nothing.

The folders that Ubuntu and Parted Magic find seem to be just generic folders. There are no specific folders that I know are on the drive. Also the partition that Vista is on shows up as 238 GB file system. When I look at it is shows 221.8 available. So there are 16 GBs of info on the partition that I just can't view. Could this be due to having a password at the start of windows?

---

### Post by Quackers on 2011-04-10
The last thin I can think of to try from the repair disc is to ignore the automatic startup reapir and select the advanced options (I think it's called) then select the command prompt option. In the command prompt window type in ```
bootrec.exe /fixmbr
``` Note the space between exe and /fixmbr.
Then press enter. Then try rebooting to see if it will boot.
I suspect though that some serious damage has been done to the file system.

As a last resort you could testdisk/photorec to recover files (if they are still on there) or take the computer or its drive to a professional data recovery service.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by K_45 on 2011-04-10
This is probably a good time to consider fresh backup's if you value your data.

---

### Post by dragonfly41 on 2011-04-11
News is none too encouraging. Data can be recovered even if the partition has been formatted or files deleted .. provided that you don't keep overwriting data in the disk.
Costs of sending a failed disk to professional data recovery specialists can be high.

As well as the advice from Quackers above in post #19 here are some other steps I suggest:-

(1) Boot up Parted Magic.   Go to System Tools > PC Man File Manager.
Can you see any of your files in any of the partitions?

(2) If you cannot see any files you have lost in PC Man File Manager.   
You can go to System Tools > Testdisk and System Tools > PhotoRec and follow the instructions in Quackers links above.   
But first I would consider creating a clone of your disk.

(3) You are going to need a backup drive after this experience so buy one now to attach through a USB 2.0 port.   The disk has to be larger than your internal drive you're trying to recover.

(4) When you have your USB drive connected via USB port you can create partitions on it using GParted in Parted Magic.

(5) Now in System Tools > CloneZilla 
    you have the choice of cloning:
    local disk to remote disk (in your external USB drive)
    or
    local partition to remote partition (in your external USB drive)

(6) Having safely cloned your disk or partition(s) to your external disk you can now try testdisk and photorec on your internal disk.

(7) There is other recovery software you can try if you have a working PC to attach the disk to.

---

