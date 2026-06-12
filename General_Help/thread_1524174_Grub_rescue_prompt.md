---
title: "Grub rescue prompt"
date: 2010-07-04
forum: General Help
---

### Post by Leoorin on 2010-07-04
Hello all..I will be quick..

Well i had three partitions one ntfs with windows 7 (250gb) one ext3 with ubuntu 9.10(200gb) and also another unformatted filesystem of 50gb.. I wanted to expand windows 7 and erase ubuntu for now and in that way keep only the ntfs format and the unformatted one..I deleted succesfully 9.10 and set swap partition as swapoff through gparted(from live cd) + resized the first partition but now i can't boot my pc in windows..It gives me a "grub rescue" prompt.Actually i read somewhere about updating my grub like [here]("https://help.ubuntu.com/community/Grub2") but i am not sure if this is what i do so i am asking before doing anything [SIZE=1]unnecessary.. 

Thanks in advance..
[/SIZE]

---

### Post by warfacegod on 2010-07-04
If you have removed Ubuntu from the system then you need to also remove GRUB and repair the Windows MBR.

This may help: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by Leppie on 2010-07-04
you probably forgot to set the mbr to factory defaults, e.g. use the active partition as boot partition.
booting off an ubuntu livecd, issue these commands to reset your mbr to factory defaults:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
ignore the warning/message that may appear. at reboot, your machine should boot straght into windows.

---

### Post by Leoorin on 2010-07-04
Tried all the comands in the link given but when it came to "sudo update -grub" it gave me this: 
[FONT=monospace]
[/FONT]```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

```But i guess if we want to remove completely grub,it has nothing to do with updates anyway right?Or maybe i am not so aware of this command...

Also i would like to state that at this time fixing the mbr through some windows cd is not possible so i would like any ideas about doing this through ubuntu live cd..


