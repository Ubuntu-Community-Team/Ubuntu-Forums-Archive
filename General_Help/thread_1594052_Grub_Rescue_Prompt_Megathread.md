---
title: "Grub Rescue Prompt Megathread"
date: 2010-10-12
forum: General Help
---

### Post by drs305 on 2010-10-12
[COLOR=MAROON][B][SIZE=4][CENTER][I]The Grub Rescue Mode Megathread

[SIZE=3](*The Grub Rescue Hijack Thread*)[/SIZE][/I][/CENTER]
[/SIZE][/B][/COLOR]

**[COLOR=DarkRed][SIZE=3]What's with the Subtitle?[/SIZE][/COLOR]** 
Adding "Me Too" Posts just aren't proper etiquette. And who can think of an original title on this subject. So feel free to discuss your problem here, but read the rules first! Oh, and it's not "Grub 2" because Grub legacy doesn't *have* a 'grub rescue' prompt; if you see 'grub rescue>', you are using Grub 2.

**[COLOR=DarkRed][SIZE=3]Should I Be Here?[/SIZE][/COLOR] ** 
If you end up at a Grub rescue prompt while trying to boot to a normal installation, this thread may help. A 'grub rescue>' prompt means that Grub 2 has read the MBR but can't find the *grub* folder, specific files, and/or a usable *grub.cfg* file. If you see a 'grub' prompt, you have more capabilities such as TAB Complete and scrollback, but you can try the same procedures to restore Grub 2.

If you are using Wubi (Ubuntu within Windows), there is a specific section for Wubi users marked "Wubi Only". However, I would recommend you proceed to forum member *Rubi 1200's* guide for dealing with Wubi related problems: [*Wubi Megathread*]("http://ubuntuforums.org/showthread.php?t=1639198"). Wubi boot problem descriptions and the rememedies are well-documented on that site.


**[COLOR=DarkRed][SIZE=3]What Should I Try First?[/SIZE][/COLOR] ** 
If possible, obtain and boot an Ubuntu installation CD (LiveCD) or bootable USB. You can obtain the Live CD iso file from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download). Preferably use a CD of the same version you are trying to recover; if you don't have the same version, use a more recent release to get a later version of Grub 2. 

From the LiveCD Desktop, there are several things that you can do that will either fix Grub 2 problems or give you information that can help.
[LIST]
[*]Use Nautilus, GParted or Disk Utility to determine your Ubuntu partition. Disk checks can be accomplished with *Disk Utility* or *Gparted*, both accessed via the *System, Administration* menu.
[*]Mount your Ubuntu installation and attempt to edit your real installation's boot files.
[*]Run the boot info script by forum member *meierfra*.
[*]Access the forums and Internet for help.
[/LIST]
If you can get to the LiveCD, many Grub 2 problems can be solved by 1) reinstalling the bootloader or 2) purging/reinstalling Grub2. Purging and reinstalling has the advantage of repairing corrupted files and installing files manually deleted by the user. Nevertheless, the reinstall option should be attempted first.


[LIST]
[*]These methods are both detailed in the following thread: [HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099").
[/LIST]

**[COLOR=DarkRed][SIZE=3]I'm Still Stuck at the 'grub rescue>' Prompt[/SIZE][/COLOR]** 
[LIST=1]
If you are reading this, it should mean: 
[*]You haven't been able to fix things from the LiveCD.
[*]You can't boot to the Desktop (no CD, no CD-ROM, no bootable USB, no Internet)
[*]You couldn't get the HOWTO referenced in the previous section to work.
[*]You didn't read the previous stuff nor view the HOWTO linked above because you are the impatient type.
[/LIST]

[LIST]
[*]**OK, fine. Hijack this thread! Let us hear your pleas! But first, read:**
[/LIST]
 
**[COLOR=DarkRed][SIZE=3]Rules for Posting ! [/SIZE][/COLOR]** 
[LIST]
[*]Your first post if you need help must include the RESULTS.txt contents from *meierfra's* boot info script
[LIST]
[*]Go to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
[*]Follow the instructions on the site on how to download and execute the script.
[*]Start a new post. Press the **#** icon in the post's menu bar. This will generate [noparse]```
 
```[/noparse] tags. You may also manually type them. Paste the contents of RESULTS.txt between the 'code' tags.
[/LIST]
 
[*]Explain why the procedures below didn't work. Include error messages if possible.
[*]**Note to helpers:** Since there may well be multiple users with problems, be sure you identify to whom your post is directed via *brief* quotes or "@ forum-username".
[*]Since multiple users will be seeeking help, be specific - [COLOR=Red]No "It didn't work" posts. Be specific on what did or did not work![/COLOR]
[/LIST]

**[COLOR=DarkRed][SIZE=3]'grub rescue>' Boot Procedures  (About Time!)[/SIZE][/COLOR]** 
The short version - the commands you must run. Substitute the correct values for [COLOR="DarkRed"]X,Y[/COLOR].  If these commands fail or you want explanations, refer to the next entry - "Commands you may need to run"
```

set prefix=(hd[COLOR="DarkRed"]X,Y[/COLOR])/boot/grub [noparse]  [/noparse] # Example: (hd[COLOR="DarkRed"]0,1[/COLOR]) , (hd[COLOR="DarkRed"]1,5[/COLOR])
set root=(hd[COLOR="DarkRed"]X,Y[/COLOR])
insmod linux
linux /vmlinuz root=/dev/sd[COLOR="DarkRed"]XY[/COLOR] ro [noparse]    [/noparse] # Example: root=/dev/sd[COLOR="DarkRed"]a1[/COLOR] , /dev/sd[COLOR="DarkRed"]b5[/COLOR]
initrd /initrd.img
boot

```

**Commands you may need to run if the previous command set failed:**
Text in **bold black** are commands to be entered at the 'grub rescue>' prompt. If there is an *X,Y* component, substitute the correct value for your Ubuntu partition. Example:  (hdX,Y) >> (hd0,5); sdXY >> sda5

[LIST=1]
[*]**[COLOR=DarkRed]Locate the Ubuntu Partition.[/COLOR]**
[LIST]
[*]**ls**  -  This will display the known drives/partitions.
[*]Drives are designated (hd0), (hd1), etc. Partitions are designated (hd0,1), (hd0,2), (hd1,1), etc
[*]The Ubuntu partition will be one of the (hdX,Y) formatted returns.
[*]If all you get is (hd0) you most likely have a partition table or disk error. Seek assistance elsewhere! (fsck, e2fsck, TestDisk, etc.)
[/LIST]
 
[*]**[COLOR=DarkRed]Locate the *grub* folder.[/COLOR]**
[LIST]
[*]**ls (hd0,1)/boot/grub**  - Try each partition (hd0,1), etc. until you find your *grub* folder
[LIST]
If you don't find the */boot/grub* folder, start with a wider search and narrow the search once you find the Ubuntu folders:
[*]**ls (hdX,Y)/** # Look for the Ubuntu folders, such as *lost+found, /bin/, /boot, /home, *
[*]**ls (hdX,Y)/boot**  # Look for the *grub* folder.
[/LIST]
[*]The *grub* folder will contain dozens of *.mod files, as well as grub.cfg
[/LIST]
 
[*]**[COLOR=DarkRed]Set *prefix* and *root*.[/COLOR]**
[LIST]
[*]**set prefix=(hdX,Y)/boot/grub**
[*]Example:  set prefix=(hd0,5)/boot/grub
[*]**set root=(hdX,Y)**
[*]Example:  set root=(hd0,5)
[/LIST]
 
[*]**[COLOR=DarkRed]Confirm the *prefix* and *root* settings.[/COLOR]**
[LIST]
[*]**set**
[/LIST]
 
[*]**[COLOR=DarkRed]Load Modules.[/COLOR]**
[LIST]
[*]No modules can be loaded until the prefix is set correctly.
[*]An incorrect path or missing file will result in an "unknown command" or "file not found" error. Use the **set** and **ls /boot/grub** or **ls /boot** commands to verify the path and look for the specific file(s).
[*]If you receive an error, return to Step 3.
[*]**insmod linux** - if you get an 'unknown command' when entering the 'linux' command later, repeat using: **insmod /boot/grub/linux.mod**
[*]Additional modules such as normal.mod and help.mod may be loaded. Not all modules are available in *rescue mode*.
[/LIST]
 
[*]**[COLOR=DarkRed]Load the Kernel & Initrd image.[/COLOR]**
[LIST]
[*]**linux /vmlinuz root=/dev/sdXY ro**
[LIST]
[*]Substitute the correct values for X,Y - Example: sda5
[/LIST]
 
[*]**initrd /initrd.img**
[*]To load a specific kernel, especially an older kernel:
[LIST]
[*]**linux /boot/vmlinuz-<kernel version> root=/dev/sdXY ro**
[*]**initrd /boot/initrd.img-<kernel version>**
[*]Example:  linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5 ro
[*]Example:  initrd /boot/initrd-2.6.35-22-generic
[/LIST]
 
[/LIST]
 
[*]**[COLOR=DarkRed]Boot.[/COLOR]**
[LIST]
**boot**
[/LIST]
[/LIST]


**[COLOR=DarkRed][SIZE=3]Wubi Only.[/SIZE][/COLOR]**
Forum member *Rubi1200* has created an excellent site for dealing with Wubi related problems. You can continue with the instructions below but I would recommend you go to his forum guide, which deals specifically with Wubi:
[*Wubi Megathread*]("http://ubuntuforums.org/showthread.php?t=1639198")

The procedures below show the procedures from a normal Wubi Grub 2 prompt. In my testing, the modules were already loaded so a bad Wubi installation may react differently. However, by seeing what is *normal* for Wubi you may be able to also return it to a bootable state. 
[COLOR="DarkRed"]
Attention Wubi 9.10 Users.[/COLOR] You may need to copy a new version of the file "*wubildr*". Here is the link to forum member *meierfra's* guide on how to do that:
[Boot Problems:Wubi 9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

Booting from the Wubi Grub prompt requires different commands as the file locations are not the same as for a normal Ubuntu installation.
[LIST]
[*]The Wubi files are not on an Ubuntu partition. They are contained in a Windows partition within a Windows file: /ubuntu/disks/root.disk
[*] If you want to inspect your Wubi files from the Live CD (and possibly repair them or retrieve data):
[LIST]
[*]Determine the Windows partition (/dev/sd*XY*) Example: /dev/sd*a1*
[*]Make the mount points and mount Windows: **sudo mkdir /mnt/windows && sudo mount /dev/sd*XY* /mnt/windows**
[*]Make  the Wubi mount point and mount the Wubi file: **sudo mkdir /mnt/wubi  && sudo mount /mnt/windows/ubuntu/disks/root.disk /mnt/wubi**
[/LIST]
 
[*]At the grub prompt, the modules are not contained in the  */boot/grub* folder, but in the Wubi folder: *(loop0)/usr/lib/grub/i386-pc/*
[*]Review the procedures and explanations in the previous sections and refer to those sections for additional guidance.
[*]If you encounted an error, review the similar step above for possible solutions.
[*]With a 'grub>' prompt, TAB COMPLETION may be available.
[*]**Run the commands only from this section. Do not run the commands in previous sections.**
[/LIST]

The short version - the commands you must run. Substitute the correct values for [COLOR="DarkRed"]X,Y[/COLOR].  If these commands fail or you want explanations, refer to the next entry - "Commands you may need to run"
```

set root=(hd[COLOR="DarkRed"]X,Y[/COLOR]) [noparse]  [/noparse] # Example: (hd[COLOR="DarkRed"]0,1[/COLOR]) , (hd[COLOR="DarkRed"]1,5[/COLOR])
loopback (loop0) /ubuntu/disks/root.disk
set root=(loop0)[/B]
linux /vmlinuz root=/dev/sd[COLOR="DarkRed"]XY[/COLOR] loop=/ubuntu/disks/root.disk ro [noparse]  [/noparse] # Example: root=/dev/sd[COLOR="DarkRed"]a1[/COLOR] , /dev/sd[COLOR="DarkRed"]b5[/COLOR]
initrd /initrd.img
boot

```


**Commands you may need to run if the previous command set failed:**
[LIST=1]
[*]**[COLOR=DarkRed]Locate the Ubuntu Partition.[/COLOR]**
[LIST]
[*]**ls** - This will display the known drives/partitions.
[*]You should see (memdisk), (loop0), and your Windows partition (hdX,Y) or (hdX,msdosY)
[/LIST]

[*]**[COLOR=DarkRed]If there is no (loop0):[/COLOR]**
[LIST]
[*]**set root=(hdX,Y)** # X,Y is your Windows partition. Example: sda1: X=0, Y=1; sdb5: X=1, Y=5
[*]**loopback (loop0) /ubuntu/disks/root.disk**
[/LIST]
 
[*]**[COLOR=DarkRed]Locate grub.cfg.[/COLOR]**
[LIST]
[*]**ls (loop0)/boot/grub** - Only the *grub.cfg* & *grubenv* files may be present.
[*]No *.mod files will be present.
[/LIST]
 
[*]**[COLOR=DarkRed]Set prefix and root.[/COLOR]**
[LIST]
[*]**set prefix=(memdisk)/boot/grub**
[*]**set root=(loop0)**
[/LIST]
 
[*]**[COLOR=DarkRed]Confirm the prefix and root settings:[/COLOR]**
[LIST]
[*]**set**
[/LIST]
 
[*]**[COLOR=DarkRed]Load Modules.[/COLOR]**
[LIST]
[*]Some modules may already be loaded.
[*]No modules can be loaded until the prefix is set correctly.
[*]Available modules: ls (loop0)/usr/lib/grub/i386-pc/
[*]An incorrect path or missing file will result in an "unknown command" or "file not found" error.
[*]You can check the currently loaded modules with: **lsmod**
[LIST]
[*]If the output scrolls off the screen: **set pager=1**
[/LIST]
 
[*]**insmod (loop0)/usr/lib/grub/i386-pc/linux.mod**
[*]To load additional modules:
[LIST]
[*]**insmod (loop0)/usr/lib/grub/i386-pc/*<module.mod>***
[/LIST]
 
[/LIST]
 
[*]**[COLOR=DarkRed]Load the Kernel & Initrd image.[/COLOR]**
[LIST]
[*]**linux /vmlinuz root=/dev/sd*XY* loop=/ubuntu/disks/root.disk ro**
[LIST]
[*]* Substitute the correct values for *X,Y* - Example: sda5
[/LIST]
 
[*]**initrd /initrd.img**
[*]To load a specific kernel, especially an older kernel:
[LIST]
[*]**linux /boot/vmlinuz-<kernel version> /dev/sd*XY* ro** # TAB to complete the kernel version but don't forget the additional entries.
[*]**initrd /boot/initrd.img-*<kernel version>*** # TAB to complete the kernel version.
* Example: linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5 ro
* Example: initrd /boot/initrd-2.6.35-22-generic
[/LIST]
[*]**initrd /initrd.img**
[/LIST]
 
[*]**[COLOR=DarkRed]Boot.[/COLOR]**
[LIST]
**boot**
[/LIST]
[/LIST]

**[COLOR=DarkRed][SIZE=3]Selected Links.[/SIZE][/COLOR]**
[Grub 2 Community Doc - Rescue Mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")
[HOWTO: Purge & Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")
[Meierfra's Boot Info Script]("http://bootinfoscript.sourceforge.net/")

---

### Post by CarpKing on 2010-10-12
I encountered this problem after installing Maverick.  I attempted to boot to my LiveUSB to reinstall grub only to have the computer boot normally after I selected "USB" from the menu.  A few more tries determined that this was the only way to avoid the rescue prompt.  Apparently Grub somehow installed itself to my USB stick.  While booted up I did:

```
sudo grub-install --recheck /dev/<proper harddrive>
```

This fixed the issue, and now my computer boots as expected.  I think I'll have to remake that LiveUSB, though.

---

### Post by drs305 on 2010-10-12
Thanks CarpKing. 

In my [_chroot_]("http://ubuntuforums.org/showthread.php?t=1581099") thread I've added the '--recheck' switch. One of my concerns is that users will go straight to the commands in this thread rather than attempt to fix the issues by reinstalling Grub 2. Since your's is the first response it will reemphasize the point.

---

### Post by Quackers on 2010-10-12
Wow, a comprehensive cornucopia of commands for grub rescue :-) Just what the doctor ordered!

---

### Post by ELMIT on 2010-10-12
It keeps the original error (with step 5):

> grub rescue> insmod linux normal help
error: the symbol 'grub_puts_' not found

---

### Post by doris orange on 2010-10-13
I'm with ELMIT in that when i get to step 5, loading modules, i get the "error: the symbol 'grub_xputs' not found" business.  any insight is appreciated!

---

### Post by drs305 on 2010-10-13
The 'xputs' error is not one that I know the  procedure will work on - I was hoping it would. I've done a bunch of searching but haven't located a solution. I'll try the Grub IRC channel and see if the devs can provide any solutions.

In the bug reports, one user said he solved it by purging/reinstalling Grub2. There is a link to this procedure in the "What should I try first?" section. Please let me know if you tried this and it didn't work.

**Update:**
The 'xputs' error is the result of an incomplete installation of Grub2. One possible cause would be selecting a bad device on which to install Grub2. In any case, reinstalling Grub 2 should fix the problem. See "What Should I Try First".

From the developers: The xputs error can be caused by installing Grub2 on one device and then booting from another one. In this case, just switching the BIOS to boot from the original device should allow Grub2 to boot. Once booted, or after 'chrooting' from the LiveCD, the user should use "sudo dpkg-configure grub-pc" to place Grub on the second drive or all drives).

---

### Post by Bernardusaurus on 2010-10-14
Guys, I'm sorry if this is not good etiquette or whatever. But I'm completely new to this. I installed ubuntu 10.10 on my Windows 7 laptop. It went fine, and it's installed. But when I restart it, I get the boot error. Windows 7 isn't on my computer anymore and ubuntu won't load up, so I can't edit any files. Also, I burned the Super Grub Disk, but every option there is says the file isn't found. Help me out, please.   

What do?

(the reason I need help is because I don't understand all the terminology and processes you that are being discussed. :\)

---

### Post by drs305 on 2010-10-14
Bernardusaurus,

Welcome to the Ubuntu forums! We can help, but we need more information. Please boot from the LiveCD/install CD and go to the following site. Download the boot info script and run it from you computer. The instructions on how to get it to run are on the site. 
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

It will generate a file called RESULTS.txt. Double click on the file and it should open up. Copy the contents and paste them in a new post here. The script will show us your partition information and where the boot files are installed.

---

### Post by Bernardusaurus on 2010-10-14
Wow. Thank you for being so willing. I'll do that as soon as I get home. 

Thanks a lot.

---

### Post by Bernardusaurus on 2010-10-14
Alright drs305.

Here is the text I got from the RESULTS.txt:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2    *     20,973,568   254,683,135   233,709,568   7 HPFS/NTFS
/dev/sda3         254,683,136   488,394,751   233,711,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7E4EF6DE4EF68DE1                       ntfs       PQSERVICE                     
/dev/sda2        EC54DD9354DD60BE                       ntfs       OS                            
/dev/sda3        2850CADC50CAAFBC                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by drs305 on 2010-10-14
Bernardusaurus,

Looking at your RESULTS.txt - There isn't any Ubuntu installation detected on any of the partitions. Grub is installed in the Master Boot Record but it looks for the files in the first Windows partition. 

It doesn't see Ubuntu anywhere on the drive. Is it possible you installed it to another drive which is now disconnected?

For now, if you want, you can get your Windows booting again by booting to the Ubuntu LiveCD Desktop. Open a terminal via Applications, Accessories, Terminal. In the terminal, type:
```
sudo apt-get install lilo
```
It will ask for a password. Enter your password and press ENTER after you have typed it. You won't see the characters as you type.

It will give you some messages about fully installing lilo, but don't worry about that. Once it has installed, run this command. This will restore the MBR so you can boot Windows.

```
sudo lilo -M /dev/sda mbr
```
Reboot. You will lose grub but you should get your Windows menu back.

---

### Post by Bernardusaurus on 2010-10-14
What do I do once I get the Windows menu back?

---

### Post by drs305 on 2010-10-14
> **Bernardusaurus said:**
> What do I do once I get the Windows menu back?

If you don't have any other drives that Ubuntu could have been installed on, including USB drives, I suppose you would have to try to reinstall Ubuntu again. Do you remember having any problems with the installation? Grub was installed, which is why I suspected Ubuntu was installed on another drive which was not connected when you ran the boot info script.

If you have/had no other drives, I would recommend backing up your data and then shrinking your data (sda3) partition in Windows. Then create an extended partition, and within it create a logical partition for Ubuntu. It should end up as sda5. I would make it 10-15GB plus whatever space you would need for any data files you might want to save inside Ubuntu.

It would probably be best at this point to move the thread to a separate one of your own with a title related to your problem, such as "Ubuntu Installation Not Found" or something similar. I would be glad to do this if you want.

---

### Post by Bernardusaurus on 2010-10-14
You know what. I just realized that my 30g external harddrive that had ALL my music and ALL my pictures on it was the one that the computer defaulted to. So it's all there, but I'll just reinstall on the harddisk. I still have to do all that partition stuff when I just fresh reinstall it?

(Is there any way to get that stuff back? :\ )

---

### Post by drs305 on 2010-10-14
> **Bernardusaurus said:**
> You know what. I just realized that my 30g external harddrive that had ALL my music and ALL my pictures on it was the one that the computer defaulted to. So it's all there, but I'll just reinstall on the harddisk. I still have to do all that partition stuff when I just fresh reinstall it?

(Is there any way to get that stuff back? :\ )

I'm not a data recovery expert. If Ubuntu installed directly over your data files on the same partition I would guess there is very little chance of recovering the data. HOWEVER, if you have no backups of those files I would not write *anything* to that drive until you discuss this on the forum. The first thing to check is whether Ubuntu might have been installed on a separate partition from one or more of your data partitions.

With a fresh install on your main drive, if you choose to install Ubuntu side by side with Windows it should make space automatically from your Windows partition. Just be very cautious and confirm what Ubuntu wants to do before allowing it to change the existing partitions. If you allow Ubuntu to proceed as it wants, I believe it's going to look at the amount of free space on your sda3 partition and split it between Windows and the new (sda5) Ubuntu partition. It may or may not split it up the way you want. 

If you don't like it, exit the installation, backup your important data on the Windows partition, and shrink the partition on your own. I'd recommend doing it with a Windows partitioning program, but GParted can do it as well.

---

### Post by Bernardusaurus on 2010-10-14
So I can't just have ubuntu and not have Windows? I HAVE TO HAVE Windows? All my important stuff was on the 30g. So the rest doesn't matter to me.

---

### Post by drs305 on 2010-10-14
> **Bernardusaurus said:**
> So I can't just have ubuntu and not have Windows? I HAVE TO HAVE Windows? All my important stuff was on the 30g. So the rest doesn't matter to me.

No, absolutely you don't need Windows. If you want to get rid of all your Windows partitions you can tell Ubuntu to use the entire disk. I guess that is what you tried to do the first time.

Some people keep Windows installed just as a backup in case there is an app or game they want to play which won't run on Ubuntu. Grub2 can boot to both, so it's possible to keep your Windows install(s) if you wish - one, the other or both. But certainly if you want to wipe the entire drive that is easy enough to do.

As far as recovering your other drive, I'd make a thread and call it something like "Overwrote Data with Ubuntu Installation - Help!" or something similar. Perhaps someone can help out, but I think it will be a very difficult recovery effort. Perhaps Photorec can recover some or all of the files.

---

### Post by Bernardusaurus on 2010-10-14
You've been a great help, man. Thanks so much. If the grub thing happens again, it's cool to post here?

---

### Post by drs305 on 2010-10-14
> **Bernardusaurus said:**
> You've been a great help, man. Thanks so much. If the grub thing happens again, it's cool to post here?

Yes, but specifically for grub rescue prompt issues (grub not booting) or if it pertains to what we've already discussed.

The disadvantage of not creating your own thread is that the title may not be specific to your actual problem. Plus many readers may bypass by a thread that already has a lot of responses - the thinking being either the problem is being worked on or possibly is not solvable.

The Ubuntu forum readers are a very helpful bunch. Searching earlier posts is generally very productive but if you need help, don't hesitate to ask!

---

### Post by sendblink23 on 2010-10-16
I need help - by the way this ubuntu install is made from Wubi

I was upgrading my laptop that had 10.04 to 10.10... but while downloading the files the system froze & after turning it off then turning it back on... when I select ubuntu...   the next screen I see is:
grub>

Well I went here and read the area of Wubi...   here is the issue

I type in: ls
I get: (hd0) (hd0,2) (hd0,1)

I do not see at all what you wrote of:  (memdisk), (loop0),....

So I decide hmm let me try: ls (hd partitions that were detected)/boot/grub     
1. ls (hd0)/boot/grub
error: unknown filesystem

2. ls (hd0,2)/boot/grub
error: file not found.

3. ls (hd0,1)/boot/grub
error: file not found.

What the hell is going on here... did downloading the upgrade files kill my grub or ubuntu install?
Sorry I don't have a livecd or any spare blank cds, nore a usb to install a ubuntu on it to re-install(on this laptop)... in other words I'm stuck on this grub> screen or going into Windows 7 to try any fix

---

### Post by Quackers on 2010-10-16
Mr sendblink, I don't know anything about wubi, never having used it.  Buuuuuuut, isn't the command you want
ls (loop0)/boot/grub
or is that for something else?

---

### Post by drs305 on 2010-10-16
> **sendblink23 said:**
> I need help - by the way this ubuntu install is made from Wubi

What the h*** is going on here... did downloading the upgrade files kill my grub or ubuntu install?
Sorry I don't have a livecd or any spare blank cds, nore a usb to install a ubuntu on it to re-install(on this laptop)... in other words I'm stuck on this grub> screen or going into Windows 7 to try any fix

You can look at (hd0,1) and (hd0,2) and see what they contain:
```
ls (hd0,1)/
ls (hd0,2)/
```
If they don't contain your Ubuntu partitions, and I have no reason to think they will, then the only way I know to repair it is to get into another OS and mount the root.disk file so you can inspect and possibly repair it.

If you don't have data on the Ubuntu wubi installation, it's probably going to be faster to reinstall it that it will be to try to determine what has happened and how to fix it.  

If you do have data in your Ubuntu install, make sure you save the Windows file /ubuntu/disks/root.disk, which is your Ubuntu install.

I am about to leave for the night but will think on this and post back if I can think of something else you can do.

---

### Post by sendblink23 on 2010-10-16
> **Quackers said:**
> Mr sendblink, I don't know anything about wubi, never having used it.  Buuuuuuut, isn't the command you want
ls (loop0)/boot/grub
or is that for something else?

Quack quack! =P

If you read the thread... it says
> Locate the Ubuntu Partition.
ls - This will display the known drives/partitions.
You should see (memdisk), (loop0), and your Windows partition (hdX,Y)

As you can see, I wrote if I type: ls   I don't see those.. I only see: (hd0) (hd0,2) (hd0,1)     :(

And just to be sure I did try that command you mentioned & the other one for fun...
1. ls (loop0)/boot/grub
error: no such disk.

2. ls (memdisk)/boot/grub
error: no such disk.

:/ facepalm to my wubi hehehee


@ drs305.. just saw your reply.. I'll check those out.. and report back soon - to the last question.. yes I have allot of data in the ubuntu install

---

### Post by Quackers on 2010-10-16
:-) :-)
Ah, sadly my wish to assist is outweighed by my lack of knowledge :-(
And not for the first time :-)

---

### Post by sendblink23 on 2010-10-16
@ Quackers  =P no worries - its fun when things get messed up... we learn new things afterwards

Okay they both give allot of things(i honestly can't type them all)... but that i can notice reading...

ls (hd0,1)/
it has in it...  $Boot ...  Volume Boot/ bootmgr BOOTSECT.BAK grldr ..... some things like that

ls (hd0,2)/
it has in it.. $Boot  and more at the end...  System Volume Information/ temp/ ubuntu/ Windows/ wubildr wubildr.mbr

Just by looking at them it seems those 2 partitions are the Windows install partitions - the 1st one is what Windows 7 uses to boot(or recovery thing) & the 2nd one is the actual Windows 7 C: drive (in it it does mentioned Document and Settings/ Program Files/ ... etc)... but it does mention the Ubuntu folder & wubi in it

No clue what hd0 is (the one its calling - unknown filesystem)... I guess that is just calling my hard drive is on crack :P

Does that help?

---

I entered Win7 ... and inside that ubuntu folder... (C:/ubuntu/ 
:( I don't have anymore /disk folder - I think somehow it erased my root.disk when downloading the upgrade files.. it probably went crazy when it froze the system while on that process

I guess I'll forget about that install & data files.. and this time do a another wubi but instead just a straight up 10.10 install :P

---

### Post by drs305 on 2010-10-16
> **sendblink23 said:**
> 
No clue what hd0 is (the one its calling - unknown filesystem)... I guess that is just calling my hard drive is on crack :P

Does that help?

It doesn't help, but it does confirm. They are your Windows partitions, as suspected. (hd0) is just the first drive.

I am writing a guide for netbook users to be able to boot into the LiveCD from the rescue prompt, accessing the ISO on a thumb drive. I am going to experiment to see if it will allow doing the same from an ISO file placed in a Windows folder. This may be a way for you to at least recover your files.

I'm signing off but will check back tomorrow to see if you have made any progress. If my test succeeds I'll offer that as a test, and possible solution.

---

### Post by ThePsychoAxeman on 2010-10-17
> If all you get is (hd0) you most likely have a partition table or disk error. Seek assistance elsewhere! (fsck, e2fsck, TestDisk, etc.)

I got (hd0). What do I do now?

---

### Post by drs305 on 2010-10-17
> **ThePsychoAxeman said:**
> I got (hd0). What do I do now?

The reason I didn't address it in the body of the guide is that partitioning problems can be difficult to analyze. When Grub returns (hd0), it means it can't find the partitions. 

If you can boot to a LiveCD, you can use *Disk Utility* or *Gparted* from the System, Administration menu to see if these apps detect your partitions. 

From the command line, you can run *sudo fdisk -l* (lowercase L) to inspect the partition structure.

The *fsck* and *e2fsck* commands may resolve errors which can cause these issues. The only commands I will provide here which might solve your issue are the following. Substitute the correct [COLOR="Red"]X,Y[/COLOR] values for the partition in question. The partition must be unmounted, so only run the commands from the LiveCD or other system rescue CD.
```

sudo e2fsck -C0 -p -f -v /dev/sd[COLOR="Red"]XY[/COLOR]
*If it finds errors:*
sudo e2fsck -f -y -v /dev/sd[COLOR="Red"]XY[/COLOR] 

```

TestDisk is an excellent analytical app that can also repair partition table problems. More than likely you will need assistance to correct any partition problems that you find. The best course of action would be to start a new post and include any information you get from running the above items.

---

### Post by xfajardo on 2010-10-17
Hello, first off, by far this is the most well addressed thread regarding the Grub issue.

I've landed here because I too have an issue with the Grub, I too have tried all possible ways to fix this and so far I've not been successful at it.

I had a stable copy of Ubuntu 9.10 installed with the Wubi from Windows XP.
I then updated to the 10.04 release from the upgrade manager from inside Ubuntu, and like all I got the grub rescue > prompt after rebooting the machine.

I tried everything with the Live CD for Ubunto 9.10 but nothing really happened, then I tried all the stpes with the Ubuntu Live CD 10.04 and nothing happened.

Tried running the script inside the 10.04 CD but I coudn't even get my flash drive to mount. Tried it with the 9.10 live cd and I could get the script to run

I'm adding here my results from the boot info scripts here:

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd2a0fe15

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   191,767,904   191,767,842   7 HPFS/NTFS
/dev/sda2         191,767,905   312,576,704   120,808,800   5 Extended
/dev/sda5         191,767,968   312,576,704   120,808,737   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       cf19aa97-3b45-4686-9a14-a6a876f334b7   ext4                                     
/dev/ramzswap0                                          swap                                     
/dev/sda1        1C189857189831AE                       ntfs                                     
/dev/sda5        12CA5D0422703041                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/1C189857189831AE  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

======================== sda5/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ntfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 12ca5d0422703041
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ntfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 12ca5d0422703041
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=es
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
	insmod ntfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 12ca5d0422703041
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 12ca5d0422703041
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
	insmod ntfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 12ca5d0422703041
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 12ca5d0422703041
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 1c189857189831ae
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sda5/Wubi: Location of files loaded by Grub: =================


   4.0GB: boot/grub/core.img
   4.7GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.31-14-generic
   1.0GB: boot/initrd.img-2.6.32-25-generic
   2.5GB: boot/vmlinuz-2.6.31-14-generic
   1.6GB: boot/vmlinuz-2.6.32-25-generic
   1.0GB: initrd.img
   1.0GB: initrd.img.old
   1.6GB: vmlinuz
   2.5GB: vmlinuz.old 
```

---

### Post by drs305 on 2010-10-17
xfajardo,

Welcome to the Ubuntu forums. :-)

