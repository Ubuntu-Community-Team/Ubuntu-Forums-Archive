---
title: "win xp win 8 and ubuntu 11.10 triboot"
date: 2012-04-10
forum: General Help
---

### Post by Geezanansa on 2012-04-10
I have managed to install windows 8 consumer preview and ubuntu 11.10 on the same hard drive
As i have installed upgraded and aupdeted grub have the choice of os after grub loads.
 
Everything was working as expected.
 
I then thought how great it would be if i can put xp on another hdd and i would be able to play my pc games online(ubuntu not quite running the games(POL,wine, steam no good certainly compared to xp, win8 gives unknown api and servers kick me)
 
So after connecting second hdd to ide ribbon as slave and installing xp can only boot to xp.
Tried choosing first hdd at boot (for win 8 and ubuntu)but no errors just eventually boots xp.
 
XP is running sweet but when i reboot system boots straight into xp.(no win 8 or ubuntu choice)
 
How do i boot to ubuntu to update grub? 
 Do i add xp option to windows bootloader in win8?  How?
 
 
How do i get to grub screen that will give me all boot options?
 
My research has been enlightening but i do not understand or have the familiarity to use fully what i have been learning.
 
The three OS's i am trying to install all have different bootloaders/managers.
Because of reinstallation losing boot ability and booting to installation media means it is making it harder for me to reference what i have been reading. (no bookmarks)Finding the same how to seems to be proving difficult. not complaining trying to explain why i am posting
 
 
 
 
 
This is  not the first time round and before using boot repair live cd again thought i would post for direction as it got me ubuntu and win 8 but lost xp last time round.
 
How do i set up so at boot i have option to boot to either win 8, win xp or ubuntu?
 
Thanks in advance.

---

### Post by flurospar on 2012-04-10
So you installed it like this:

Windows 8 first
Ubuntu second
and XP third.

Note that older Windows supersede the bootloaders of newer Windows versions. And all Windows versions supersede the Linux bootloaders.

IOW, a Linux installer will care to check if Windows is there, but an old Windows installer won't care about Linux or newer Windows versions, but newer Windows versions care about older Windows installs, but not about Linux.

I doubt if anything can be done in this case.

---

### Post by Geezanansa on 2012-04-10
Hi flurospar

> Windows 8 first
Ubuntu second
and XP third.

Yep.
Win 8 and ubuntu on hdd0 and xp on hdd 1

> I doubt if anything can be done in this case.

well there are plenty of posts indicating otherwise here is a link to one i am referring to  [http://ubuntuforums.org/showthread.php?t=1271600&page=2](http://ubuntuforums.org/showthread.php?t=1271600&page=2)

It would appear boot-repair could be the answer   [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

On my previous attempt (when after connecting and installing xp hdd to ubuntu/win8 hdd system and on reboot only xp boots) used boot repair to try and fix(after using ubuntu live usb session to install and run boot repair)the result of which on rebooting grub would load automatically and give me the choice of linux kernels and windows recovery option. Loading windows recovery option got me into windows 8 but could not see xp from ubuntu or windows 8.(or grub)

Apperently using gpart(or boot repair) to remove boot flag from other windows installations (either on same hdd or not) before installing second windows os helps give each os its own grub entry...

Here is a link to the results of my (most recent)boot repair scan


Please note the following URL:
   [http://paste.ubuntu.com/923195/](http://paste.ubuntu.com/923195/)
   If  you still experience boot problems, indicate this URL to:
           [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] 
or to your favorite support forum.
No change has been performed on your computer. See you soon!

Hope that helps in helping folks to help :lolflag:

---

### Post by Geezanansa on 2012-04-10
Where did xp boot files go ?   

:refURL:
   [http://paste.ubuntu.com/923195/](http://paste.ubuntu.com/923195/)

So after booting ubuntu live usb to get into ubuntu session no xp boot files?

Is windows 8 bootloader managing xp boot files?

How do i get grub to manage/show all installed os's at grub menu on boot?

---

### Post by Geezanansa on 2012-04-10
to recap boot repair scan files were prepared as report i did not run the boot repair fix([http://paste.ubuntu.com/923195/](http://paste.ubuntu.com/923195/).  If i apply fix i lose xp but get ubuntu/win8 option at boot.  I do not know how to access xp if boot repair fix applied.
After making last post i tried rebooting and xp loads-no grub menu to select ubuntu/win8.
After rebooting  to ubuntu live usb my familiar ubuntu desktop has appeared (not live session(???))

All i want is three os's on my system with the ability to choose which os at boot.

---

### Post by Geezanansa on 2012-04-10
Found this again
> **oldfred said:**
> 
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

To understand Windows multibooting with BIOS and MBR. Not new UEFI.

To get each MS to have its own boot loader make a second primary NTFS  partition and set its boot flag on, then install the 2nd product in it.  Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

If you want two entries in grub you may have to repair your second  windows install if it is a primary partition. Otherwise both Windows  will be one entry in grub and then Windows will ofter the two choices of  Windows versions.
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

> Note that older Windows supersede the bootloaders of newer Windows  versions. And all Windows versions supersede the Linux bootloaders.

IOW, a Linux installer will care to check if Windows is there, but an  old Windows installer won't care about Linux or newer Windows versions,  but newer Windows versions care about older Windows installs, but not  about Linux.

I doubt if anything can be done in this case. 	

Try looking at this [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html) and [http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
 

What does IOW mean?

Sorry might not be catching on to what you mean, are you saying no can do?  Doesnt grub manage all the mbr and dependent files wether windows or linux?

---

### Post by Geezanansa on 2012-04-10
and this
> **oldfred said:**
> Win7 combines its boot loader with XP, so only  one windows boots and then you choose from that. You cannot then  directly boot from grub to both windows.

One workaround I saw but have not seen anyone confirm was to turn off  the boot flag on the first windows install. The second install will not  see the first and installs standalone. You then cannot boot both windows  from windows but can from grub.

Both windows have to be in primary partitions. Some installs of win7  after XP will install to a logical partition and will work only because  the boot is really from the XP install in the primary partition.

Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing]("http://members.iinet.net/%7Eherman546/p15.html#BOOTMGR_is_missing")
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.
which was found here [http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

This thread recommends installing xp>win7>ubuntu
i am using win8 so i should try installing xp>win8>ubuntu 

Been finding these waiting on boot repair running.

Had a look in advanced settings and seperated boot partition on xp drive sda2.

Reboot next.:p


 
I ran boot repair from terminal and on shutdown when finished this was in terminal ```
(glade2script:2231): Gtk-WARNING **: Could not load image 'os-uninstaller.png': Failed to open file '/usr/share/boot-sav/os-uninstaller.png': No such file or directory

(glade2script:2231): Gtk-WARNING **: Could not load image 'os-uninstaller.png': Failed to open file '/usr/share/boot-sav/os-uninstaller.png': No such file or directory
Traceback (most recent call last):
  File "/usr/bin/glade2script", line 2339, in set_widget
    exec( arg )
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Failed to open file 'boot-repair.png': No such file or directory
Traceback (most recent call last):
  File "/usr/bin/glade2script", line 2339, in set_widget
    exec( arg )
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Failed to open file 'boot-repair.png': No such file or directory
```

---

### Post by oldfred on 2012-04-10
Did you at least review the pictures on the multibooters site. That helps to understand how Windows (and BIOS/MBR based) works.

Windows only know how to boot from one primary partition with the boot flag. The Windows MBR only knows to jump to the active partition (boot flag in Linux) and boot from there. So multiple installs of Windows literally combine the boot files into the active partition. Grub will boot each version of Windows but you have to split them (and maybe repair them when split).

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Backup all the boot files. Move the XP boot files to the XP partition and repair the PBR or partition boot sector. Boot.ini in XP already says rdisk(1) so it knows it is in sdb. You may also have to edit BCD with bcdEdit in Windows7 to remove the XP entries.

You mentioned IDE type cables for hard drives. Does you BIOS let you choose which drive to boot? Most older IDE systems set boot with jumpers on drive (or location on cable), new SATA drives do not have jumpers and use BIOS to choose boot drive.

---

### Post by Geezanansa on 2012-04-10
I am posting asking for help.  As a relatively new user have been really struggling to catch on how to do what i need to and posted asking for help.  Really working out what is what and trying what other posters/threads recommend or worked for them.(if confident in relevancy)

Thank you oldfred i have found your input in other folks threads more than clear and precise instruction with plenty of reference to help posters/viewers/community understand how and why what you think.  This is a lot more helpful than folks posting and just saying what they think.

> Did you at least review the pictures on the multibooters site. That helps to understand how Windows (and BIOS/MBR based) works.I did find the pictures very helpful to get an overview of what and how is happening at boot time after posting.
There are a lot of reading hours also on learning and understanding why.

Boot repair does not see xp boot files so not sure how to access/move or copy them.(see boot repair log here [http://paste.ubuntu.com/923195/](http://paste.ubuntu.com/923195/) )
 has windows 8 taken over bootloader/manager for xp?

> Does you BIOS let you choose which drive to boot? F11 gives boot option and both hdd show in list but need to do some rebooting so i can update/recap on what is happening when system boots



signing off for now

Would like to confirm that all i am trying to achieve is a system with  win xp(sdb1) win 8 consumer preview(sda1) and ubuntu 11.10(sda2) with  the option of what to boot to at boot time(grub)

---

### Post by oldfred on 2012-04-10
Does Windows 8 let you make a repairCD or USB? I only have XP. 

I downloaded the Windows 7 repair ISO and made a USB flash drive. I found chkdsk worked better from the Windows 7 repair than from XP but had to use the Windows 7 bootsect.exe to restore an XP boot sector as the chkdsk converted it to Windows 7.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I only know a few basic commands for Windows repairs and have to search Windows forums for anything major.

---

### Post by Geezanansa on 2012-04-10
After installing xp first time round i could _**only **_boot into xp.
used ubuntu live usb live session to install and update grub.
rebooted and then on reboot selected windows 8
rebooted to ubuntu then on next reboot could not load any os
 (xp would not show in ubuntu or windows 8 file systems)
used win 8 installation media to recover win8
next reboot to ubuntu gave system not found error
tried to boot to xp but no good no ntldr
tried to boot win 8 but could not
tried recovering xp with installation media but could not load
recovered ubuntu with live usb session and  then windows 8 appears again and if i boot from ubuntu live usb grub loads with choice of windows recovery and linux kernels



As i had win 8 and ubuntu on same hdd working as expected went for reinstalling xp on the other hdd again.


XP was the only bootable os so i started this thread and ask advice
since have started live session but my usual desktop ubuntu system has loaded have allso ran boot repair again and still not checked usable results yet. 
here g:popcorn:oes

---

### Post by Geezanansa on 2012-04-10
yippee! I can boot to xp 
yippee! can boot to ubuntu
tut! no win 8

Grub OS list is loading at boot now and had two windows recovery environment loaders one being at /dev/sdc2

I have rebooted to ubuntu removed the flash drive and running boot repair again:lolflag:

boot repair finnished scanning again applied fix and gave [http://paste.ubuntu.com/923568/](http://paste.ubuntu.com/923568/)

so now i got xp and ubuntu no win 8:lolflag:


how not to triboot.....


is it poss to win xp, win 8 and ubuntu on my system?

i aint giving in yet:lolflag:
i want this to happen the more i try

---

### Post by oldfred on 2012-04-10
All the boot files are in sda1 still, so you are booting XP thru the Windows 8 partition. I am more surprised that Windows 8 does not still boot. You should be getting a BCD menu from Windows not an XP boot.ini menu. Or is it just directly booting into XP using boot.ini not the BCD?

Grub found all the boot files for both XP & Windows 7 in your sda, so that is the windows boot it presents. Not sure if XP install after 8 then messed up 8 somehow?

Did you backup boot files. And can you immediately press f8 to get to a Windows repair console? Some say f8 has to be quick or almost the same time as you press enter in grub on the Windows entry as the timing is faster than a Windows boot from the MBR. May have to try several times.

---

### Post by Geezanansa on 2012-04-10
thanks for tips oldfred.

will let you know how i am getting on

mentioned earlier that through boot repair i checked the box to sepereate/boot partition of sdb1 so now al ntldr files for xp on sda1

which gave me xp but lost win8

still working on it thanks for direction though

---

### Post by oldfred on 2012-04-10
If BIOS lets you boot sdb directly you can test if XP booting is fixed on its own. I do not see a boot flag on sdb1, so for Windows to boot XP from the MBR of sdb you will need that boot flag. You can use gparted, disk utility or from Windows makeactive to set boot flag on sdb1.
You also will need to move/copy the three XP boot files to the sdb1 partition from sda1. Then you could try booting XP by choosing the drive that is sdb - 80GB drive.

You should still have the Windows 8 boot files on sda1. And likewise you could directly test that 8 boots by installing a Windows boot loader to sda. (you of course will still have to reinstall grub2's boot loader to sda after you know Windows 8 works.)

Once sda boots Windows and sdb boots XP then you can reinstall grub2 boot loader to sda and run this to update the grub menu to boot both systems.

sudo update-grub

---

### Post by Geezanansa on 2012-04-11
Thanks for providing fix oldfred i must be catching on cos i can see exactly what you i need to do....
 
but[
 
 
QUOTE] 
If BIOS lets you boot sdb directly you can test if XP booting is fixed on its own
[/QUOTE]
 
Yep. Tried that to confirm i had goofed (boot-repair>advanced options seperate/boot files to sdb1
 
So tried booting to XP drive and no go. Could not fathom how to fix (without more mistakes/goofs)
 
Starting from scratch this time xp and win 8 on same drive different partitions then ubuntu on other drive.
 
After installing xp then used easeus partition master from within windows xp to resize, rename, relabel and reformat drives.
 
Then realised i should maybe have uninstalled grub and its files as i am getting two xp listings at boot in windows recovery like screen-even though all drives except xp partition have been formatted.
On the drive with xp there is a 2gb partition that i can remove files but can not resize or format etc. i think this could be something to with grub/bootrepair.
 
Would it be fixable with ubuntu live usb and uninstall undo grub till i get windows in then reinstall ubuntu after windows dual boot confirmed and working?
 
If only i had checked threads before working on own initiative...

---

### Post by Geezanansa on 2012-04-11
Running setup.exe (from .iso)for win8cp from inside XP should give options to upgrade or install alongside.
The XP being used is 32bit and the win8cp is 64bit = no go for upgrade from xp.  Maybe this is why i am struggling to get boot option to xp...
 
will keep trying

---

### Post by Geezanansa on 2012-04-11
okay time to recap
 
I originally tried out win8cp by upgrading xp to windows 8(on different system)
 
I liked win8cp so much but can not play games online(similar probs with ubuntu) so wanted xp and win8cp side by side rather than win8cp bootloader managing xp (win8cp xp dual boot)
 
I could not believe how familiar win8cp is after using Ubuntu 11.10 so wanted to start learning and doing more on ubuntu. I have used 11.10 since its release and due to hardware configuration was struggling to use my system as pc. It must be said oneiric has come a long way since its release but I still struggle to play the games I want/have online through ubuntu
 
If I can use all three os's one system then I would have everything I want for what I want do when I want and all from the comfort of my big comfy sofa
 
I now have xp installed to /dev/sda1(hdd0/0)and win8cp to /dev/sd2(hdd0/1)
 
removing the boot flag from xp partition before installing win8cp
 
all I need to do to boot either xp or win8cp is move the boot flag to the appropriate partition/drive using gparted livecd (from boot)
 
 
 
So now I go for Ubuntu installation then install and update grub and everything be sweet  (right?)

---

### Post by oldfred on 2012-04-11
I thought you had already installed or I would have posted this sooner. Windows only boots thru one active (boot flag) partition. So when installing if you move boot flag it separates the Windows installs so you can directly boot with grub2.

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by Geezanansa on 2012-04-11
yep they were installed but could not work out how to get xp ntldr back to xp partition so i could boot win8cp. seperately then 
i lost access to win 8 and xp so started from scratch. again.:lolflag:
 
I know this is no instant or live messaging service but i can only work within my own knowledge and understanding. using these forums has been a huge help and am doing things on machine i thought only years of it experience and diplomas would be able to produce.
 
I have been trying to update this thread as i go along 
 
My head actually hurts due to information overload and practice makes perfect right.
 
If only i had read your previous post referirng to what to do to fix boot ini etc. I can see how the log files from boot repair tell me what to do just my unfamiliarity with command handling and input which is something i am getting more confident using man, help etc to find my feet but still struggling i know what i want to do it just telling machine what to do is real eye opener/learning curve
 
 
However after using gparted livecd from boot to remove boot flag from sda2 after installing win8cp (previously removing bootflag /dev/sda1 after xp installation) and format sdb1 to ext4.
I booted up on ubuntu installation desktop.iso and installed ubuntu 11.10 to sdb1
 
used the install alongside windows xp installation choice.
 
Installation was successfull
 
Guess what happened at reboot?:guitar:
 
 
I got grub screen with ubuntu and xp loaders with win8cp recovery loader:guitar:
 
 
Now that is what i am talking about 
 
 
I know i have failed where many have succeeded but oldfred i must thank you for your contribution to this community as every thread that was relevant in me achieving this has had input from you.
 
 
live n learn if ye aint learning ye aint alive:popcorn:

---

### Post by oldfred on 2012-04-11
You are welcome and I am glad you got it working.

When I have multiple systems or multiple drives I like to run a copy of boot script just to document where everything is at.

If you run bootinfoscript from Boot-Repair the link will not last a long time so you need to copy it to a text file. Or you can directly run bootinfoscript. You do not need to post it, but save it for docuementation. I always run it before & after any major system change.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Geezanansa on 2012-04-12
now after restarting and booting into all os and updating xp now can not boot to win8cp.

Still got xp and ubuntu

windows recovery environment(loader) no worky 

[QUOTE]To get each MS to have its own boot loader make a primary NTFS partition  and set its boot flag on, then install the 2nd product in it.  Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)/[QUOTE]

seen similar sig/link in other threads you have posted and these have been my guidance.
I  have been running two systems over last year or tw and have been trying  to get gaming on ubuntu but not good results.  Have upgraded hardware  recently and trying out win8cp which got me reminiscining about ubuntu(went back to xp last six months or so for gaming) so  fired up ubuntu and after updating was much more user friendly(plug n  play)certainly compared to when it was first released.  
So the result of which i had different os 's and really do think it would be an amazing feat to get all three on one system so **_initially_**  i had ubuntu and win8cp on current system and tried to install xp last  to add to system. Nearly had it working but could not work out how to  undo a boot repair change ( seperate /boot file-advanced settings)


And then did XP>Win8cp>ubuntu  from scratch as this thread attempts to describe.

I  am now confident i understand the principle of removing boot flag of  existing media and adding boot flag to partition where additional media  will be installed before installation

previous posts in this thread do describe this but i struggle to fathom what i am on about when reading so how can anybody else?
Will  look up how to screenshot boot menu, grub prompts etc so i can show  rather than describe VMing one way but i want system running as i like  before learning about install VMware

I can boot xp and ubuntu from grub at boot but not  win8cp.  error codes "look" serious but will try boot repair first i think

---

### Post by Geezanansa on 2012-04-12
after using gparted livecd to move boot flag  (which was on ubuntu(/dev/sb1)to win8cp (/dev/sda2) restarted and windows 8 boots again
 
Previous attempts to boot win8 was giving "attempting automatic repair" then gave error screen press power to restart.... or the like 
 
just update grub might work or time for boot repair
 
still working on this but light at :lolflag:and end of tunnel

---

### Post by oldfred on 2012-04-12
Grub2 cannot boot a non-working Windows so it is good to get both XP & Windows 8 working on their own.

Then a reinstall of grub2's boot loader to the MBR and a sudo update-grub should have you booting everything.

---

### Post by Geezanansa on 2012-04-12
>  reinstall of grub2's boot loader to the MBR i did not do but after confirming win8cp is working(by moving boot flag with gparted) then moved boot flag back to ubuntu restarted and got to ubuntu desktop.
After opening terminal tried updating grub but not installed.

Used ```
man grub -k 
```to find```
 grub2-update
``` so ran ```
sudo grub2-update
```  and did not give any errors

exited and rebooted same grub list and win8cp tries to boot but fails/crashes sometimes  error code:0x00000050 and parameters are given

will reconfirm win8cp boots individually through its own boootloader and not grub then will follow the instruction from your last post oldfred

---

### Post by oldfred on 2012-04-12
You can use Boot-Repair or just install the grub2 boot loader to the MBR with a mount & grub-install.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda2 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda2 if not correct:
sudo fdisk -l
#confirm that linux is sda2
sudo mount /dev/sda2 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by Geezanansa on 2012-04-12
i have reformatted and reinstalled since last bootrepair log

Do i want grub directory in root of ubuntu drive


sudo fdisk -l gives
ubuntu-11-10@ubuntu1110-desktop:~$ sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bfd87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   118029554    59013753+   7  HPFS/NTFS/exFAT
/dev/sda2       118029555   235930589    58950517+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe02ae02a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   138814516    69407227   83  Linux
/dev/sdb2       138815486   156301311     8742913    5  Extended
/dev/sdb5       138815488   152109055     6646784   83  Linux
/dev/sdb6       152111104   156301311     2095104   82  Linux swap / Solaris


so then
```
ubuntu-11-10@ubuntu1110-desktop:~$ sudo mount /dev/sdb1 /mnt
ubuntu-11-10@ubuntu1110-desktop:~$ 
```
 but the next bit...

realised what i was doing (running this when allready mounted)

 xp=sda1 win8cp=sda2 ubuntu=sdb1


After booting fom ubuntu live usb
In terminal
sudo mount /dev/sdb1 /mnt

and


sudo grub-install --boot-directory=/mnt/boot /dev/sdb

"i see" said the blind man

---

### Post by Geezanansa on 2012-04-12
Just updating once again.

As i was feeling brave i tried to follow
> #Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda2 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda2 if not correct:
sudo fdisk -l
#confirm that linux is sda2
sudo mount /dev/sda2 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sdachanging sdX  as appropriate

and on reboot got to grub prompt tried loading linux kernel by ```
kernel /boot/vmlinuz
``` but command not recognised
checked booting to both windows by the gparted boot flag method
all good.
ran boot repair which removed and reinstalled grub rebooted to to ubuntu again so far and wasnot paying attention so missed grub menu if appeared

did sudo update-grub once in installed ubuntu everything showed up and listed as expected so here goes with the multi booting:popcorn:


here is url to most current boot repair log [http://paste.ubuntu.com/927048/](http://paste.ubuntu.com/927048/)

[]("http://paste.ubuntu.com/927048/")

---

### Post by Geezanansa on 2012-04-12
looking at blkid section of log file shows pen drive (which was installation source) having  to do with sdb1 (ubuntu)  
will hunt for source but i read somewhere in grub documentation after installing ubuntu/grub make sure sytem bios first boot choice is selected as same source of installation device

USB pendrive in my case

changing should could help

working on it:popcorn:

---

### Post by oldfred on 2012-04-12
Did you change BIOS to boot hard drive first? Or use one time boot key(f12 on my system) to choose hard drive not USB?

Boot script looks ok to me if booting from the drive that is sda.

Manual boot:
See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
linux (hd0,2)/vmlinuz root=/dev/sda2 ro
initrd (hd0,2)/initrd.img
boot

---

### Post by Geezanansa on 2012-04-12
System is tribooting:popcorn::guitar:
When post screen appears just before ram check 20-30 sec hang (which is annoying) then does check and boots as expected to grub menu list.

As mentioned earlier my system has only one ide connector on board and am using a master slave ide cable to connect the two hdd's.   sda1(winxp) and sda2(win8cp) on a 120GB drive set on cable as master then sdb1(ubuntu) on 80GB on the slave.  Mobo has 4 sata connectors so plenty upgrading for future 

Looking at bios settings i do have the option to change which is the bootable hdd between two hard drives with out rearranging hardware/cable around and have made sure sdb1(Maxtor 80GB) was selected as a device in BIOS(boot device priority list)

i think on installation the installer has labeled the drive being installed to the first part of the label of installation media( bootrepair log ref to pendrive in blkid section) 
just left my first bios boot device as floppy then set sdb1(changed first hdd to 80gb(ubuntu))  as second bios boot device

fdisk -l gives
```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bfd87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   118029554    59013753+   7  HPFS/NTFS/exFAT
/dev/sda2       118029555   235930589    58950517+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe02ae02a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   138814516    69407227   83  Linux
/dev/sdb2       138815486   156301311     8742913    5  Extended
/dev/sdb5       138815488   152109055     6646784   83  Linux
/dev/sdb6       152111104   156301311     2095104   82  Linux swap / Solaris
```sdb1 only boot flag so my bios adjustment is applicable(?)

Thank you again for your time and direction oldfred 
I am probably enjoying all this tooo much:lolflag:

---

### Post by Geezanansa on 2012-04-12
> grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see  (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

think prompt was grub only ,  sure i tried ls > unrecognised command.  maybe grub2 prob?
after reading some of [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)   unsure if grub or grub rescue prompt
i do have older version linux kernels gong back to 9 or 8 versions ubuntu they show up in grub menu list as linux older versions.  Something conflicting with grub2?

i tried ```
kernel /boot/vmlinuz
``` but maybe ```
boot kernel /boot/vmlinuz
``` could have enabled me to reinstall grub then reboot and update-grub once booted into installed ubuntu.

---

### Post by oldfred on 2012-04-12
One quirk of booting, not sure if it is BIOS or grub, but the drive you boot from is always hd0. I think the BIOS reports the boot drive and then grub numbers the rest. When I plug a USB flash drive in and do not have search line in grub I have to often adjust the boot drive if chaining to another drive.

Many BIOS seem to promote IDE drives to first in boot order and SATA drives then become later. I have converted all to SATA primarily because I just had too many issues with the tiny jumpers on the drive and the wide PATA cables not staying fully plugged in whenever I opened computer case.

If you never use floppy, change boot order to the drive you boot as the first. You should also have a one time boot key and some BIOS have a quick memory test so it does not take so long for BIOS to boot.

---

### Post by Geezanansa on 2012-04-13
Thanks for input oldfred and breaking up mono log!

Does master slave cable "take over" or have higher influence in designating master and slave status than jumpers?(i.e. cable selects regardless jumper settings)
there are jumpers for cable select and can change in bios disk drive selection to anonomate which installed drive to be used as bootable device. (only one hdd  can be selected as a boot device. allthough have two hdd and at least four boot device options but can not designate both hdd in boot device list at same time)
 so this quite confusing for me because i want both drives to be bootable  (do i not?)
win xp and win8cp on sda
ubuntu on sdb

grub struggling with win8cp for some reason(different bootloader?)


win8cp kernel does not show up in grub only wndows recovery environment(loader) for win8cp

Starting machine up after reinstalling grub win8cp(using the grub menu entry for windows recovery)does boot up but this time only(replicating each time round)
After shut down from win8cp machine goes to some altered hibernation mode. press power button on system and win8cp will start up again so to get to grub menu do a restart from win8cp

At this stage xp will boot from grub as well as ubuntu
but win8cp crashes and system resets/restarts back to grub menu.

Moving the boot flag with gparted livecd to sda2 allows booting to win8cp which automatically repairs itself(takes about an hour) 


Then win8cp will start from grub again for one time only then tries recovery (when restarted/selected from grub list) and crashes thereafter until boot flag shift and completes recovery

Just trying to lay out what is happening.

feeling a bit dizzier than usual with all this runni:lolflag:ng round in circles

How do i get win8cp bootloader to work through grub?

---

### Post by Geezanansa on 2012-04-13
sorry
> Does master slave cable "take over" or have higher influence in  designating master and slave status than jumpers?(i.e. cable selects  regardless jumper settings)
there are jumpers for cable select and can change in bios disk drive  selection to anonomate which installed drive to be used as bootable  device. (only one hdd  can be selected as a boot device. allthough have  two hdd and at least four boot device options but can not designate both  hdd in boot device list at same time)
Thinking out loud and will try jumpers set  to cable select on both hdd as they are on same cable.
if i had two cables two hdds jumper master and slave respectively depending on mobo connector selection.

---

### Post by Geezanansa on 2012-04-13
> How do i get win8cp bootloader to work through grub?

Try setting win8cp as default in grub?  
currently on ubuntu as default (cos that what i want)

---

### Post by oldfred on 2012-04-13
Someone recently posted this.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)


But I would think a lot of Windows 8 testers would be dual booting with Windows 7 and it should have a setting somewhere to revert to a slower reboot, but not corrupt files.

The old IDE 40 conductor cable required you to jumper master & slave and only the master was bootable. New BIOS that support SATA have to have the capability to choose boot drive as SATA drives have no jumper. I gather that cable select then lets newer BIOS choose, but someone with an old Dell had one IDE & one SATA and could only boot from the IDE drive. So it still depends on BIOS.

---

### Post by Geezanansa on 2012-04-14
System is still booting xp and ubuntu; which is good.
 
Win8CP has been unable to recover either automatically or from installation media.
 
either tries to reboot after attempting recovery or gives something like ```
 your computer needs to restart.  Please hold down the power button.
error code:  0x00000050
parameters
0xFFFFFA8001A00000
0x00000000000000000
0xFFFFF80396E26C90
0x00000000000000002
```
 
booted into xp and tried formatting partition i had win8cp previously then restarted with win8cp dvd to go for custom install but gives something like ```
unable to locate partition. see log file
```
once selected partition i want win8cp to be.
 
 
been going  back and trying to assimilate the information you have been kind enough to share oldfred
 
still trying for triboot....

---

### Post by Geezanansa on 2012-04-14
>  
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)


 
> *"Windows 8 PCs will use the next-generation booting specification known as Unified Extensible Firmware Interface (UEFI). In fact, Windows 8 logo devices will be *[*required to use the secure boot portion of the new spec*]("http://www.networkworld.com/community/node/78727")*. Secure UEFI is intended to thwart rootkit infections by using PKI authentication before allowing executables or drivers to be loaded onto the device. Problem is, unless the device manufacturer gives a key to the device owner, it can also be *[*used to keep the PC's owner from wiping out the current OS*]("http://mjg59.dreamwidth.org/5552.html")* and installing another option, *[*such as Linux*]("http://lwn.net/Articles/447381/")*."*
 
yuccccggh
 
apology due to flurospar; "sorry"

---

### Post by oldfred on 2012-04-14
If reinstalling Windows 8, make sure partition is a primary NTFS partition with the boot flag. It will not see a partition without the boot flag and gets confused with all the Linux partitions if on same drive.

It seems like you need to turn off the fast boot/hibernate function in Win8. 

There still is a lot of discussion by the large Linux companies and how vendors will support dual booting.

---

### Post by Geezanansa on 2012-04-14
Now have xp and win8cp running side by side after uninstalling Ubuntu.
Have made sure the fast boot feature in the power settings in win8cp is set to OFF. Shutdown now shuts down system. So after pressing system power button system posts and boots to win8cp (no recovering from hibernation blue screen)
 
Time to hunt out me Ubuntu live usb&#8230; again:lolflag:
:popcorn:oldfred you are a :KS

---

### Post by Geezanansa on 2012-04-29
Just a quick update.
 
After spending some time learning about partitions and user rights/priveleges and all the rest of the relative bios settings and hardware configuration I do have a fast booting and as fast as it ever has run system.
 
Still only running xp and win 8 cp on same drive.  Spent some time applying what i been learning on ubuntu system on windows system. (not using user account with admin privs) Have been amazed at my new gt520 which has more than rejuvenated my machine and been enjoying gaming too much so am still tweaking my xp and win 8cp installations so not got round to going for triboot as yet.
 
As part of multi booting i would like to assign a partition to allocate for files, pictures, documents, emails etc that could be accessed from any of the operating systems.
 
Is it as simple as making a NTFS partition on hdd and drag and drop from whatever OS booted in?

---

### Post by oldfred on 2012-04-29
Yes & no.

Windows has a nasty habit of converting to dynamic partitions when you add more than the MBR(msdos) partition limit of 4 primary partitions. Dynamic is a one way conversion, is not compatible with Linux and seems to not even work with all the Windows tools. 

Windows reads from logicals and even a second install of Windows will work from a logical partition as long as you have the primary partition to boot from. So use Windows tools to shrink Windows primary partitions, but use third party Windows tools or gparted to create an extended partition and logical partitions.

---

### Post by Geezanansa on 2012-05-01
After installing ubuntu 11.10 and then upgrading to 12.04, windows 8 cp has broken(again)

awwwgghhhh:(

:lolflag:

So now have xp and ubuntu 12.04 booting from grub list:P

---

### Post by oldfred on 2012-05-01
I probably posted before that Windows only boots from the active partition or boot flag. It literally moves its boot files from a second install to the first install, so both can boot.

Then grub only finds one Windows install as all the boot files are in the one partition with the boot flag. Windows 7 used to take over the XP boot files in the XP partition and show booting of both. I would expect 8 to do the same.

To see where everything is at down this and run the Boot-Info & post link to report.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

### Post by Geezanansa on 2012-05-01
Will do.
 
 
 
 
 
Have been working on creating a xp asr floppy but do not have the free usable space to use the asr wizard in windows xp to make recovery disc with boot ini files etc.
> 
Did you at least review the pictures on the multibooters site. That helps to understand how Windows (and BIOS/MBR based) works.
 
Windows only know how to boot from one primary partition with the boot flag. The Windows MBR only knows to jump to the active partition (boot flag in Linux) and boot from there. So multiple installs of Windows literally combine the boot files into the active partition. Grub will boot each version of Windows but you have to split them (and maybe repair them when split).
 
Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 
 
Backup all the boot files. Move the XP boot files to the XP partition and repair the PBR or partition boot sector. Boot.ini in XP already says rdisk(1) so it knows it is in sdb. You may also have to edit BCD with bcdEdit in Windows7 to remove the XP entries.
 
You mentioned IDE type cables for hard drives. Does you BIOS let you choose which drive to boot? Most older IDE systems set boot with jumpers on drive (or location on cable), new SATA drives do not have jumpers and use BIOS to choose boot drive.

 
and
> 
Does Windows 8 let you make a repairCD or USB? I only have XP. 
 
I downloaded the Windows 7 repair ISO and made a USB flash drive. I found chkdsk worked better from the Windows 7 repair than from XP but had to use the Windows 7 bootsect.exe to restore an XP boot sector as the chkdsk converted it to Windows 7.
 
Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/w...em-repair-disc]("http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc")
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
 
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-re...tion-dvd-disc/]("http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/")
[http://www.webupd8.org/2010/10/creat...usb-drive.html]("http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html")
 
I only know a few basic commands for Windows repairs and have to search Windows forums for anything major.

 
 
Would love to be able to back up straight to large external hdd but do not have resources at moment. Simple as. Which means using xp asr wizard i do not have appropriate space to back up sysytem with all the apps and games etc on back up file.
 
Really do not want to go through the clean install option again so have to make backing up a higher priority.
Did not have floppy working and only got a usable floppy on third device/attempt so it's been one of those days ... again. (Have moved items for recycling so bad hardware lying about cannot be confused for good again.)
 
Since updating to ubuntu 12.04 and rebooting can see windows 8 (loader) rather than windows recovery environment(loader) as on previous attempts however still only getting to windows attempting recovery and failing.
Choosing windows xp or ubuntu from grub list boots at will.
Will look at making recovery cd for xp to back up boot files before trying to fix grub/windows 8.

---

### Post by Geezanansa on 2012-05-01
Here is bootinfo script link [ http://paste.ubuntu.com/961207]("http://paste.ubuntu.com/961207")

---

### Post by qaissi on 2012-05-01
In my case I am actually doing a multi boot with Ubuntu 12.04, XP, Vista, 7 Ultimate, and 8.  Not that I am bragging.  But I have had lots of fun over the years trying to figure out how to get things to work properly.

Again my situation is a little different from your because I have more hard drives and some are Sata while one is still IDE.

From my experience what I would do is this.

Remove the slave drive.

Install XP on the first drive (master) in a primary partition the size of your choosing.

Then install Ubuntu (whichever version you want) on the same drive.

Once Ubuntu is set up you should have a dual boot for XP and Ubuntu.

Remove that hard drive from the machine - change the slave drive to a master drive - put it in the machine and install windows 8.

Once that is done remove it, set it back to a slave, put the original master with XP and Ubuntu in and make sure you still reboot to XP and/or Ubuntu.

Then power off the machine

Attach the slave drive and reboot.  You should still get the XP and Ubuntu options.  Go into Ubuntu and do a sudo update-grub.  It should then find the Windows 8.

Reboot and check it out.

I have used this process repeatedly with great success.

---

### Post by oldfred on 2012-05-01
Some good suggestions from qaissi. But you have XP & 8 on one drive and Ubuntu on the other drive. You are booting with grub in the MBR of sda for the Ubuntu install in sdb1.

Does you system let you choose which drive to boot from? You have no boot loader in sdb. Even if you cannot directly boot from sdb, it may be worthwhile to install grub to sdb also incase you use the sdb without the sda drive.

From Ubuntu 
sudo grub-install /dev/sdb

Can you boot both Windows? It looks like grub has added boot stanzas for both.

The repairCD is just oneCD for Windows that has the capability to run chkdsk or make other repairs. If Windows is damaged, it is about the only way to fix it other than restoring from full backup or reinstalling.

---

### Post by Geezanansa on 2012-05-02
Thank you for advice qaissi.
At this stage will try to learn more about configuring grub.  But if win8cp needs reinstalling as well as ubuntu will follow your advice qaissi.  It good to know it is possible and easy to do.
 
after mounting xp drive in ubuntu session noticed i could view all system files including boot ini/ntldr and ntdetect.com
If i burn these to a bootable cd could i use this to make repair cd?
I guess what i am asking is it possible to make windows recovery disc by using windows installation media and mounted xp device in a ubuntu desktop session?
 
Depending on the state of system and installed apps etc i can now see the value of using windows backup features.  creating an asr disc makes a back up of all selected folders(complete shadow/clone if desired) and a floppy start up disc.
 
Which recovers state of system  to when last backup was made.
 
A lot better than relying on installation media alone(clean install)
 
I have not been giving backing up enough time and effort but more than intend changing my ways.....
 
 
oldfred asked,
> Can you boot both Windows? It looks like grub has added boot stanzas for both.


 
>  
Since updating to ubuntu 12.04 and rebooting can see windows 8 (loader) rather than windows recovery environment(loader) as on previous attempts however still only getting to windows 8 attempting recovery and failing.
 

Choosing windows xp or ubuntu from grub list boots at will.


 
XP, Win8CP and ubuntu kernels all show in grub list at boot.
 
Ubuntu 11.10 was installed from an alternate cd then 11.10 updated and upgraded then updated again so now running 12.04lts
 
When installing bootloader from alternate cd install the installer advised me that installing the bootloader to sda would be good so let it do its thing.
 
It looks like win8cp not fixable.  Spending time to back up xp but simply do not have resources/hardware.
 
Will keep plodding away at this.

---

### Post by Geezanansa on 2012-05-02
So the point of recovery cd, asr disk or installation media alllow user to access recovery console.
Different options will be available at recovery console using different means of access to recovery console so depending on state of system different discs do have different applications. Just the terminology so similar it hard for me to give accurate description or get understanding what is what.
Allso the different ways of doing same thing from different os overwhelming 
Do understand backing up an important part of pc maintenance and time for me to start trying. Just my first xp machine had a 4gb and a 6gb hdds. little room for backing up(or even using)that was just a couple of years ago so have progressed up the evolution chain slightly since then.  Just do not have hardware/resources.


I am sure the ubuntu installer led me to believe for grub to be certain to work for windows os grub would be better installed on drive with both windows os .  (sda)
Somehow grub is booting ubuntu no probs as well as xp.  I am sure windows 8 is broken at ubuntu install and automatic repair unsuccessful so looks like reinstall.

But first i would like to try and confirm wether it grub/bootloader prob or something else.

Will install grub to sdb as oldfred advises.

If grub was removed from sda  then sda drive removed from system then could boot from sdb to confirm working ubuntu but before doing so thought i would ask "how do i remove grub from sda?"

Think this might help to be able fix win8cp(after removing sdb and reconnecting sda (without grub))

---

### Post by oldfred on 2012-05-02
You do not normally remove a boot loader from a MBR. But just load a new one. There is a way to zero it out, but not any real reason to.

Your XP disk is a full install disk and works as a repair CD for XP. But it will not work for Windows 7 or 8. Windows 7 has a way to create a repairCD or USB from the repair console.

Window boot loader in the MBR, just checks for the primary partition with the boot flag (active partition in Windows terms) and jumps to more Windows boot code in the PBR - partition boot sector. Windows XP and Windows Vista/7 & 8?  have a different boot sector. If you put a Windows boot loader into the MBR of sda, it will only boot whichever Windows has the boot flag. You can use gparted to move boot flag. At a Windows terminal yo move boot flag with make active, but you have to have set diskpart, I do not remember exact commands.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I believe if boot flag is on Windows 8 partition, you can restore the XP boot loader to the MBR and it would boot Windows 8. But it may have some newer features which I do not yet know about. We use many different Windows work alike boot loaders as they all just jump to the partition with the boot flag. 

Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

### Post by Geezanansa on 2012-05-02
Would like to confirm that windows8cp installation media has been used in trying to recover windows 8 cp.
I do not know the commands in order to fix win8cp from command prompt in recovery advanced options.  Automatic repair fails.

Tried disconnecting sdb and rejumpering and rebooting sda but no joy.(as well as just disconnecting sdb)
Have managed to reconfigure and reboot to xp and ubuntu once again but win8 broken.

Other attempts at fixing win8 (in previous attempts at triboot) breaks ubuntu and xp

Possibly what has happened when i installed ubuntu the boot flag was never removed from win 8 after its install(xp>win8>ubuntu) so maybe conflict between ubuntu/grub and win8 system protection thing(which recovery options is a part of)
Win 8 partition still has boot flag(viewing with gparted in ubuntu desktop session)
As an observation that could be relative never have had windows bootloader choice screen due to fast boot option being active(ref xp Boot ini)
I had been using the disk management method(marking boot flag)  to switch from one windows to other windows on reboot.
Only after installing ubuntu do i get choice of kernels at boot time(which is what this is all about)

Will spend more time googling diskpart,  checking out links etc and thanks again for the input oldfred

---

### Post by Geezanansa on 2012-05-02
I can not boot to or repair win8cp by any obvious means.

How do i go about fixing this without having to start again with reinstalling xp after it breaking due to wiping ubuntu/win8cp?

Still have xp and precise booting from grub list at boot time.

---

### Post by qaissi on 2012-05-02
I am sorry but this topic seems to be getting more complicated then it should be - maybe just me.

If you have XP and Ubuntu on one IDE drive and Windows 8 on the slave drive just remove the master drive with XP and Ubuntu on it.

Change the slave drive to a master -Windows 8, and try to boot off of it.  If it can not boot then use the Windows 8 DVD to repair it and get it booting.

Once that is working remove it and set it back to a slave - put the original master in and boot into Ubuntu

Once there, in a terminal run sudo update-grub and it should find everything and you are on your way.

---

### Post by Geezanansa on 2012-05-02
well sda1 =xp sda2=win8cp and sdb1=ubuntu
do get the gist of what you are saying so 
remove sdb1 and recover win8cp (on sda2) then reconnect sdb1 then update grub from within ubuntu and all good,  easy peasy

My mobo only has one ide connector therefor am using a cable to connect two hdds to one mobo connector so am using cable select jumper settings(as previous pages of this thread mention)i.e. positioning of hdds to master/slave cable connector designates master and slave
moving the boot flag is not complcated but very helpful in achieving side by side installations so that seperate kernels show up in grub once ubuntu installed
for whatever reason installing ubuntu breaks windows 8

so when i disconnect sdb and try to boot no such device found error given. This happens after posting at bootloader/grub screen time
If then windows installation disc(win8cp) is booted to recovery options automatic fix fails as there is a problem starting windows recovery and it shuts itself down back to options screen.

I have in previous attempts simply reformatted and uninstalled the win8cp and ubuntu but this breaks
win xp and end up having to do clean install from xp then win8 then ubuntu(not a five minute job)

oldfred has highlighted some older mobo/bios only allow one hdd on ide to be boot device but as i have the choice to boot from either hdd from one time boot list(F8) even when both on same cable.  this is  I think is not a  problem
i do have an ide to sata bridge i could try to eliminate this as possible trouble.(mobo has three spare sata as odd using first)

i think windows8 is unrecoverable due something more than bootloader but cannot access any recovery options successfully.

So how to repair win8cp installation after installing ubuntu?

---

### Post by qaissi on 2012-05-02
Have you tried using Boot-Repair CD

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Download and burn to CD

Boot off the CD and just run the default option

---

### Post by Geezanansa on 2012-05-02
Have run recommended repair from boot repair
Boot repair reminded me to make sure sdb in bios is first boot device

As oldfred has suspected and more than hinted at my system can not do this through bios/ide limitations
So now have removed ubuntu drive to try and recover both windows

---

### Post by Geezanansa on 2012-05-03
There is light at end of tunnel.  Thank you qaissi.
After removing ubuntu drive then
using bootrec /rebuildbcd > recovered both windows=easy peasy
using easybcd> made sure windows 8 boot loader manages xp bootloader i.e.get bootmanager screen with choice of windows at boot

THis next bit is where i have been going wrong

Just jumper hard drive with ubuntu on as master and make sure windows drive slave.  Reboot.

Make sure all os booting.

copy grub.cfg to desktop(for reference)

sudo update-grub

Simple as



:popcorn:qaissi

---

### Post by Geezanansa on 2012-05-03
Win8 not booting
XP good ubuntu good
Used boot repair again rebooted bit still win8 can not boot even after disconnecting ubuntu drive to fix windows

Could not fix windows(grub prompt)
Reconnected ubuntu drive and can boot xp and ubunti


I really can not work out how to get grub to boot windows8

This what I now aim to do to get triboot:

Boot to xp from grub
Format win8 partition
Mark xp partition active
Shutdown and disconnect ubuntu drive
Boot to xp
Install ubuntu to same drive as xp
Install win8 to second drive

---

### Post by oldfred on 2012-05-03
I know XP's boot.ini has a direct reference to which drive it is. Grub will try to use map or map device to make it still think it is that drive, but in your case as you can only boot from one, the mapping may not help. 
I think Win7 used something like grub/Ubuntu's UUIDs so changing drives does not matter so much. I would then think Win8 would be the same way.
Because you can only boot from one drive, it makes it a bit more difficult.

---

### Post by Geezanansa on 2012-05-04
Time to recap once again as have been busy!
 
xp broken again so have had to start from clean install of xp
 
now have xp and ubuntu on one drive with windows 8 on the other drive
 
 
Installing xp and then ubuntu on one hdd and after checking grub booting xp removed drive from system.
 
Windows 8 was then installed to second drive after making sure it is the only hdd on system and jumpered master.
 
 
After updating and sfc/ scannow all clear in windows 8 the system was shut down making sure fast boot is switched off.
 
Shutdown and restarted to confirm hibernation/fast boot is not active.
 
After shutting down again set jumpers for windows 8 drive as slave and connected ubuntu drive as master
 
On reboot only ubuntu could boot so copied the then current grub.cfg then updated grub and rebooted once again.
When XP was chosen from grub it tried to do chkdsk and crashed/froze after completing first test. Had to reset system to reboot. This was replicated at each attempt at loading xp from grub.(was hoping for chkdsk to complete!)
 
When windows 8 was chosen from grub list it simply crashed and rebooted.
 
Running boot-repair did not fix anything with regards to booting up xp and windows 8. I did note url for bootinfoscript for before and after repair for reference (just need to go get them!)
 
After disconnecting windows8 drive and rebooting i can boot both xp and ubuntu(without updating grub)
 
I should be able to edit grub.cfg to get xp bootable after putting second drive in system(using info from backed up older grub.cfg file mentioned earlier)
 
Still can not work out if windows8 is breaking because of moving jumpers after install or how to get grub to be more domineering or maybe windows 8 and grub just do not like each other
 
 
Would installing grub to windows8 drive be a good idea?
 
 
System bios version is most current from mobo manufacturer.

---

### Post by oldfred on 2012-05-04
No, I do not install grub to the Windows 8 drive.

You should be able to repair XP, if all the boot files are there. XP has boot.ini that refers to the drive & partition it is in. Grub tries to map device if XP is not in same drive but with grub in the same drive that should not be required.

Not sure what other differences Windows 8 has. It may have to see itself as sda also? If that is the case then maybe since you can only boot sda, we will have to install grub there. 

I think part of the issue is your system is older and Windows 8 is so new it may not have the flexibility to multi-boot.

---

### Post by Geezanansa on 2012-05-04
from most recent post i made
> After disconnecting windows8 drive and rebooting i can boot both xp and ubuntu(without updating grub)
understand that installing ubuntu to xp drive gives grub control of boot loaders for xp and ubuntu.

So disconnecting the ubuntu drive before installing windows 8 on the second drive prevents windows detecting xp and taking over control of bootloader for xp.  (or that is intention of doing so)

After connecting second drive (win8 as slave and ubuntu drive as master rebooted to ubuntu and updated grub.
The outcome was only ubuntu could boot from the grub list at boot(all three os were listed)



can i stop windows 8 from seeing xp?
Is windows 8 seeing xp breaking grub?

**Do not understand how grub is expected to boot a non operating/booting windows because if jumpers have moved so does bios ref so grub cfg no worky(as well as windows own ref not matching with bios so will not boot any way)**

How to fix windows path names/drive assignment?

So how to update/fix windows installation(from sda to sdb) without allowing installer to" Take over" xp boot loader control?




Surely have repeated the cycle enough times to conclude something is a miss.  Regardless of configuration/install method the outcome is the same in that i cannot boot from more than two grub listings.

Any help in diagnosing would really be appreciated.

All i am trying to achieve is xp, windows 8 and ubuntu all on one system with the option of what to boot to at boot time. 

Thanks in advance.

---

### Post by oldfred on 2012-05-04
If you install Windows 8 without the XP drive it should not see the XP drive. But if you connect both drives then 8 will move its boot files to the XP partition.

I have lost track, did I post this before? Explaination of Vista should be like Windows 8, but we do not know some of the changes.
To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Post new run of boot info script or link from Boot-Repair.

---

### Post by qaissi on 2012-05-09
Just to update the status on this thread:

Ultimately his issue was that he had a Seagate hard drive and a Maxtor hard drive that were not playing together nicely.

So long as the Seagate (which of course happens to be the smallest drive) is the master and the Maxtor is the slave it is a simple setup.

When the Maxtor was the master it would not allow his computer to boot anything off of the Seagate.

This has been resolved.

---

### Post by Geezanansa on 2012-05-09
Thank you qaissi the troubles with multi booting for me are hopefully history.

qaissi may i commend you for your patience as well as thank you for all the time and effort you gave to teach me what i need to know in order to understand exactly what is going on at boot time.
As well as determining that the hard drives simply do not work with each other in that particular configuration.


For reference the mobo involved here is an asrock alivenf6gvsta.  It has one 40 pin ide and one floppy ide connectors. Four sata.

Now the bios version that was showing at boot from the beginning of attempting tribooting was the most current from mobo manufacturers. Or so i was led to believe.

The sytem case that this mobo is an asetek vapochill xe which is basically a pc tower case with a 12v dc refrigeration unit plumbed so that you can deep freeze your cpu so that it runs more quickly(that is theary) There is a seperate control unit for this fridge so it can control when to power down system and what temp to drop to before starting up system as well as therm sensors and heater pads to stop condensation(not good for cpu lol)  When the system was running with refrigeration unit the cpu  temp was given as -38 deg C
Basically this control unit had to be flashed with a bios file from  asetek.  But all this is not connected.  Just a standard fan and heatsink cooling cpu right now.
The point i  am making here is that the bios file from asrock is different from the  version that was in machine which was the asetek one.  
Both say 2.2 at boot but if i enter bios settings with the  asrock file  there are a few obvious changes like extra options and a more modern look.

As an observation and as this is an older mobo the drivers from asrock are outdated.
On a new install of xp let windows update do the updates first which left with only smbus and hd audio drivers to fetch from asrock.  
Choose only the smbus driver from the nvidia all in one driver package.  But all this is after getting tribooting(updates and drivers etc)


So here is the method of how i got tribooting  

Make sure bios is correct version and most recent.
Connected maxtor 120GB to system as master
Install XP
Make sure xp boots without disk.
Shutdown.
Disconnect Maxtor and connect Seagate to system as master.
Install windows 8
Update windows 8
Shutdown
Install ubuntu alongside windows 8
Update ubuntu
Update grub (sudo update-grub)
Make a copy of grub.cfg(/boot/grub/grub.cfg) and save to somewhere you can find it.
Shut down.
Jumper maxtor as slave and connect as slave to system.
Boot to ubuntu.
If that all ok boot windows 8.
If all ok reboot to ubuntu and update grub.
Now reboot and load xp.


Now a tribooter.

Get on with building xp and get gaming.

It really is as simple as that.  
The hardware i am using simply is not keen on working in the configuration i had.

Thanks folks for input.  This has been more than a challenge for me and really do appreciate all the help.

---

### Post by oldfred on 2012-05-09
Are both your drives IDE/PATA? Motherboards with SATA drives use BIOS to choose boot drive since SATA has no jumpers.

You may need to use the 80 conductor cable and jumper IDE drives to cable select, but then you should be able to choose boot from BIOS.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by Geezanansa on 2012-05-10
I would like to confirm that the mobo has two ide connectors only. One ide 40 pin connector to attatch hdds.  One smaller connector for floppy.  
So on this system there is two hdds; which are attatched to the mobo 40 pin ide connector with a master/slave cable currently the 80gb seagate as master and 120GB maxtor as slave.
There is a floppy drive connected to the other ide connector on mobo.

Yes oldfred both the hdds are pata/ata/ide whatever you want to use.  The cable i am using to connect the hdds has black connectors and it is twisted, shrink wrapped with big rubber boots to go over connectors.  Each connector on this cable is labelled but not color coded.
So we can conclude that because the connectors on this cable in this system is not colour coded that it is the older type cable.
The master hdd is jumpered master and connected to master connector on cable.  (Seagate 80GB-Windows8CP and Ubuntu)
The slave is jumpered as slave and connected to the slave connector on cable.  (Maxtor 120GB-XP)
Earlier in this thread i may have mentioned trying to use the cable select jumpers as well as an ide to sata bridge to connect ata hdd to sata connector so maybe this is why you advise but the most recent post is the current status.

Just confirming everything is as is you advise.



So now a 24 hour period has passed with no problems tribooting and as well as being educated in what is happening at boot.

I am confident i have achieved what i set out to do.

At boot i have choice of which os to boot to from grub listing.  Each os is booting at will.


Thank you.

---

### Post by oldfred on 2012-05-10
I think if you upgraded to the 80 conductor & changed jumpers to cable select, you then could choose boot drive in BIOS, but that is up to you. 

If it is working it may be best not to change.

---

### Post by Geezanansa on 2012-05-11
My mobo does have a blue connector.
So to get full potential from  hardware will try an 80 conductor cable.  Pretty sure if moving jumpers  ok then so should changing cable.  My line of thought is that i should  upgrade to 80 conductor as i now understand that what the mobo made  for.  There is a history of people having trouble with cable select  settings though.  I will do this after looking at slipstreaming xp  updates and backing up/cloning with clonezilla. 
Just been using what  i have at hand.  The best form of recycling is to reuse but folks throw  out or stop using things for a reason and i have more time than money.   Upgrading my graphics card from a GeForce 6800ultra to a GT520 has  triggered all this off and has unleashed the power of hd albeit on a  small lcd monitor right now.  But realising this upgrade has given me  the equivalent of any gaming platform/ blue ray video/ HD audio and 3d  potential and looking at the new F! game - gaming has come a long way in  recent years.  Light years since 97F1 on playsation 1 last time i  played anything like that.  

Another thing i had been doing  without understanding was installing all the raid drivers from mobo  manufacturers in previous attempts after installing xp.  These drivers  are part of an all in one driver for the nvidia chipset which includes a  seperate smbus driver which i now realise is the only one i need to  install from the all in one driver package.  As stated in my post  yesterday when updating how i have achieved tribootability i had to  flash bios after identifying different versions(asetek and asrock)
Been  taking my time to enjoy what i have managed to achieve here the last  couple of days and have not looked at boot devices in bios settings yet  since flashing to the asrock version bios all though i can confirm the  bios definitely looks and feels different when in the settings compared  to what it was.

But will report back later after checking what my  new bios is saying in bios settings regarding boot devices(i.e. one or  two hdds in boot priority list and boot devices list)

Definitely  been an accumulation of far to many things not right on this build.  Now  benefiting from getting on top of them all.  Ignorance used to be  bliss.
Plug n play has obviously been very kind to me in the passed.

:popcorn:

Apparently 5% of pc shipped this year will have ubuntu 12.04 on.  Now that is interesting.:wink:

---

### Post by Geezanansa on 2012-05-11
After rebooting each os again(still can not believe it working) i entered bios settings and then then boot settings.
I can only select one hdd as boot device.

So if i upgrade to 80 conductor i should have the choice of two hdds in boot settings to choose from regardless of  the position of hdds on cable which makes cable select different from master/slave settings?

Which is different from choosing which drive to boot from in the one time boot list at boot regardless of config.

Thank you.:popcorn:

---

### Post by oldfred on 2012-05-11
To me the advantage is you can then keep Windows on one drive and directly boot if need be and have grub/Ubuntu on the other and directly boot it. Windows always prefers to be sda or first so I still have my old XP as sda.

I built my system 6 years ago and converted immediately to SATA. The touted advantage was smaller cables for better cooling, but for me it was no more little jumpers that I could not see well or handle. I also seemed to partially disconnect cable enough that it looked connected when I closed computer but did not work. A firm push and then it would work.

I go back to before labels and Internet and if you lost the little piece of paper with pin layout, you had no idea how to change jumpers if you wanted to add a drive. I think SATA was about $10 more per drive when I converted and now I understand it is hard to get PATA drives.

---

### Post by Geezanansa on 2012-05-12
After having a rumble about in my oem spare parts centre(recycling bin)lol i have found an ide cable with blue,grey and black connectors on.
The print on cable is e101344-d awm 20647 LL80671 csa awm I a105??150v ft-1
googling this cable info all most certainly id this as 30 or 40 conductor.
I am sure this cable was giving me problems when trying to add second drive at the beginning of all the multi boot efforts.(it has vaseline on blue connector when it was running only one hdd in system when it was using the vapochill single phase cpu freezer, in an effort to prevent condensation building up in any air gaps especially at mobo connectors.)
So again the particular hardware being used which has worked for me in the passed on either this or other systems and my ignorance has held me back.  
Really do and have enjoyed learning how my pc works and then making it work is even more satisfying.  Just need to learn how to use the thing now. lol  Threefold  rflol

I am splashing out on a brand new 80 conductor cable..  :popcorn: because i like the idea of bios pointing bios as well as grub pointing bios if booting that drive with grub on. So all this would give single or multiboot options without having to take the tower case side covers off. As well as handy plan b.

Still enjoying a tribooting system:guitar:

---

### Post by Geezanansa on 2012-09-20
Some months have passed and have not been trouble free.  The configuration that is now current is windows 8 on sda and ubuntu sdb with easybcd managing boot options which means that windows boots to give me option of ubuntu boot. Which is not what was originally intended.  But it seems to be the more stable option.
Kept on having bios problems(problems in that settings appeared to be changing without my input).  This led to fatal/unrecoverable errors. So after using seatools to test both hdds both hdds were then formatted using seatools.  Becoming more familiar with the many windows power saving and sleep/hibernation settings in windows 8 led to understanding the need to enable sleep to ram in bios settings. Updating to newer build of windows 8 has also eliminated many problems.

So parts have escaped rubbish bin one last time:lolflag:

---

### Post by oldfred on 2012-09-20
Some of your issues with Windows 8 may be related to its default hibernation mode. That makes for fast boot, but even dual booting two versions of Windows can cause issues.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by Geezanansa on 2012-09-20
After rereading this thread thought i would spend time trying to clarify a few things.

Reading this thread it is not clear wether or not my bios and hardware could boot from either of both the hard drives when both connected.  Thank you oldfred for your patience and multiple explanations that this system should do exactly that.

So i powered down and rejumpered  both hdds to cable select and can boot any of the two from the one time boot list (F11)at boot.


Current config is sda=windows 120gb and sdb=ubuntu 80gb.
Both hard drives jumpered to cable select.

Have removed easybcd from windows drive so this bios method(F11) is what is getting used to get to other os at moment.  After rebooting to windows the blue windows boot option showed. So used bcdedit to remove ubuntu choice entry and now have a super quick booting windows.  

Just gonna do some more reading before configuring or updating grub. lol:lolflag:
Thanks for warning again oldfred about hibernation/corruption will look into it more.

The current windowsrp build seems to be a lot more reliable and stable certainly a lot more so compared to cp build.  Setting bios to allow suspend to ram and managing power settings in windows by  running performance test/rating thing.  Turning off the harddrive sleep/power off option.  Make sure windows is activated.  There are other things to do but this is wrong place to be going on about such like!

---

### Post by Geezanansa on 2012-09-20
So now ...:lolflag:  after updating grub and rebooting; system hung at post screen so choose F11 to reboot Ubuntu. After this rebooted again going into bios settings to change boot device to sdb Seagate80GB as first device in order to get grub screen at boot.
Two hard drives were available as boot devices when Maxtor120GB(sda) set as first device in the boot device list in bios boot settings/hard drive menu. Only the Seagate80GB(sdb) hard drive is available as a boot device in boot device list in bios boot settings/hard drive menu when it is selected as the first device in hard drive menu.
 
So I need to install grub to sda!?
 
The option to boot either os from one time boot list (F11)is still good.  
 
So is this 
>  
```
#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda2 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda2 if not correct:
sudo fdisk -l
#confirm that linux is sda2
sudo mount /dev/sda2 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub
```

all that is required to get grub screen at boot!?  That is after changing bios back to Maxtor120GB(sda) as first boot device:lolflag:

---

### Post by oldfred on 2012-09-20
I find it strange that sometimes you see two drives and sometimes one?

While grub does not use boot flag & Windows has to have a boot flag, some BIOS require a boot flag on a primary partition (They assume Windows?). 
Do you have a boot flag on a Ubuntu drive primary partition, does not matter which one, but must be primary as it just is for BIOS not grub.

---

### Post by Geezanansa on 2012-09-21
Did not install grub to sda to maxtor120GB.

> I find it strange that sometimes you see two drives and sometimes one?

When configured to cable select the maxtor 120GB hdd is set on cable black connector which =sda
Changing seagate 80GB to first boot device in bios settings and rebooting still gives Maxtor120GB as master boot device and seagate80GB as slave at post screen but seagate80GB boots not maxtor120GB.
Because i told bios to do that.
seagate is dma5  maxtor is dma 6 !?
Previous posts show that when seagate is master changing bios settings to maxtor as first device will  give maxtor as only boot device.
so when the drive that is NOT sda is set to first device it is the only device available because there can not be two sda'!?
It is strange but not random.  Bios querk.  You have mentioned upgrading to sata drive and using sata as master or slave. Look forward to that!
Bios unable to change sd allocation but bios is moving the boot flag!? i.e. changing boot device priority does not change sd allocation.

The configuration of maxtor120G(windows) and seagate80GB(ubuntu) with easybcd (grub2 and kludge) acting as boot manager for windows/ubuntu worked flawlessly.

Okay what we got is two os on two hard drives.  Both are bootable from F11 one time boot list.  In order for grub screen to show  - make ubuntu drive first boot device.  Which boots and does give grub screen then selecting ubuntu does boot but selecting windows does not boot from grub list.

[http://www.multibooters.co.uk/multiboot.html]("http://http://www.multibooters.co.uk/multiboot.html")  It would be good to see a diagram like those with grub in the picture:lolflag:



```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000299a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   240117759   119699456    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b9903

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   152109055    76053504   83  Linux
/dev/sdb2       152111102   156301311     2095105    5  Extended
/dev/sdb5       152111104   156301311     2095104   82  Linux swap / Solaris
```





Will change bios back to give maxtor120gb sda as first boot device and Maxtor80GB as second device in order to get two bootable devices in bios


Will run a boot info script.

So if grububuntu on segate80GB sdb, How to get grub loading at boot? How to get grub to point bios to sda?   
> Do you have a boot flag on a Ubuntu drive primary partition, does not  matter which one, but must be primary as it just is for BIOS not grub. 	
[ATTACH]224466[/ATTACH]
Will get it sorted.

---

### Post by oldfred on 2012-09-21
Windows XP has hard coded drive number in boot.ini, so changing boot order can make XP not work. Ubuntu often adds a map device command to make Windows think it still is the drive(0) when the computer is booted from the second drive. There is something that BIOS records on drive that system use to know drives when booting and that has to map to boot info.

---

### Post by Geezanansa on 2012-09-21
From first page
> Windows only know how to boot from one primary partition with the boot  flag. The Windows MBR only knows to jump to the active partition (boot  flag in Linux) and boot from thereFrom last post
>                               Do you have a boot flag on a Ubuntu drive primary partition, does  not  matter which one, but must be primary as it just is for BIOS not  grub.                      So have to create/make primary partitition and 
>  then a reinstall of grub2's boot loader to the MBR and a sudo update-grub should have you booting everythingso something like
```
#Comments are anything after the #, enter commands in terminal session #Install MBR from LiveCD/usb, Ubuntu install on sdbX and want grub2's bootloader in drive sdb's MBR:
#Find linux partition, change sdbX to correct:
sudo fdisk -l #confirm that linux is  primary with boot flag and sdbX 
sudo mount /dev/sdbX /mnt #If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sdb  # If no errors on previous commands reboot into working system and run this:
 sudo update-grub
```or use boot repair cd (would be easy option but wanted to work out what is going on)

or keep using F11 to boot to windows as ubuntu boots just fine now after a few reboots i.e.no hanging at post.:lolflag:  It is just not logical;)
BootInfoScript: [ATTACH]224474[/ATTACH]

---

### Post by Geezanansa on 2012-09-21
Did use boot repair cd to make backup of mbr this time round lol before doing a bootinfo script.

---

### Post by Geezanansa on 2012-09-24
From first page
Quote:
Windows only know how to boot from one primary partition with the boot flag. The Windows MBR only knows to jump to the active partition (boot flag in Linux) and boot from there



From last post
Quote:
Do you have a boot flag on a Ubuntu drive primary partition?, does not matter which one, but must be primary as it just is for BIOS not grub. 

bootinfoscript says
Quote:
=================== parted -l:

Model: ATA Maxtor 6Y120L0 (scsi)
Disk /dev/sda: 123GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  368MB  367MB  primary  ntfs         boot
2      368MB   123GB  123GB  primary  ntfs


Model: ATA ST380011A (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  77.9GB  77.9GB  primary   ext4            boot
2      77.9GB  80.0GB  2145MB  extended
5      77.9GB  80.0GB  2145MB  logical   linux-swap(v1)

.. so to answer the question - yes!



BIOS is set to boot sdb with jumpers set to both hdds as cable select. BIOS says sdb only bootable device when that device selected as first bootable hdd through bios settings.  POST screen confirms BIOS detecting Maxtor120GB(Windows 8 ) as master/hd0.   i.e. Seagate80GB(Ubuntu)sdb is not master all though selected as first boot device in bios boot/boot settings/1st boot device.!?

Here is what i think happens when ubuntu boots and layout of hardware config:

[ATTACH]224596[/ATTACH]

Here is what does happen:
Grub loads and Ubuntu boots when selected from grub list. When Windows 8 is selected from grub list it does not boot but tries to start recovery/automatic repair then system reboots.
boot info script says
Quote:
=================== os-prober:
/dev/sda1:Windows Recovery Environment (loader):Windows:chain
/dev/sdb1:Ubuntu 12.04.1 LTS (12.04):Ubuntu:linux

and blkid section ends with
Quote:
2 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.


Windows not detected by os-prober on sda2.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

So bootinfoscript very handy. Seems a lot more readable than it was six months ago...


If F11 selected at post time on rebooting then Maxtor120GB is selected from list- Windows 8 boots as expected.

Quote:
Ubuntu often adds a map device command to make Windows think it still is the drive(0) when the computer is booted from the second drive. There is something that BIOS records on drive that system use to know drives when booting and that has to map to boot info.

uuid?

So it would be possible to press "c" at grub list and enter a command to tell bios to boot hd0!?

But BIOS is boss - it tells grub what to do.

So grub has to have a link with of all mbrs and pbrs in order to boot all available os. This has to be so before trying to launch kernel from grub list option.
These links can get mixed up after switching/changing first boot device in bios.  

grub-install should take care of it 


Have found info grub!

Not marked this unsolved as am sure more than enough info/links and advice given in thread already. Working it out.

---

### Post by oldfred on 2012-09-24
Was Windows 8 still in its (automatic) hibernate mode? 

I think I have seen several cases where the only solution with some of the older IDE/PATA drive systems was to install grub into the first (Windows) drive so BIOS reporting was the Windows drive. I prefer to have each drive be totally stand alone, but some system just do not allow it.

---

### Post by Geezanansa on 2012-09-24
> Was Windows 8 still in its (automatic) hibernate mode? 

Yes  and still is.  I think it is a good thing. Want a side by side  installation without any encryption and no file sharing.   Windows 8  reliable. Had been using easy bcd for multiboot with success.  Doing  this only added ubuntu to boot list for choosing after loading windows  bootmanager.  A full reboot to post was needed to boot ubuntu when that  option was selected which meant waiting twice as long compared with how  long to wait if grub was bootmanager and bootloader for ubuntu to boot  as default.
Which has led to the interest in multibooting again in  order to try and achieve side by side os installations with the option  to boot both installed os at grub option list at boot time.

Have  been using old boot-repair cd to give boot info script and noticed boot  repair is soon to be available through ubuntu software centre.(without  adding ppa) so that is good.  So will make a new cd with the most  current iso.  Probably just means boot repair does not have to download  as many files for updating when starting.

To boot windows i have been using f11 one time boot selection.
Both os are bootable from f11 one time boot list. 
Just  need to manage how they load by working out why they will not both boot  wether be it bios or grub set up limiting the outcome. 
Possibly windows 8 limiting outcome as well.

Time to try putting grub into sda....

---

### Post by Geezanansa on 2012-09-24
So down to ubuntu booting only.  Time to try windows rebuild bcd....

Pre repair boot info [ATTACH]224617[/ATTACH]
Post repair boot info [ATTACH]224618[/ATTACH]

---

### Post by Geezanansa on 2012-09-26
Installing grub to sda when ubuntu on sdb/windows sda (cable select) did not work for booting windows
Had to do system restore after restoring windows 8 mbr to get windows 8 booting.
And ubuntu booting after restoring mbr.

So bios only gives one bootable device in bios boot settings when everything fired up on cs configuration.
Bios  gives two harddrives in  bios boot settings>hdds to choose from.   Both of which boot from F11 one time boot list when everything fired up  on cable select configuration.

Leaving bios to select drive gives  me what i want - two os side by side with both being selectable at boot  time.  Using bios to select drive allows hibernation mode settings in  windows 8; (if that drive selected as default/master/bootable), to be  on.
Maybe windows 8 does not like the rewriting of mbr by third party - which is for obvious reasons and is a good thing!

On cable select - maybe bios not giving two bootable devices not letting grub do its job.

Changing jumpers to master and slave will give two boot devices in bios settings.

How to get grub into sda without breaking windows?   -would mean using windows bootmgr!?-working more like easybcd!?

---

### Post by oldfred on 2012-09-26
Your BIOS and older IDE drives seem to be the issue. Not sure if some BIOS setting may help, but beyond that I just do not know.

Since you have this thread posted as Solved not many will look at it. If you want more help, it may pay to start a new thread and include what you have found so far. Many will not read this entire thread to understand your system.

---