//edit: 
> **Leppie said:**
> you probably forgot to set the mbr to factory  defaults, e.g. use the active partition as boot partition.
booting off an ubuntu livecd, issue these commands to reset your mbr to  factory defaults:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```ignore the warning/message that may  appear. at reboot, your machine should boot straght into  windows.

just saw this..i will try this and see what happens then:)

---

### Post by Leppie on 2010-07-04
cool, let us know how it works out.

---

### Post by Leoorin on 2010-07-04
hmm,apparently something changed but now it says

BOOTMGR IS MISSING
Press alt+ctrl+del for reboot..

---

### Post by Leppie on 2010-07-04
ok, then you have to use the windows 7 recovery disk to restore the boot manager.
if you don't have a recovery disk, you can download it here: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by Leoorin on 2010-07-04
thanks man! i will try it right away..

may sound a little bit noobish but this has to do only with mbr right?
I mean with this recovery cd i can remove also the grub?

---

### Post by Leppie on 2010-07-04
> **Leoorin said:**
> thanks man! i will try it right away..
you're welcome :)

> **Leoorin said:**
> may sound a little bit noobish but this has to do only with mbr right?
I mean with this recovery cd i can remove also the grub?
no, this is no longer just the mbr. the mbr has been reset, that's why you get the "BOOTMGR IS MISSING" error. something may have gone wrong while playing around with the partitions. did you use gparted to resize the ntfs partition?

---

### Post by Leoorin on 2010-07-04
yeah tried all these resizing,deleting etc from gparted..It was the only way i knew actually..

well seems that i will have to burn that .iso file tomorrow morning at my pc in work and see what happens with the mbr..

i will come with more news by tomorrow if things are solved or got more complicated..:p

---

### Post by warfacegod on 2010-07-04
You might be wise to post the boot script info from the link I posted earlier. If things go badly, it could help in diagnosing your problem.

Leppie, leave my age out of this. Gods are timeless.... ....................................................................................................................................................................................................................................................................................................................................................................................................................... See? That took eons.

---

### Post by Leppie on 2010-07-04
> **Leoorin said:**
> yeah tried all these resizing,deleting etc from gparted..It was the only way i knew actually..
resizing of ntfs partitions is best done in windows...

---

### Post by warfacegod on 2010-07-04
> **Leppie said:**
> resizing of ntfs partitions is best done in windows...

Depends on the Windows. Vista and 7 will likely scream bloody murder and repairing can be a quest to make The Lord of the Rings look like a stroll to the corner store for beer. XP is usually much more forgiving.

But, these are *not* absolutes. Any OS, or partition for that matter, is vulnerable, to one degree or another, to being resized. There is no 100% perfectly safe way to mess with partitions. It's just a matter of reducing the risks, and that includes

.01 Foresight and planning with a clear goal in mind

.02 Using the proper tools (to put some air back into Leppie's balloon) 

.03 Checking and rechecking (the ol' measure twice, cut once rule)

.04 Leaving undone what shouldn't be done (if you're not sure, come here, there's always someone lurking about that knows what they're doing)

Or you can skip ahead and go straight to Rule .05

.05 Break it on purpose (this is hands down my favorite rule)

---

### Post by Leoorin on 2010-07-05
> **warfacegod said:**
> If you have removed Ubuntu from the system then you need to also remove GRUB and repair the Windows MBR.

This may help: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

> **warfacegod said:**
> You might be wise to post the boot script info from the link I posted earlier. If things go badly, it could help in diagnosing your problem.


well i don't know if it makes any sence but in the terminal i get this when i try to do the last step in your link(as i said earlier);

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

This was before trying anything Leppie said and actually i asked if updating is the correct term here as i want to actually delete grub..Or i think so..:S

Now when i tried to boot it before Leppie advice it was as in the very beggining.I mean showing the grub rescue prompt..

I haven't tried yet for a recovery windows 7 cd,but it's only a matter of time(i need to find a pc with dvd writer:P).If i could fix the MBR through live cd it would save me a lot of time otherwise it will take me till tomorrow or something till i get that recovery cd..

---

### Post by warfacegod on 2010-07-05
> /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

That means it's looking for a partition with Linux in it and can't find one. Because you removed it.

I really think you should hold off until you can get the Windows Disc. However, I'm never one to stop a guy from trying so here, read Section #12: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Leoorin on 2010-07-05
> **warfacegod said:**
> That means it's looking for a partition with Linux in it and can't find one. Because you removed it.

I really think you should hold off until you can get the Windows Disc. However, I'm never one to stop a guy from trying so here, read Section #12: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

good!thanks!Already saw that topic a while before and started reading it..:popcorn:

I will come up with more soon when i use that recovery cd..

---

### Post by Leppie on 2010-07-05
> **Leoorin said:**
> If i could fix the MBR through live cd it would save me a lot of time otherwise it will take me till tomorrow or something till i get that recovery cd..
the windows boot manager actually is on a windows partition. the mbr was restored when you did the "lilo" thing.

---

### Post by Leoorin on 2010-07-06
> **Leppie said:**
> ok, then you have to use the windows 7 recovery disk to restore the boot manager.
if you don't have a recovery disk, you can download it here: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

well finally i burned that cd and tried to boot it changing my first bootable device to cd/dvd from bios but nothing happened..strange :confused: it contiues saying that "BOOTMGR IS MISSING"

> **warfacegod said:**
> 
I really think you should hold off until you can get the Windows Disc.  However, I'm never one to stop a guy from trying so here, read Section  #12: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)[]("http://ubuntuforums.org/showthread.php?t=1195275")

well tried to execute the lines in paragraph 12 till the point it was saying for installation again..

I mean i back uped all grub files through that: 

sudo cp /etc/default/grub /etc/default/grub.old
sudo cp -R /etc/grub.d /etc/grub.d.old
sudo cp -R /boot/grub /boot/grub.old
and after that i continued with the unistallation..

sudo apt-get purge grub-common grub-pc

after some warnings like: "after this operation 6,615kb disk space will be freed [y/n]" unistallation was complete..

Should i have done the next steps that paragraph 12 says?I mean that part: 

> Install GRUB 2
[LIST]
[*] 	Code:
 	sudo apt-get install grub-common grub-pc 

[LIST]
[*]The user will be asked for any special commands to add to  the default "linux" line. If you aren't sure, leave it blank, press the  TAB key to highlight "OK" and press ENTER.
[*]Select the appropriate *drive* on which to install Grub2 (sda,  sdb, etc) by highlighting the entry and pressing the space bar. Normally  a partition (sda1, etc) should **not** be selected.
[/LIST]
[*] 	Code:
 	sudo update-grub 
[*]Reboot
[/LIST]


It's confirmed i am ver much complicated right now:P

---

### Post by warfacegod on 2010-07-06
No. You want to get rid of GRUB not install it again.

> It's confirmed i am ver much complicated right now

I did warn you.:rolleyes:

---

### Post by Leoorin on 2010-07-06
yeah i think i have got the main idea of what i should be doing now...removing grub(as grub is a bootloader for linux) and repairing mbr but i am a little bit confused..is it fixed through that "lilo" command (as leppie said) i executed in the terminal yesterday?Or i should repair it through that recovery cd?

the question is what i repair with what:p

---

### Post by warfacegod on 2010-07-06
> **Leoorin said:**
> yeah i think i have got the main idea of what i should be doing now...removing grub(as grub is a bootloader for linux) and repairing mbr but i am a little bit confused..is it fixed through that "lilo" command (as leppie said) i executed in the terminal yesterday?Or i should repair it through that recovery cd?

the question is what i repair with what:p

I'm fairly sure you should be using the CD but it might be wise to wait for Leppie to get back. Of course, we both know what happened the last time I suggested waiting...:P

---

### Post by Leppie on 2010-07-06
> **Leoorin said:**
> ... but i am a little bit confused..is it fixed through that "lilo" command (as leppie said) i executed in the terminal yesterday?Or i should repair it through that recovery cd?
as i stated before, if you completed the lilo instructions succesfully your mbr is now set to factory defaults.
the windows 7 recovery disk is rebuild the windows boot manager (amongst other things).

> **Leoorin said:**
> the question is what i repair with what:p
well, if you could provide me some more information we can determine what you need to do. booting off an ubuntu livecd, could you please download the boot info script: [http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.55/boot_info_script055.sh/download](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.55/boot_info_script055.sh/download)
save it to your desktop and issue the command:
```
sudo bash ~/Desktop/boot_info_script*.sh
```then post the generated RESULTS.txt

---

### Post by warfacegod on 2010-07-06
Speak of the Leprechaun and he shall appear.

---

### Post by Leoorin on 2010-07-06
here you are:

> 
            Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   872,313,434   872,313,372   7 HPFS/NTFS
/dev/sda2         872,313,435   976,768,064   104,454,630   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        09DAA59B3AE86F01                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)




---

### Post by Leppie on 2010-07-06
> **warfacegod said:**
> Speak of the Leprechaun and he shall appear.
it's a kind of magic... :lolflag:


the windows partition apparently got a bit messed up.
install the package ntfsprogs:
```
sudo apt-get install ntfsprogs
```
repair the windows partition:
```
sudo ntfsfix /dev/sda1
```
then try rebooting, if it does detect windows (which would of course be good) you need to run checkdisk from windows.

---

### Post by warfacegod on 2010-07-06
This should be done from a Live Environment, if I'm not mistaken.

---

### Post by Leppie on 2010-07-06
> **warfacegod said:**
> This should be done from a Live Environment, if I'm not mistaken.
yes, ubuntu livecd.

i'm getting old as well...  :lolflag:

---

### Post by Leoorin on 2010-07-06
Well tried to run these commands from the terminal and i paste you the complete log:

```
ubuntu@ubuntu:~$ sudo apt-get install ntfsprogs
Reading package  lists... Done
Building dependency tree       
Reading state  information... Done
ntfsprogs is already the newest version.
0  upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ sudo ntfsfix /dev/sda1
Mounting volume... $MFTMirr  location mismatch or first 4 records are fragmented. Run chkdsk.
Failed  to load $MFTMirr: Input/output error.
Failed to startup volume:  Input/output error.
FAILED
Attempting to correct errors... $MFTMirr location mismatch or  first 4 records are fragmented. Run chkdsk.
Failed to load $MFTMirr:  Input/output error.
FAILED
Failed to startup volume: Input/output  error.
Volume is corrupt. You should run chkdsk.
ubuntu@ubuntu:~$ 
```when i tried rebooting it nothing changed(as i guessed because of those FAILED in the very end of the log above:p) 
And yes i ran it in a livecd environment..More than that what is a checkdisk?:confused:

edit [google is our best friend:P]

**"CHKDSK** (short for **Checkdisk**) is a command on computers  running [DOS]("http://en.wikipedia.org/wiki/DOS"), [OS/2]("http://en.wikipedia.org/wiki/OS/2") and [Microsoft Windows]("http://en.wikipedia.org/wiki/Microsoft_Windows") operating systems that displays the [file  system]("http://en.wikipedia.org/wiki/File_system") integrity status of [hard disks]("http://en.wikipedia.org/wiki/Hard_disk") and [floppy  disk]("http://en.wikipedia.org/wiki/Floppy_disk") and can fix logical file system errors. It is similar to the [fsck]("http://en.wikipedia.org/wiki/Fsck") command  in [Unix]("http://en.wikipedia.org/wiki/Unix"). "

---

### Post by Leppie on 2010-07-06
yes, you should run checkdisk. are you sure the copy of the recovery is ok?

---

### Post by Leoorin on 2010-07-06
Well i think i am making some progress here:)

i tried and burned another copy of that recovery disk,tried it after booting,it actually worked but...! there was a windows like menu with many options and i tried the very first option that was "start up repair".After a while it said to reboot and after rebooting the same message "BOOTMGR IS MISSING" was still there not letting boot normaly the computer:(

I am thinking now an alternative way..Back then in that menu there was a last option of entering a "command prompt" window and giving by yourself some commands there.What if it works like that?Is there any command for windows to repair their boot manager through that?

Just for the record i tried a second time doing that "start up repair" but the system found no mistakes in the second time..

---

### Post by Leppie on 2010-07-06
at the command prompt, issue this command:
```
[FONT=Arial][SIZE=2][FONT=Verdana]Bootrec /RebuildBcd[/FONT][/SIZE][/FONT]
```

---

### Post by warfacegod on 2010-07-06
At this point, I vote for setting the damn thing on fire.

---

### Post by Leoorin on 2010-07-06
> **warfacegod said:**
> At this point, I vote for setting the damn thing on fire.
lmao!!:p 

> **Leppie said:**
> at the command prompt, issue this command:
```
[FONT=Arial][SIZE=2][FONT=Verdana]Bootrec /RebuildBcd[/FONT][/SIZE][/FONT]
```

nice!trying it and coming up with more...

---

### Post by Leppie on 2010-07-06
> **warfacegod said:**
> At this point, I vote for setting the damn thing on fire.
that's why i don't really use windows anymore... and whoever comes to me asking to fix their pc, will find ubuntu installed after i return their machines... :)

---

### Post by Leoorin on 2010-07-06
well nothing in particular changed..i get the same error message : "BOOTMGR IS MISSING"

when i tried it it said something for identified windows installations (it was zero)
and after that a line that operation was successful..

---

### Post by warfacegod on 2010-07-06
warface Industries: Divinity Division. Providing plucky comic relief since the dawn of humanity.

I saw in the bootscript output that Lilo was in the MBR. At one point you also had GRUB2. Did you install them both on purpose?

---

### Post by Leoorin on 2010-07-06
> **warfacegod said:**
> warface Industries: Divinity Division. Providing plucky comic relief since the dawn of humanity.

I saw in the bootscript output that Lilo was in the MBR. At one point you also had GRUB2. Did you install them both on purpose?

what do you mean?i don't get it at all:confused: i mean mbr should be fixed right now from what i tried till now..my only objective is removing grub i think..guess i am really messed up:p

---

### Post by warfacegod on 2010-07-06
```
Boot Info Script 0.55 dated February 15th, 2010