I am not sure about the partition designations found by the boot info script. I don't have a lot of experience with Wubi.  I do note that several of the Wubi boot files are at or beyond 4GB into the disk. There was a problem in 9.10 where wubi failed if it's files were further into the disk than that. The remedy was to replace the Windows file "wubildr".

Fortunately, you replace the file from within Windows. Here is the link on how to fix that problem. It was written by forum member *meierfra* and is something you might try.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

If that isn't the problem:
You are left at the "rescue" prompt?

Do you have important data files in the Wubi install and have you tried to access them by mounting Windows and then root.disk?

If you were running the commands from the "Wubi Only" section, at what point did they fail?

Often reinstalling wubi is far easier than trying to repair it. Wubi is not as 'robust' as a normal installation. Although it is not designed to fail, as you can see it can be more difficult to repair when it does.

Try the "wubildr" solution and consider the questions I've asked. Let us know how you get on.

---

### Post by xfajardo on 2010-10-17
Well, the problem is I can't boot into Windows either, I don't have a bood CD, since it's a really old PC and I'm not even sure it even had a CD, prolly just got installed by someone with a pirated version.

Of the problems mentioned in the sourceforge article, I encountered two of them:
"The booting problems come in many different forms:
The Grub menu does not appear at boot up. Instead you get a "grub:rescue>" or "grub:sh>" prompt
-----
The Grub menu appears, but trying to boot Wubi results in "file not found"."

I can access the the main drive and it's windows directories if I mount them via the LIve CD. Should I try and drop the new wubilder file through there?

---

### Post by xfajardo on 2010-10-17
> **drs305 said:**
> 

Do you have important data files in the Wubi install and have you tried to access them by mounting Windows and then root.disk?

If you were running the commands from the "Wubi Only" section, at what point did they fail?



Ok, so, I tried to change the wubildr file throught the Live CD interface, but it yeilded no new results.

I don't have any information on the Wubi partition, sin I never really had a chance to get to know it that much, because the upgrade manager asked me if I wanted to install the new 10.04 release and I said yes. So I don't care if it gets lost, my only concern is for my Windows partition data. 

I would very much like to erase all of the Ubuntu failed partition at this point, and maybe try again in another computer sometime in the future. I did like Ubuntu quite a lot actually, but the install was for my sister on her PC, and she is pretty pissed of at me right now.

I'm not sure what you mean when you ask if I'd tried to mount Windows and root to disk or the "Wubi Only" commands.

---

### Post by drs305 on 2010-10-17
> **xfajardo said:**
> The Grub menu appears, but trying to boot Wubi results in "file not found"."

I can access the the main drive and it's windows directories if I mount them via the LIve CD. Should I try and drop the new wubilder file through there?

Yes, you should be able to just copy the file into the correct folder. From what I remember, there is no command to run. If that was the problem, Ubuntu should just boot the next time it is selected.

You also say you can't boot into Windows, so you have more than just Grub problems since the Ubuntu file comes *after* the Windows bootloader.

Did you intentionally or unintentionally try to install Ubuntu into a normal partition? 

However, I'm not a Windows expert so I'll stop asking Windows questions. ;-)


If updating the wubildr file doesn't work, if you can mount root.disk you should be able to recover any files you want to save before you reinstall (either Wubi or Windows & Wubi).

---

### Post by ThePsychoAxeman on 2010-10-18
Thanks, but my CD drive isn't working. Can you link me to a Live USb download thingy? 
I can't find one on the internet. :(

---

### Post by drs305 on 2010-10-18
> **ThePsychoAxeman said:**
> Thanks, but my CD drive isn't working. Can you link me to a Live USb download thingy? 
I can't find one on the internet. :(

I just wrote a guide this weekend for booting from the grub rescue prompt if you have a previous installation that went bad. I also detailed how you can do an install from the prompt if you have a current ISO. 

At the moment, I'm testing a network install and should have those instructions in the guide as well by the end of the day if I don't get called out to work.

[ HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")

I don't have a link to the LiveUSB but it should be easy to find.

---

### Post by drs305 on 2010-10-19
> **xfajardo said:**
> 
I'm not sure what you mean when you ask if I'd tried to mount Windows and root to disk or the "Wubi Only" commands.

Sorry the wubildr file didn't solve things. What I meant about mounting Windows and "Wubi only" was that there was a section of the guide that applies only to Wubi installs. If you had tried to use the other section it wouldn't work.

If it isnt' out yet, you might want to try the 10.10 version of Wubi. Hopefully some of the issues in Wubi will be resolved. I've always been more comfortable with a real Ubuntu installation but understand why people would like to try it within Windows first - if it works!

---

### Post by pgoffa01 on 2010-10-20
Hey everyone.  I'm a long time mint user and a few days ago, I converted with the release of 10.10. I had everything working great for three days. Then I test drove the new Peppermint and loved that as well. I installed peppermint to a flashdrive, played with it a couple of times and everything was great. Tonight, I fired up peppermint, showed my wife how cool it was etc etc. Then I shut down, removed the flash and restarted to boot buntu. To my horror, I got the device not found, grub rescue prompt. I see this is becoming a big problem but the scenarios are different.

I'm single booting Ubuntu 10.10. No wubi. Normal installation. 

Now, I'm not a total noobie, I used peppermint usb to boot ubuntu. Once it was running I unmounted flash and did a grub update. No luck. My opinion, grub updated the mbr for some reason, when peppermint was running and now its half on the thumb and half on the hdd.

Thanks,
Paul

---

### Post by Quackers on 2010-10-20
Please go to the site below and download the boot script to your desktop then, in the terminal, run the command given . This will create a Results.txt file on your desktop. Please copy the contents of this file and then click on New Reply and then on the # symbol in the toolbar. This creates code tags for you to paste your file in between them.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by drs305 on 2010-10-20
pgoffa01,

Run the boot script with the flash drive attached. You will probably find that Grub points to the flash drive (look at the first few lines of the RESULTS.txt). Updating grub won't change where the system boots. 

If you can boot into your Ubuntu on the hard drive, even if you need to have the flash drive inserted:
```
sudo grub-install /dev/sd[COLOR="Red"]X[/COLOR]
```

This will make sure your hard drive's MBR points to the Grub files in your normal Ubuntu installation and you should be able to boot without the flash drive connected.

If you have to boot from a LiveCD:
```
sudo mount /dev/sd[COLOR="Red"]XY[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/sd[COLOR="Red"]a[/COLOR]
```
Specify the partition in the first command, but only the drive in the second. Replace the [COLOR="Red"]X,Y[/COLOR] values to match your system.

---

### Post by pgoffa01 on 2010-10-20
```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Peppermint
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    74,864,639    74,862,592  83 Linux
/dev/sda2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sda5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    78,161,919    78,159,872   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8032 MB, 8032092160 bytes
99 heads, 18 sectors/track, 8803 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048    15,685,631    15,683,584  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2dc4cc19-1e29-472e-8219-58d6b5d2d5bd   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D2F065E0F065CAF5                       ntfs       New Volume                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        a0cb7669-8218-432d-adeb-f0254cbcf051   ext4                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/a0cb7669-8218-432d-adeb-f0254cbcf051 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2dc4cc19-1e29-472e-8219-58d6b5d2d5bd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2dc4cc19-1e29-472e-8219-58d6b5d2d5bd

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        2dc4cc19-1e29-472e-8219-58d6b5d2d5bd
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=2dc4cc19-1e29-472e-8219-58d6b5d2d5bd ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        2dc4cc19-1e29-472e-8219-58d6b5d2d5bd
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=2dc4cc19-1e29-472e-8219-58d6b5d2d5bd ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        2dc4cc19-1e29-472e-8219-58d6b5d2d5bd
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        2dc4cc19-1e29-472e-8219-58d6b5d2d5bd
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 2dc4cc19-1e29-472e-8219-58d6b5d2d5bd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 2dc4cc19-1e29-472e-8219-58d6b5d2d5bd
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2dc4cc19-1e29-472e-8219-58d6b5d2d5bd
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=2dc4cc19-1e29-472e-8219-58d6b5d2d5bd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2dc4cc19-1e29-472e-8219-58d6b5d2d5bd
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=2dc4cc19-1e29-472e-8219-58d6b5d2d5bd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2dc4cc19-1e29-472e-8219-58d6b5d2d5bd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2dc4cc19-1e29-472e-8219-58d6b5d2d5bd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c8d274c7-78d1-4f24-b844-708b0607cde4 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  23.7GB: boot/grub/core.img
   4.5GB: boot/grub/grub.cfg
  23.8GB: boot/grub/menu.lst
   2.1GB: boot/initrd.img-2.6.35-22-generic
  23.8GB: boot/vmlinuz-2.6.35-22-generic
   2.1GB: initrd.img
  23.8GB: vmlinuz

=========================== sdc1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd2,1)'
search --no-floppy --fs-uuid --set a0cb7669-8218-432d-adeb-f0254cbcf051
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd2,1)'
search --no-floppy --fs-uuid --set a0cb7669-8218-432d-adeb-f0254cbcf051
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Peppermint, 2.6.32-24-generic (/dev/sdg1)" --class peppermint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a0cb7669-8218-432d-adeb-f0254cbcf051
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a0cb7669-8218-432d-adeb-f0254cbcf051 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry "Peppermint, 2.6.32-24-generic (/dev/sdg1) -- recovery mode" --class peppermint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a0cb7669-8218-432d-adeb-f0254cbcf051
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a0cb7669-8218-432d-adeb-f0254cbcf051 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a0cb7669-8218-432d-adeb-f0254cbcf051
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a0cb7669-8218-432d-adeb-f0254cbcf051
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2dc4cc19-1e29-472e-8219-58d6b5d2d5bd
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=2dc4cc19-1e29-472e-8219-58d6b5d2d5bd ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2dc4cc19-1e29-472e-8219-58d6b5d2d5bd
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=2dc4cc19-1e29-472e-8219-58d6b5d2d5bd ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdg1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=c8d274c7-78d1-4f24-b844-708b0607cde4 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

=================== sdc1: Location of files loaded by Grub: ===================


   4.6GB: boot/grub/core.img
   4.6GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.32-24-generic
   4.6GB: boot/vmlinuz-2.6.32-24-generic
    .6GB: initrd.img
    .1GB: initrd.lz
   4.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  35 a6 e6 75 ab 08 4d e1  d2 33 f7 60 43 3a e0 61  |5..u..M..3.`C:.a|
00000010  bb 4f 1d 3d 87 fb c4 c6  3a f5 83 60 47 10 82 4d  |.O.=....:..`G..M|
00000020  41 ed 97 c9 ba 55 ca 6e  9e 73 fc 3e 05 cf aa a4  |A....U.n.s.>....|
00000030  ba 79 8c e1 07 4e 1d 50  24 20 2b 36 fc b3 77 dc  |.y...N.P$ +6..w.|
00000040  7c 61 31 8e ac 2f b7 cb  ad 65 d0 43 a0 c6 6e 78  ||a1../...e.C..nx|
00000050  b8 e6 87 9e b0 7d c7 95  c8 9e ae 20 1a 03 4f 06  |.....}..... ..O.|
00000060  01 58 42 cb 01 84 cc 27  93 b4 67 85 c0 39 43 1c  |.XB....'..g..9C.|
00000070  1f c7 4e a4 66 94 4b 4f  7c 6f 01 2e 91 50 b1 3b  |..N.f.KO|o...P.;|
00000080  72 06 d4 b5 16 ec da 0a  74 ae ce b0 de a9 08 ed  |r.......t.......|
00000090  7b ba 00 a0 64 2c 2a 34  ff 96 ee cd 23 73 e6 11  |{...d,*4....#s..|
000000a0  3f 3b be c7 28 33 04 57  3a e3 cd 3a cd 62 b5 1a  |?;..(3.W:..:.b..|
000000b0  fd c9 53 3c cc 9e e2 92  fa 52 ad 57 bc 4e 3b 2b  |..S<.....R.W.N;+|
000000c0  27 ea 5d 61 f6 35 36 55  1e a8 03 e0 5f a0 24 7c  |'.]a.56U...._.$||
000000d0  3a 9e 2b a9 b1 ec 76 c1  dc b0 4b db a9 43 9a 9d  |:.+...v...K..C..|
000000e0  4e c4 07 69 12 96 4b b5  f2 89 91 af 43 14 67 be  |N..i..K.....C.g.|
000000f0  39 b8 7d db db 2d 88 bf  0b 91 b0 ba cc 17 ea 4a  |9.}..-.........J|
00000100  bc 7f 43 a1 ef cd e6 04  08 13 f6 be 41 92 7d fa  |..C.........A.}.|
00000110  cb e0 ad 42 8a 5f b0 9d  e1 91 07 4f 32 1e 10 27  |...B._.....O2..'|
00000120  5a 23 1d f7 ec 84 80 52  2d 1e 51 5d 89 72 4a 6c  |Z#.....R-.Q].rJl|
00000130  a7 ee 1a 65 f2 fb 9e bd  92 39 27 4f 9e c8 67 20  |...e.....9'O..g |
00000140  a6 11 1f 9c f8 49 34 eb  6e f8 53 c1 72 f9 47 56  |.....I4.n.S.r.GV|
00000150  03 7d 64 b8 5c 23 9e f9  33 db 99 26 9d b5 05 1c  |.}d.\#..3..&....|
00000160  bf ea 56 5e 5c 37 21 ae  ef 72 cd f4 79 7c df 51  |..V^\7!..r..y|.Q|
00000170  b2 63 6b c5 35 d1 2d 4d  00 1e ee 5b b8 2a 49 97  |.ck.5.-M...[.*I.|
00000180  5f 7b 3d 01 db 69 26 3e  5d e7 5b 73 4f 6a b4 b2  |_{=..i&>].[sOj..|
00000190  a5 03 ec 56 a2 c0 6c 5e  e8 7a 8c 8f 35 e1 43 dc  |...V..l^.z..5.C.|
000001a0  f1 d8 3b 26 0f d8 6d 1f  80 27 0c b9 2c 10 bd d7  |..;&..m..'..,...|
000001b0  f8 9a 6e 82 c1 cd d4 e2  75 15 be af 94 0f 00 fe  |..n.....u.......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 50 32 00 00 00  |...........P2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg

```

---

### Post by drs305 on 2010-10-20
pgoffa01,

Thank you for posting the boot info. 

I've moved your posts and the replies here since the thread you were posting to belonged to someone else. This thread concerns the "rescue prompt" and I don't mind who 'hijacks' it.  ;-)

I see no major problems with your setup. Have you tried running the commands I suggested from a LiveCD?
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

If not, try running them and reboot.

If you still get the grub rescue prompt, review the first post in this thread and see if you can boot following the described procedure.

---

### Post by pgoffa01 on 2010-10-20
Can it be any live cd or does it need to be Ubuntu again?  I burned over the cd because i thought it seemed stable lol

---

### Post by drs305 on 2010-10-20
> **pgoffa01 said:**
> Can it be any live cd or does it need to be Ubuntu again?  I burned over the cd because i thought it seemed stable lol

Well, since it's not working anyway ...   ;-)

I am guessing you want to use the Peppermint CD? And that is an offshoot of Mint, which is similar to Ubuntu. That one I would guess would be acceptable although I can't guarantee it. There is a specific Ubuntu version of Grub2 (grub-pc 1.98 5ubuntu3) so you can check to see if that is what will be installed.

In the LiveCD, open Synaptic or the equivalent and check the version of the available grub-pc package.

---

### Post by pgoffa01 on 2010-10-20
ok, now im really confused.  I booted with the cd, and ran the command that you told me.  here is my output.

```
peppermint@peppermint ~ $ sudo mount /dev/sda1 /mnt
peppermint@peppermint ~ $ sudo grub-install --root-directory=/mnt /dev/sda1
error: cannot open `/dev/sdc' while attempting to get disk size.
error: cannot open `/dev/sdc' while attempting to get disk size.
error: cannot open `/dev/sdc' while attempting to get disk size.
error: cannot open `/dev/sdc' while attempting to get disk size.
error: cannot open `/dev/sdc' while attempting to get disk size.
error: cannot open `/dev/sdc' while attempting to get disk size.
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
peppermint@peppermint ~ $ 
 
```

what that looks like is that this command will first look for a grub conf file, saw that sdc held the MBR for the whole system somehow, and wants to know why my mbr is missing and i want a bootloader on a different primary part.  right?  lol...i am in college for this stuff.  So how do i make sdc1 a distant memory?

---

### Post by drs305 on 2010-10-20
pgoffa01,

You are running the command incorrectly, adding a number to the end of the drive designation. You mount the partition but you install to the drive (only):
Not:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda**[COLOR="Red"]1[/COLOR]**
```

But:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by pgoffa01 on 2010-10-20
Also, Peppermints Grub is PC1.98 5-1UbuntuMint2 so yeah, can i do a sudo apt get ..... from the ubuntu deck or should i just download the .iso again?

---

### Post by pgoffa01 on 2010-10-20
So Linux wants the bootloader on a drive and not a primary system partition?  Weird

---

### Post by drs305 on 2010-10-20
> **pgoffa01 said:**
> Also, Peppermints Grub is PC1.98 5-1UbuntuMint2 so yeah, can i do a sudo apt get ..... from the ubuntu deck or should i just download the .iso again?

I'd try it. It's not exactly the same but it might work. I don't know what the Mint customizations are. If so, good. If not, you'll have to burn the CD in either case so nothing lost.

---

### Post by pgoffa01 on 2010-10-20
Alright, I rebooted live just so I could get a fresh start

I entered this 
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```I then recieved
```
 ______________________________________
( Tell the truth or trump--but get the )
( trick.                               )
(                                      )
( -- Mark Twain, "Pudd'nhead Wilson's  )
( Calendar"                            )
 --------------------------------------
  o
   o   \_\_    _/_/
    o      \__/
           (oo)\_______
           (__)\       )\/\
               ||----w |
               ||     ||
peppermint@peppermint ~ $ sudo grub-install --root-directory=/mnt /dev/sda
error: cannot open `/dev/sdc' while attempting to get disk size.
error: cannot open `/dev/sdc' while attempting to get disk size.
error: cannot open `/dev/sdc' while attempting to get disk size.
error: cannot open `/dev/sdc' while attempting to get disk size.
error: cannot open `/dev/sdc' while attempting to get disk size.
error: cannot open `/dev/sdc' while attempting to get disk size.
Installation finished. No error reported.
peppermint@peppermint ~ $ 


```:(

is there a way to remove grub from the buntu partition and do like a fresh grub install?  Or since im live, can I erase the grub.conf file and make it rebuild itself?

---

### Post by drs305 on 2010-10-20
> **pgoffa01 said:**
> 
is there a way to remove grub from the buntu partition and do like a fresh grub install?  Or since im live, can I erase the grub.conf file and make it rebuild itself?

I wrote this guide to do just that (but again using the strict Ubuntu version of Grub - so no cute terminal art):
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by pgoffa01 on 2010-10-20
Well we did it.  I used your guide, pulled the crippled grub off through peppermint live, reinstalled the grub (somehow it automatically grabbed it from ubuntu and not peppermint) and it rebooted just fine.  Thank you sir, and thanks Peppermint lol :P

Maybe some day, I can help people on here too!

---

### Post by drs305 on 2010-10-20
> **pgoffa01 said:**
> Well we did it.  I used your guide, pulled the crippled grub off through peppermint live, reinstalled the grub (somehow it automatically grabbed it from ubuntu and not peppermint) and it rebooted just fine.  Thank you sir, and thanks Peppermint lol :P


:-)

When you were able to chroot into your real Ubuntu install and did the apt-get update and grub install, it was using the online repositories for Ubuntu, so it grabbed the Ubuntu version of Grub. At the time we discussed it earlier I wasn't considering the chroot option...

> Maybe some day, I can help people on here too!

We all started somewhere, and the forums are a great place to learn as well as help.

---

### Post by didkaticos on 2010-10-20
[B] GNU GRUB version 1.97 (Today's update screwed my Wubi)

[/B]I am using Wubi with Ubuntu 9.10 the Karmic Koala. This morning I found some updates (please, don't ask me which ones because I don't remember). Anyhow, I updated, shut down, and went to work. Now that I am coming back, my Ubuntu doesn't want to start. When I choose Ubuntu, it makes a long beep, and then I got the following screen:
 	Code:
 	GNU GRUB version 1.97
[ Minimal BASH-like line editing is supported. For the first word, TAB
lists possible command completions. Anywhere else TAB lists possible
device/file completions. ]

sh:grub> 
I got a CD-BOT, that's why I was able to get to the forums.

What do I need to do to get my Ubuntu back? Please notice that I am a complete illiterate about Linux - Ubuntu :sad:.

Thanks a lot for your help!
[B][B]
OK, here I am, a complete newby trying to fix my issue. I ran the Boot Info, and I got this:

[/B][/B]```
   	 	 	 	 	 	                  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe621e621

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,420,479   234,420,417   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       e2b6ccfd-4689-42d9-b065-ffc71baae2da   ext4                                     
/dev/sda1        A0947B03947ADAEC                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

======================== sda1/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="2"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a0947b03947adaec
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a0947b03947adaec
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a0947b03947adaec
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a0947b03947adaec
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a0947b03947adaec
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a0947b03947adaec
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a0947b03947adaec
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


   6.7GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.31-14-generic
   3.4GB: boot/initrd.img-2.6.31-21-generic
   7.4GB: boot/initrd.img-2.6.31-22-generic
   2.1GB: boot/vmlinuz-2.6.31-14-generic
   3.0GB: boot/vmlinuz-2.6.31-21-generic
   4.0GB: boot/vmlinuz-2.6.31-22-generic
   7.4GB: initrd.img
   3.4GB: initrd.img.old
   4.0GB: vmlinuz
   3.0GB: vmlinuz.old

```
[B][B]
Do you think that you could help me? Thanks drs305!
[/B][/B]

---

### Post by drs305 on 2010-10-20
didkaticos,
 

**[COLOR="DarkRed"]Added:[/COLOR]** I see you are using an older release - 9.10. You may need to copy a new version of the file "*wubildr*". Here is the link on how to do that:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

I can try to help, but there are many others that may be able to help you as well. Don't limit yourself!  ;-)

Edit: It appears you may be missing  the grub core.img file. This file is normally created by the "grub-install" command. I don't use Wubi much so I'm still learning about it and don't know for sure if it should be in the Windows folder.

Try to use the "Wubi Only" section of the first post. Enter the commands in that section and hopefully you will be able to boot. It may be just a problem with the *prefix* or *root* setting and you will reset both of those as you complete the steps. 

If you have any questions or problems as you accomplish the steps post back here.

---

### Post by didkaticos on 2010-10-20
Thanks a lot for your help drs305, but the suggestions that you are giving me are beyond my comprehension: let's face it: there are people like me that doesn't know anything! (besides my bad English).

When I looked the link that you gave to me it says:

***Boot into Windows** and click on the following link to download the file "wubildr": *
*[wubildr]("http://launchpadlibrarian.net/36920146/wubildr")* (Highlighted is mine).

The problem is that if I go to Windows I don't have Internet connection. The reason: I don't know why. I was happy with my Ubuntu, then I stopped using Windows. One day I went there and I couldn't find a way to get Internet connection. Who cared: I wasn't using Windows at all, so I switched completely to Ubuntu (or at least I thought that I had done that when the truth is that I need Windows to run my Wubi). So, I wouldn't been able to fix the *wubildr* issue.

As I said, I am a newbie. Your instructions in the first post look like Greek to me. So, I think it is my fault for making an update that (maybe) I didn't need it since my PC was working perfectly.

I am sorry, but I am really frustrated. I have been having issues since I had made some updates that I cannot understand why I am having this problems. Just take a look at this thread four weeks ago: [http://ubuntuforums.org/showthread.php?t=1577699](http://ubuntuforums.org/showthread.php?t=1577699)

Thanks a lot again, but I just give up!

Good luck!

---

### Post by drs305 on 2010-10-20
didkaticos,

Here is the file. I had to compress it to get it attached (forum rules).

I understand the instructions can be difficult - even for English majors.

Try the wubildr file if you can. 

If you take each of the commands one by one I think you could get through all the instructions, but I understand why you would prefer not to.

If there are data files on your wubi install that you need to retrieve we can get them back if you wish. If you don't have any data, reinstalling is often easier than following all these complicated instructions.  :-)

Please let me know if I can help in some other way.

---

### Post by didkaticos on 2010-10-21
OK, today is a new day, and I am ready again to see if I can fix this thing. Thanks a lot for your patience drs305 and I apologize for my outburst last night.

I already replace the wubildr on C:drive. Thanks for bringing it here.

I need to leave to work soon, but I would like to start fixing my wubi as soon as I get back tonight. I have a question that, I know, is a stupid question: where do I need to enter the instructions in post #1? In the terminal? As you can see, I may need more detail instructions that the rest of people.

Thanks a lot again, and I will see you later!

---

### Post by drs305 on 2010-10-21
> **didkaticos said:**
> where do I need to enter the instructions in post #1? In the terminal? 

Copying the wublildr file would be inside a running Windows OS, but otherwise all of the commands assume that the Wubi boot fails and you are at the "grub>" or "grub rescue>" prompt. You would follow the instructions in the "Wubi Only" section.

Once again, the alternative to trying to run these procedures is to just reinstall Wubi. This is the best option if 1) you haven't done a lot of customization to Wubi and 2) you don't have data files on your Wubi install that you need.

---

### Post by didkaticos on 2010-10-21
Replacing the ***wubildr*** on C:drive fixed all my problems: my regular Wubi is back :P!

Thanks a lot for your help drs305! It was easier than I thought!

---

### Post by beharder on 2010-10-21
Hi all,

I'm trying to install Ubuntu 10.10 as Dualboot with Win XP and even though I've tried about half a dozen reinstallations using different formatting options I keep getting the "unknown filesystem" error and the grub rescue prompt. I have also worked myself through the "Purge and reinstall grub" thread and followed all instructions but this didn't have the desired result either.

Some days ago I have opened a thread for my problem here 

[http://ubuntuforums.org/showthread.php?t=1599222](http://ubuntuforums.org/showthread.php?t=1599222)

and some experienced users have already very generously offered me their help, but until now we still couldn't fix the problem.

I'm not sure if it's a good idea to repost all the details here in this thread, I think generally it's rather confusing when a problem is discussed in several threads simultaneously, so may I kindly ask you guys to take a look at my thread and give me some help? I have also posted the results.txt there.

thx

---

### Post by drs305 on 2010-10-21
@ beharder,

Since you have tried installing several times and also mention it is an old system my guess is that it is a BIOS limitation that is not picking up the location of the Grub files. Newer BIOS's have settings that allow the user to switch to be compatible with larger drives. I think the older ones don't have the capability and the newer ones are set to do it automatically.

You might do some research on your specific motherboard/BIOS to see if there are any disk size limitations.

> 
I'm not sure if it's a good idea to repost all the details here in this thread, I think generally it's rather confusing when a problem is discussed in several threads simultaneously, so may I kindly ask you guys to take a look at my thread and give me some help? I have also posted the results.txt there.


That was very considerate of you. One of the reasons I created the megathread was because many users were just jumping onto someone else's thread. I figured if hijacking was necessary, at least we could try to contain it here.  ;-)  Ideally a user needing assistance would create their own thread, refer to this one, and then post questions or information in their own thread.

Since your situation was something that I haven't yet covered in the original post I wanted to mention it here just to get the hard drive size issue into the thread.

---

### Post by beharder on 2010-10-24
Hi drs305,

thanks a lot for your help, yes, it was really the old 137GB limit plus the fact my mainboard doesn't support formatting according to MiB, but only according to cylinders. This is a short summary of what finally worked that I have already posted in my own thread:

> **beharder said:**
> 
I deleted the partitions one more time, shrunk the sda1 (Windows XP  drive C), inserted a 300MB boot partition between sda1 and sda2 (sda2 = Windows drive D, containing my data). Then I  created an extended partition containing two logical partitions for swap  and /. Then I reinstalled Ubuntu 10.10 one more time. And now  everything works fine!  

At first when I tried to shrink sda1 with gparted I forgot to use the  alignment=cylinder option and the process ended with an error message.  From then on I used this option for every partition I changed or created  and everything worked fine. So obviously my problems have been caused  by both, the old mainboard not supporting the formatting according to  MiB, and the old 137GB-limit for the boot-Partition.


These problems occurred on an Acer Travelmate 2350 I bought in 2005. If anybody having similar problems needs more specific information, e.g. instructions on how to change the kernel boot parameters such that gparted allows you to format a partition according to cylinders, please take a look at my thread:

[http://ubuntuforums.org/showthread.php?t=1599222](http://ubuntuforums.org/showthread.php?t=1599222)

bye

---

### Post by drs305 on 2010-10-24
beharder,

Thanks for update. One more thing to put into our bag of knowledge / tricks.

Happy Ubuntu-ing!

---

### Post by salviablue on 2010-10-27
So I take it then that there is no way of fixing this without a computer with internet access if your live cd has been used as a frisbee by the kids and they disappeared your live usb stick too? 
Also this issue occurred for me after having to disassemble the laptop due to a minor liquid spill knockout the touchpad. After reassembly, all was fine, except I'd forgotten to screw in the hdd cover. A few days later when thee wife picked the lappy up, the drive half fell out.
When I ls (hd0,1) I get the folders showing, however if I try to ls into them I get the error message.
I can't use my dads computer as his runs Windows 7 and has hit the "hang on classpnp.sys at startup" problem.
The only internet access I have is on my htc desire. 
I take it them that the grub config file cant be written manually at the grub rescue prompt?  And I know it sounds like I've lost all my data AGAIN, but I need to try all options before buying yet another hdd, then tearing my hair out trying to recover aetleast some vestige of my data.

---

### Post by drs305 on 2010-10-27
> **salviablue said:**
> So I take it then that there is no way of fixing this without a computer with internet access if your live cd has been used as a frisbee by the kids and they disappeared your live usb stick too? 

If you are able to get to the Grub prompt you may be able to boot an Ubuntu ISO directly from the hard drive or a flash drive.

I wrote a guide on how to do this. Initially I was thinking about netbook users but during my testing found that others might be able to use it when they couldn't produce a CD. 

Depending on what your system is capable of seeing from the Grub prompt, this may be an option for you.
[HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")

---

### Post by jamesamccarty on 2010-11-02
I have tried steps 2 through 5 at  [HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099").  No luck.
When I power up my Dell Inspiron 6000, this is what I get:
-------
GNU GRUB  version 1.98-1ubuntu7

Minimal BASH-like line editing is supported.  For the first word,
TAB lists possible command completions. Anywhere else TAB
lists possible device or file completions.

grub> _
-------
I am able to get to the operating system by typing the following commands:

linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 ro
initrd /boot/initrd.img-2.6.32-25-generic
boot

This brings up ubuntu 10.04 LTS and everything works as it should from there, until I boot up the computer the next time.

I have attached my results.txt file.

---

### Post by drs305 on 2010-11-02
@ jamesamccarty, 

I answered your post over in the [HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099") thread, so let's stick to that one for now.

---

### Post by Unit43 on 2010-11-04
Good day all,

I am quite new to the linux front, have been using Ubuntu for a year as desktop and I work with Solairs. Couple of days ago I decided to upgrade from Ubuntu 9.10 to Ubuntu 10.04. All went well, I went to bed and the next morning I was greeted by the **GRUB RESCUE>** prompt, and the following **"error: the symbol 'grub_puts_' not found**. Grub is a dark area for me so naturally I did not know what to do. Between google and this Forum, I stumbled upon these very informative threads by [B]drs305. 

[/B]Let me explain my setup, as my fix for this was a combination of the threads and an Ubuntu Document about Grub2, I think **drs305** published this link too. [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 

I don't have any duel boot options, it is a single install of Ubuntu 9.10 that was upgrade to 10.04.
I have 3 sets of drives, 1x300Gb for boot {This is suppose to be the Ubuntu disk /dev/sda1)
1 x 300GB for recreational stuff {NTFS - Took the drives from my old windows box}
3x 300GB RAID for data/work etc. {NTFS - Took the drives from my old windows box}

After trying the whole "Purge and Reinstall" as well as " Boot & install Ubuntu from the Rescue Prompt" I had only failures and errors, mounting issues and grub not liking the idea. I eventually fiddled, and this is what solved my problem: {btw, before I upgraded, I did an apt-get install and apt-get upgrade on my 9.10 box, don't know if that would have made any difference}

1. Boot from the LiveCD
2. Enter a Terminal session
3. Verified quickly the disks *$sudo fdisk -l* just to confirm the correct disk which was /dev/sda1
4. Mount my drive [I]$sudo mount /dev/sda1 /mnt
5. [/I]Do the Chroot thing: [I]$sudo chroot /mnt
[/I]6. Then just checked the version: *# grub-install -v *{This is from the Grub2 Doc, myne was 1.98 beta}
7. And this was the winner! This is actually to upgrade the GRUB2 by installing the grub-pc package, I entered the command as on the doc, not realising I was root already: [I]# sudo aptitude install grub-pc

[/I]It installed , then I rebooted and viola, Grub came up and booted normally into my Desktop. Also, no internet was needed for this.

I really hope this can help someone, all I would like to know is why does these error's happen? If someone could explain.

Thanks guys. :twisted:

*[SIZE=1]Thought for the day: " A computer once beat me at chess, but was no match for me at kick boxing"[/SIZE]*

---

### Post by drs305 on 2010-11-04
Unit43,

Glad you are now able to boot Grub2. Thanks for posting your experiences.

Do you know why the Purge & Reinstall thread didn't work for you, since that is essentially what you did via the chroot/install grub-pc you mention as 'what worked'?

As to why you couldn't boot initially: I can't tell you why it failed, but the *error: the symbol 'grub_puts_' not found* message means that parts of Grub2 failed to install completely. To be honest, I'm glad you were able to resolve the problem, since I would probably have blamed RAID for the problems when the reinstall didn't work.  ;-)

---

### Post by Unit43 on 2010-11-04
Hi,

Thanks, I learn allot out of Forums. :)

As to why the "Purge and Reinstall" did not work, I don't document my home processes that much, bad habbit. :mad: The first command: *sudo grub-install --recheck /dev/sda1*, did not work, kept giving me an error {something about it finding or recognising the Grub files, which led me to believe corruption with install} and a wise old man once told me that if Linux gives you an error, believe the machine. So I did.... 

I then skipped that, as the chroot was a logical door for me to open as it allows the user to interface as if on the hardware. After that I could update/upgrade the either corrupted or missing Grub, if that makes sense. The update-grub also gave me errors, as if to say the basics is not there to do the update; as I said, I did not document so I am explaining my though process. 

All and all, the purge and reinstall does guide you in a very good direction to start opening your mind and look a bit further than just a copy and paste solution. When I realised that an update won't work, I went along the same lines and did an upgrade, which eventually worked.

I would almost want to say, with a future update, allow the user to interactively install Grub, to ensure the user can customise the usage of Grub with either a single or multi boot option, or to leave Grub out totally. I know I don't understand Grub that well, because it is a part of Linux or Unix I very seldom deal with.

Again, thank you for the great assistance. :P

---

### Post by drs305 on 2010-11-04
Thank you for taking the time to post this Unit43.

---

### Post by sprocketrx on 2010-11-07
Hi drs305,

I am a total newbie when it comes to linux, I have used Ubuntu 9.04, 9.10 and 10.04 before but the whole doing things in a Terminal before has frightened me.

Some background of my problem:
I am using a emachines e350 Netbook, with XP Home SP3 as the original install.
I decided to try Ubuntu 10.10 Netbook (remix I think), I didnt like it so I decided I would rather the full 10.10.
I installed from a live USB I made and all was fine, it worked great, I could boot into Ubuntu or Windows without any problems. 

I then decided to buy a new 4Gb USB and make a live USB 10.10 to have as a backup incase anything happened. It installed onto the USB without any problem. After I installed I decided to boot from it to make sure it worked OK. Yes no problem there either. So I did the normal procedure to shut down.
Then when I tried to reboot my machine with out the USB I got, 
error: no such partition
grub rescue>

I have read your tutorial, How to purge and reinstall  grub2, and found it very easy to follow, however when I tried to reboot the machine I get the same error

As I mentioned before I am fairly new to Linux, I have been a Windows user who is in favour of Linux and have slowly been using it more and more and enjoying it, however I would still like to have my XP for occasional use.

I hope I have provided enough info and hopefully it wasnt to long winded.

Please Help

Forgot to mention, when booting from Live USB there is an option to - Boot from first HDD, I tried that and got:
no init found. Try passing init=bootarg
then a load of text, then
(initramfs)

btw I can boot no problem at all from the Live USB.
Here is my Boot Script Info:


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             38     7,839,719     7,839,682   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    23,070,719    23,068,672  12 Compaq diagnostics
/dev/sdb2    *     23,070,720   223,548,196   200,477,477   7 HPFS/NTFS
/dev/sdb3         223,549,438   312,580,095    89,030,658   5 Extended
/dev/sdb5         263,780,352   310,466,559    46,686,208  83 Linux
/dev/sdb6         310,468,608   312,580,095     2,111,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7026-4E9A                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A27294AA729484A7                       ntfs       PQSERVICE                     
/dev/sdb2        06B0BC6AB0BC61BB                       ntfs       OS                            
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        be04d65a-ed24-4e25-83a2-06c2f42427db   ext4                                     
/dev/sdb6        db4280d8-9acb-4863-b59f-f55e89acdbf5   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set be04d65a-ed24-4e25-83a2-06c2f42427db
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set be04d65a-ed24-4e25-83a2-06c2f42427db
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set be04d65a-ed24-4e25-83a2-06c2f42427db
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=be04d65a-ed24-4e25-83a2-06c2f42427db ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set be04d65a-ed24-4e25-83a2-06c2f42427db
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=be04d65a-ed24-4e25-83a2-06c2f42427db ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set be04d65a-ed24-4e25-83a2-06c2f42427db
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set be04d65a-ed24-4e25-83a2-06c2f42427db
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a27294aa729484a7
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 06b0bc6ab0bc61bb
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=be04d65a-ed24-4e25-83a2-06c2f42427db /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=db4280d8-9acb-4863-b59f-f55e89acdbf5 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 137.3GB: boot/grub/core.img
 137.6GB: boot/grub/grub.cfg
 152.5GB: boot/initrd.img-2.6.35-22-generic
 137.6GB: boot/vmlinuz-2.6.35-22-generic
 152.5GB: initrd.img
 137.6GB: vmlinuz
```

---

### Post by drs305 on 2010-11-07
sprocketrx,

Welcome to the Ubuntu forums.

I have a suspicion of what is happening - I think it may be a BIOS limitation which doesn't allow the system to see beyond 137GB on the drive.

The clues include:
```
 137.3GB: boot/grub/core.img
 137.6GB: boot/grub/grub.cfg
 152.5GB: boot/initrd.img-2.6.35-22-generic
 137.6GB: boot/vmlinuz-2.6.35-22-generic
 152.5GB: initrd.img
 137.6GB: vmlinuz
```
Notice they are all at 137GB execpt initrd.img. 

The location of the initrd.img, beyond the 137GB, could be the cause of
> when booting from Live USB there is an option to - Boot from first HDD, I tried that and got:
no init found. 

If the limit is the problem, it would also explain why the reinstall seemed to go fine but then fails to boot. I am not sure of the mechanics, but apparently G2 can install beyond the 137GB limit, or it installs below the limit but when a file is updated (initrd.img) it is inadvertently placed outside the limit.

Soooo,
Take a look in your BIOS and see if there is a setting to enable a large drive feature. I don't know exactly what it would be called. You might also find a reference in BIOS to the drive size. Also look on your motherboard manufacturer's website to see if there is a BIOS update.

If you can't do that, we have to do something else to move initrd.img earlier in the disk. You will probably have to 'chroot' into the hard drive install on sdb5 (link in my signature line). 

To 'chrooot' run "sudo fdisk -l" (lowercase L) first to confirm the Ubuntu partition. It may be sdb5, but it may also be sda5. If it is not sdb5 make sure you change to the correct device when you first mount the partition and before you chroot into it. 

Once you have 'chrooted' into the proper partition:
```
sudo grub-install --recheck /dev/sdb
sudo update-grub

```

Now we start analyzing if it was successful. You will need to download and run the boot info script again. Look in the results at the last entry  and see if all the "files loaded" by Grub are below 137GB. If so, the problem may be solved. If not, try renaming /boot/initrd.img-2.6.35-22-generic and then run "update-initramfs -u" and see if a new initrd.img-<version> was created below the 137GB limit.

Once you get all the files within the first 137GB, if that was indeed the problem, it should boot if you have BIOS point to that drive first.

Long term, the BIOS should be changed or updated so there isn't the same problem in the future. 

The second option would be to create a /boot partition at the start of the drive.

And you think you are long winded...  ;-)

---

### Post by sprocketrx on 2010-11-07
Thanks for the response. I am about to head off to work here, but I will try your suggestions this evening and let you know the result. Thanks again.

---

### Post by Stanley King on 2010-11-08
Hello.I m new to ubuntu and i have a problem.I have installed ubuntu 10.04 with wubi because i ve heard good things about this OS.I m using windows vista home premium 32 bit on an Acer 5920G.I have Ubuntu installed before a week.Today i logged in as i do everyday and said me to do updates.I do updates and then say me to make restart.I do restart and it says me the following...

error:no such device:315b etc grub rescue>

It doesnt boot neither windows nor ubuntu.i havent got a Live CD because i downloaded it and installed it.What can i do to fix it???

---

### Post by drs305 on 2010-11-08
Hello Stanley, welcome to the Ubuntu forums.

First, a wubi installation shouldn't have affected your Windows installation since it is a file *within* the Windows system. However, what *should* happen doesn't help if your machine isn't working...

Since you are 'trying' wubi, I'd first try to get your Windows working again using your Windows recovery or installation CD. Here are a couple of links on repairing the Windows bootloader:
[http://ubuntuforums.org/showpost.php?p=10049238&postcount=4]("http://ubuntuforums.org/showpost.php?p=10049238&postcount=4")
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

If you want to try to boot Wubi from the grub rescue prompt you can try the steps at the start of this thread. Normally you would use the instructions in the "Wubi Only" section. 

If these do not work: Since you are getting the grub rescue prompt before seeing the Windows menu, you could also try the instructions in prior section. If grub2 was mistakenly installed in the MBR of your Windows drive these instructions might work.

You might also try holding down the SHIFT key during boot to see if the Grub menu displayed. If it does appear, select another kernel, the recovery mode, or Windows.

---

### Post by Stanley King on 2010-11-08
Thanks for the reply drs305.I havent got a windows recovery disk because im using a laptop.They dont gave me a recovery disk so i cant boot from CD.I tried to follow the wubi only instructions but when i typing the code i have some errors.Wubi only section needs a Live CD and i dont have one.I tried to press Shift button and says me GRUB loading. and then the same error i have already written above.

---

### Post by drs305 on 2010-11-08
Here is a link for downloading a Windows repair CD:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

And forum member *oldfred* has put together some Windows repair links:
[http://ubuntuforums.org/showthread.php?p=9826152]("http://ubuntuforums.org/showthread.php?p=9826152")

If none of these work, you might be able to use a procedure I wrote for netbook users who needed to boot from an ISO file. To be able to use this procedure though you must be able to locate the Grub2 modules on your current system (try Step 2 first to see):

[http://ubuntuforums.org/showthread.php?t=1599293]("http://ubuntuforums.org/showthread.php?t=1599293")

---

### Post by sprocketrx on 2010-11-09
drs305,

Well I finally got time to try your suggestions.I had a look in my BIOS but there was no setting to change drive size. Also I had recently done a BIOS upgrade, so I didnt go down that path.
So the I did the chroot, whilst doing that I went  further and tried grub purge and reinstall again, well it worked this time and I now have my XP back. BUT.... I only have the netbook version of 10.10, unfortunately I would like the full 10.10 version so I can get all my emails back.

At this stage I would be happy to uninstall all signs of Ubuntu and go with a fresh install, but I dont know how to go about doing that

I really appreciate the time you have put into solving these problems for Ubuntu idiots like me, ....but I am getting there and enjoying the learning experience.

Huge Thanks

---

### Post by drs305 on 2010-11-09
> **sprocketrx said:**
> drs305,
So the I did the chroot, whilst doing that I went  further and tried grub purge and reinstall again, well it worked this time and I now have my XP back. BUT.... I only have the netbook version of 10.10, unfortunately I would like the full 10.10 version so I can get all my emails back.

At this stage I would be happy to uninstall all signs of Ubuntu and go with a fresh install, but I dont know how to go about doing that

I really appreciate the time you have put into solving these problems for Ubuntu idiots like me, ....but I am getting there and enjoying the learning experience.

You are quite welcome. I keep learning more about Ubuntu myself when these things come up. 

Regarding a reinstall: My thought is to have Windows (plus boot/recovery partitions) AND Ubuntu within the first 135GB of your drive. That way Ubuntu couldn't have any files outside that limit. If Windows currently occupies more than the first 120GB or so, it may mean shrinking your Windows partition first. The Ubuntu partition really only needs to be 10-15GB if your data files are kept on another partition.

If you set up your partitions and then choose manual partitioning during the installation you should be able to avoid the 137GB and can install the version of Ubuntu you desire. 

As far as how to do a fresh install, you would just create the partition structure you want, then boot an Ubuntu LiveCD and select the "Install" option and choose manual partitioning. 

I don't know if you have seen it, but I have a guide on how to install Ubuntu from the grub rescue prompt. Even though you are not having problems with grub at the moment, you could use that procedure if creating a CD is a problem. You would download the Ubuntu ISO and then just boot to your grub menu and then press "c" to get to the grub terminal. Here is the link for installing without a CD:
[http://ubuntuforums.org/showthread.php?t=1599293]("http://ubuntuforums.org/showthread.php?t=1599293")

Since I haven't run into the 137GB limit on my systems, I have a question. Other than grub problems, once you are booted into either Windows or Ubuntu, can you create and access files past the 137GB limit - e.g. does Windows see the drive as being 137GB or 160GB (minus formatting, etc)? Since Grub created files outside the limit, it would seem that at least Ubuntu can. 

Of course, before changing partitions, wiping an install, etc, make sure you back up your important files somewhere that won't be formatted or erased during these operations.

---

### Post by dcheesi on 2010-11-22
I was having this same problem, and both Windows XP and the Ubuntu CD were able to access the entire drive. The only thing that couldn't was Grub itself; even the SuperGrub boot CD failed to find my Ubuntu partition (even though I could see it from the live-CD OS). Reinstalling Ubuntu at the 100GB mark on the HDD did the trick (thanks!).

---

### Post by dcheesi on 2010-11-22
Oops, I spoke too soon. It booted up perfectly the first time, but after restarting I'm now staring at a grub command prompt again?!? It's the regular prompt this time, rather than the rescue version. But I sill don't know why it isn't bringing up the menu?

---

### Post by drs305 on 2010-11-22
> **dcheesi said:**
> Oops, I spoke too soon. It booted up perfectly the first time, but after restarting I'm now staring at a grub command prompt again?!? It's the regular prompt this time, rather than the rescue version. But I sill don't know why it isn't bringing up the menu?

Run the boot info script and see where the grub files are located (they are the last items listed in RESULTS.txt).

It's possible the install placed your Grub files within the portion seen by BIOS but that an update rewrote one of the files to an area outside the limits. If so, you need to create a small /boot partition which will always remain completely within your BIOS limit (or put Grub on a thumb drive, but it would always have to be connected during boot).

Of course, it could be something completely different this time, so if you run the boot info script please post it and we can take a look if you can't figure it out.

---

### Post by dcheesi on 2010-11-23
Ok, I reinstalled it with everything below the 137GB boundary ("duh!"), and this time it survived the update process. So far, so good... 

[s]EDIT: Ok, I'm just going to stop posting like this :( It appeared to boot up fine, but when I logged in, I got a bunch of error messages and no desktop. Obviously a different problem; I'll search for answers but I think it's almost time to declare this experiment a failure... :([/s]

EDIT^2: Nevermind, PEBKAC

---

### Post by sperman13 on 2010-11-26
Hey guys, 

Very new to the whole linux system and I've had my wonderful ubuntu for o month and now my first problem  

So first some background I guess: 

I installed Ubuntu on my LG Netbook x110 through WUBI and things were going great. But yesterday the update manager came up and told me to install a bunch of updates which I always do. The only thing out of the ordinary was that one of the updates had to do with the grub loader and it asked me if I wanted to proceed..big mistkae. So it installed everything and told me to restart the computer to make the changes effective. So when I restart the computer I'm greeted by this message: 

Error: No such device: af9251f2-3174-48c1-a75f-b06bd29962bf
grub rescue> 


Help?!

PS 

Cant boot into windows either so yeah:(

---

### Post by drs305 on 2010-11-26
sperman13,

If you are now seeing the Grub2 menu first, instead of the Windows menu first (or not seeing the Windows menu at all), you probably installed G2 to the MBR.

The first thing to do is restore the Windows bootloader. You can do this with the Windows repair disk, but since you are probably already booted to a LiveCD (if you are still using that computer), try rewriting the MBR with lilo.
This assumes your Windows is on sda (first drive):
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
You aren't fully installing lilo, so don't worry about the lilo install warning messages.

See if that gets Windows booting again. If not, do a search of these forums for "/fixmbr" for the past 24 hours and you will find links/instructions.

Once you have Windows sorted out, let us know if you can now boot into Ubuntu.

You'll be happy to know, now that lots of wubi installs have been broken in similar fashion, a new Grub2 version was released today so that wubi users aren't given the choice to install the bootloader (since so many users exercised this option, which really isn't a good idea in wubi).

---

### Post by jay3 on 2010-11-27
I am getting the error "the symbol grub_xputs not found" error upon the restart after an upgrade from 10.04 to 10.10.  I cannot get my 9.10 live cd to start the system (it hangs up when i select the option to start from the cd).  So, I am trying the section from our notes entitled 'grub rescue > Boot Procedures (About Time!).  I have been successful in running through steps 1-4 (to determine the grub folder and set the prefix and root).  When I try step 5 (Load Modules) by entering the 'insmod linux' command I receive the error again that says "the symbol grub_xputs not found".  What can/should I do at this point?

---

### Post by drs305 on 2010-11-27
> **jay3 said:**
> When I try step 5 (Load Modules) by entering the 'insmod linux' command I receive the error again that says "the symbol grub_xputs not found".  What can/should I do at this point?

The xputs error generally means that Grub2 is not completely installed, which of course causes problems and may prevent booting even from the rescue prompt (if certain files are missing or corrupted).

If the modules won't load, you can try a couple of things. First, try using the complete path, such as (hdX,Y)/boot/grub/linux.mod
You can use the "ls (hdX,Y)/boot/grub" command to see if the modules exist.

If they aren't there, you can try loading them from their 'backup' location. See if the modules are located in "(hdX,Y)/usr/lib/grub/i386-pc" using the "ls" command. If found,, try loading them using that path and the complete module name.

---

### Post by jay3 on 2010-11-27
Thank you for the suggestions.  I entered the ls (hd0,1)/boot/grub and more than a screenful of files were listed including many mod files.  However, when i then ran insmod (hdo,1)/boot/grub/linux.mod I still receive the error msg "grub_xputs" not found.  Then entered the ls (hd0,1)/usr/lib/grub/i386-pc to find that there are many mod files there as well.  However, upon running insmod (hd0,1)/usr/lib/grub/i386-pc/linux.mod I still receive the "grub_xputs" not found.

---

### Post by drs305 on 2010-11-27
> **jay3 said:**
> Thank you for the suggestions.  I entered the ls (hd0,1)/boot/grub and more than a screenful of files were listed including many mod files.  However, when i then ran insmod (hdo,1)/boot/grub/linux.mod I still receive the error msg "grub_xputs" not found.  Then entered the ls (hd0,1)/usr/lib/grub/i386-pc to find that there are many mod files there as well.  However, upon running insmod (hd0,1)/usr/lib/grub/i386-pc/linux.mod I still receive the "grub_xputs" not found.

Even though there can be many reasons, it's sounding like you aren't going to be able to boot via your normal installation. 

Since you CD isn't working, if you can access the Grub menu and also an image of the Ubuntu ISO (ubuntu...iso), you may be able to boot to the LiveCD via that method.

Edit: Sorry, I forgot the following requires you to be able to load the modules, although maybe I explain it a bit differently there...
Here is the guide I wrote on trying to boot an Ubuntu ISO via the Grub rescue prompt:
[HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")

If that doesn't work I guess I'd recommend trying to find out why your working CD won't boot...

---

### Post by jay3 on 2010-11-27
Thank you so much for your ongoing assistance.  I think I am there (or almost).  I managed to get a new live cd for Ubuntu 10.10 and was able to 'boot' from it.  As per your directions in the thread (what to try first) I did the following:
 
sudo mount /dev/sda1/mnt
sudo grub-install --root-directory=/mnt /dev/sda
 
These two commands executed ok.  I then removed the live cd and tried a restart from the hard drive.  I did receive an error/problem msg of some kind at the top of the black screen on this reboot (I didn't make note of it).  However, the ubuntu 10.10 did start up.  Everything seems to work.  I went back to restart/reboot in order to see what that msg was (and make note of it), however, I don't seem to get that msg anymore although when restarting the cursor does blink at the top left corner of the black screen for a while (~ 30 secs) where the msg did earlier display.  Following this the Ubuntu 10.10 starts up.
 
So I am assuming I am ok?  Thank you so much for your excellent assistance.

---

### Post by drs305 on 2010-11-27
> **jay3 said:**
> 
So I am assuming I am ok?  Thank you so much for your excellent assistance.

You are welcome. 

The blinking upper left cursor usually means there is some sort of video problem. It's not Grub. Usually when problems are reported on the forums the blinking cursor doesn't resolve itself - in your case it does.

You might try going to System, Administration, Additional Drivers and see if there are any already listed for whatever kind of video card you are using. You could also do a search of the forums listing your specific video card and Maverick to see if there have been any posts about it.

---

### Post by zeiz on 2010-11-30
The computer was working fine. No updates at that moment. 
Firefox was opened, some other docs too. Tried to open Skype. Computer got frozen. After forced shutdown and reboot - **grub rescue>** prompt.
Only **ls** works:
```
grub rescue> ls
(hd0) (hd0,1) (hd0,2) (hd0,3) (hd0,4)
grub rescue> ls (hd0,3)
invalid filesystem
```

As it's shown there are 4 primary partitions on the disk: hd0,1 - Windows7, hd0,2 - linux swap, hd0,3 - Ubuntu10.4, hd0,4 -Storage (fat32).
So Ubuntu installed as stand alone OS without wubi and it looks like it's gone.
From Live CD - no way to mount sda3 - "invalid filesystem". Disk utility (where is GParted btw?) show sda3 - "unknown". 
GParted from Rescue CD shows sda3 in black - "unknow". Something was corrupted for sure.

I'd rather reinstall Ubuntu since I don't want use LILO.
However I'd like to understand what actually happened?
What was wrong?
Please help!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 163830870.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   118,784,609   118,784,547   7 HPFS/NTFS
/dev/sda2         118,784,610   127,186,604     8,401,995  82 Linux swap / Solaris
/dev/sda3         127,186,605   163,830,869    36,644,265  83 Linux
/dev/sda4         163,830,870   312,576,704   148,745,835   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        738FA65765B5AC23                       ntfs                                     
/dev/sda2        dac2416b-ad4e-4661-b161-54f7fa608a48   swap                                     
/dev/sda4        48EA-3091                              vfat                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by drs305 on 2010-11-30
zeiz,

First I'd try doing an fsck check. The partition needs to be unmounted, but that won't be a problem. Whether e2fsck will see the partition or not is another matter.
```
sudo e2fsck -f -y -v /dev/sda3
```

---

### Post by shellacked on 2010-11-30
First off: thanks to all who support this thread and these forums :)

I have a system 76 starling netbook (which is great btw).  I was doing one of the periodic updates when I got some error message about Grub not finding what it expected at a certain location.  It asked me to pick a partition (I think?) and suggested if I wasn't sure to select both, which I did.  The update completed (with several ominous warning/error messages) and when I rebooted the computer it didn't load Ubuntu but instead just sat there with the cursor flashing in the upper left corner.

I made a bootable thumb drive and ran the boot info script.  I'd really appreciate some help as I'm a bit of a noob!

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 138719809 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 138944257 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004e98b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *              1   308,677,734   308,677,734  83 Linux
/dev/sda2         308,677,735   312,581,807     3,904,073   5 Extended
/dev/sda5         308,677,736   312,581,807     3,904,072  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2004 MB, 2004877312 bytes
129 heads, 32 sectors/track, 948 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     3,915,775     3,915,744   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        c96252e4-5388-4f1d-803d-8bf57606a7ec   ext4                                     
/dev/sda5        7b54abcf-57b4-402b-94fb-e8f44cab57c0   swap                                     
/dev/sdb1        B8B4-E828                              vfat       LINUX                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/disk              ext4       (rw,nosuid,nodev,uhelper=hal)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc    /proc    proc    nodev,noexec,nosuid    0    0
# / was on /dev/sda1 during installation
UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec    /    ext4    errors=remount-ro    0    1    # /dev/sda1
# swap was on /dev/sda5 during installation
UUID=7b54abcf-57b4-402b-94fb-e8f44cab57c0    none    swap    sw    0    0    # /dev/sda5

=================== sda1: Location of files loaded by Grub: ===================


  71.1GB: boot/grub/core.img
 155.0GB: boot/grub/grub.cfg
  71.0GB: boot/initrd.img-2.6.32-21-generic
  82.5GB: boot/initrd.img-2.6.32-24-generic
  83.2GB: boot/initrd.img-2.6.32-25-generic
  83.3GB: boot/initrd.img-2.6.32-26-generic
  71.0GB: boot/vmlinuz-2.6.32-21-generic
  71.2GB: boot/vmlinuz-2.6.32-24-generic
  71.2GB: boot/vmlinuz-2.6.32-25-generic
  71.2GB: boot/vmlinuz-2.6.32-26-generic
  83.3GB: initrd.img
  83.2GB: initrd.img.old
  71.2GB: vmlinuz
  71.2GB: vmlinuz.old



```

---

### Post by zeiz on 2010-12-01
> **drs305 said:**
> zeiz,

First I'd try doing an fsck check. The partition needs to be unmounted, but that won't be a problem. Whether e2fsck will see the partition or not is another matter.
```
sudo e2fsck -f -y -v /dev/sda3
```

That's it, my problem solved!
I've been using Ubuntu as my production OS already long enough and that was my first problem with it. No problems - no knowledge :)
Besides the problem happened on my daughter's machine located in another city...

Dear drs305,
You really do tremendous work to help people. Many thanks!

---

### Post by drs305 on 2010-12-01
> **shellacked said:**
> 
I made a bootable thumb drive and ran the boot info script.  I'd really appreciate some help as I'm a bit of a noob!
shellacked,

Welcome to the Ubuntu forums!

At the risk of having to take it back, your situation looks fairly simple to resolve.  ;-)

Start Ubuntu from your USB or LiveCD. Open a terminal (Applications, Accessories, Terminal).

Mount your Ubuntu partition:
```
sudo mount /dev/sda1 /mnt
```
Install Grub2 to the sda drive (do not include the partition number):
```
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot, and as long as your BIOS is looking at sda first it should boot into Ubuntu.

---

### Post by bcbc on 2010-12-01
I just wanted to add a wubi related comment. If you install grub to the drive MBR on a Wubi install, you get a very limited grub rescue> prompt.

I did it to test (this will leave your computer unbootable):
sudo grub-install.real /dev/sda
If you do a bootinfoscript afterwards you'll see this:
> => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
All I got from "ls" was (hd0).
ls (hd0) and ls (hd0,2) gave unknown filesystem or could not read partition table (something like that)

The command "set" gave prefix=(hd0)/boot/grub and root=(hd0)
lsmod gave 'unknown command'

From what I can tell there is no way to boot Ubuntu from this rescue prompt - the only fix is to install the windows bootloader or lilo.

Note: this usually only happens to users who have Wubi on an 'drive' other than C:. You can test it on any install by using the command I showed at top. Have a repair CD handy.

---

### Post by shellacked on 2010-12-01
> **drs305 said:**
> shellacked,

Welcome to the Ubuntu forums!

At the risk of having to take it back, your situation looks fairly simple to resolve.  ;-)



Well I think it partially worked ;)

Here is the output from grub-install after mounting sda1:

```


sudo grub-install --root-directory=mnt /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect, fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb


```

Upon rebooting without the thumb drive I get a grub prompt "grub >".  It's not "grub rescue>"

---

### Post by drs305 on 2010-12-01
> **shellacked said:**
> Well I think it partially worked ;)
sudo grub-install --[COLOR="Red"]root-directory=mnt[/COLOR] /dev/sda


You are missing a / before "mnt"
```
sudo grub-install --root-directory=[COLOR="Red"]**/**[/COLOR]mnt /dev/sda
```

---

### Post by shellacked on 2010-12-01
> **drs305 said:**
> You are missing a / before "mnt"
```
sudo grub-install --root-directory=[COLOR=Red]**/**[/COLOR]mnt /dev/sda
```

I booted off the thumb drive and ran the following commands.  I copied / pasted the input / output this time.  

Embarrassingly, in my last post, I didn't know I could copy / paste out of a terminal window so I typed the output into my post and apparently I missed the / in front of mnt.  ](*,)

```


ubuntu@ubuntu:/$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:/$ sudo grub-install --root-directory=/mnt /dev/sda
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
ubuntu@ubuntu:/$ 


```The output looks the same, so I *think* I only forgot the / in front of mnt in my post. :oops:

Then, out of curiosity, I ran the boot_info_script again.  Different output this time but it doesn't mean much to me :p

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks at sector 
    138714625 of the same hard drive for the stage2 file. A stage2 file is at 
    this location on /dev/sda. Stage2 looks on partition #1 for 
    /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 138944257 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004e98b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *              1   308,677,734   308,677,734  83 Linux
/dev/sda2         308,677,735   312,581,807     3,904,073   5 Extended
/dev/sda5         308,677,736   312,581,807     3,904,072  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2004 MB, 2004877312 bytes
129 heads, 32 sectors/track, 948 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     3,915,775     3,915,744   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             48     7,831,551     7,831,504   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        c96252e4-5388-4f1d-803d-8bf57606a7ec   ext4                                     
/dev/sda5        7b54abcf-57b4-402b-94fb-e8f44cab57c0   swap                                     
/dev/sdb1        B8B4-E828                              vfat       LINUX                         
/dev/sdc1        43E6-0D3B                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     ext4       (rw)
/dev/sdc1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c96252e4-5388-4f1d-803d-8bf57606a7ec
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc    /proc    proc    nodev,noexec,nosuid    0    0
# / was on /dev/sda1 during installation
UUID=c96252e4-5388-4f1d-803d-8bf57606a7ec    /    ext4    errors=remount-ro    0    1    # /dev/sda1
# swap was on /dev/sda5 during installation
UUID=7b54abcf-57b4-402b-94fb-e8f44cab57c0    none    swap    sw    0    0    # /dev/sda5

=================== sda1: Location of files loaded by Grub: ===================


  71.1GB: boot/grub/core.img
 155.0GB: boot/grub/grub.cfg
  71.0GB: boot/grub/stage2
  71.0GB: boot/initrd.img-2.6.32-21-generic
  82.5GB: boot/initrd.img-2.6.32-24-generic
  83.2GB: boot/initrd.img-2.6.32-25-generic
  83.3GB: boot/initrd.img-2.6.32-26-generic
  71.0GB: boot/vmlinuz-2.6.32-21-generic
  71.2GB: boot/vmlinuz-2.6.32-24-generic
  71.2GB: boot/vmlinuz-2.6.32-25-generic
  71.2GB: boot/vmlinuz-2.6.32-26-generic
  83.3GB: initrd.img
  83.2GB: initrd.img.old
  71.2GB: vmlinuz
  71.2GB: vmlinuz.old



```Upon rebooting I get a grub prompt:

```

    [ Minimal BASH-like line editing is supported.  For 
      the first word, TAB lists possible command 
      completions.  Anywhere else TAB lists the possible 
      completions of a device/filename. ]

grub>

```Sorry for the confusion, and many thanks for the help!

---

### Post by drs305 on 2010-12-01
> **shellacked said:**
> Sorry for the confusion, and many thanks for the help!

Well, it's progress of sorts.

What kind of Ubuntu drive did you boot off of? It installed Grub legacy according the the results.txt. Is your thumb drive OS hardy? 

In any case, there is no menu.lst, which is what Grub legacy would have to have to boot. 

We have a couple of options, but I'll need to know if you have a bootable copy of the Lucid LiveCD or a copy of the ISO on a thumb drive or on your hard disk that Grub 2 might be able to access.

---

### Post by shellacked on 2010-12-01
> **drs305 said:**
> Well, it's progress of sorts.

What kind of Ubuntu drive did you boot off of? It installed Grub legacy according the the results.txt. Is your thumb drive OS hardy? 

In any case, there is no menu.lst, which is what Grub legacy would have to have to boot. 

We have a couple of options, but I'll need to know if you have a bootable copy of the Lucid LiveCD or a copy of the ISO on a thumb drive or on your hard disk that Grub 2 might be able to access.

I had 9.04 live on a thumb drive that I used to boot and reinstall grub.  I just formatted that thumb drive and I'm installing 10.04 live which (I think) is the same thing as lucid.

---

### Post by shellacked on 2010-12-03
> **drs305 said:**
> 
We have a couple of options, but I'll need to know if you have a bootable copy of the Lucid LiveCD or a copy of the ISO on a thumb drive or on your hard disk that Grub 2 might be able to access.

I have Lucid Live on a thumb drive

---

### Post by drs305 on 2010-12-03
> **shellacked said:**
> I have Lucid Live on a thumb drive

Since you ended up with Grub legacy installed on your OS, I'd recommend booting the Lucid CD and using the 'chroot' method to purge all Grub(s) and reinstall them. Here is the link on how to do this:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099").

When you are mounting the 'real' installation, first check to make sure what it is called (sda or sdb).

---

### Post by shellacked on 2010-12-03
> **drs305 said:**
> Since you ended up with Grub legacy installed on your OS, I'd recommend booting the Lucid CD and using the 'chroot' method to purge all Grub(s) and reinstall them. Here is the link on how to do this:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099").

When you are mounting the 'real' installation, first check to make sure what it is called (sda or sdb).

Worked like a charm!!!  Thanks *so* much for your help!!!

---

### Post by DvineINFEKT on 2010-12-03
At this point, I've been trying for two hours, and am in dire need of help. If I can't get this back up and running ASAP, I'm in serious trouble for school (finals are in less than two weeks).

If anyone would be so kind as to help me, It would be very appreciated. I spend about 60%/30% of my time between windows and ubuntu. Today, it asked me to update something or other and I remember clearly asking me about installing something or other called GRUB. The help recommended I do it, and so I did.

Now it wont restart and if I try to boot without a Live CD (as I am doing now) I get the Grub Rescue> prompt. I really need to get back into windows or I'm screwed into redoing 20+ hours of work in less than two weeks.

I followed the instructions as much as I could, and here are the "Results" file -- 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   809,161,919   809,159,872   7 HPFS/NTFS
/dev/sda2         809,161,920 1,953,520,064 1,144,358,145   f W95 Ext d (LBA)
/dev/sda5         809,161,983 1,953,520,064 1,144,358,082   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   572,122,844   572,122,782   7 HPFS/NTFS
/dev/sdb2         572,122,845   894,467,069   322,344,225   7 HPFS/NTFS
/dev/sdb3         894,467,131 1,250,263,039   355,795,909   f W95 Ext d (LBA)
/dev/sdb5         894,467,133 1,185,752,518   291,285,386   7 HPFS/NTFS
/dev/sdb6       1,185,753,088 1,247,514,623    61,761,536  83 Linux
/dev/sdb7       1,247,516,672 1,250,263,039     2,746,368  82 Linux swap / Solaris


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 8011 MB, 8011120640 bytes
41 heads, 41 sectors/track, 9307 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1               8,064    15,646,719    15,638,656   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       0a20d074-40cf-46a9-8974-8479193f4738   ext4                                     
/dev/sda1        01CA976C239F6030                       ntfs       Storage                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        01CA95D1925AAD00                       ntfs       Media Storage                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        01CA97FA4528F250                       ntfs       Windows 7 64-bit              
/dev/sdb2        01CB6CA7CBE56DA0                       ntfs       Windows Vista                 
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        01CB6CA7CDC83760                       ntfs       Ubuntu                        
/dev/sdb6        9d5a3272-5a6f-439f-8467-3efda84edd76   ext4                                     
/dev/sdb7        116ce12f-df57-4144-99cb-ae7fabb5da26   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        1B26-EC79                              vfat       PATRIOT                       
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdg1        /media/PATRIOT           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


======================== sdb5/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ntfs
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 01cb6ca7cdc83760
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ntfs
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 01cb6ca7cdc83760
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod ntfs
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 01cb6ca7cdc83760
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sdb5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod ntfs
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 01cb6ca7cdc83760
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sdb5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod ntfs
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 01cb6ca7cdc83760
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sdb5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod ntfs
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 01cb6ca7cdc83760
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sdb5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 01cb6ca7cdc83760
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sdb5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 01cb6ca7cdc83760
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sdb5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
    insmod ntfs
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 01cb6ca7cbe56da0
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdb5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sdb5/Wubi: Location of files loaded by Grub: =================


  10.8GB: boot/grub/core.img
  28.3GB: boot/grub/grub.cfg
   1.7GB: boot/initrd.img-2.6.32-24-generic
   1.7GB: boot/initrd.img-2.6.32-25-generic
   1.7GB: boot/initrd.img-2.6.32-26-generic
  11.1GB: boot/vmlinuz-2.6.32-24-generic
  11.2GB: boot/vmlinuz-2.6.32-25-generic
  11.2GB: boot/vmlinuz-2.6.32-26-generic
   1.7GB: initrd.img
   1.7GB: initrd.img.old
  11.2GB: vmlinuz
  11.2GB: vmlinuz.old

=========================== sdb6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 9d5a3272-5a6f-439f-8467-3efda84edd76
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 9d5a3272-5a6f-439f-8467-3efda84edd76
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 9d5a3272-5a6f-439f-8467-3efda84edd76
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9d5a3272-5a6f-439f-8467-3efda84edd76 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 9d5a3272-5a6f-439f-8467-3efda84edd76
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9d5a3272-5a6f-439f-8467-3efda84edd76 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 9d5a3272-5a6f-439f-8467-3efda84edd76
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 9d5a3272-5a6f-439f-8467-3efda84edd76
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 01cb6ca7cbe56da0
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=9d5a3272-5a6f-439f-8467-3efda84edd76 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=116ce12f-df57-4144-99cb-ae7fabb5da26 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


 611.5GB: boot/grub/core.img
 615.9GB: boot/grub/grub.cfg
 610.0GB: boot/initrd.img-2.6.35-22-generic
 611.5GB: boot/vmlinuz-2.6.35-22-generic
 610.0GB: initrd.img
 611.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  f2 ba 08 00 00 00 41 b8  28 01 00 00 bf 0e 00 07  |......A.(.......|
00000010  80 ff 15 71 62 f9 ff 48  85 c0 48 8b d8 74 18 48  |...qb..H..H..t.H|
00000020  8d 05 da 70 fb ff 48 89  03 48 8d 05 20 72 fb ff  |...p..H..H.. r..|
00000030  48 89 83 10 01 00 00 48  85 db 74 6c ba 19 00 00  |H......H..tl....|
00000040  00 48 8b cb 44 8d 42 ea  e8 6f 4c 00 00 85 c0 8b  |.H..D.B..oL.....|
00000050  f8 78 49 4c 8d 0d 1e 9f  03 00 48 8d 15 6f c4 03  |.xIL......H..o..|
00000060  00 41 b8 01 00 00 00 48  8b cb c6 44 24 20 00 e8  |.A.....H...D$ ..|
00000070  d4 19 fe ff 8b f8 8b 05  00 9f 03 00 83 f8 ff 74  |...............t|
00000080  17 83 e8 01 89 05 f2 9e  03 00 75 0c 48 8d 0d e5  |..........u.H...|
00000090  9e 03 00 e8 60 98 fd ff  85 ff 79 0c b2 01 48 8b  |....`.....y...H.|
000000a0  cb e8 7a 5e fd ff 33 db  48 89 1e 48 8b 5c 24 40  |..z^..3.H..H.\$@|
000000b0  48 8b 74 24 48 8b c7 48  83 c4 30 5f c3 cc cc cc  |H.t$H..H..0_....|
000000c0  cc cc cc cc 48 83 ec 28  44 8b 41 10 41 3b d0 73  |....H..(D.A.A;.s|
000000d0  0c 48 8b 41 08 8b d2 48  8b 04 d0 eb 10 48 8b 0d  |.H.A...H.....H..|
000000e0  4c e5 03 00 41 2b d0 48  8b 01 ff 50 08 48 83 c4  |L...A+.H...P.H..|
000000f0  28 c3 cc cc cc cc cc cc  40 53 48 83 ec 20 48 8b  |(.......@SH.. H.|
00000100  d9 48 8b 0d 28 e5 03 00  48 8b 01 ff 50 10 03 43  |.H..(...H...P..C|
00000110  10 48 83 c4 20 5b c3 cc  cc cc cc cc cc cc cc cc  |.H.. [..........|
00000120  48 8b 05 09 e5 03 00 c3  cc cc cc cc cc cc cc cc  |H...............|
00000130  48 83 ec 28 48 39 4a 30  75 04 b0 01 eb 0d 48 8b  |H..(H9J0u.....H.|
00000140  0d eb e4 03 00 48 8b 01  ff 50 30 48 83 c4 28 c3  |.....H...P0H..(.|
00000150  cc cc cc cc cc cc cc cc  48 83 ec 28 48 3b d1 75  |........H..(H;.u|
00000160  04 b0 01 eb 0d 48 8b 0d  c4 e4 03 00 48 8b 01 ff  |.....H......H...|
00000170  50 38 48 83 c4 28 c3 cc  cc cc cc cc cc cc cc cc  |P8H..(..........|
00000180  40 53 48 83 ec 20 f6 c2  01 48 8d 05 20 73 fb ff  |@SH.. ...H.. s..|
00000190  48 8b d9 48 89 01 74 05  e8 fb a8 fb ff 48 8b c3  |H..H..t......H..|
000001a0  48 83 c4 20 5b c3 cc cc  cc cc cc cc 40 53 48 83  |H.. [.......@SH.|
000001b0  ec 20 f6 c2 01 48 8d 05  44 73 fb ff 48 8b 00 fe  |. ...H..Ds..H...|
000001c0  ff ff 07 fe ff ff 02 00  00 00 8a a9 5c 11 00 fe  |............\...|
000001d0  ff ff 05 fe ff ff 8c a9  5c 11 39 6a ae 03 00 00  |........\.9j....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

Where do I go from here? Please help! I'm on the verge of tears >.<;!

---

### Post by drs305 on 2010-12-03
> **DvineINFEKT said:**
> 
Where do I go from here? Please help! I'm on the verge of tears >.<;!

DvineINFEKT.

Welcome to the Ubuntu Forums.

No crying. However, head banging *is* allowed.  	](*,)

You have a wubi install  (sdb5) and a Maverick install on sdb6. This will get your Maverick working (most likely). Assuming you are on the LiveCD, open a terminal and run these commands. Do NOT put the partition number in the second command:
```
sudo mount /dev/sdb6 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```
After it runs, reboot, and make sure the BIOS boots your sdb drive (640GB) one first. Once it boots, run "sudo update-grub".

---

### Post by ck007 on 2010-12-04
Hi,

I am bit new to linux and specially all this command prompts.

I installed Ubuntu on an external hard disk and took it to connect it to another system, but it is failing to boot and getting an error:

```

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdine)
   - Check rootdelay = (did the system wait long enough?)
   - Check root = (did the system wait for right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sdc1 does not exist. Dropping to a shell!

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built in shell (ash)


```

Please let me know how to rectify this error.

I tried all steps that is shown at first post but then i don know what to give as sdx,y in last part of steps so could not complete steps.

Please help...!!!

---

### Post by drs305 on 2010-12-04
> **ck007 said:**
> Hi,

I am bit new to linux and specially all this command prompts.

I installed Ubuntu on an external hard disk and took it to connect it to another system, but it is failing to boot and getting an error:

Please let me know how to rectify this error.

I tried all steps that is shown at first post but then i don know what to give as sdx,y in last part of steps so could not complete steps.

Please help...!!!

Please go to the following site and download the boot info script. Run it from the LiveCD/Ubuntu install CD and then post the contents of the RESULTS.txt. It will help us determine the status of your boot files.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by mps69 on 2010-12-04
Like everyone else unfortunately I'm having the same boot problems
I've tried a few time to get myself back up and running but seem to hit a bit of a brick wall.
Dual booting using Wubi XP Home and 10.04. I've also got the 10.10 Live CD up and running
The Results.txt is as follows
```
              
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => HP/Gateway is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk /boot/grub/core.img

sdb2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.8 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders, total 60058656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    30,732,344    30,732,282   7 HPFS/NTFS
/dev/sda2          30,732,345    60,050,969    29,318,625   5 Extended
/dev/sda5          30,732,408    60,050,969    29,318,562   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     7,076,159     7,076,097   c W95 FAT32 (LBA)
/dev/sdb2    *      7,076,160   101,833,199    94,757,040   7 HPFS/NTFS
/dev/sdb3         101,833,200   312,575,759   210,742,560   5 Extended
/dev/sdb5         101,833,263   228,417,839   126,584,577   7 HPFS/NTFS
/dev/sdb6         228,417,903   312,575,759    84,157,857   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       ef111d81-54c0-483e-8489-f9151ec48bd9   ext4                                     
/dev/sda1        EAC80987C809536D                       ntfs       Spare                         
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6EDC9872DC983675                       ntfs       Family Drive                  
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1BC3-2411                              vfat       PRESARIO_RP                   
/dev/sdb2        92F48B27F48B0D23                       ntfs       Boot Drive                    
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        84EEAB7BB09BD020                       ntfs       Spare                         
/dev/sdb6        6B79617F2F385B04                       ntfs       Spare                         
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb1/boot.ini: ================================

[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
C:\wubildr.mbr = "Ubuntu"

================================ sdb2/boot.ini: ================================

[boot loader]
timeout=10
default=C:\wubildr.mbr

[operating systems]
C:\wubildr.mbr="Ubuntu"
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

=================== sdb2: Location of files loaded by Grub: ===================


    hpGB: boot/grub/core.img

======================== sdb2/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ntfs
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 92f48b27f48b0d23
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ntfs
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 92f48b27f48b0d23
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
	insmod ntfs
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 92f48b27f48b0d23
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
	insmod ntfs
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 92f48b27f48b0d23
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
	insmod ntfs
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 92f48b27f48b0d23
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
	insmod ntfs
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 92f48b27f48b0d23
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sdb1)" {
	insmod fat
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 1bc3-2411
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu (on /dev/sdb2)" {
	insmod ntfs
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 92f48b27f48b0d23
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdb2/Wubi/etc/fstab: =============================

proc                          /proc                proc     nodev,noexec,nosuid         0  0  
/dev/sdb2                     /host                fuseblk  nosuid,nodev                0  0  
/dev/sda5                     /media/Family_Drive  ntfs-3g  defaults,locale=en_GB.utf8  0  0  
#/dev/sdc1                     /media/Music         ntfs-3g  nosuid,nodev                0  0  
#/dev/sdd1                     /media/My\040Book    ntfs-3g  nosuid,nodev                0  0  
/dev/sda1                     /media/Spare         ntfs-3g  defaults,locale=en_GB.utf8  0  0  
/dev/sdb5                     /media/Spare_        ntfs-3g  defaults                    0  0  
/dev/sdb6                     /media/Spare__       ntfs-3g  defaults                    0  0  
/dev/sdb1                     /media/sdb1          vfat     defaults                    0  0  
#/dev/sdc5                     /media/sdc5          ntfs     nls=iso8859-1,ro,umask=000  0  0  
#/dev/sdc6                     /media/sdc6          ntfs-3g  defaults,locale=en_GB.utf8  0  0  
#/dev/sdd5                     /media/Back\040Up    ntfs-3g  nosuid,nodev                0  0  
#/dev/sdd6                     /media/Movies        ntfs-3g  nosuid,nodev                0  0  
/host/ubuntu/disks/root.disk  /                    ext4     loop,errors=remount-ro      0  1  
/host/ubuntu/disks/swap.disk  none                 swap     loop,sw                     0  0  

================= sdb2/Wubi: Location of files loaded by Grub: =================


   1.5GB: boot/grub/grub.cfg
   7.9GB: boot/initrd.img-2.6.32-25-generic
  10.6GB: boot/initrd.img-2.6.32-26-generic
  15.3GB: boot/vmlinuz-2.6.32-25-generic
  14.5GB: boot/vmlinuz-2.6.32-26-generic
  10.6GB: initrd.img
   7.9GB: initrd.img.old
  14.5GB: vmlinuz
  15.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```
If some kind person would point me in the right direction, and if need be treat me like an eight year old, if they need to explain thing ;)
I'm sorely tempted once this is fix just to format the drive and go completely with Ubuntu, but meanwhile I need a couple of files off the Ubuntu side before I do anything.
TIA, if there is more information required I be able to get it asap.

---

### Post by drs305 on 2010-12-04
> **mps69 said:**
> Like everyone else unfortunately I'm having the same boot problems.

The first thing to try is to copy the c:\ubuntu\winboot\wubildr file to c:\

You can do this from the LiveCD via these commands:
```
sudo mkdir /mnt/windows /mnt/wubi
sudo mount /dev/sd**b2** /mnt/windows
cp /mnt/windows/ubuntu/winboot/wubildr /mnt/windows
```

Reboot and see if copying Ubuntu's wubildr file to Windows restored your Ubuntu boot. If not, please tell us what is happening when you try to boot Ubuntu:

Do you see the "Ubuntu" option?
When you select it, what happens?  (Include error messages if you can.)

Bonus: After running the first command above, if you just want to view your Wubi files, you can mount the "root.disk" file with the following command and view/edit them. They will be located in /mnt/wubi.
```
sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/wubi
```

---

### Post by mps69 on 2010-12-04
Firstly thanks for taking a look at my problem.
I carried out the commands as per the instructions but nothing has changed.
When I boot up, I am first of all given the choice of which OS I boot into, Ubuntu, Windows XP or Windows recovery Mode.
When I choose Ubuntu, I end up with:
Minimal BASH-like line editing is supported....
and the command prompt:
GRUB>
The only why I can get out of this is using Ctrl-Alt-Del, this reboots the system.
I can still boot into Windows fortunately enough.
I also tried the "bonus" command, but this didn't seem to mount any drive that I could see.

---

### Post by drs305 on 2010-12-04
> **mps69 said:**
> I also tried the "bonus" command, but this didn't seem to mount any drive that I could see.

When you run the command you won't see a response in the terminal (unless there is an error). But your Wubi files should now be mounted on /mnt/wubi. If you open a file browser and look under /mnt/wubi you should see your Ubuntu files.

Back to the boot issue. Run the commands again, *including the last one to mount root.disk*.
```
sudo mkdir /mnt/windows /mnt/wubi
sudo mount /dev/sdb2 /mnt/windows
sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/wubi
gksu gedit /mnt/wubi/boot/grub/grub.cfg
```

The Wubi grub.cfg file should be open for editing. Normally we don't edit this file, but in this case it's the easiest way to fix things.

Delete every line before the first "menuentry" line (it will probably be about 40 lines down). Save the file and try rebooting again.

---

### Post by mps69 on 2010-12-04
Can't thank you enough for your time, I have my wonderful Ubuntu back up and running after editing the GRUB. =D>
Just in case things go pear-shaped again what is the best way to back up the GRUB file, or how could it be done?
Cheers

---

### Post by drs305 on 2010-12-04
> **mps69 said:**
> Can't thank you enough for your time, I have my wonderful Ubuntu back up and running after editing the GRUB. =D>
Just in case things go pear-shaped again what is the best way to back up the GRUB file, or how could it be done?
Cheers

The good news is that the devs are aware of the problem and have released a patch. It may not have found it's way into the Ubuntu Grub files yet but should shortly.

You ask a good question.
To prevent this from happening again, if you are in Wubi, create a temp folder in /boot called "grubbackup" (or something). Move *all* the files and the *locale* folder *except* **grub.cfg** and **grubenv** (if it exists) to the backup folder. All that should be in /boot/grub are those two files. To move the others, you have to do it as root so open nautilus as root (gksu nautilus /boot/grub). 

Moving the files should allow you to run "update-grub" in the future and not have to edit the grub.cfg file again.

There is another thing you can do to make things a bit easier if it fails again for the same reason. 

As for a backup, here is what I would like you to try (the next time you boot, instead of clicking on the menuentry, try the "configfile" method after you have created grub.bak.cfg:

Make a copy of the 'edited/shortened' grub.cfg file and save it as "grub.bak.cfg" in the /boot/grub folder.

If Wubi fails again after a grub update:
If you can get to the Grub menu, you should be able to enter the Grub terminal by pressing "c". Once there, type the following (assuming your Windows is on sda1):
```
configfile (hd0,1)/boot/grub/grub.bak.cfg
```

I think the failure will occur before you get to the Grub menu. If you can't do the above, you can mount your Wubi install (root.disk) and copy grub.bak.cfg to grub.cfg. (You won't have to edit grub.cfg). This is a short term fix, as over time the menuentry in grub.bak.cfg may no longer work if that kernel isn't available in Wubi any longer due to updates.

---

### Post by Phillip_C on 2010-12-08
Hey, I'd like to say that this is a fantastic thread.  Ahem, now to the juicy stuff.  I'm getting a Grub rescue problem after installing an update today on my laptop, and it kinda sucks.

Pertinent info:

- Laptop is an ASUS N71JQ
- I've partitioned my HDD such that I am under the "Wubi" category, done with the standard partitioning thing when I first got the computer
- Did not download and install updates for Ubuntu 10.10 until today, and upon restart I got the Grub Rescue dealio.


Okay, so I read the thread up and down and tried to go step be step for Wubi users.  Hilariously, the very first command, "is" command returns "Unknown command 'is'".  So, I really have no clue where Ubuntu is on my HDD now.  Wonderful!  Moving along the list, step 2 obviously doesn't work, but step 3 and 4 did(I think.  It returned:

prefix=(hd0)/boot/grub
root-hd0
setprefix=(memdisk)/boot/grub
setroot=(loop0)

But now we get to step 5, and I return this:

error: no such disk.

So yeah, I'm at a complete loss for what to do.  Nothing I've looked up has really given me an answer, so hopefully you guys can figure it out.

Thanks!

---

### Post by drs305 on 2010-12-08
Phillip_C,

Welcome to the Ubuntu forums.  :-)

One of two things will most likely fix your Wubi problem. Copying Ubuntu's *wubildr* file to the Windows C:\ directory, or editing the grub.cfg file and removing most of it's contents.

Fortunately, forum member *Rubi1200* has just put out a "Wubi Megathread" that specifically covers how to do those things.

Here is the link:
[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by Phillip_C on 2010-12-08
Awesome, and thanks for the prompt response.

---

### Post by Phillip_C on 2010-12-08
Nevermind, fixed.

---

### Post by jlinux86 on 2010-12-11
Hello, I was stuck at the same screen after I updated, but I found redemption through following this thread: 

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

I simply booted to Windows, downloaded the file to my C:/ drive and replaced the old one, then restarted. Booted into Ubuntu just fine.

---

### Post by burnz2304 on 2010-12-13
Hello all, i hope someone still monitors this thread.
Alright i have my thinkpad x200 tablet i had it dual booting win7 (original) and a ubuntu 10. i decided i no longer needed linux on the laptop because i just use the desktop for linux. So i deleted the partition through the windows management when i rebooted im stuck with

error: unknown filesystem.
grub rescue> 


i have read the forum and i do know to fix this issue i need a windows disc. well the laptop did not come with one and it also doesnt have a CD drive at all. so someone please help me get my laptop booting my windows 7 again

---

### Post by drs305 on 2010-12-13
> **burnz2304 said:**
> i have read the forum and i do know to fix this issue i need a windows disc. well the laptop did not come with one and it also doesnt have a CD drive at all. so someone please help me get my laptop booting my windows 7 again

You can run unetbootin to create a bootable Ubuntu thumb drive. 
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

Change your BIOS if necessary to boot the external/thumb drive first.

Once booted into Ubuntu, open a terminal and run these two commands. Don't worry about the lilo messages since you aren't going to be fully installing it. As long as your Windows partition has the boot flag and the boot files are not damaged or missing, this should restore your Windows boot process.

Assuming your Windows drive is "sda":
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by burnz2304 on 2010-12-14
wow that worked perfectly, i love you :) 
Do you have any distro reccomendations for someone coming from windows to learn linux on?

---

### Post by drs305 on 2010-12-14
> **burnz2304 said:**
> wow that worked perfectly, i love you :) 
Do you have any distro reccomendations for someone coming from windows to learn linux on?

Ubuntu has several flavors and spinoffs: Ubuntu, Xubuntu, Kubuntu, then Lubuntu, Edbuntu, etc.  Installing Ubuntu you can switch Desktops with some of the others to see which interface you like the best.

And of course will all of those comes the support of the Ubuntu forum.  ;-)

If you have specific hardware needs some other linux distros might prove a better fit, especially if your system's resources are very small. "Distrowatch" covers most versions you might consider.
[http://distrowatch.com/]("http://distrowatch.com/")

---

### Post by Alpine725 on 2010-12-31
Well, having read through all - well, almost all - I left out the ones I thought didnt apply to my situation (wubi, non-ubuntu, etc...) - I am still trying to get my grub back.

First of all, I fired up my Toshiba Satellite A105 laptop (on which ubuntu 10.04 has been the only OS - no other partitions - since its release) this morning for the first time in a week (was away for Christmas).  After firing it up, needing a charge, I plugged in my iPod Touch.  I dont think it would have affected the startup since ubuntu typically starts to usable in about 45 seconds to a minute and I plugged in the iPod after a couple minutes.  When I sat down to use the laptop, I had the "task bar" at the top with a blank desktop (not the picture I left when I shut it down a week ago) and several notification boxes that instead of english text, they all had squares where the text would be and at the bottom of each, it said something about something being prevented from running.  I had the option of 'delete' and 'dont delete'.  Thinking back to my windows boxes, I saw the squares for text and though "malware" and proceeded to click on 'delete'.  After that, the only thing that worked was the mouse pointer.  I shut down and rebooted and here I am.

After the Toshiba s[plash screen, all I see is:
error: unknown filesystem
grub rescue>

I have honestly tried the commands in the first post of this thread and the only commands that do NOT return "Unknown command '<coimmand>'" are 'ls' and 'set'.  When I tried the 'insmod linux' command, I get:
error: unknown filesystem
grub rescue>

ls returns:
(hd0) (hd0,5) (hd0,1) (fd0) (fd1) - in that order

I have tried 'set'ting both partitions and still get the same thing.

I downloaded and burned ubuntu 10.10 onto a CD.  I can get to the screen where I can choose to install or try it (on this screen it does connect to my network and I can shutdown, restart, suspend or hibernate.  When I click 'try it', it acts like it is loading but I am only left with a black screen and a mouse pointer.

Ordinarily, I wouldnt really care much about it and I would just reinstall the OS, however, I didnt get the chance to back up the sentimental data.

Is there anyone out there than can help me out of my little predicament?

Sorry for the lengthy message but I wanted to make sure I got everything.  I am sure I forgot something so please let me know what it was and I will fill you in.
I thank you very much in advance!!!

PS - Since I cant seem to figure out how to get the boot info, I was unable to post the text file you had asked for.

---

### Post by drs305 on 2010-12-31
Alpine725,

Since you are having trouble with the CD, let's try once more booting from the grub prompt.

From the "ls" command I can't be sure which partition Ubuntu is on, but I'll assume it's on sda1 and swap is sda5. If not, you will have to change the values.
sda1 = (hd0,1)
sda5 = (hd0,5)

Try running these commands from the grub prompt. If you get errors you can stop. If the command works or you get no error message, continue with the next command:
```
ls (hd0,1)/boot  # Do you see the vmlinuz and initrd files? If not, try (hd0,5)
ls (hd0,1)/boot/grub # Do you see a lot of *.mod files
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
insmod (hd0,1)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img 
boot
```

If at any point a command fails tell us what the command was and the error message it generated.

---

### Post by joetheplumber67 on 2010-12-31
I have a major problem with "grub rescue>" as well.

I just installed Ubuntu 10.04 on a separate partition on my computer so I can dual boot with Windows 7. However, whenever I boot up, it just says:

Error: file not found.
grub rescue>

I had other dual boot problems before and I have another thread ([http://ubuntuforums.org/showthread.php?t=1654864&page=3](http://ubuntuforums.org/showthread.php?t=1654864&page=3))

The current problems are mostly on page 3, where posts said that Grub 2 may be installed on sda instead of sdb (Ubuntu partition). However, I'm not sure how to fix this? I'm also new to Ubuntu, so I don't know how to fix a lot of things on my own yet.

---

### Post by drs305 on 2011-01-04
johnnyhop,

Not getting the LiveCD to boot may mean you have to use certain kernel options in the "linux" line, but right now I don't know what they are. 

Let's see if we can boot from the grub prompt. If you get the G2 menu, press "c". If you don't see the menu, hold down the SHIFT key during boot until it appears.

Run these commands:
```
ls (hd0,1)/boot/grub  # If you don't see a lot of *.mod files, stop and tell us.
ls (hd0,1)/boot  # If you don't see a vmlinuz-2.6... and initrd.img-2.6... file, stop.
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot
```

If it boots, since your files *appear* ok, it would probably be best to purge/reinstall Grub2 following Steps 2-5 of the following guide:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by Alpine725 on 2011-01-09
> **drs305 said:**
> Alpine725,

Since you are having trouble with the CD, let's try once more booting from the grub prompt.

From the "ls" command I can't be sure which partition Ubuntu is on, but I'll assume it's on sda1 and swap is sda5. If not, you will have to change the values.
sda1 = (hd0,1)
sda5 = (hd0,5)

Try running these commands from the grub prompt. If you get errors you can stop. If the command works or you get no error message, continue with the next command:
```
ls (hd0,1)/boot  # Do you see the vmlinuz and initrd files? If not, try (hd0,5)
ls (hd0,1)/boot/grub # Do you see a lot of *.mod files
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
insmod (hd0,1)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img 
boot
```

If at any point a command fails tell us what the command was and the error message it generated.
@drs305
I thank you very much for the reply.  Sorry I didnt get back to you sooner, I was waiting for the email notification saying someone had replied to the thread but nothing came.

Just as you thought, yes, sda1 is the primary partition and sda5 is the swap drive - I confirmed this when I started the install process.

I have tried the commands you suggested:

- ls (hd0,1)/boot
- ls (hd0,1)/boot/grub
Returns - error: unknown filesystem.

- set prefix=(hd0,1)/boot/grub
- set root=(hd0,1)
These two appear to work (brings me back to the grub rescue prompt.

- insmod (hd0,1)/boot/grub/linux.mod
Returns - error: unknown filesystem.

- linux /vmlinuz root=/dev/sda1 ro
- initrd /initrd.img 
- boot
linux, initrd and boot are "Unknown command"s

Is there anything else I can try?  If not, and I tried to install ubuntu 10.10 along side of ubuntu 10.04, given that the 10.04 install is using the full drive, would I lose my personal data from the 10.04 install?

Thanks again!!

PS - Just for laughs, I tried to run off the CD again - same result as before.  :-(

---

### Post by drs305 on 2011-01-09
> **Alpine725 said:**
> Is there anything else I can try?  If not, and I tried to install ubuntu 10.10 along side of ubuntu 10.04, given that the 10.04 install is using the full drive, would I lose my personal data from the 10.04 install?

Yes, I believe unfortunately you would lose your personal data if you installed 10.10 over 10.04 from a CD, assuming your data was in the 10.04 partition. Note: There is an option during the installation that allows you to select whether to format the partition during the installation. If that is not checked, it *might* not overwrite your data files but I wouldn't count on that. Someone else may be able to answer this.

From your last post, I think you still cannot boot any Ubuntu LiveCD? 

At the grub prompt, do you get a list of partitions by just running: *ls*  ? If it doesn't work, try setting the 'prefix' line first (as described in the earlier post).

---

### Post by Alpine725 on 2011-01-09
> **drs305 said:**
> Yes, I believe unfortunately you would lose your personal data if you installed 10.10 over 10.04 from a CD, assuming your data was in the 10.04 partition. Note: There is an option during the installation that allows you to select whether to format the partition during the installation. If that is not checked, it *might* not overwrite your data files but I wouldn't count on that. Someone else may be able to answer this.

From your last post, I think you still cannot boot any Ubuntu LiveCD? 

At the grub prompt, do you get a list of partitions by just running: *ls*  ? If it doesn't work, try setting the 'prefix' line first (as described in the earlier post).

Thanks for the prompt response.
Unfortunately you are correct...I still get a blank screen with the cursor.  I suppose it could be a display driver issue.

Sorry for not mentioning it before...yes, I do get a list of drives/partitions with the "ls" command.  They appear in the same order as in my first post.

---

### Post by drs305 on 2011-01-09
> **Alpine725 said:**
> Thanks for the prompt response.
Unfortunately you are correct...I still get a blank screen with the cursor.  I suppose it could be a display driver issue.

Is this when you boot the CD? If so, you can try changing the options while booting the CD. After selecting the language, press F6 and select the 'nomodeset' option. If it's a video problem that is the problem with the LiveCD this may solve it. 

The above is based on a doc I created about the options available while booting the LiveCD:
[https://help.ubuntu.com/community/LiveCDBootOptions]("https://help.ubuntu.com/community/LiveCDBootOptions")

---

### Post by Alpine725 on 2011-01-09
> **drs305 said:**
> Is this when you boot the CD? If so, you can try changing the options while booting the CD. After selecting the language, press F6 and select the 'nomodeset' option. If it's a video problem that is the problem with the LiveCD this may solve it. 

The above is based on a doc I created about the options available while booting the LiveCD:
[https://help.ubuntu.com/community/LiveCDBootOptions]("https://help.ubuntu.com/community/LiveCDBootOptions")
Well sir, you rock!  I tried the 'nomodeset' switch on startup and I got into the LiveCD.  All I had for a CD was version 10.10 so for anyone else reading this, I had to tap the F6 button as soon as the, in my case, Toshiba splash screen went away to get to the menu options.  Otherwise, it loads to the GUI version and getting to the F6 switch options is a little less than obvious.

Now, being a windows user trying to convert to linux/ubuntu, I amk stuck as to what to do once I get in.  I checked out Disk Utility but didnt see any obvious ways to fix the drive to a bootable state.

I am going to check out the HOWTO you (drs305) wrote on purging and reinstalling Grub2.  If you think there I can do something else first, I will wait until I hear back before I do anything drastic.

Thanks again...

---

### Post by drs305 on 2011-01-09
Alpine725,

If your issue was with Grub2 the purge/reinstall will most likely fix it. However, if you are having problems with the blinking cursor with your normal install, you will want to add the **nomodeset** option to the end of the 'linux' line of any menuentry you want to boot. 

When you are reinstalling G2, the installation will present a line on which you can add kernel options. This is where you want to add **nomodeset** in the highlighted area, then tab to OK and press ENTER.

If Grub2 is already installed, you can put it in the "GRUB_CMDLINE_LINUX_DEFAULT=" line of /etc/default/grub.

---

### Post by Alpine725 on 2011-01-09
So...I ran that boot infor script.

How can I get it to you?  Should I copy and post the whole thing here?

---

### Post by drs305 on 2011-01-09
> **Alpine725 said:**
> So...I ran that boot infor script.

How can I get it to you?  Should I copy and post the whole thing here?

Open the RESULTS.txt and copy the entire contents. 
Start a new post, and press the # icon in the post's menubar. 
This will generate [noparse] ```
 
``` [/noparse] tags. 
Paste the content between the code tags. Pasting between tags will shorten the space it takes in the post.

Please briefly restate what you *currently* are trying to do and what is happening so new readers don't have to go back too far to catch up.  ;-)

---

### Post by Alpine725 on 2011-01-09
> **drs305 said:**
> Open the RESULTS.txt and copy the entire contents. 
Start a new post, and press the # icon in the post's menubar. 
This will generate [noparse] ```
 
``` [/noparse] tags. 
Paste the content between the code tags. Pasting between tags will shorten the space it takes in the post.

Please briefly restate what you *currently* are trying to do and what is happening so new readers don't have to go back too far to catch up.  ;-)
I started a new thread...

[http://ubuntuforums.org/showthread.php?p=10337228#post10337228](http://ubuntuforums.org/showthread.php?p=10337228#post10337228)

Please say you can help!!

---

### Post by didkaticos on 2011-01-25
[B][B]OK, here I am (again), a complete newby trying to fix my issue. I ran the Boot Info, and I got this:

[/B][/B]```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe621e621

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,420,479   234,420,417   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A0947B03947ADAEC                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu"
```

I am using Wubi with Ubuntu 9.10 the Karmic Koala. When I choose Ubuntu, it makes a long beep, and then I got the following screen:
 	```
  	GNU GRUB version 1.97
[ Minimal BASH-like line editing is supported. For the first word, TAB
lists possible command completions. Anywhere else TAB lists possible
device/file completions.

sh:grub> 
```

[COLOR=Blue]*Last time that I had the same problem I was able to [I]replace the wubildr on C:drive and fix all my problems. I tried today to do the same thing again, but it didn't work.*[/I][/COLOR]******[I]If you could help me, I would really appreciate it. Thanks a lot!
[/I]

---

### Post by bcbc on 2011-01-25
@didkaticos,
Your root.disk is missing. There should be a directory c:\ubuntu\disks\ that contains the root.disk and swap.disk.

---

### Post by didkaticos on 2011-01-25
> **bcbc said:**
> @didkaticos,
Your root.disk is missing. There should be a directory c:\ubuntu\disks\ that contains the root.disk and swap.disk.Thanks bcbc! So, what do I need to do? Remember that I am totally illiterate, so please, be patient, OK?

---

### Post by bcbc on 2011-01-25
> **didkaticos said:**
> Thanks bcbc! So, what do I need to do? Remember that I am totally illiterate, so please, be patient, OK?
Well... honestly I don't know what causes this and I'm not sure how to fix it either. In the cases I've seen, it doesn't end well :(
Hopefully you have your important data backed up.

In [one recent case]("http://ubuntuforums.org/showthread.php?t=1674576") it appears that the c:\ubuntu\disks directory was corrupted. You could try running chkdsk from windows but I recall other cases where this did nothing, and possibly booting windows could overwrite these files further.

Sorry I can't be more help

---

### Post by didkaticos on 2011-01-25
> **bcbc said:**
> Well... honestly I don't know what causes this and I'm not sure how to fix it either. In the cases I've seen, it doesn't end well :(
Hopefully you have your important data backed up.

In [one recent case]("http://ubuntuforums.org/showthread.php?t=1674576") it appears that the c:\ubuntu\disks directory was corrupted. You could try running chkdsk from windows but I recall other cases where this did nothing, and possibly booting windows could overwrite these files further.

Sorry I can't be more helpUnfortunately I don't have my important data backed up, that's the main reason why I wanted to fix this, instead of reinstall it.

Oh well... Thanks anyway for your help!

---

### Post by cirkomortale on 2011-01-25
Please help, I lose all day trying to solve this. ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    34,836,479    34,836,417   7 HPFS/NTFS
/dev/sda2          34,845,046   312,580,095   277,735,050   f W95 Ext d (LBA)
/dev/sda5          34,845,048   301,855,679   267,010,632   7 HPFS/NTFS
/dev/sda6         301,856,768   305,762,303     3,905,536  82 Linux swap / Solaris
/dev/sda7         305,764,352   312,580,095     6,815,744  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        253B29687D93D951                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        89EC3F1B4730B3BE                       ntfs                                     
/dev/sda6        e3d59482-c810-4fe4-9479-5e2b13cd4ff9   swap                                     
/dev/sda7        a02327b9-df03-486f-9d50-8333f1de2d0a   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         A423-A7D9                              vfat       USB                           

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /media/USB               vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set a02327b9-df03-486f-9d50-8333f1de2d0a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set a02327b9-df03-486f-9d50-8333f1de2d0a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a02327b9-df03-486f-9d50-8333f1de2d0a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a02327b9-df03-486f-9d50-8333f1de2d0a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a02327b9-df03-486f-9d50-8333f1de2d0a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a02327b9-df03-486f-9d50-8333f1de2d0a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a02327b9-df03-486f-9d50-8333f1de2d0a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a02327b9-df03-486f-9d50-8333f1de2d0a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 253b29687d93d951
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=a02327b9-df03-486f-9d50-8333f1de2d0a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e3d59482-c810-4fe4-9479-5e2b13cd4ff9 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 157.6GB: boot/grub/core.img
 157.6GB: boot/grub/grub.cfg
 158.3GB: boot/initrd.img-2.6.35-22-generic
 157.6GB: boot/vmlinuz-2.6.35-22-generic
 158.3GB: initrd.img
 157.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ef 49 8a e5 62 61 15 a1  f3 ec 11 83 f3 4d 35 bd  |.I..ba.......M5.|
00000010  a8 29 10 b6 68 62 fa 18  d6 b5 98 90 d5 06 8b 9e  |.)..hb..........|
00000020  8d 31 ea 27 06 ad a7 53  ff fe 3b fe f3 82 64 ae  |.1.'...S..;...d.|
00000030  07 0d b9 7b 09 5e 2f 88  86 34 f8 67 49 05 fc 56  |...{.^/..4.gI..V|
00000040  4b 49 5e 2c 33 1a 36 27  32 2e 82 28 46 19 bc 33  |KI^,3.6'2..(F..3|
00000050  16 19 d1 83 fe 68 5f c1  c7 23 5f 86 c3 3f 9e fc  |.....h_..#_..?..|
00000060  b4 16 49 c9 7a e3 22 f2  b3 c5 ec 0b 01 de e1 4a  |..I.z."........J|
00000070  97 d6 0e 2b 0a 4b d8 36  5e c1 f4 e5 5d 40 31 fa  |...+.K.6^...]@1.|
00000080  d8 d7 01 2c bf 58 3e 0e  f7 0b 24 13 fc a8 f5 16  |...,.X>...$.....|
00000090  8b 24 0b c9 a8 b5 0e 2f  09 5b 6c 43 14 38 5d 95  |.$...../.[lC.8].|
000000a0  7c ec 13 ea 8a 57 d3 1a  c8 c6 ec c4 a4 e2 f2 d4  ||....W..........|
000000b0  c2 ef c4 99 f5 97 0d e1  c7 a9 ec 66 5a d7 c2 a1  |...........fZ...|
000000c0  6c 81 65 c0 4a 23 f9 d6  c4 7c 6c 44 f9 e4 a0 96  |l.e.J#...|lD....|
000000d0  22 99 71 88 d4 d0 98 66  03 bf f7 bf 87 a6 30 37  |".q....f......07|
000000e0  bd ed 32 2d ce 3e 75 14  a7 73 94 c3 ce 43 3c 16  |..2-.>u..s...C<.|
000000f0  10 0b 7b fe 64 02 c5 bc  33 57 84 b7 2b 24 e2 34  |..{.d...3W..+$.4|
00000100  f3 c1 ce 21 d3 41 9d 09  85 ff 42 ba 4f 43 17 8b  |...!.A....B.OC..|
00000110  57 b6 0b d5 9f f9 a0 cd  39 56 cf 02 e1 f9 07 f6  |W.......9V......|
00000120  00 85 6c 12 b9 39 56 91  01 f2 f6 88 95 a2 3a 25  |..l..9V.......:%|
00000130  b6 8c c3 93 95 60 ba 1f  8a 55 e7 4d 2b 16 38 5f  |.....`...U.M+.8_|
00000140  cf 51 50 05 fc 56 2c ac  fb 6d 02 ef eb 12 03 49  |.QP..V,..m.....I|
00000150  05 bb a5 6f 4a 4e e1 7a  d8 51 58 f3 5c d4 7d 64  |...oJN.z.QX.\.}d|
00000160  9e d0 73 74 b3 46 a2 f2  a3 4c 2b a0 12 41 7b 84  |..st.F...L+..A{.|
00000170  c2 bd dc 64 46 e8 4d fa  c6 60 f3 e3 a4 89 85 8c  |...dF.M..`......|
00000180  0d 15 af 01 4f c4 6b c2  65 7c 60 2e 44 4d 5a e0  |....O.k.e|`.DMZ.|
00000190  39 33 41 24 30 4b fd ef  ff af d2 37 8a 07 9a 78  |93A$0K.....7...x|
000001a0  9d e9 ce 0b 86 3c 4c de  25 31 e3 a1 b9 e7 d2 42  |.....<L.%1.....B|
000001b0  a7 8b c7 2b 3d 46 40 b0  16 ac f1 7e 3d 58 00 ef  |...+=F@....~=X..|
000001c0  ff ff 07 ef ff ff 02 00  00 00 48 42 ea 0f 00 fe  |..........HB....|
000001d0  ff ff 05 fe ff ff 4a 42  ea 0f 40 9c 3b 00 00 00  |......JB..@.;...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```i try
sudo mount /dev/sda7 /mnt 
sudo grub-install --root-directory=/mnt /dev/sda
but it is not working 
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.
even put in bioss to boot first from hdd
same screen
error: no such partition
grub rescue>

---

### Post by drs305 on 2011-01-25
cirkomortale,

Unfortunately I won't be home and have time to take a closer look at this until late tomorrow. But don't worry, your files look ok so you haven't lost your data. 

Have you already tried changing the BIOS to boot the LiveCD first and then running the commands?

If the LiveCD boots first you should not get a grub rescue prompt. Running the commands again may fix it. 

If you don't get help and want to try something else without waiting, you can boot the LiveCD and completely remove and reinstall Grub2 using the 'Chroot' link in my signature line.

---

### Post by cirkomortale on 2011-01-25
ajaja i do all this all steps, reinstall grub on MBR 
did not help
during reinstalation of grub i have same warning that sector 32 is used.... warn: Sector 32 is already in use by FlexNet; avoiding it.  This  software may cause boot or other problems in future.  Please ask its  authors not to store data in the boot track..

only i was try to instal on mbr, now i will try to install on linux partition sda7 and it is my last chance, i will update result if is negative or positive
i hope we gona solve this tommorow

=)

not results,
please help

maby i will wait version 11, i never have such kind of problem and i can see on forum that is quite massive

---

### Post by drs305 on 2011-01-26
> **cirkomortale said:**
> ajaja i do all this all steps, reinstall grub on MBR 
did not help
during reinstalation of grub i have same warning that [COLOR="Red"]sector 32 is used.... warn: Sector 32 is already in use by FlexNet[/COLOR]; avoiding it.  This  software may cause boot or other problems in future.  Please ask its  authors not to store data in the boot track..

This is the problem. Certain Windows programs such as Dell DataSafe, FlexNet and others write to an area in the MBR Grub2 normally tries to use. If prevented from writing to this area Grub2 may fail to install. 

One solution is to boot into Windows (if possible) and remove the Adobe FlexNet program. You will be able to find other solutions by searching for FlexNet and boot issues.

---

### Post by cirkomortale on 2011-01-27
> **drs305 said:**
> This is the problem. Certain Windows programs such as Dell DataSafe, FlexNet and others write to an area in the MBR Grub2 normally tries to use. If prevented from writing to this area Grub2 may fail to install. 

One solution is to boot into Windows (if possible) and remove the Adobe FlexNet program. You will be able to find other solutions by searching for FlexNet and boot issues.

Update,
Really strange, i format my hdd, make fdisk on mbr install fresh clean copy of XP, right after, without installing any driver for XP, I was try to install ubuntu 10.10 but after instalation it was all same. :lolflag:  I think that this is one fine failure. I am tired i think it is time for some other distribution.

---

### Post by drs305 on 2011-01-27
> **cirkomortale said:**
>  I think that this is one fine failure. I am tired i think it is time for some other distribution.

I'm sorry you spent all that time and weren't able to get Ubuntu installed. Do you get the same error message about FlexNet? If so, any distribution which uses Grub2 that you install the same way will give you the same error message.

In addition to Adobe Flexnet there are other apps such as Dell DataSafe, HP ProtectTools, and Dell Recovery that can also do the same thing and need to be removed. If it's a Dell, don't remove the Dell recovery partition, but it's ok to remove the Dell Utility partition.

Good luck with whatever decision you make.

---

### Post by cirkomortale on 2011-01-29
> **drs305 said:**
> I'm sorry you spent all that time and weren't able to get Ubuntu installed. Do you get the same error message about FlexNet? If so, any distribution which uses Grub2 that you install the same way will give you the same error message.

In addition to Adobe Flexnet there are other apps such as Dell DataSafe, HP ProtectTools, and Dell Recovery that can also do the same thing and need to be removed. If it's a Dell, don't remove the Dell recovery partition, but it's ok to remove the Dell Utility partition.

Good luck with whatever decision you make.

It is old laptop HP nx7300. No protective tools, nothing similar, I am just curious what is problem. I will try now with some other hdd just to try to locate problem. :(


....................................................
finally i install windows 7 and Ubuntu 10.10 and all works, there is some problem with windows xp professional and Ubuntu 10.10,

all people who trying to install ubuntu, and haveing problem with that i can recommended to keep trying because ubuntu 10.10 really rulez. I stop to use windows. Ubuntu 10.10 rulez.

---

### Post by Kozlov8 on 2011-02-06
I'm REALLY confused. I tried to boot Ubuntu (I dual-boot W7 and Ubuntu), and that command screen popped up, only with a partition error before the grub rescue. I don't know what to do; i'm a beginner.
 
Please help! All my vital files are on W7.

---

### Post by drs305 on 2011-02-06
> **Kozlov8 said:**
> I'm REALLY confused. I tried to boot Ubuntu (I dual-boot W7 and Ubuntu), and that command screen popped up, only with a partition error before the grub rescue. I don't know what to do; i'm a beginner.
 
Please help! All my vital files are on W7.

Please download and the run boot info script from the following link. You can do this from the LiveCD. It will generate a file called RESULTS.txt.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")
 
If you are using Wubi, (Ubuntu within Windows), please go to this thread:
[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")
and post the contents of RESULTS.txt and explain what is happening.

If you are running a normal Ubuntu system (independent partition), post the contents of RESULTS.txt here.

---

### Post by Kozlov8 on 2011-02-06
> **drs305 said:**
> Please download and the run boot info script from the following link. You can do this from the LiveCD. It will generate a file called RESULTS.txt.
[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)
 
If you are using Wubi, (Ubuntu within Windows), please go to this thread:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
and post the contents of RESULTS.txt and explain what is happening.
 
If you are running a normal Ubuntu system (independent partition), post the contents of RESULTS.txt here.
 I don't have the LiveCD. And also, I don't think the Ubuntu partition exists on my computer anymore. I deleted it, and it resulted in this error.... (I'm on a diff computer).
 
Thanks.

---

### Post by drs305 on 2011-02-07
> **Kozlov8 said:**
> I don't have the LiveCD. And also, I don't think the Ubuntu partition exists on my computer anymore. I deleted it, and it resulted in this error.... (I'm on a diff computer).
 
Thanks.

Post #7 by *oldfred* is a good summary of Windows repair options.
[http://ubuntuforums.org/showthread.php?p=9826152]("http://ubuntuforums.org/showthread.php?p=9826152")

Pointing to the Windows bootloader from the MBR is fairly easily accomplished from the Ubuntu LiveCD, but if you don't have one available the above link can provide methods to restore Windows.

---

### Post by danbuter on 2011-02-07
I'm stuck on grub rescue. I had started shredding my entire hd1, since I plan to resell the laptop. However, now when I boot, I get the "error: unknown filesystem" and then grub rescue prompt. Grub rescue lets me ls and set, but when I try to insmod, I get unknown filesystem. I've tried booting from the Ubuntu LiveCD and a SuberGrub livecd (both on USB, as I have no CD drive), and I always end up back at the grub rescue prompt. Any help would be appreciated.

The ls output is 
(hd0) (hd0,msdos5) (hd0,msdos1) (hd1) (hd1,msdos1)

I do not have a Window partition, as I used the entire drive to install ubuntu. I also do not have a Windows install disc.

---

### Post by drs305 on 2011-02-07
> **danbuter said:**
> 
I do not have a Window partition, as I used the entire drive to install ubuntu. I also do not have a Windows install disc.

Are you sure you started shredding your non-OS drive?



Without having the boot info, you could try this from the grub prompt:

Determine if the boot files exist:
```

ls (hd0,1)/boot/grub
ls (hd0,5)/boot/grub
ls (hd1,1)/boot/grub

```
Your Ubuntu partition should display a long list of *.mod files. Substitute the value of *(hd0,1)* and */dev/sda1* below to the correct partition if it is different. 

```
set root=(hd0,1)
set prefix=(hd0,1)/boot/grub
insmod (hd0,1)/boot/grub/linux.mod
linux (hd0,1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,1)/initrd.img
boot

```

---

### Post by danbuter on 2011-02-07
for 0,1 and 0,5 I get: unknown filesystem
for 1,1 I get: hd1,1 cannot get C/H/S values

I tried the other commands, at insmod I get unknown filesystem.

---

### Post by danbuter on 2011-02-07
I was shredding /dev/sda3, I believe.

---

### Post by drs305 on 2011-02-07
danbuter, 

It looks like you will need to work on getting a LiveCD to boot to try to recover your files. Normally when a user gets the grub prompt with a LiveCD it's because the BIOS is still booting the hard drive rather than the CD.

Enter BIOS during the first part of boot. You have to press a key, which one may be displayed on the screen. It's usually a function key (F1-F12) or the DEL key. Once in the BIOS setup, make sure the system is booting the CD first. You should hear the CD spin up as the computer first starts, indicating it's trying to access the CD.

If that still doesn't work, you could try making a bootable flash drive if you BIOS supports it.

---

### Post by danbuter on 2011-02-07
That worked. I thought I had the right USB port loading before the HDD, but it wasn't it. I had 4 USB options, and the only one not in front of the HDD was the one I needed. Thanks! :guitar:

---

### Post by jasonread on 2011-02-09
Hi there, 

I have been happily using a dual boot Vista/UBuntu 10.04 system for some time now. I recently left my laptop with a friend who decided he wanted to check something online; when presented with the bootloader screen he chose what he thought was a Vista loader. I did not see which selection he made (sigh) and he doesn't remember exactly what it said (sigh), The boot process failed and on reboot I get the grub rescue error. ls gives me (hd0), (hd0,5), (hd0,2) and (hd0,1). Set shows me "prefix=(hd0,6)/boot/grub root=hd0,6"

I've tried the ls (hdx.y)/ commands on all the ls partitions and get "unknown filesystem". when I ls (hd0,6)/ it gives me "no such partition".

I have a feeling I am well and truely screwed with recovering my wonderful ubuntu install (it was so fast and looked great!) but perhaps someone out ther has some ideas?

thanks..

---

### Post by jasonread on 2011-02-10
Here is the results of my boot-script

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,482,047    20,480,000  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     20,482,048   256,940,015   236,457,968   7 HPFS/NTFS
/dev/sda3         256,943,671   625,141,759   368,198,089   f W95 Ext d (LBA)
/dev/sda5         333,053,952   625,141,759   292,087,808   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             48     7,831,551     7,831,504   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        D47622BC76229F6C                       ntfs       VistaOS                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        2C16BA5716BA21AE                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        14DD-3835                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

---

### Post by drs305 on 2011-02-10
The Ubuntu partitions are not showing. I'll talk you through TestDisk if you wish to try to restore them or take a look at this site:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

---

### Post by drs305 on 2011-02-12
Update on *jasonread*:
[LIST]
[*]Created a bootable USB device after multiple problems with the CD
[*]Used TestDisk to find and restore the Ubuntu partition
[*]Mounted the Ubuntu partition (now in sda3) and reinstalled Grub2
[LIST]
[*]sudo mount /dev/sda3 /mnt
[*]sudo grub-install --root-directory=/mnt /dev/sda
[/LIST]
[*]Rebooted.
[/LIST]
Ubuntu booted successfully with Grub 2 and also recognized Windows OS.

---

### Post by cirkomortale on 2011-02-20
any idea how to remove Adobe Flexnet?:(

---

### Post by drs305 on 2011-02-21
> **cirkomortale said:**
> any idea how to remove Adobe Flexnet?:(

If you search for "Remove FlexNet" you will find dozens of guides. I rarely use Windows and have not used any of the methods so I can't really recommend one over the other. Please read about the consequences of removing FlexNet as well, and stick to a solution where the poster was able to remove it and  suffered no ill effects to subsequently running Windows software. To possibly solve the Grub2 issue, you would have to find a solution that remove FlexNet, not just disable it, as its contents in the boot sector would need to be removed *if* your Grub2 won't work without this procedure.

---

### Post by nuncio1 on 2011-03-07
Hi to all,,

I am very new to Ubuntu, I had a windows vista on single hard drive (320.1 GB), then I  added a second hard drive (250.1 GB) to install Ubuntu... after the installlation I got the "error : no such device : xxxxxxxxxx grub rescue" message at the start up... nothing else. tried to start with windows vista  cd but didnt work. It didnt see any hard drive letter to pick or any vista installation... 
I have important documents on my vista hard drive (sda: 320.1 GB), right now my first priority is to get access to my vista drive... then install Ubuntu on second hard drive with dual boot with vista.

Please help... 
Thanks to all

attached is the info script result
------------------------------------------------

---

### Post by drs305 on 2011-03-07
nuncio1,

The RESULTS.txt doesn't show any files or Windows formatted partitions on sda, so there is a problem there. Perhaps with the partition table. 

We can get Ubuntu working (and without writing any data to sda, which may be important) by booting a LiveCD and running the following commands:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

Do not use the partition number in the second command.
Reboot, and as it starts to boot enter the BIOS setup and change the first boot device to your 250GB drive.

If you get Ubuntu working then hopefully someone will be able to determine what is wrong with your Windows drive.

---

### Post by nuncio1 on 2011-03-08
Codes are really worked, Ubuntu is now working !!!  thanks a lot :)
 I still dont see my sda harddrive when I click on my computer icon. it shows in disk utulity like that : [IMG]http://img18.imageshack.us/i/screenshotwr.png/[/IMG]
[[IMG]http://img18.imageshack.us/img18/5396/screenshotwr.png[/IMG]](http://img18.imageshack.us/i/screenshotwr.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

pls let me know what can I do to have access to my hard drive again ? 


attached is the new result.txt 

thank you all..

---

### Post by drs305 on 2011-03-08
> **nuncio1 said:**
> pls let me know what can I do to have access to my hard drive again ? 

nuncio1,

Your 'Grub' problem is now solved and your problem now is that either your Windows drive has been wiped clean or the partition table is corrupt. It appears that the Windows drive has been reformatted to a linux format. Do not do anything that might write to sda - it may be possible to recover all your data using something like TestDisk.

In either case, it would be better to open a new thread and don't include 'Grub' or 'Boot' in the title. Many users who might be able to help with partition recovery may not read threads about boot issues.

In addition to attaching the RESULTS.txt, you should probably also include the results of "sudo fdisk -l" in the original post.

---

### Post by drs305 on 2011-03-08
> **systamd4 said:**
> o I have two hard-drives installed in my computer.  One with Windows XP  (Master) and one with Ubuntu (Slave).  A while back, my aunt who works  at a Goodwill store, gave me a couple of hard-drives they had received.

systamd4,

Congratulations, I suppose and welcome to the Ubuntu forums.  

Now, is there something we can help you with?  ;-)

---

### Post by comp_007 on 2011-04-29
@ Friends,

by mistake my partition got deleted where ubuntu 11.04 was residing and due to the same reason i am unable to access it, I also have windows 7 (dual boot),


now i am getting the error
unknown filesystem 
grub rescue> 

I haven't read this thread since I am posting through mobie, buy is there anny method by which I can log into windows ? I want to install a fresh copy of ubuntu now.

thanks

---

### Post by drs305 on 2011-04-29
> **comp_007 said:**
> @ Friends,

by mistake my partition got deleted where ubuntu 11.04 was residing and due to the same reason i am unable to access it, I also have windows 7 (dual boot),


now i am getting the error
unknown filesystem 
grub rescue> 

I haven't read this thread since I am posting through mobie, buy is there anny method by which I can log into windows ? I want to install a fresh copy of ubuntu now.

thanks

The easiest method to restore Windows if you can boot an Ubuntu LiveCD is to partially install an app called *lilo* to point the system back to Windows. 

In the following I'm assuming your Windows drive is sd**a**. If it isn't, change it to the correct drive. Also, when you run these 2 commands, you will see messages about running the lilo configuration commands. Do not do this. You only need the following 2 commands:
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Reboot and you should see your Windows bootloader.

If you can not use the LiveCD, you will have to use the Windows restore CD.

---

### Post by Neoxhadowespio on 2011-06-07
I'm typing from a small netbook I use. I need help with GRUB. This is  the first time I've ever had a serious problem with my PC ever since I  got Linux. And I must say, I love it. But what I was trying to do was  recover lost data from my HDD using Testdisk. As some of you can  imagine, I recovered the lost partition and restarted. That was the  first time I was greeted with the message "unknown filesystem, grub  rescue> _" :sad:  So I finally got a Live USB and booted from that but then it gave me  "Boot Error." Now, I checked everything and even got a different OS on  there but still no marshmallow. Then I tried Rescatux and Super GRUB  Disk but still the same damn message. I think this "Boot Error" might be  a long term error because when the PC did work fine, if I restarted  with the USB in the port (I carry Ubuntu Netbook along with other stuff  in there) it would give me the message. I heard somewhere that you have  to change the USB Emulation to .zip or something but my BIOS does not  support it. I do not have an blank disk around and I won't be getting  one too soon so please help!

---

### Post by Neoxhadowespio on 2011-06-07
And also, I am very sorry if I am repeating a question, I know it must be a pain with all the typing you must do.

---

### Post by drs305 on 2011-06-07
Neoxhadowespio,

Are you able to get a Grub menu or boot to any Linux system? It would help if we could see the RESULTS.txt file generated by the boot info script. It can be run from any linux system. You can download it from the "BIS" link in my signature line.

If you can't boot to anything, at the grub prompt type "ls" and look for your former Ubuntu partition. If you recognize it, type "ls (hdX,Y)/boot" or experiment with various combinations until you get a result for it. Can you find a kernel and initrd.img?

---

### Post by Neoxhadowespio on 2011-06-07
The only OS I have is Ubuntu. The "ls" command gives me the following(ish) >(hd0) (hd0,MSDOS5) (hd0, MSDOS). I cannot boot from any flash drive because of the "boot error" I mentioned earlier.I do not have a blank disk. Also, if I try to look into the folders from the rescue prompt it give me the "unknown filesystem" again.

---

### Post by drs305 on 2011-06-07
> **Neoxhadowespio said:**
> The only OS I have is Ubuntu. The "ls" command gives me the following(ish) >(hd0) (hd0,MSDOS5) (hd0, MSDOS). I cannot boot from any flash drive because of the "boot error" I mentioned earlier.I do not have a blank disk. Also, if I try to look into the folders from the rescue prompt it give me the "unknown filesystem" again.

I'd like to be able to provide some assistance but the 'boot error' is probably not a Grub error but a problem or limitation with your system. If it's an older computer it may not be able to boot from a USB, which is why you have had no success with this option. Do you have access to an external CD/DVD from which you could boot Ubuntu?

I think you would have a better chance of finding an answer by starting a new thread with a descriptive title. Many people who may be familiar with the 'boot error' message wouldn't read posts in this thread. If I come up with anything I'll find your new post.

---

### Post by Neoxhadowespio on 2011-06-08
I have made a thread on this and it is a recent machine (Dell Inspiron from the Vista SP1 era). In fact I installed Ubuntu on it from an USB drive. Thanks anyway.

---

### Post by Clex19 on 2011-06-24
Hello, everyone. My problem is similar to Neoxhadowespio's problem, but I don't get the "unknown filesystem" error. Also, my laptop is several years old, maybe 6 or 7.

I have Lubuntu 11.04, and every time I try booting my computer, it goes to the grub rescue prompt after almost 5 minutes. I've tried using the Live USB, which I installed Lubuntu from, to boot from it to try to figure out what's wrong. However, that failed; it couldn't get past the flashing cursor. And I can't use a CD or DVD because my optical drive doesn't work.

At the grub rescue prompt, it said "error:hd0 read error" before "grub rescue>". I did "ls", and here is the output:

```
(hd0) (hd0,msdos5) (hd0,msdos1)
```

Whenever I try finding the grub folder, it either says "error:hd0 read error" again or "error:bad filename". 

Any help is greatly appreciated. Everything was working very well before this problem, and I was planning on taking my laptop with me to college...I'm not sure if that will work out anymore.

---

### Post by drs305 on 2011-06-24
> **Clex19 said:**
> 
Any help is greatly appreciated. Everything was working very well before this problem, and I was planning on taking my laptop with me to college...I'm not sure if that will work out anymore.

Clex19,

There is an app called Boot Repair that may be of use, but I think you'd have to be able to create a LiveUSB or be able to run Ubuntu to use it. You can check out the thread to see if it can help:
[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

If your system can't read the disk, first check your cables in case something came loose. Have you had any disk problems lately?

Performing a check of the disk using fsck or e2fsck would also be a good thing to do, but again you would have to be able to run a Linux OS to do so. 

Another thing to check is how large your BIOS thinks your disk is. If you enter the BIOS setup during boot, see if it reports the disk size as either 8GB or 137GB. If your disk is larger than the reported size, it could be the BIOS can no longer 'see' your Grub files. This can happen after an update when the Grub files are moved farther into the disk.

Unless you can get to a bootable situation (LiveCD/USB/DVD) it's going to be tough to troubleshoot this. If you can boot into a Linux OS, please run the boot info script and post the contents of RESULTS.txt. Click on the "BIS" link in my signature line to go to the site for instructions and to download the script.

---

### Post by Clex19 on 2011-06-24
Thanks for replying so quickly, drs305!

> If your system can't read the disk, first check your cables in case something came loose.

What do you mean by "cables"? The only cable I know of is the power cable that I hook into my laptop to charge.

>  Have you had any disk problems lately?

Well, last week sometimes I had the current problem or this one

```
BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands. 

(initramfs)
``` 

which I figured out all I needed to do was type "return". But now  I just keep getting the grub rescue prompt.

I guess I'll try booting from the Live USB more and try to get a Live USB of a different distro.

---

### Post by drs305 on 2011-06-24
> **Clex19 said:**
> I guess I'll try booting from the Live USB more and try to get a Live USB of a different distro.

While an Ubuntu distro would be nice, Slax is a good one to try if you have to run an fsck check and have problems with "busy" messages. For some reason Slax seems more forgiving. 

Sorry about the 'cables' reference - forgot you were on a laptop. It's not impossible, but much less likely.

---

### Post by Clex19 on 2011-06-24
Good news! I got it to boot from the Live USB, and I'm using my laptop to type this. However, I tried using the boot info script, but I didn't get a RESULTS.txt file. Here is what I got when I ran the script with the terminal:

```
boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

```

Then it has the cursor but not the usual "ubuntu@ubuntu:~$" like normal. And like I said there are no results in a .txt file.

So right now I guess I'll try doing Boot Repair. Also, I don't know what "fsck or e2fsck" are, but I hope that Boot Repair will fix it. 

Thanks for your help so far, though!

---

### Post by drs305 on 2011-06-24
> **Clex19 said:**
> Good news! I got it to boot from the Live USB, and I'm using my laptop to type this. However, I tried using the boot info script, but I didn't get a RESULTS.txt file. Here is what I got when I ran the script with the terminal:

```
boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

```

Then it has the cursor but not the usual "ubuntu@ubuntu:~$" like normal. And like I said there are no results in a .txt file.

So right now I guess I'll try doing Boot Repair. Also, I don't know what "fsck or e2fsck" are, but I hope that Boot Repair will fix it. 

Thanks for your help so far, though!

You can install gawk if you want with the following (if on the LiveCD, you would have to do this each time you boot the CD to run the boot info script if you want to use gawk):
```
sudo apt-get install gawk
```
but the original RESULTS.txt will probably be sufficient if you post the contents.

fsck/e2fsck checks for errors of the filesystem and sometimes can repair them. From the Desktop, open a terminal and run the following. Change X to the Ubuntu partition number. The partition must not be mounted when you run the check, but if you have just booted the CD it won't be by default.
```
sudo e2fsck -f -y -v /dev/sdaX
```
Example: sudo e2fsck -f -y -v /dev/sda5

Please run this and try booting to see if it fixes things, before posting the RESULTS.txt

---

### Post by Clex19 on 2011-06-24
Okay, I used:

```
sudo e2fsck -f -y -v /dev/sda1
```

But I don't know if it was the right partition since it won't let me check which one has the grub folder. Before that, I did the same thing, except I used 5 for the X instead of 1, and it said that it was mounted and would cause severe damage so I didn't continue. My question now is how do I know when it's okay to reboot? After I used the code above, it said:

```
e2fsck 1.14.41 (22-Dec-2010)
```

I don't know if it's supposed to display more output or if I can go ahead and reboot. For some reason, ever since I booted with the Live USB, my computer has been using 100% of the CPU. Thus, it's going kinda slow and I don't know if it's done with the check. Right now, I can't move the mouse at all.

---

### Post by drs305 on 2011-06-24
> **Clex19 said:**
> Okay, I used:

```
sudo e2fsck -f -y -v /dev/sda1
```

But I don't know if it was the right partition since it won't let me check which one has the grub folder. Before that, I did the same thing, except I used 5 for the X instead of 1, and it said that it was mounted and would cause severe damage so I didn't continue. My question now is how do I know when it's okay to reboot? After I used the code above, it said:

```
e2fsck 1.14.41 (22-Dec-2010)
```

I don't know if it's supposed to display more output or if I can go ahead and reboot. For some reason, ever since I booted with the Live USB, my computer has been using 100% of the CPU. Thus, it's going kinda slow and I don't know if it's done with the check. Right now, I can't move the mouse at all.


You can attempt to unmount a partition with the following command. Before running it, close any apps that might be trying to access it, such as Nautilus:
```
sudo umount /dev/sda5
```

Normally the line you quoted when running e2fsck (e2fsck 1.14.41 (22-Dec-2010) ) is the first line generated and until it is completed nothing else may show. When the command is finished it will show a summary and the final line will be something like "226484 files" and the command prompt will again appear. On my machine, when running normally, it usually takes less than 10-20 seconds.

If you reboot, you can mount /dev/sda5 (or even sda1) with the following command, and then use Nautilus to inspect the contents:
```
sudo mount /dev/sda5 /mnt
gksu nautilus /mnt

```
If you can't get your installation to boot, you should at least be able to access your files and copy any important data files you have on that partition. 

If you were able to run the boot info script please post the contents of RESULTS.txt

---

### Post by Clex19 on 2011-06-24
The e2fsck finally finished. It says:

```
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

```

I installed gawk and tried the BSI again. Here is the output:

```
boot_info_script version: 0.60        [17 May 2011]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
```

It doesn't seem to me that these methods are working...Oh, well. Maybe I'll just have to reinstall Lubuntu.

---

### Post by Popo2po on 2011-06-25
Hi!
I have some problem by grub rescue!
I have win7 and had ubuntu 11.04 on two different partition. after removing ubuntu (partition) in win7 I was going to boot my notebook via Win-DVD to repair boot issue.
suddenly after a low battery alarm my system went to hibernate state and now I can not access BIOS nor boot device selection menu to boot from a cd.

It says:
```

error: unknown filesystem
grub rescue >

```I can see disks and partition using "LS" but I cannot use commands like:
```

ls (hd0,1)

```to map! :)

All commands print:
```
error: unknown filesystem
```I can use "set" command but no thing happens.

I know that I have 1 other linux partition and also a swap.

what can I do?

---

### Post by drs305 on 2011-06-25
@ Clex19,

It sounds like you have a filesystem or disk error that fsck isn't fixing. The boot info script is starting as it should but the entire script should run in under 30 seconds. Everything seems to be taking an unusual amount of time. Although I don't often recommend it, I think I'd save the data off the Ubuntu partition, if you have any, and try to reformat and reinstall Ubuntu.

@ Popo2po
Do you know the partition your Ubuntu installation was on? The grub rescue prompt means that Grub is not finding it's Grub folder and the boot files. If you can boot a LiveCD please download, extract and run the boot info script from the "BIS" link in my signature line. Then post the contents of the RESULTS.txt

A simple second option would be to attempt to reinstall Grub from the LiveCD. X is the drive your Ubuntu installation is on, and Y is your Ubuntu partition number (Example: /dev/sda5)
```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX

```
Do not use the partition number in the second command.

The third option would be to try to use the Boot Repair app, after booting the LiveCD:
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
Do not use the partition number in the second command.

---

### Post by Popo2po on 2011-06-25
@Drs305:
thank you.
I think I know what happend but i can not have access to boot menu or bios set-up to boot from any rescue disk(win7, herins etc.) or fixmbr.
I'm not sure but think that I cannot access to bios because win7 went hibernated!
I know ubuntu should be on (hd0,11) but it says "unknow filesystem"! So it must not be there!
Non of my partitions can be listed using "ls" command.
I had formated a usb as Ext3 (on another system) and copied some grub files from an fullgrub image (i think). The error not taken but it says "bad file name" and nothing happens aftes "set prefix=(hd1,1)/boot/grub root=hd1,1".
What could i do eccept doing fixmbr on my harddrive using a sata-to-usb box!?

---

### Post by Clex19 on 2011-06-25
@drs305

> I think I'd save the data off the Ubuntu partition, if you have any

How exactly do I do that? Do I have to boot from the Live USB or can I do it from the grub rescue prompt, or what?

---

### Post by drs305 on 2011-06-25
> **Clex19 said:**
> @drs305

How exactly do I do that? Do I have to boot from the Live USB or can I do it from the grub rescue prompt, or what?

If you can again boot the LiveCD, get to the Desktop, open a terminal and then run the first command to display the partition listing, and the second to mount your Ubuntu partition (sdXY, substituting the correct values). Next open a file browser so you can copy files/folders to a USB  or other storage device.

```

sudo fdisk -l  # Lowercase L. This should display the partitions
sudo mount /dev/sdXY /mnt  # Example: sudo mount /dev/sda5 /mnt
gksu nautilus /mnt
```

If you still don't know the correct partition, the fdisk command's last column entry of your Ubuntu partition should be "Linux".

---

### Post by SpinDoctaa on 2011-09-12
hi so i type ls and get (hd0) [noparse](hd0,msdos8) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)[/noparse]

(hd0,msdos7) is the linux folder and cannot find a grub folder anywhere

have  tried about twenty different methods and have also tried a pxe boot  over a lan to reinstall linux, usb stick not working and not cd drive am  using a netbook, and my gf will not let me put my harddrive in her  laptop.

PLEAASE HELP ME

have been doing this for so loong now

---

### Post by drs305 on 2011-09-12
> **SpinDoctaa said:**
> hi so i type ls and get (hd0) [noparse](hd0,msdos8) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)[/noparse]

(hd0,msdos7) is the linux folder and cannot find a grub folder anywhere

have  tried about twenty different methods and have also tried a pxe boot  over a lan to reinstall linux, usb stick not working and not cd drive am  using a netbook, and my gf will not let me put my harddrive in her  laptop.

PLEAASE HELP ME

have been doing this for so loong now

SpinDoctaa,

Welcome to the Ubuntu forums. 

Have you tried using the Boot Repair tool?
[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

If the above app doesn't work, you will have to provide us with more information for us to help. Please download/extract/run the boot info script from the "BIS" link in my signature line, then post the contents of RESULTS.txt

---

### Post by SpinDoctaa on 2011-09-12
Hi, thanks for the welcome, i have tried the boot recovery using u net boot in and it will not pick it up on my usb. Nor the reinstall on linux. I have tried what you previously mentioned but it would not pick that up either. I am trying to boot the usb device through ls/dev but any what i try it comes up saying file not found and there is no grub anywhere to be found in any drives. I was reinstalling linux last night and the computer froze so i turned it off and now it says grub rescue. Is there any way of doing a reinstallation over the internet from grub rescue?? Please advise. :(

Thank you very much

---

### Post by drs305 on 2011-09-12
> **SpinDoctaa said:**
> I was reinstalling linux last night and the computer froze so i turned it off and now it says grub rescue. Is there any way of doing a reinstallation over the internet from grub rescue?? Please advise.

If you mean the installation of the complete OS, I don't know a way of doing it from the Grub rescue prompt. The rescue prompt means that Grub can't find any of it's files. Normally you might be able point to these files from the Grub rescue prompt, but since the installation didn't complete there is a good chance the files aren't available and you need to reaccomplish the full installation.

If Grub is installed and working, you can actually boot an Ubuntu ISO file and complete the installation from the ISO file (not a burned CD). But Grub has to be working for this procedure.

If you mean reinstallation of Grub2, you can do it from a running Ubuntu boot or from a LiveCD/USB; basically as long as you can get to an Ubuntu Desktop. You would then chroot into your real Ubuntu partition, purge Grub2 and then install it again. The instructions on how to do it are found on the "Chroot" link in my signature line.

In many cases, troubleshooting takes more time than doing a complete reinstallation, but the decision as to whether this is the desired option can depend on other factors only the user can know (Internet, customizations, etc).

---

### Post by SpinDoctaa on 2011-09-12
Hi, so completely off key but i have booted up an old mandriva hard drive would you recommend creating a fresh ubuntu usb from here? Thanks very much

---

### Post by drs305 on 2011-09-12
> **SpinDoctaa said:**
> Hi, so completely off key but i have booted up an old mandriva hard drive would you recommend creating a fresh ubuntu usb from here? Thanks very much

You can do that. I've only used UNetbootin but whichever one you choose should do the job.

---

### Post by SpinDoctaa on 2011-09-12
> **drs305 said:**
> You can do that. I've only used UNetbootin but whichever one you choose should do the job.


ok so i finally have got to the unetbootin but anything i select takes me to a system called busybox and i do not have a clue about this, what do you advise??

thanks

lol

---

### Post by drs305 on 2011-09-12
I'm not a 'boot from usb' expert. Have you ever been able to successfully boot Ubuntu? 

Assuming your computer is booting from the LiveCD and Unetbootin was installed correctly it means that Grub2 has transferred control but the kernel is having a problem booting. It could be a problem with the initrd.img or a variety of other issues. Sometimes the messages that appear as the system attempts to boot will provide you with the information about where it is having problems.

As UNetbootin boots, are you given the chance to add kernel options? On a LiveCD, you can add special kernel options such as "noapci", "nomodeset" etc which sometimes gets the system booting. 

When you say an 'old version' of mandiva I'm assuing it isn't using Grub 2 to boot. If by chance it is, there is a way to boot and install Ubuntu from an ISO image downloaded to the hard drive (without burning/using a CD). But you have to have Grub 2 installed/working to use this method.

As I mentioned, I'm not a usb expert, and probably not may helpers review the posts in this thread any longer. It might be more useful to create a new thread if the problem continues to be a usb booting issue. I can usually help recover a 'broken' grub filesystem but usb installations and kernel troubleshooting unfortunately aren't my strong suit.

---

### Post by Elchund on 2011-11-28
I got "Error: (a bunch of numbers)
Grub rescue 

Then I followed the first post to the letter and the system booted right back up. Complete magic to me, thank you so much!

I do not understand how I broke grub in the first place though, I run ubuntu 11.10 on my thinkpad, then I installed xubuntu on a second harddrive (substituted for the dvd drive in the docking station of my x60)and it all went fine until I had shut down, removed the xubuntu hdd and tried to start up on my main drive (with ubuntu) again.

Anyway, its all good now, thanks again. 

Elchund

---

### Post by drs305 on 2011-11-28
Eichund,

When you installed xubuntu, it wrote its information, including its UUID number, into the main drive's MBR and took control of the boot process. When you removed the xubuntu drive, it's Grub information still remained on the MBR of the installed drive (I think it tries to write to sda unless you specify otherwise).

The next time you booted, the MBR of the boot drive pointed to the xubuntu partition, which was no longer available and thus told you it couldn't find UUID xxxxxx.  

By following the instructions, you merely told Grub where to find it's files, loaded the modules, kernel and initrd image and booted. Once booted, running 'grub-install' rewrites your existing OS's information back to the MBR and update-grub then refreshes the menu.

Glad you were able to get it sorted out.

I wrote this guide when there wasn't a lot of guidance on fixing grub 2 problems. Today I'm happy to say there is an excellent GUI app that can do a lot of what you had to do manually. If you have the problem again and wish to use an app to fix it, take a look at Boot Repair. The link is in my signature line.

---

### Post by Elchund on 2011-11-29
It does make sense when you explain it to me. I rebooted the xubuntu drive a couple of times and remember that the grub menu listed ALL my installed kernels, also those of the ubuntu install on the main drive. 

I love to tinker, so I will definitely have a look at that GUI, I will need it sooner or later...

Elchund

---

### Post by sceo on 2011-12-26
I recently installed a second hard drive, an SSD, into my optical bay in my laptop.

I have a 640GB HDD in there already. It has Windows on it, and it used to have Ubuntu on it. I have since mussed with the partitions on the 640GB, leaving only Windows and my home partition there.

Using the installer, I'm able to get the OS installed to the SSD, and I have told grub to install to the 640GB drive. (I've also tried a number of other forum-suggested options, which involved re-installing grub from chroot, and at that point I installed grub on ALL drives).

No matter, what, I get "error: no such device: <UUID OF SSD / partition>" and a grub rescue prompt.

When running through the rescue steps, I get stopped up at trying to find my linux partition.

grub rescue> ls
-shows-
(hd0) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos1)

grub rescue> ls (hd1,msdos1)/
-shows-
error: unknown filesystem.

In fact, everything except (hd0,msdos5) tells me that. (hd0,msdos5) is my old /home partition from my previous ubuntu install.

My RESULTS.txt file:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

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
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 12 Lisa
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 20110518
    Boot sector info:   Syslinux looks at sector 14929742 of /dev/sdc1 for 
                       its second stage. SYSLINUX is installed in the  
                       directory. According to the info in the boot sector, 
                       sdc1 starts at sector 0. But according to the info 
                       from fdisk, sdc1 starts at sector 2048.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2    *        206,848    30,926,847    30,720,000   7 NTFS / exFAT / HPFS
/dev/sda3          30,926,848   155,299,839   124,372,992   7 NTFS / exFAT / HPFS
/dev/sda4         206,514,174 1,250,262,222 1,043,748,049   5 Extended
/dev/sda5         206,514,176 1,250,262,222 1,043,748,047  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    39,999,487    39,997,440  83 Linux
/dev/sdb2          40,001,534   234,440,703   194,439,170   5 Extended
/dev/sdb5          40,001,536   218,439,035   178,437,500  83 Linux
/dev/sdb6         218,439,680   234,440,703    16,001,024  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 16.0 GB, 16039018496 bytes
256 heads, 63 sectors/track, 1942 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048    31,326,207    31,324,160   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DELLUTILITY
/dev/sda2        CC70378A703779F2                       ntfs       Recovery
/dev/sda3        AC7C4EC27C4E86D4                       ntfs       OS
/dev/sda5        116a413a-9831-4970-8e23-35c516ecc59e   ext4       
/dev/sdb1        41e6c7ed-dd09-416d-960e-e172e138b022   ext4       
/dev/sdb5        f4514f3a-641d-4847-861a-5087ae6ffb22   ext4       
/dev/sdc1        2298-18EF                              vfat       âPNG
 

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 41e6c7ed-dd09-416d-960e-e172e138b022
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root 41e6c7ed-dd09-416d-960e-e172e138b022
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,0,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Linux Mint 12 64-bit, 3.0.0-12-generic (/dev/sdb1)' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 41e6c7ed-dd09-416d-960e-e172e138b022
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=41e6c7ed-dd09-416d-960e-e172e138b022 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Linux Mint 12 64-bit, 3.0.0-12-generic (/dev/sdb1) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 41e6c7ed-dd09-416d-960e-e172e138b022
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=41e6c7ed-dd09-416d-960e-e172e138b022 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 41e6c7ed-dd09-416d-960e-e172e138b022
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 41e6c7ed-dd09-416d-960e-e172e138b022
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root CC70378A703779F2
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root AC7C4EC27C4E86D4
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=41e6c7ed-dd09-416d-960e-e172e138b022 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=f4514f3a-641d-4847-861a-5087ae6ffb22 /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
#UUID=450bb03c-467c-4fec-95f2-9d5f5ed2e653 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.405982971 = 4.730888192    boot/grub/core.img                             1
   4.406044006 = 4.730953728    boot/grub/grub.cfg                             1
   1.227539062 = 1.318060032    boot/initrd.img-3.0.0-12-generic               3
  16.133975983 = 17.323724800   boot/vmlinuz-3.0.0-12-generic                  1
   1.227539062 = 1.318060032    initrd.img                                     3
  16.133975983 = 17.323724800   vmlinuz                                        1

=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=white/light-gray

menuentry "Start Linux Mint" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/mint.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Start Linux Mint (compatibility mode)" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/mint.seed boot=casper xforcevesa ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --
	initrd	/casper/initrd.lz
}
menuentry "Check the integrity of the medium" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}

--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/mint.seed boot=casper quiet splash --

label ubnentry0
menu label Start Linux Mint
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper  quiet splash --

label ubnentry1
menu label Start Linux Mint (compatibility mode)
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper xforcevesa  ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --

label ubnentry2
menu label Check the integrity of the CD
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry3
menu label Memory Test
kernel /isolinux/memtest
append initrd=/ubninit 

label ubnentry4
menu label Boot from local drive
kernel /ubnkern
append initrd=/ubninit 

label ubnentry5
menu label Check the integrity of the medium
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```

NOTES: 
[LIST]
[*]/dev/sdc is the live USB I'm using.
[*]I've also tried Rescatux and Boot Repair from the Live CD (USB, really), as well as the chroot-reinstall method.
[/LIST]

Needless to say, I'm pretty stumped here. My inclination is to think that GRUB is actually able to load and find /boot/grub/grub.cfg in sdb1, but how could it do that if it actually can't find that drive by UUID?

---

### Post by drs305 on 2011-12-26
sceo,

If you hadn't provided the extra information one thing I would have recommended is that you make sure sdb is the first drive listed in the BIOS boot order.

One thing that needs attention is that your sdb1 fstab still contains a listing for a separate /home. You indicated it was an 'old' home partition, so if you aren't using it you should get rid of the listing in fstab. You can do this by mounting the sdb1 partition from the LiveCD and then editing it (gksu gedit /mountpoint/etc/fstab).

I have no experience with SSD drives, so I don't know why your system isn't recognizing it. You might try running an fsck check on it to see if there are some errors which are causing the problem. Make sure the partition isn't mounted when you run it. I use "e2fsck -f -y -v /dev/sdXY" when I accomplish fsck checks - I don't know if it being an SSD makes a difference or not.

I'd also recommend you try the Boot Repair app to see if it can fix things. Its an excellent program and may be able to help you. Click the 'Boot Repair' link in my signature line.

---

### Post by sceo on 2011-12-26
I did try Boot Repair at one point, which did not work. I had the same thought about the BIOS boot order, to which I could only prioritize "CD ROM" above "Hard Disk" (which I did attempt, since the SSD was in the optical bay). This had no effect.

That got me thinking that perhaps the hard drive boot order was "hardcoded" in the BIOS, and not configurable. I swallowed hard and decided to take the laptop apart and put the SSD in the primary hard drive's spot, and move the 640GB platter-drive into the optical bay. 

Sure enough, this totally did the trick, and booted right into my new install. The 640GB now mounts on demand (thought I need to now figure out how to decrypt my old home folder with ecryptfs :) ), which is perfect for my needs.

For the search engines: this is related to installing an SSD into a Dell Inspiron 15r and booting Ubuntu, using the old drive as a secondary in the optical bay.

I would've loved to know if the duplicate /home was the source of any of my woes, but I'm not opening that beast back up just to try it. :)

---

### Post by drs305 on 2011-12-26
sceo,

Nice that you were able to figure this out. The old /home partition existed and was properly referenced in fstab (even though it's contents may not have been usable), so it should have at least tried to boot before failing. That means it would most likely have progressed past the Grub loading and failed after transferring control to the kernel if that was the source of your difficulties.

Happy Ubuntu-ing !

---

### Post by Trent T on 2012-01-11
Failed Grub Restoration using Boot-Repair -- 
Comments first, then paste-bin results--

Hi all,
First, thanks to all who posted guides that address this problem!!
Your combined information ALMOST has my Ubuntu 10.04.3 system working again--I feel that there may be one small thing I've left undone that will lead to success;

**HISTORY:**

My Ubuntu 10.04.3 installation ran well for several years.  I think it developed some bad sectors that took out  GRUB2, making the system unbootable.  I was able to get a complete system backup using .TAR before the system froze and shut down.  Since my data is available on an external backup drive, I can tinker with restoration a bit.

**WHAT I HAVE TRIED SO FAR:**

1) **Restoration of hard drive from TAR** to original 160 GB Hard drive appears to have hung.
'Properties' shows a completely full hard drive, with error messages,
        'Some contents unreadable'
and 'No room on drive.'

I am unable to delete files from the full drive.
The original system drive and files used less than 58 GB of space.

2) Formatted 500 GB internal backup drive, then restored system from TAR as before.
    Restoration results in 230 GB of files.  Files can be added, read, and deleted.

I disconnected power and SATA cables on two other internal drives (to avoid confusing myself).
Current system has /media/sda on 500 GB drive connected to SATA-1, and DVD burner connected to SATA-2. 

3) Numerous **chroot installations** from Ubuntu 10.10 and 11.04 installation disks.
[Following excellent instructions from pritam_par, posted 6 Aug 2011 at this link;
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore&page=25](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore&page=25)
]

Manual installations appear to work, with no error messages.
When system is rebooted, the reboot attempt ends with the following lines;

Checking battery              [OK]
The disk drive for UUID=33722ffb-2f7a-4a8f-b1b7-5516b95c8146 is not ready yet or n
Continue to wait; or Press S to skip mounting or M for manual recovery

Pressing S or M have no effect.
Pressing the [up-arrow] key toggles from an Ubuntu 10.04 splash screen with 4 (four) dots, blinking sequentially between white and orange, and the above error message.

Waiting all night has no effect.

4) Numerous **Boot-Repair** sessions appear to be successful (ie., no error messages at end) as before.
However, system reboot results in the same error message;
[B]
Checking battery              [OK]
The disk drive for UUID=33722ffb-2f7a-4a8f-b1b7-5516b95c8146 is not ready yet or n
Continue to wait; or Press S to skip mounting or M for manual recovery[/B]

5) Numerous Rescatux sessions appear to succeed, but result in the same error message upon reboot.