============================= Boot Info Summary: ==============================

=> Lilo is installed in the MBR of /dev/sda

sda1: __________________________________________________ _______________________

File system:
Boot sector type: Windows Vista/7
Boot sector info:
Mounting failed:
mount: unknown filesystem type ''

```

According to your bootscript, you had Lilo installed. I assume that it was next to GRUB2. Purely an academic question.

---

### Post by Leoorin on 2010-07-06
yeah what i actually did there was trying to restore mbr through live cd (as leppie proposed some posts before) through that command.. check that [link]("http://ubuntuforums.org/showthread.php?t=1195275")  @ #16..[:]("http://ubuntuforums.org/showthread.php?t=1195275")

> 
**Restoring Windows MBR without a Windows CD**
If you want to boot directly to Windows but Grub has overwritten the  MBR, the  normal procdeure is to use the Windows CD to restore things.  If you do not have access to the Windows CD, the following commands will  rewrite the MBR, removing Grub and allowing the system to boot directly  into Windows. 

Boot the Ubuntu LiveCD, open a terminal (Applications, Accessories,  Terminal) and enter the following commands. Make sure you correctly  identify the Windows device (normally *sda*):
     Code:
     sudo apt-get install lilo
sudo lilo -M /dev/sd**[COLOR=DarkRed]a[/COLOR]** mbr 

all that was done before i get today that recovery disk and try to repair windows start up..

---

### Post by warfacegod on 2010-07-06
Yes, I remember now. Has the Windows CD finished its thing?

---

### Post by Leppie on 2010-07-06
lilo isn't really installed in the mbr, but leaves a trace.

---

### Post by Leoorin on 2010-07-07
well i searched some more in google and found these commands also;

bootrec.exe /fixmbr
bootrec.exe /fixboot
bootrec.exe /scanos

here is the source[ link]("http://www.sevenforums.com/187758-post2.html") where also that ***/RebuildBcd** *command is noticed*.* 

tried all those above commands entering them in the command prompt and seems something changed..

When i boot now my pc the line; BOOTMGR IS MISSING is gone but now it won't boot showing nothing as an error.It just stops booting:P 

Did the problem mbr had is solved now?An other one is to be solved?what?#-o

---

### Post by Leppie on 2010-07-07
> **Leoorin said:**
> When i boot now my pc the line; BOOTMGR IS MISSING is gone but now it won't boot showing nothing as an error.It just stops booting:P 

Did the problem mbr had is solved now?An other one is to be solved?what?#-o
as i stated before, the BOOTMGR IS MISSING error is [COLOR=Red]***not a mbr error***[/COLOR] at all. ubuntu uses grub2 as the boot loader, bootmgr is the boot loader used in windows vista and 7.

in what order did you execute those commands?

---

### Post by Leoorin on 2010-07-07
i see..i somehow get it now how it works..

well first of all i executed yesterday the command /rebuildbcd as you told me but as i said nothing happened..

After that today i executed it in the following order;

bootrec.exe /fixmbr (it just said something about operation complete)
bootrec.exe /fixboot (it just said something about operation complete)
bootrec.exe /scanos [it actually gave me a log of all those 4 commands (fixmbr,fixboot,scanos and rebuildbcd) and a simple explanation of every command..]

After that i restarted my pc.I saw that the line BOOTMGR IS MISSING was missing.Then i tried again those commands but with this order: 

bootrec.exe /fixboot (it just said something about operation complete)
bootrec.exe /fixmbr (it just said something about operation complete)
 
Reboot after that and the problem was still there, with "bootmgr is missing" line to be missing but the pc would not be bootable.

---

### Post by Leppie on 2010-07-07
so basically the scanos option didn't do anything (other than displaying the possible switches)?

---

### Post by Leoorin on 2010-07-07
yup..

---

### Post by Leppie on 2010-07-07
try downloading the [Ultimate Boot CD]("http://www.ultimatebootcd.com/") and use one of the partition managers to check the windows partitions.

---

### Post by Leoorin on 2010-07-07
In the meantime i installed again in the empty filesystem of those 50gb ubuntu 9.10 and the rest are ntfs formatted now.tried to boot again with windows though grub but it's only a black screen that appears with a cursor and nothing more..

well at least i can now burn all the recovery cd i need and that as well at home and not wandering around searching for a dvd rw (as booting with a live cd and attempting to burn a cd at the same time with only one driver was pain in the ***:P)

coming up with more..

---

### Post by Leppie on 2010-07-07
what actually may be a good option is to use the win7 installation disk, if you have it.
it should provide you the option to repair a system.

---