6) Booting from SuperGrub2 disk fails to boot the system with the default selection.
     Using the 2nd selection (something like 'Detect any GRUB installation')
     allows me to select GRUB2.  Rebooting with any of the kernels listed ends with the error message above.

    Rebooting in 'Recovery Mode' kernel gets me to the CLI prompt for Ubuntu 10.04.3
    I am able to login and use CLI commands, but so far have not been able to restart the GUI.

Logs from the Paste Bin

Two Boot-Repair logs from the Paste Bin can be reviewed here;

[http://paste.ubuntu.com/801014/](http://paste.ubuntu.com/801014/)
[http://paste.ubuntu.com/801301/](http://paste.ubuntu.com/801301/)

My System:
FIC motherboard, 32-bit PC with 2 GB RAM, 500 GB SATA drive containing sda1, 2, and 5.  No other operating systems.  LightScribe DVD burner  on SATA-2.  External 3 TB backup drive connected by WiFi, but not currently mounted to this Ubuntu computer.

Any suggestions appreciated!
--Trent T

From paste.ubuntu.com/801014/
```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 721696712 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 1 for /boot/grub.
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   976,584,703   976,582,656  83 Linux
/dev/sda2         976,586,750   976,771,071       184,322   5 Extended
/dev/sda5         976,586,752   976,771,071       184,320  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4040 MB, 4040748544 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7892087 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,887,914     7,887,852   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        a07cba89-e6a8-4ad6-afbb-d8dacfec0484   ext4       
/dev/sda5        613c4f87-bdac-4630-8cda-37ccf3b5220f   swap       
/dev/sdb1        208C-4584                              vfat       ADATA UFD

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev             /media/a07cba89-e6a8-4ad6-afbb-d8dacfec0484/dev none       (rw,bind)
/dev/pts         /media/a07cba89-e6a8-4ad6-afbb-d8dacfec0484/dev/pts none       (rw,bind)
/dev/sda1        /media/a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/ADATA UFD         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.38-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	linux	/boot/vmlinuz-2.6.38-13-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro   quiet splash
	initrd	/boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	echo	'Loading Linux 2.6.38-13-generic ...'
	linux	/boot/vmlinuz-2.6.38-13-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	linux	/boot/vmlinuz-2.6.32-37-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	echo	'Loading Linux 2.6.32-37-generic ...'
	linux	/boot/vmlinuz-2.6.32-37-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	linux	/boot/vmlinuz-2.6.32-36-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	echo	'Loading Linux 2.6.32-36-generic ...'
	linux	/boot/vmlinuz-2.6.32-36-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	linux	/boot/vmlinuz-2.6.32-35-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-35-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	echo	'Loading Linux 2.6.32-35-generic ...'
	linux	/boot/vmlinuz-2.6.32-35-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-35-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	linux	/boot/vmlinuz-2.6.32-34-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	echo	'Loading Linux 2.6.32-34-generic ...'
	linux	/boot/vmlinuz-2.6.32-34-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	echo	'Loading Linux 2.6.32-33-generic ...'
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	echo	'Loading Linux 2.6.32-32-generic ...'
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	linux	/boot/vmlinuz-2.6.31-23-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	echo	'Loading Linux 2.6.31-23-generic ...'
	linux	/boot/vmlinuz-2.6.31-23-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	linux	/boot/vmlinuz-2.6.28-19-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	echo	'Loading Linux 2.6.28-19-generic ...'
	linux	/boot/vmlinuz-2.6.28-19-generic root=UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a07cba89-e6a8-4ad6-afbb-d8dacfec0484
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=10
    else
      set timeout=10
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=10
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
# Commented out by Dropbox
# UUID=cf1f6b0e-147b-48c3-bfd2-e639780e58b4 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=33722ffb-2f7a-4a8f-b1b7-5516b95c8146 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=cf1f6b0e-147b-48c3-bfd2-e639780e58b4 / ext3 relatime,errors=remount-ro,user_xattr 0 1
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 344.131835938 = 369.508745216  boot/grub/core.img                             1
 344.128353119 = 369.505005568  boot/grub/grub.cfg                             1
 344.371768951 = 369.766371328  boot/initrd.img-2.6.28-19-generic              1
 344.272853851 = 369.660162048  boot/initrd.img-2.6.31-23-generic              1
 344.320896149 = 369.711747072  boot/initrd.img-2.6.32-32-generic              1
 344.328346252 = 369.719746560  boot/initrd.img-2.6.32-33-generic              1
 344.361476898 = 369.755320320  boot/initrd.img-2.6.32-34-generic              1
 344.339050293 = 369.731239936  boot/initrd.img-2.6.32-35-generic              1
 344.354026794 = 369.747320832  boot/initrd.img-2.6.32-36-generic              1
 344.258426666 = 369.644670976  boot/initrd.img-2.6.32-37-generic              1
 389.016601562 = 417.703395328  boot/initrd.img-2.6.35-22-generic              2
   0.522338867 = 0.560857088    boot/initrd.img-2.6.38-13-generic              2
 344.331600189 = 369.723240448  boot/vmlinuz-2.6.28-19-generic                 1
 344.280250549 = 369.668104192  boot/vmlinuz-2.6.31-23-generic                 1
 344.342811584 = 369.735278592  boot/vmlinuz-2.6.32-32-generic                 1
 344.276615143 = 369.664200704  boot/vmlinuz-2.6.32-33-generic                 1
 344.262191772 = 369.648713728  boot/vmlinuz-2.6.32-34-generic                 1
 344.265956879 = 369.652756480  boot/vmlinuz-2.6.32-35-generic                 1
 344.346576691 = 369.739321344  boot/vmlinuz-2.6.32-36-generic                 1
 344.365242004 = 369.759363072  boot/vmlinuz-2.6.32-37-generic                 1
   0.308685303 = 0.331448320    boot/vmlinuz-2.6.35-22-generic                 2
 389.048160553 = 417.737281536  boot/vmlinuz-2.6.38-13-generic                 1
 344.258426666 = 369.644670976  initrd.img                                     1
 344.354026794 = 369.747320832  initrd.img.old                                 1
 344.365242004 = 369.759363072  vmlinuz                                        1
 344.346576691 = 369.739321344  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  95 dd 08 51 e8 cc 06 7a  ce 33 ca 9d 5d 88 3c 89  |...Q...z.3..].<.|
00000010  ff 00 6e 5b 3c 17 d9 90  00 02 7a e1 15 71 d4 b7  |..n[<.....z..q..|
00000020  77 aa bd 14 0f 49 f8 54  0a a5 d2 d6 2f 0e 42 89  |w....I.T..../.B.|
00000030  90 5e b5 de 6c 9e 43 20  33 a1 ed a6 6a b7 f7 16  |.^..l.C 3...j...|
00000040  7b 13 fd 61 ac 31 38 29  76 3a 2f be df 6a 83 5f  |{..a.18)v:/..j._|
00000050  c7 d6 73 92 d3 f2 51 cc  cc be 38 22 5c 8b 36 51  |..s...Q...8"\.6Q|
00000060  da a1 81 36 bc 83 21 9f  68 d6 a6 8b 21 7f 14 4d  |...6..!.h...!..M|
00000070  bb 93 06 a5 63 1f 68 3b  39 f4 9e 5b 89 a6 c9 c3  |....c.h;9..[....|
00000080  b3 e2 94 97 3b 1f de 98  e5 10 a5 53 96 99 7b 82  |....;......S..{.|
00000090  92 00 45 2f cd 5d 7d 39  7c cc 99 da 98 e1 1b 05  |..E/.]}9|.......|
000000a0  7a 13 d1 7f b9 e0 6c 9e  f6 3d d4 bd 8c d2 59 49  |z.....l..=....YI|
000000b0  13 18 c3 82 da 00 c6 9b  3a 83 de d0 82 a8 ef 6b  |........:......k|
000000c0  e0 68 bc 07 3f 77 43 43  15 b5 48 5a c1 78 96 65  |.h..?wCC..HZ.x.e|
000000d0  0d 51 db 84 bf 64 de 54  32 a5 88 28 8e 73 17 ce  |.Q...d.T2..(.s..|
000000e0  36 c7 7e 4c 4f 97 95 ad  63 2e 92 96 9b a4 f9 d1  |6.~LO...c.......|
000000f0  66 ab 8e 1f e6 cf f4 8e  0d b5 a7 cd 63 89 e6 7e  |f...........c..~|
00000100  99 7b 14 6d 2c bf 29 67  ec 6b 0e 2c 2a bf 97 a1  |.{.m,.)g.k.,*...|
00000110  62 da 05 be fc 1a db ee  62 63 9b 5d 3b 21 56 53  |b.......bc.];!VS|
00000120  b9 cc 5b e6 39 ad 00 1b  b8 86 9b 70 ee a1 d6 ee  |..[.9......p....|
00000130  73 8e f8 25 a5 87 ad 39  0f f6 32 23 8a 19 19 90  |s..%...9..2#....|
00000140  a2 85 34 55 9b 04 c0 81  b7 e9 1a 76 8f 4a 93 d5  |..4U.......v.J..|
00000150  7a 0a ef 0b fb cd 76 fb  0e 29 f8 c7 bb 8f 66 0d  |z.....v..)....f.|
00000160  9b 6e 99 f4 72 83 4b 59  a5 ef 43 fc 70 92 d0 06  |.n..r.KY..C.p...|
00000170  26 92 e3 92 c4 f9 5a ba  78 67 d5 68 34 c4 79 99  |&.....Z.xg.h4.y.|
00000180  68 a9 d4 7a 2e d2 96 75  19 ef 54 97 5b 35 c2 61  |h..z...u..T.[5.a|
00000190  72 46 78 0e 21 44 46 f8  a4 82 c2 d7 67 8c 04 0d  |rFx.!DF.....g...|
000001a0  6c de 7d 9e 70 67 a9 0c  45 e6 52 21 aa 61 18 79  |l.}.pg..E.R!.a.y|
000001b0  c2 86 76 73 b8 5e e6 5b  12 42 65 32 b1 2b 00 fe  |..vs.^.[.Be2.+..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 02 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-01-11__20h23 ****************
boot-repair version : 3.04-0ppa3~maverick
boot-sav version : 3.04-0ppa2~maverick
internet: connected
boot-sav-gui version : 3.04-0ppa6~maverick
LIVESESSION is : yes
BYTES_BEFORE_PART[1] (sda) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[2] (sdb) = 63 sectors * 512 bytes = 32256 bytes.
OSPROBER: /dev/sda1:Ubuntu 10.04.3 LTS (10.04):Ubuntu:linux
BLKID: /dev/sda1: UUID="a07cba89-e6a8-4ad6-afbb-d8dacfec0484" TYPE="ext4"
/dev/sda5: UUID="613c4f87-bdac-4630-8cda-37ccf3b5220f" TYPE="swap"
/dev/loop0: TYPE="squashfs"
/dev/sdb1: LABEL="ADATA UFD" UUID="208C-4584" TYPE="vfat"
sda1 contains Ubuntu 10.04.3 LTS (linux)
1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.
Total of 1 OS detected on sda disk.
sda contains minimum one OS
FDISK
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009ecbd

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976584703   488291328   83  Linux
/dev/sda2       976586750   976771071       92161    5  Extended
/dev/sda5       976586752   976771071       92160   82  Linux swap / Solaris

Disk /dev/sdb: 4040 MB, 4040748544 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7892087 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7887914     3943926    b  W95 FAT32

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009ecbd

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976584703   488291328   83  Linux
/dev/sda2       976586750   976771071       92161    5  Extended
/dev/sda5       976586752   976771071       92160   82  Linux swap / Solaris

Disk /dev/sdb: 4040 MB, 4040748544 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7892087 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7887914     3943926    b  W95 FAT32
TABLE_TYPE of sda is MSDos
TABLE_TYPE of sdb is MSDos
sda1 : sda, not-sepboot, no-grub, aptget, 32, no boot, /media/a07cba89-e6a8-4ad6-afbb-d8dacfec0484, with-os, no-gpt, notEFItable, fstab-without-efi.
sdb1 : sdb, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /media/ADATA UFD, no-os, no-gpt, notEFItable, no-fstab.
PARTED: Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  500GB  500GB   primary   ext4            boot
2      500GB   500GB  94.4MB  extended
5      500GB   500GB  94.4MB  logical   linux-swap(v1)


Model: ADATA USB Flash Drive (scsi)
Disk /dev/sdb: 4041MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  4039MB  4039MB  primary  fat32        boot



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label
MOUNT aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/a07cba89-e6a8-4ad6-afbb-d8dacfec0484 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1 on /media/ADATA UFD type vfat (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev on /media/a07cba89-e6a8-4ad6-afbb-d8dacfec0484/dev type none (rw,bind)
/dev/pts on /media/a07cba89-e6a8-4ad6-afbb-d8dacfec0484/dev/pts type none (rw,bind)
/proc on /media/a07cba89-e6a8-4ad6-afbb-d8dacfec0484/proc type none (rw,bind)
/sys on /media/a07cba89-e6a8-4ad6-afbb-d8dacfec0484/sys type none (rw,bind)
/sys/block/fd0:  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd fd0 fd0u1040 fd0u1120 fd0u1440 fd0u1600 fd0u1680 fd0u1722 fd0u1743 fd0u1760 fd0u1840 fd0u1920 fd0u360 fd0u720 fd0u800 fd0u820 fd0u830 full fuse fw0 hidraw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem pktcdvd port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda5 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 vga_arbiter zero
/dev/mapper:  control
DF Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    975M  137M  839M  14% /
none      devtmpfs    969M  296K  969M   1% /dev
/dev/sr0   iso9660    694M  694M     0 100% /cdrom
/dev/loop0
squashfs    661M  661M     0 100% /rofs
none         tmpfs    975M  276K  975M   1% /dev/shm
tmpfs        tmpfs    975M  2.8M  972M   1% /tmp
none         tmpfs    975M   92K  975M   1% /var/run
none         tmpfs    975M  4.0K  975M   1% /var/lock
/dev/sda1     ext4    459G  271G  165G  63% /media/a07cba89-e6a8-4ad6-afbb-d8dacfec0484
/dev/sdb1     vfat    3.8G  2.3G  1.5G  62% /media/ADATA UFD
FDISK
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009ecbd

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976584703   488291328   83  Linux
/dev/sda2       976586750   976771071       92161    5  Extended
/dev/sda5       976586752   976771071       92160   82  Linux swap / Solaris

Disk /dev/sdb: 4040 MB, 4040748544 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7892087 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7887914     3943926    b  W95 FAT32
Logs saved into /media/a07cba89-e6a8-4ad6-afbb-d8dacfec0484/var/log/boot-sav/log/2012-01-11__20h23boot-repair02
combobox_ostoboot_bydefault_fillin
set_checkbutton_reinstall_grub
combobox_separateboot_fillin
separate_bootpart and efi show_hide sda1
efi_show_hide 1 (no-gpt)
combobox_efi_fillin sda1
************************Before mainwindow appear
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, MBR_ACTION purge REINSTALL_POSSIBLE no PURGE_POSSIBLE yes UNHIDEBOOT_ACTION yes (10.s) PART_TO_REINSTALL_GRUB  () PART_TO_REINSTALL_GRUB_PURGE 1 (sda1) FORCE_GRUB all NOFORCE_DISK  REMOVABLEDISK  UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no (sdb1) grub-pc (sda1)
/usr/share/boot-sav/clean-gui-tab-mbr.sh: line 95: 13435 Terminated              while true; do
done
RETOURCOMBO_purge_grub : sda1 (Ubuntu 10.04.3 LTS)
combobox_separateboot_fillin
separate_bootpart and efi show_hide sda1
efi_show_hide 1 (no-gpt)
combobox_efi_fillin sda1
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sdb1
RETOURCOMBO_efi (EFIPART_TO_USE) : sda1
set_radiobutton_place_alldisks
set_checkbutton_reinstall_grub
combobox_separateboot_fillin
separate_bootpart and efi show_hide sda1
efi_show_hide 1 (no-gpt)
combobox_efi_fillin sda1
/usr/share/boot-sav/clean-gui-tab-other.sh: line 110: _combobox_bootflag: command not found
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sdb1
RETOURCOMBO_efi (EFIPART_TO_USE) : sda1
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sdb1
RETOURCOMBO_efi (EFIPART_TO_USE) : sda1
internet: connected
************************Before Repairing
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, MBR_ACTION purge REINSTALL_POSSIBLE no PURGE_POSSIBLE yes UNHIDEBOOT_ACTION yes (10.s) PART_TO_REINSTALL_GRUB  () PART_TO_REINSTALL_GRUB_PURGE 1 (sda1) FORCE_GRUB all NOFORCE_DISK  REMOVABLEDISK  UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no (sdb1) grub-pc (sda1)
Freed space function
internet: connected
Purge the GRUB of sda1
Unmount (force) all OS partitions except / and partition where we reinstall GRUB (sda1)
Activate all repositories in /media/a07cba89-e6a8-4ad6-afbb-d8dacfec0484/etc/apt/sources.list
dpkg_function
internet: connected
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) jaunty/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages
404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages
404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages
404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages
404  Not Found [IP: 91.189.92.180 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.180 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists...

Reading state information...
E: Couldn't find package grub-gfxpayload-lists
Reading package lists...

Reading state information...
E: Couldn't find package grub-pc-bin
Reading package lists...

Reading state information...
E: Couldn't find package grub2-common
DEBCHECK debNG, grub-gfxpayload-lists grub-pc-bin grub2-common, sda1
Reading package lists...

Reading state information...
The following packages were automatically installed and are no longer required:
sdparm acroread-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
grub-common
Suggested packages:
multiboot-doc grub-emu desktop-base
The following NEW packages will be installed:
grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 9 not upgraded.
Need to get 609kB/2,193kB of archives.
After this operation, 6,771kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main grub-pc 1.98-1ubuntu12 [609kB]
Download complete and in download only mode
Reading package lists...

Reading state information...
The following packages were automatically installed and are no longer required:
sdparm acroread-common
Use 'apt-get autoremove' to remove them.
Suggested packages:
multiboot-doc grub-emu
The following NEW packages will be installed:
grub-common
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 1,584kB of archives.
After this operation, 4,489kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main grub-common 1.98-1ubuntu12 [1,584kB]
Download complete and in download only mode
Reading package lists...

Reading state information...
The following packages were automatically installed and are no longer required:
sdparm os-prober acroread-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 9 not upgraded.
Need to get 68.1kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main ucf 3.0025 [68.1kB]
Download complete and in download only mode
Reading package lists...

Reading state information...
The following packages were automatically installed and are no longer required:
sdparm os-prober acroread-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 9 not upgraded.
Need to get 148kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main debconf 1.5.28ubuntu4 [148kB]
Download complete and in download only mode
DEBCHECK debOK, grub-pc grub-common ucf debconf, sda1
VALIDSOURCE   Candidate: 1.98-1ubuntu12 , DEBCHECK debOK
/usr/share/boot-sav/clean-gui-update.sh: line 167: 19023 Terminated              while true; do
done
internet: connected
Restore the original repositories in /media/a07cba89-e6a8-4ad6-afbb-d8dacfec0484/etc/apt/sources.list
Force mount all OS partitions for the logs
Unhide boot menu (10 seconds) if Wubi detected
Unhide GRUB boot menu in sda1/boot/grub/grub.cfg
internet: connected
/usr/share/boot-sav/bootrepair-actions.sh: line 250: 22628 Terminated              while true; do
done
E: Package 'pastebinit' has no installation candidate
Activate all repositories in /etc/apt/sources.list
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin:
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Restore the original repositories in /etc/apt/sources.list

```

---

### Post by drs305 on 2012-01-12
Trent T,

I'd don't have much time this morning and my intent was merely to add the 'code' tags for formatting purposes until I could return to review your post.

However, I do note that at least one of the problems is that your /etc/fstab entry for / is not the same UUID as what Grub2 is posting. I would guess the fstab entry is the UUID of the earlier partition/drive and that the entry has not been updated to the correct partition/UUID.

You seem to know your way around Ubuntu to be able to fix this, but if you need assistance on how to edit the entry just ask. As I said, this may or may not be the solution, but it definitely needs fixing. 

I'll return here when I have a bit more time.

---

### Post by Trent T on 2012-01-13
Thanks!  I will read up a bit on fstab, attempt to edit fstab, then post the results.
Thanks again for the prompt reply & your insights!  --Trent T

---

### Post by Trent T on 2012-01-14
I tried replacing the UUID for the boot drive in /etc/fstab, so;

```

/etc/fstab contents

20120114 – Current (broken) fstab

# /etc/fstab: static file system information. 
# 
# Use 'vol_id --uuid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# / was on /dev/sda1 during installation 
# Commented out by Dropbox 
# UUID=cf1f6b0e-147b-48c3-bfd2-e639780e58b4 /               ext3    relatime,errors=remount-ro 0       1 
# swap was on /dev/sda5 during installation 
UUID=**33722ffb-2f7a-4a8f-b1b7-5516b95c8146** none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 
UUID=cf1f6b0e-147b-48c3-bfd2-e639780e58b4 / ext3 relatime,errors=remount-ro,user_xattr 0 1
```

'New' /etc/fstab
```

# /etc/fstab: static file system information. 
# 
# Use 'vol_id --uuid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# / was on /dev/sda1 during installation 
# Commented out by Dropbox 
# UUID=cf1f6b0e-147b-48c3-bfd2-e639780e58b4 /               ext3    relatime,errors=remount-ro 0       1 
# swap was on /dev/sda5 during installation 
UUID=a07cba89-e6a8-4ad6-afbb-d8dacfec0484 none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 
UUID=cf1f6b0e-147b-48c3-bfd2-e639780e58b4 / ext3 relatime,errors=remount-ro,user_xattr 0 1
```

This also did not work :confused:

So I followed the excellent advice of oldfred (link) and restored the /home directory from my backup to a fresh install;

[http://ubuntuforums.org/showthread.php?t=1850522highlight=HOWTO%3A+Restore+Ubuntu+drive](http://ubuntuforums.org/showthread.php?t=1850522highlight=HOWTO%3A+Restore+Ubuntu+drive)

**Here are the steps I took;**

**1) Housecleaning on the /home directory in your backup.**
   Mine had the .TAR backup file in it, and a bunch of other stuff I really didn't need to keep.
[B]
2) Fresh install of the desired Ubuntu version to the target drive.[/B]
   In my case, Ubuntu 10.10.  Should be the same or a more recent release.
   You should be able to start it normally, and run the rest of the steps from within the new drive.  The target drive becomes "File System".

**3) Be sure your old /home directory will fit on the target drive.**
   Go to Places > Computer.
   Find the /home directory on the backup drive.
   Right click, select 'Properties.'
   Note the size of the directory.

   Right click the target drive (ie., File System)
   Select 'Properties.'
   Be sure you have room to spare after loading /home.

**4) Reload any desired additional software apps.**
   I didn't do this step, so I will have to reload data from backup
   after installing apps like Korganizer.  
[B]
5) Transfer the /home directory.[/B]
   Go to Applications > Accessories > Terminal
   ```
sudo nautilus
```
   to move the files.
   Copy the /home directory from backup.
   Paste the /home directory into the root directory of the File System disk.
   You'll know you are in the right place, since there is a /home directory there already (a mostly empty one).

**6) Merge vs. Overwrite?**
   I merged the directories, and it seemed to work OK.
   Select 'replace all' when duplicate files are detected.
   As /home was merged, there were about 10 to 20 errors. 
   I chose to default errors to 'skip' and it seems to have come out OK.
   There may be advantages to Overwriting or Merging-- Maybe someone 
   will comment on which is best.
   Next time this happens, I may select 'Overwrite' at the beginning.

**7) Plan for the future.**
   Complete recovery was possible because I was able to back up my data before the system crashed.
   After this, I'm going to try to automate my backups, in case the next system crash is not so benign.
   I'm also going park a document on my desktop for the names of the additional packages I install, so I can remember what they were! :D

Thanks to all who posted on related topics before, especially drs305, oldfred, and pritam_par!

---

### Post by Trent T on 2012-01-15
Ahh, one more problem, that may not belong here;

After restoring the /home directory, I find that most subdirectories are now owned by Root, instead of by me.  I can  view the files, but not delete or change them.  Is there any quick way to change file permissions?

Thanks,

Trent T

---

### Post by drs305 on 2012-01-16
> **Trent T said:**
> Ahh, one more problem, that may not belong here;

After restoring the /home directory, I find that most subdirectories are now owned by Root, instead of by me.  I can  view the files, but not delete or change them.  Is there any quick way to change file permissions?

Since everything in your HOME folder should be owned by you, you can change the ownership with the 'chown' command. The following command changes the ownership of all files in the user's home directory to the current USER (which should be you) and also assigns them to your group.

Be very careful with permission and chown commands. A typo can render your system unusable!

```
sudo chown -R $USER: ~/home
```

---

### Post by Trent T on 2012-01-17
Yikes!  Now I'm sweating--

I'd like to add some detail to your comment to be sure I understand it.

From your note, the change ownership command in CLI (Terminal) would be;

```
sudo chown -R username: /home/username
```
-R switch makes it Recursive to all subdirectories.
Applied to my own system, that command would be

```
sudo chown -R trent: /home/trent
```

I am specifying my own subdirectory within /home, since my wife has an account on this computer as well.  She would brain me if I assigned ownership of all her files to myself! :)

The manual page in CLI (Terminal)
```
chown --help
```
allows me to specify the group for files as well-- 
Since the current group seems to mostly be ROOT, I may issue chown as
```
sudo chown -R username:usergroup /home/username
```
to be sure all the ROOT groups convert over to me.
Applied to my own case, this would be
```
sudo chown -R trent:trent /home/trent
```

I think this is right.
Will post to let you know the results.
Thanks again for your assistance!

> **drs305 said:**
> Since everything in your HOME folder should be owned by you, you can change the ownership with the 'chown' command. The following command changes the ownership of all files in the user's home directory to the current USER (which should be you) and also assigns them to your group.

Be very careful with permission and chown commands. A typo can render your system unusable!

```
sudo chown -R $USER: ~/home
``` 

---

### Post by Trent T on 2012-01-17
One other thing--
Since Ubuntu 10.10 assigns a suffix to the UserID now, do I need to add the suffix when identifying change of ownership in CLI?

For example, when I log in, my user ID comes up as trent-MS-7366.
Within the File System, my UserID is only 'trent' (without quotes).
OTOH, the prompt in CLI/Terminal is
trent@trent-MS-7366:~$

---

### Post by drs305 on 2012-01-18
Trent,

The alphanumerics after the @ should be the name of the computer. Before the @ is the username. 

Using the ":" after a username in the chown command is the same as repeating the username for the group --  *trent:* is the same as *trent:trent*  Either one is fine.

If you use the commands as we've both discussed your home directory should be owned by you, and your wife should remain happy as well.  ;-)

---

### Post by Trent T on 2012-01-18
I entered 
```
sudo chown -R username:usergroup /home/username
```
in the terminal (with my own name and group entered).  This has cleared up all of the problems-- AND without aggravating my wife! :P 

Thanks again for your timely assistance!!
Trent T

---

### Post by Andrew_nuts on 2012-02-05
This solution is given on below link post

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
[http://ubuntuforums.org/showthread.php?t=1417672](http://ubuntuforums.org/showthread.php?t=1417672)

Both the post solve the same issue. hope this help

---

### Post by Tranas on 2012-02-28
> **drs305 said:**
> [COLOR=MAROON][B][SIZE=4][CENTER][I]The Grub Rescue Mode Megathread

[SIZE=3](*The Grub Rescue Hijack Thread*)

[/SIZE][/I][/CENTER]
[/SIZE][/B][/COLOR]
**[COLOR=DarkRed][SIZE=3]I'm Still Stuck at the 'grub rescue>' Prompt[/SIZE][/COLOR]**

error after a fresh install of Ubuntu 11.10 on a WinXP Thinkpad laptop -

Used boot repair disk
     Executed the 1 click recommended repair
     Executed the "Purge and reinstall" option
     
Filed bug report
     [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/929322](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/929322)

Used RescaTux
     Executed Restore Grub 
     Executed Update Grub


```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    31,449,599    31,449,537   7 NTFS / exFAT / HPFS
/dev/sda2          31,449,600   465,317,999   433,868,400   7 NTFS / exFAT / HPFS
/dev/sda3         486,445,054   488,396,799     1,951,746   5 Extended
/dev/sda5         486,445,056   488,396,799     1,951,744  82 Linux swap / Solaris
/dev/sda4         465,319,936   486,443,007    21,123,072  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/sda1        921022FE1022E945                       ntfs       OS
/dev/sda2        A69536E52B808954                       ntfs       Data
/dev/sda4        2d5031cc-e70a-4ac0-82d3-bb3f5e1b2443   ext4       
/dev/sda5        27149e7c-268f-42cb-af20-663eaffbc583   swap       
/dev/sdb         844E-61D3                              vfat       NEW VOLUME

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda4        /media/sda4              ext4       (rw)
/dev/sdb         /media/sdb               vfat       (rw,utf8)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda4/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set=root 2d5031cc-e70a-4ac0-82d3-bb3f5e1b2443
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos4)'
  search --no-floppy --fs-uuid --set=root 2d5031cc-e70a-4ac0-82d3-bb3f5e1b2443
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 2d5031cc-e70a-4ac0-82d3-bb3f5e1b2443
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=2d5031cc-e70a-4ac0-82d3-bb3f5e1b2443 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 2d5031cc-e70a-4ac0-82d3-bb3f5e1b2443
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=2d5031cc-e70a-4ac0-82d3-bb3f5e1b2443 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 2d5031cc-e70a-4ac0-82d3-bb3f5e1b2443
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 2d5031cc-e70a-4ac0-82d3-bb3f5e1b2443
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 921022FE1022E945
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=2d5031cc-e70a-4ac0-82d3-bb3f5e1b2443 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=27149e7c-268f-42cb-af20-663eaffbc583 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 228.323280334 = 245.160255488  boot/grub/core.img                             1
 228.321300507 = 245.158129664  boot/grub/grub.cfg                             1
 223.160148621 = 239.616385024  boot/initrd.img-3.0.0-12-generic               1
 228.305812836 = 245.141499904  boot/vmlinuz-3.0.0-12-generic                  1
 223.160148621 = 239.616385024  initrd.img                                     1
 228.305812836 = 245.141499904  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: (stdin): Compressed data is corrupt
  No volume groups found
mdadm: No arrays found in config file or automatically




```

---

### Post by Tranas on 2012-02-28
> **Tranas said:**
> error after a fresh install of Ubuntu 11.10 on a WinXP Thinkpad laptop -


And after updating grub via "geek"

Grub still does not fly.

just one of the reasons you only have 1% if market even when you give it away.

```


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d6525c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    31449599    15724768+   7  HPFS/NTFS/exFAT
/dev/sda2        31449600   465317999   216934200    7  HPFS/NTFS/exFAT
/dev/sda3       486445054   488396799      975873    5  Extended
/dev/sda4       465319936   486443007    10561536   83  Linux
/dev/sda5       486445056   488396799      975872   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /usr/ /mnt/usr
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# sudo grub-install --recheck /dev/sda
Installation finished. No error reported.
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev
ubuntu@ubuntu:~$ sudo umount /mnt/proc
ubuntu@ubuntu:~$ sudo umount /mnt/sys
ubuntu@ubuntu:~$ sudo umount /mnt/usr
ubuntu@ubuntu:~$ sudo umount /mnt
ubuntu@ubuntu:~$ sudo reboot

```

net result after almost a month -

[B]error: unknown filesystem.
grub rescue>
[/B]

---

### Post by kaykelkar on 2012-02-28
> **CarpKing said:**
> I encountered this problem after installing Maverick.  I attempted to boot to my LiveUSB to reinstall grub only to have the computer boot normally after I selected "USB" from the menu.  A few more tries determined that this was the only way to avoid the rescue prompt.  Apparently Grub somehow installed itself to my USB stick.  While booted up I did:

```
sudo grub-install --recheck /dev/<proper harddrive>
```

This fixed the issue, and now my computer boots as expected.  I think I'll have to remake that LiveUSB, though.
hi there,
i think i've done something similar to you. well i wanted to install a ubuntu on an SD card and so i did it. but while selecting the boot loader i messed up and selected it as the SD Card. Now everytime i need to start the laptop to use win-xp, i need to have the card inserted into it....else id give the grub>rescue prompt. pls help me i need to do away with the ubuntu and grub in the win xp MBR!

appreciate your help in advance :)

---

### Post by circusmask on 2012-05-30
Hi folks,

I'm trying to install Ubuntu 12.04 on my netbook (Asus EEE PC 1000H) and have hit a wall. I chose to upgrade from 10.04 because the last two kernel upgrades gave me trouble with my wireless connectivity.

I worked my way through the installation process and made the mistake of trying to repartition my hard drive (in retrospect I didn't know enough about what I was doing to do it right). Consequently, when I rebooted I got the grub rescue prompt and am now trying to get everything working again.

I've tried going through the steps here but have run into some trouble. I was able to figure out which partition I want to set as prefix and root (hd0,5), but when I enter the command:
```
insmod linux
```
I get this:
```
error: the symbol 'grub_mm_base' not found.
```
I've tried using Rescatux (here:[http://www.supergrubdisk.org/rescatux/]("http://www.supergrubdisk.org/rescatux/")). I installed it on a stick using the universal USB installer. When I set the boot priority to the stick, I get:
```
error: the symbol 'grub_xputs' not found.
```
Alternately, if I set the priority to the stick and disable the hard drive (just under boot priority, not totally), I get:
```
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key
```
I can't run any of the scripts I've seen for gathering more information, as I can't get anything other than the grub rescue prompt.

I am doing my best to wrap my head around all of this (I've been scouring forum posts and web pages for the last 24 hours), but I'm only minimally versed in these things. Where should I be looking? I know it's possible only to run a handful of commands from the grub rescue shell. Is there a way to restore grub_mm_base? Is that something I can put on a stick and access through the rescue shell?

Any help much appreciated!

---

### Post by drs305 on 2012-05-31
circusmask,

Sorry you are having problems with Grub. The error messages you are getting usually mean that Grub isn't fully installed on your system. If you think the rest of the installation went ok and want to fix grub, the way to do it is to use the 'chroot' method from a LiveCD.

You boot the LiveCD, mount your real Ubuntu files and then chroot into the system. From then on, the commands you run will affect your real installation and not the CD's file.

You can find guidance on this in the 'Chroot' link in my signature or from the Ubuntu community doc:
[https://help.ubuntu.com/community/Grub2/Installing#ChRoot]("https://help.ubuntu.com/community/Grub2/Installing#ChRoot")

---

### Post by Pokn on 2012-06-08
Hi, 

My laptop has/had ubuntu 11.04 and windows 7 installed.

Yesterday I decided to delete the partition with ubuntu installed from computer management within windows (dumb, i know)

Now I am stuck.

I have tried to boot from both the ubuntu 11.04 and windows 7 installation disks but none of them will boot. 

When I power up my laptop I get the first screen which has the intel logo etc, then a flash of white writing which is too quick to read even one word, then straight into the "error: no such partition. grub rescue>" screen

if i use the command "ls" i get:
(hd0) (hd0,msdos2) (hd0,msdos1)

here is where I am stuck and nothing at all seems to work...

I really need some help please because my laptop is now useless to me and i have important files on there

Thanks

---

### Post by drs305 on 2012-06-08
Pokn

Welcome to the Ubuntu forums. :-)

Sorry you are having problems booting.

If the first thing your computer is seeing is a grub message it would appear that the MBR is using Grub, which can't find it's files. 

Since you want to use Windows, I would normally recommend using a Windows repair CD. As that apparently isn't working either, I would next suggest creating a bootable CD with a boot repair app. SuperGrub Disk or Boot Repair (see link in my signature line) may be able to get your Windows boot back.

A quick fix, if you have a bootable Ubuntu LiveCD, would be to boot the CD, open a terminal, and install lilo. It can fix an MBR problem so it points to your Windows files.
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

When you install lilo it will say that it is not fully  installed and that you need to run more commands. This is not necessary, just run the above commands and reboot. If the Windows boot files are intact and the boot flag is on your Windows partition this may be all you need to be able to boot into Windows.

---

### Post by Pokn on 2012-06-08
Hey drs305,

I will use any operating system I can get to work right now, I have tried using a supergrub usb, tried booting from an ubuntu cd, tried windows cd, but I get the same result every time...

For some reason I cant even get into the bios to check that the boot order is correct.

No matter what I do I am at the grub repair screen within seconds

:( ....any other ideas?

As a last resort I'm willing to lose everything just to get my laptop back... is there a way I can do that?

Thanks

---

### Post by drs305 on 2012-06-08
> **Pokn said:**
> 

No matter what I do I am at the grub repair screen within seconds

:( ....any other ideas?

As a last resort I'm willing to lose everything just to get my laptop back... is there a way I can do that?

Thanks

I think getting into BIOS should be your first priority. You need to be able to get into something bootable. If you haven't been able to boot a USB drive or CD then it would appear the BIOS is happy to boot only the one drive with GRUB installed on it.

If you aren't sure what key needs to be pressed to enter BIOS during boot you should be able to Google your laptop's manufacturer to find out. 

You could try to use the "ls" command at the grub rescue prompt to explore your partitions in the off chance you have some Grub files left. Without them, you couldn't load a Windows module to try to boot Windows.

Try "ls (hd0,1)/" and "ls (hd0,2)/" to see what the partitions are and if there are any Ubuntu files on them.

Other than that, I'd probably start a new thread with an emphasis on how to get into BIOS and boot a USB or CD.

---

### Post by Pokn on 2012-06-08
> **drs305 said:**
> I think getting into BIOS should be your first priority. You need to be able to get into something bootable. If you haven't been able to boot a USB drive or CD then it would appear the BIOS is happy to boot only the one drive with GRUB installed on it.

If you aren't sure what key needs to be pressed to enter BIOS during boot you should be able to Google your laptop's manufacturer to find out. 

You could try to use the "ls" command at the grub rescue prompt to explore your partitions in the off chance you have some Grub files left. Without them, you couldn't load a Windows module to try to boot Windows.

Try "ls (hd0,1)/" and "ls (hd0,2)/" to see what the partitions are and if there are any Ubuntu files on them.

Other than that, I'd probably start a new thread with an emphasis on how to get into BIOS and boot a USB or CD.

Thank you for your replies. I know how to get into the bios but the issue is that I do not get chance...

I switch on my laptop, and there is no time to get into bios... it goes straight to the grub repair screen within about 5 seconds, the bios is not possible to get in to.

I deleted the partition which ubuntu was installed on and formatted it, so i dont have any files left, i only have files on the windows partition...

do i need to buy a new hard drive?

---

### Post by drs305 on 2012-06-08
> **Pokn said:**
> 
do i need to buy a new hard drive?
No. 

You just need to get into BIOS. If you know the key to press, start pressing it as soon as you press the Power key and keep pressing it until it appears. The GRUB prompt will not appear until the system has accessed BIOS, so there should be a way to interrupt the boot to get into BIOS setup.

I think there are ways to reset the BIOS such as holding a button on the motherboard or removing the CMOS battery. I believe most BIOS would default to booting a removable device before an internal hard drive but you'd need better information than I can provide for that.

---

### Post by lferree on 2012-06-09
I'm getting grub rescue> in Lubuntu 12.04 after an update froze and I rebooted. Comparing files to a virtual machine (hd0,msdos1)/boot/grub/* seems to be missing several files. Any thoughts on what I can do to fix this?

Settings in grub.cfg seem OK. I'm guessing Grub was being updated, but froze before all the new files could be copied over. 208 files in (hd0,msdos1)/boot/grub/* on my virtual machine, 34 on the system not booting.

Trying to copy missing grub/* files from USB drive off LiveCD is failing due to permissions. Not sure how to get a working sudo pcmanfm.

Files on source USB stick have "lubuntu" permissions, target has "root" permissions.

---

### Post by drs305 on 2012-06-09
> **lferree said:**
> I'm getting grub rescue> in Lubuntu 12.04 after an update froze and I rebooted. Comparing files to a virtual machine (hd0,msdos1)/boot/grub/* seems to be missing several files. Any thoughts on what I can do to fix this?

You are probably going to have to 'chroot' into your installation by booting a LiveCD and reinstalling Grub 2. You can do this from the LiveCD desktop by installing Boot Repair, which can walk you through the procedure. I'd recommend trying this first. The link for Boot Repair is in my signature line.

You can also purge/reinstall following the instructions from the community doc site:
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System]("https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System")
This section of the Grub 2 docs details several different ways of getting the files back on your system; purging/reinstalling is the most comprehensive but is a bit more complicated that the other methods mentioned.

(The chroot instructions are also on the UF at the "Chroot" link in  my signature line.)

---

### Post by Pokn on 2012-06-09
> **drs305 said:**
> No. 

You just need to get into BIOS. If you know the key to press, start pressing it as soon as you press the Power key and keep pressing it until it appears. The GRUB prompt will not appear until the system has accessed BIOS, so there should be a way to interrupt the boot to get into BIOS setup.

I think there are ways to reset the BIOS such as holding a button on the motherboard or removing the CMOS battery. I believe most BIOS would default to booting a removable device before an internal hard drive but you'd need better information than I can provide for that.

OK thanks, I will have to try to remove the CMOS battery. Failing that I will just purchase a new hard drive.

I have noticed something fwiw...

If I switch on the laptop without a bootable CD inside, I am presented with the first start up screen (with the intel logo etc), and then immediately after, the grub repair message. I can not get into the bios no matter what.

But, if there is a bootable CD inserted, I hear the DVD drive going to work and the Grub message takes up to 20 seconds to appear. Still impossible to get into bios tho.

I'm not sure if that means it's trying to boot from CD or not...

Thanks for your help but it sounds like i need to break out the screwdrivers... sigh

---

### Post by drs305 on 2012-06-09
> **Pokn said:**
> 
But, if there is a bootable CD inserted, I hear the DVD drive going to work and the Grub message takes up to 20 seconds to appear. Still impossible to get into bios tho.


Sounds like it's trying to boot the CD. Have you tried a more than one CD? If you have a commericial CD see if it boots. If so, you may still be able to create a bootable rescue CD that might help you resolve this issue.

---

### Post by Pokn on 2012-06-09
> **drs305 said:**
> Sounds like it's trying to boot the CD. Have you tried a more than one CD? If you have a commericial CD see if it boots. If so, you may still be able to create a bootable rescue CD that might help you resolve this issue.

i have the original ubuntu livecd that i installed on the machine (11.04)

I have the original windows 7 CD that I used to install

I also have tried the latest ubuntu liveCD...

Nothing works. Every time it goes to the grub error and nothing will actually boot...


EDIT: I should also mention that I have the same Windows 7 version installed on my pc... could I make a recovery CD on that and try it?

---

### Post by Pokn on 2012-06-12
Bump.

I still have no success getting my laptop to boot.

I have tried the latest supergrub 1.99 disk and when I instert it and restart the laptop the screen stays black but does nothing

Any ideas? I'm really stuck :(

---

### Post by Pokn on 2012-06-12
> **Pokn said:**
> Bump.

I still have no success getting my laptop to boot.

I have tried the latest supergrub 1.99 disk and when I instert it and restart the laptop the screen stays black but does nothing

Any ideas? I'm really stuck :(

Fixed... 

Inserted the laptop HDD in my pc and recovered files/formatted that way

---

### Post by lferree on 2012-06-12
Thank you. This ended up working. First time, it froze during install. (Like what happened with updates b4 all this mess) Think I might have a failing hdd. Luckily I got a backup -- just running simple TeamSpeak server.

Now I got a strange Ubuntu boot menu -- but I can live with that!
Thanks again!

> **drs305 said:**
> You are probably going to have to 'chroot' into your installation by booting a LiveCD and reinstalling Grub 2. You can do this from the LiveCD desktop by installing Boot Repair, which can walk you through the procedure. I'd recommend trying this first. The link for Boot Repair is in my signature line.

You can also purge/reinstall following the instructions from the community doc site:
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System]("https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System")
This section of the Grub 2 docs details several different ways of getting the files back on your system; purging/reinstalling is the most comprehensive but is a bit more complicated that the other methods mentioned.

(The chroot instructions are also on the UF at the "Chroot" link in  my signature line.)

---

### Post by Vaarala on 2012-08-28
Hello everyone!

I upgraded from 10.04 to 12.04 on a computer that is rather old, and has a broken optical disc drive, and no booting possibility from usb. Ubuntu is the only operating system on the computer/hard drive.

I got the grub rescue prompt.

I found this thread, and was able to proceed thus far:
I found the */boot/grub* folder with a lot of .mod files in it.
I made these settings:

prefix=(hd0,1)/boot/grub
and
root=hd0,1

However, when I tried the command "insmod linux",
I got stuck with this error message: 

error : the symbol 'grub_mm_base' not found


(And on a side note, assuming I get help with this, how will I know what are the right values for X and Y in the next phase, number six:
**[COLOR=DarkRed]Load the Kernel & Initrd image.[/COLOR]**
[LIST]
[*]**linux /vmlinuz root=/dev/sdXY ro**
[LIST]
[*]Substitute the correct values for X,Y - Example: sda5
[/LIST]
 
[/LIST]
The command ls does give the drives/partitions, but not the device. Am I to assume that it's sda1, which would be the most logical option?)

Hopefully I was clear enough. :)


Edit: I was able to fix the issue with an optical drive that I found and with the program called boot repair.

---

### Post by zamolxis on 2012-10-20
Tried installing on an old PII-333 computer on a 61 GB Diamond Max drive. This drive can only be used in this computer with a "jumper limitation" - recognized by the Mobo as 8GB but seen by the OS as 60 GB. It's the smallest IDE drive I have available but unfortunately, it poses some unique problems.

After the install is concluded and I reboot without the CD, I always get the grub rescue prompt with the error "out of disk". Trying to "rescue" with prefix, root and insmod linux results in another "out of disk" error right after insmod (and all the other commands in the list thereafter).

I've tried various other configurations but nothing seems to work. It seems that such a drive cannot be used as a boot drive in this setup. This is rather shameful, as Windows can use it - it's just Linux that cannot.

---

### Post by drs305 on 2012-10-21
> **zamolxis said:**
> Tried installing on an old PII-333 computer on a 61 GB Diamond Max drive. This drive can only be used in this computer with a "jumper limitation" - recognized by the Mobo as 8GB but seen by the OS as 60 GB. It's the smallest IDE drive I have available but unfortunately, it poses some unique problems.

After the install is concluded and I reboot without the CD, I always get the grub rescue prompt with the error "out of disk". Trying to "rescue" with prefix, root and insmod linux results in another "out of disk" error right after insmod (and all the other commands in the list thereafter).

I've tried various other configurations but nothing seems to work. It seems that such a drive cannot be used as a boot drive in this setup. This is rather shameful, as Windows can use it - it's just Linux that cannot.

It's possible that with your configuration the system can't see any Grub configuration files past the 8GB limit (even though the OS, once booted, can). This is a very old limitation; later BIOS could see to 137GB, and the newest don't have that limitation. 

The solution in each case is to place a boot partition within the limits the BIOS can see (for you perhaps 8GB). If you do a search on these forums for posts discussing the 137GB BIOS limitation you will find how to go about creating a boot partition in the correct location. 

With a 137GB limitation, finding an area to create a boot partition isn't normally a problem. If you have to find space in the first 8GB of the drive it could be more of a problem. You might have to install and boot from a secondary drive or an external drive if you can't put the partition on your main drive.

---

### Post by Jacob72 on 2013-02-15
Hello, 

I am getting this error and am running off a bootable USB.  I had this problem before on a upgraded ubuntu version. I fixed it, but decided to install the latests Ubuntu from fresh, now it has happened again. I have not deleted the old install yet as I wanted to get all my settings setup on the new one first. 

Thanks for your help :)


```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid a21352e9-6e72-44d9-9583-1130a0f34f84 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 2012-10-23
    Boot sector info:  Syslinux looks at sector 61468 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   102,402,047   102,400,000  83 Linux
/dev/sda2         102,402,048   204,802,047   102,400,000  83 Linux
/dev/sda3         204,802,048   215,042,047    10,240,000  82 Linux swap / Solaris
/dev/sda4         215,044,094   488,396,799   273,352,706   5 Extended
/dev/sda5         215,044,096   481,714,175   266,670,080  83 Linux
/dev/sda6         481,716,224   488,396,799     6,680,576  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
135 heads, 14 sectors/track, 516811 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   976,771,071   976,769,024   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 16.1 GB, 16134438912 bytes
64 heads, 32 sectors/track, 15387 cylinders, total 31512576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             32    31,512,575    31,512,544   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        a21352e9-6e72-44d9-9583-1130a0f34f84   ext4       
/dev/sda2        84bd6e93-5de7-4879-a2d4-a829707f8638   ext4       
/dev/sda5        ad8d4cea-c0fc-4548-bb16-724ef811fbd8   ext4       
/dev/sda6        4ff20651-b033-4694-8eb5-03d3e999007e   swap       
/dev/sdb1        CE5C8AC35C8AA5B5                       ntfs       Folders
/dev/sdd1        1605-231E                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
    linux    /boot/vmlinuz-3.2.0-36-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-36-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
    echo    'Loading Linux 3.2.0-36-generic ...'
    linux    /boot/vmlinuz-3.2.0-36-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-36-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
    linux    /boot/vmlinuz-3.2.0-35-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-35-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
    echo    'Loading Linux 3.2.0-35-generic ...'
    linux    /boot/vmlinuz-3.2.0-35-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-35-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
    linux    /boot/vmlinuz-3.2.0-34-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-34-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
    echo    'Loading Linux 3.2.0-34-generic ...'
    linux    /boot/vmlinuz-3.2.0-34-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-34-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
    linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-33-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
    echo    'Loading Linux 3.2.0-33-generic ...'
    linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-33-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
    linux    /boot/vmlinuz-3.2.0-32-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
    echo    'Loading Linux 3.2.0-32-generic ...'
    linux    /boot/vmlinuz-3.2.0-32-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-32-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-27-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0a996161-6e83-4d3d-add0-cb32e47100d7
    linux /boot/vmlinuz-3.0.0-27-generic root=UUID=0a996161-6e83-4d3d-add0-cb32e47100d7 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-27-generic
}
menuentry "Ubuntu, with Linux 3.0.0-27-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0a996161-6e83-4d3d-add0-cb32e47100d7
    linux /boot/vmlinuz-3.0.0-27-generic root=UUID=0a996161-6e83-4d3d-add0-cb32e47100d7 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-27-generic
}
menuentry "Ubuntu, with Linux 3.0.0-26-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0a996161-6e83-4d3d-add0-cb32e47100d7
    linux /boot/vmlinuz-3.0.0-26-generic root=UUID=0a996161-6e83-4d3d-add0-cb32e47100d7 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-26-generic
}
menuentry "Ubuntu, with Linux 3.0.0-26-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0a996161-6e83-4d3d-add0-cb32e47100d7
    linux /boot/vmlinuz-3.0.0-26-generic root=UUID=0a996161-6e83-4d3d-add0-cb32e47100d7 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-26-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0a996161-6e83-4d3d-add0-cb32e47100d7
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=0a996161-6e83-4d3d-add0-cb32e47100d7 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0a996161-6e83-4d3d-add0-cb32e47100d7
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=0a996161-6e83-4d3d-add0-cb32e47100d7 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=84bd6e93-5de7-4879-a2d4-a829707f8638 /home           ext4    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=2db26554-ca81-40e7-8e42-35bc416f8e1e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-32-generic               2
               =                boot/initrd.img-3.2.0-33-generic               2
               =                boot/initrd.img-3.2.0-34-generic               1
               =                boot/initrd.img-3.2.0-35-generic               2
               =                boot/initrd.img-3.2.0-36-generic               2
               =                boot/vmlinuz-3.2.0-32-generic                  1
               =                boot/vmlinuz-3.2.0-33-generic                  1
               =                boot/vmlinuz-3.2.0-34-generic                  2
               =                boot/vmlinuz-3.2.0-35-generic                  1
               =                boot/vmlinuz-3.2.0-36-generic                  2
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ad8d4cea-c0fc-4548-bb16-724ef811fbd8
else
  search --no-floppy --fs-uuid --set=root ad8d4cea-c0fc-4548-bb16-724ef811fbd8
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-ad8d4cea-c0fc-4548-bb16-724ef811fbd8' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ad8d4cea-c0fc-4548-bb16-724ef811fbd8
    else
      search --no-floppy --fs-uuid --set=root ad8d4cea-c0fc-4548-bb16-724ef811fbd8
    fi
    linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=ad8d4cea-c0fc-4548-bb16-724ef811fbd8 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-23-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-ad8d4cea-c0fc-4548-bb16-724ef811fbd8' {
    menuentry 'Ubuntu, with Linux 3.5.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-23-generic-advanced-ad8d4cea-c0fc-4548-bb16-724ef811fbd8' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ad8d4cea-c0fc-4548-bb16-724ef811fbd8
        else
          search --no-floppy --fs-uuid --set=root ad8d4cea-c0fc-4548-bb16-724ef811fbd8
        fi
        echo    'Loading Linux 3.5.0-23-generic ...'
        linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=ad8d4cea-c0fc-4548-bb16-724ef811fbd8 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-23-generic-recovery-ad8d4cea-c0fc-4548-bb16-724ef811fbd8' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ad8d4cea-c0fc-4548-bb16-724ef811fbd8
        else
          search --no-floppy --fs-uuid --set=root ad8d4cea-c0fc-4548-bb16-724ef811fbd8
        fi
        echo    'Loading Linux 3.5.0-23-generic ...'
        linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=ad8d4cea-c0fc-4548-bb16-724ef811fbd8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-ad8d4cea-c0fc-4548-bb16-724ef811fbd8' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ad8d4cea-c0fc-4548-bb16-724ef811fbd8
        else
          search --no-floppy --fs-uuid --set=root ad8d4cea-c0fc-4548-bb16-724ef811fbd8
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=ad8d4cea-c0fc-4548-bb16-724ef811fbd8 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-ad8d4cea-c0fc-4548-bb16-724ef811fbd8' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ad8d4cea-c0fc-4548-bb16-724ef811fbd8
        else
          search --no-floppy --fs-uuid --set=root ad8d4cea-c0fc-4548-bb16-724ef811fbd8
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=ad8d4cea-c0fc-4548-bb16-724ef811fbd8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ad8d4cea-c0fc-4548-bb16-724ef811fbd8
    else
      search --no-floppy --fs-uuid --set=root ad8d4cea-c0fc-4548-bb16-724ef811fbd8
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ad8d4cea-c0fc-4548-bb16-724ef811fbd8
    else
      search --no-floppy --fs-uuid --set=root ad8d4cea-c0fc-4548-bb16-724ef811fbd8
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a21352e9-6e72-44d9-9583-1130a0f34f84' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a21352e9-6e72-44d9-9583-1130a0f34f84
    else
      search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
    fi
    linux /boot/vmlinuz-3.2.0-36-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-36-generic
}
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-a21352e9-6e72-44d9-9583-1130a0f34f84' {
    menuentry 'Ubuntu, with Linux 3.2.0-36-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-36-generic--a21352e9-6e72-44d9-9583-1130a0f34f84' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a21352e9-6e72-44d9-9583-1130a0f34f84
        else
          search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
        fi
        linux /boot/vmlinuz-3.2.0-36-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-36-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-36-generic-root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro recovery nomodeset-a21352e9-6e72-44d9-9583-1130a0f34f84' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a21352e9-6e72-44d9-9583-1130a0f34f84
        else
          search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
        fi
        linux /boot/vmlinuz-3.2.0-36-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-35-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic--a21352e9-6e72-44d9-9583-1130a0f34f84' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a21352e9-6e72-44d9-9583-1130a0f34f84
        else
          search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
        fi
        linux /boot/vmlinuz-3.2.0-35-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-35-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro recovery nomodeset-a21352e9-6e72-44d9-9583-1130a0f34f84' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a21352e9-6e72-44d9-9583-1130a0f34f84
        else
          search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
        fi
        linux /boot/vmlinuz-3.2.0-35-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-34-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-34-generic--a21352e9-6e72-44d9-9583-1130a0f34f84' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a21352e9-6e72-44d9-9583-1130a0f34f84
        else
          search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
        fi
        linux /boot/vmlinuz-3.2.0-34-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-34-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-34-generic-root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro recovery nomodeset-a21352e9-6e72-44d9-9583-1130a0f34f84' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a21352e9-6e72-44d9-9583-1130a0f34f84
        else
          search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
        fi
        linux /boot/vmlinuz-3.2.0-34-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-33-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-33-generic--a21352e9-6e72-44d9-9583-1130a0f34f84' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a21352e9-6e72-44d9-9583-1130a0f34f84
        else
          search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
        fi
        linux /boot/vmlinuz-3.2.0-33-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-33-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-33-generic-root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro recovery nomodeset-a21352e9-6e72-44d9-9583-1130a0f34f84' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a21352e9-6e72-44d9-9583-1130a0f34f84
        else
          search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
        fi
        linux /boot/vmlinuz-3.2.0-33-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic--a21352e9-6e72-44d9-9583-1130a0f34f84' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a21352e9-6e72-44d9-9583-1130a0f34f84
        else
          search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
        fi
        linux /boot/vmlinuz-3.2.0-32-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic-root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro recovery nomodeset-a21352e9-6e72-44d9-9583-1130a0f34f84' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a21352e9-6e72-44d9-9583-1130a0f34f84
        else
          search --no-floppy --fs-uuid --set=root a21352e9-6e72-44d9-9583-1130a0f34f84
        fi
        linux /boot/vmlinuz-3.2.0-32-generic root=UUID=a21352e9-6e72-44d9-9583-1130a0f34f84 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-32-generic
    }
}

### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=ad8d4cea-c0fc-4548-bb16-724ef811fbd8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4ff20651-b033-4694-8eb5-03d3e999007e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.5.0-17-generic               1
               =                boot/initrd.img-3.5.0-23-generic               2
               =                boot/vmlinuz-3.5.0-17-generic                  1
               =                boot/vmlinuz-3.5.0-23-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

========================= sdd1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/menu.c32                              1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdd1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/menu.c32                  :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  5f 5f 5f 5f 5f 5f 5f 5f  5f 5f 5f 5f 5f 5f 5f 5f  |________________|
*
000001b0  5f 5f 5f 5f 5f 5f 5f 5f  5f 5f 5f 5f 5f 5f 00 fe  |______________..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 10 e5 0f 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 10  e5 0f 00 f8 65 00 00 00  |............e...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sde 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/xubuntu/Downloads/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
  No volume groups found


```

---

### Post by JRazalas on 2013-06-30
NOTE FOR WUBI INSTALLERS: 
- First, let me state that I downloaded the alternate wubildr file, as stated above, and still required the "Wubi Only" command list

- Now, you may need to execute "set root=(loop0)", if the ```
linux /vmlinuz 
``` command isn't working for you. When you type ```
linux /vml
```, you should be able to hit tab for autocompletion. If nothing shows up, this may be an indicator that this is your issue.

---

### Post by XKsmnRB on 2013-10-07
Hello, I can't install Windows after Ubuntu, I get dropped into grubrescue. Sorry if somebody had the same problem (which apparently nobody in the universe has) but I'm very, very desperate.

---

### Post by oldfred on 2013-10-09
@XKsmnRB
Please start a new thread. Few look at a mega-thread. Best to have good title with enough info to attract those who may know your issue. Since Windows issue please use Other OS sub forum for your thread.

---

