---
title: "Can't boot! error: out of disk grub rescue&gt;"
date: 2009-11-19
forum: General Help
---

### Post by etomar on 2009-11-19
I'm running a dual-boot of Ubuntu 9.10 and Vista on my MSI VR440X. I used my laptop this morning and everything was working fine. But I just got home and turned on the laptop and it won't boot! I get:

GRUB loading (as usual)

but after that I get:

error: out of disk.
grub rescue>

I even tried booting from an Ubuntu CD. I  boots, but any option I choose gives me a black screen with nothing but a _ as if I have to type a command or something. I know it can't possibly mean I'm out of disk space; I had plenty left. Besides, it all worked perfectly this morning. In fact, I didn't even run Ubuntu this morning, I used Vista! I anyone could help me I would really appreciate it. By the way, I'm a total newb when it comes to command prompts and whatever... ;) Anyway, thx!

---

### Post by etomar on 2009-11-19
Please! I can't boot Ubuntu or Windows... No one knows what I could do??

---

### Post by Jabb3r on 2009-11-19
Hi. I saw your post. Sorry yu sys is playin up. I aint no expert with any of this, but mebe one thing that might get you somewhere is to look @ the grub commands so you try to boot your linux image direct and see if that helps. I can't think of the commands off the top of my head but I know grub is pretty powerful to get things up and running again.

Will update with the kinda thing I mean.

Edit: Found this with a quick search. Ignore the making a floppy part but look @ the commands and see if you can adjust as necessary.

[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

Good luck

---

### Post by mihaimm on 2009-11-20
I have exactly the same problem. Started last night, after a reboot. When inspecting (hd0,1)/dev... I see no sda1 there... no sda at all actually. No wonder grub can't find the disk.
The big questions now... how can /dev/sda be missing, what causes this and, most important, how to fix it?

---

### Post by mihaimm on 2009-11-20
> **Jabb3r said:**
> 
[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

This article is from 2001... this is a problem with grub 2.

---

### Post by OnlyTim on 2009-11-20
Seems odd that this happened to me yesterday as well? After doing a update manager session, I came back to the computer a couple of hours later and it had locked up. I did a reboot, and got the error:out of disk,grub rescue.  Using live CD now to post this. I was running dual HDs with the grub on HD0, which, now cannot be seen. 

My question...I want to load grub on the HD1 and remove HD0 (which is failing anyway) anyway to do that using live CD?

Thanks

---

### Post by lmarmisa on 2009-11-20
May be you could try to reinstall grub2.

Start the system with a LiveCd.

Open a terminal and type:

**fdisk -l**

Take note of the Linux partition (I'll suppose that it's /dev/sda1 but change it if neceesary)

[B]mount /dev/sda1 /mnt
mount --bind /dev /mnt/dev
chroot /mnt
install-grub /dev/sda
update-grub2
[/B]
That is all.

Best regards,

Luis

---

### Post by OnlyTim on 2009-11-20
Hi Luis,

I used the fdisk -l and received no output. Still a newbie of sorts so thanks for your patience.

I can mount the HD which is dev/sda1 with my working boot file and see the grub folder. can I reconfigure it there?

---

### Post by lmarmisa on 2009-11-20
I am sorry.

I forgot the first command

**sudo bash**
[B]fdisk -l
...
[/B]
Regards,

Luis

---

### Post by drs305 on 2009-11-20
Getting a grub-rescue prompt normally means G2 can't find the grub.cfg file. Fortunately the Grub 2 rescue prompt will let you search for the partition on which the system is installed.

Try using the Grub 2 Rescue mode to identify the correct partition and boot to it. Here are the community doc instructions on how to use the Rescue mode:
[Grub2 Rescue Mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")

---

### Post by etomar on 2009-11-20
Hi. Thanks a lot for the replies. Well, I managed to boot from a livecd (after waiting forever), but when I try to reinstall Ubuntu, I get this at step 4:

[http://img688.imageshack.us/img688/5117/screenshotc.png](http://img688.imageshack.us/img688/5117/screenshotc.png)

Its blank! No options to choose from... And if I click Forward I get that "No root fie system is defined". Please don't tell me I've lost all my data! I have a lot of important documents and work in there that cannot be replaced! What can I do?? I mean, can't I just boot Windows somehow? I don't even understand how this all happened in the first place... Sorry for all the trouble and thanks again!

---

### Post by utnubuuser on 2009-12-14
I had this same error: grub error:out of disk and could only reach grub recovery.
The solution in my case was to boot through grub rescue, -
 Instruction (Rescue Mode):[/help.ubuntu.com/community/Grub2#Command Line & Rescue Mode]("/help.ubuntu.com/community/Grub2#Command Line & Rescue Mode")
In my case it was a triple boot and following all the steps in the above listed how to, booting into Ubuntu, then reinstalling grub with > sudo grub-installand afterwards doing a > sudo update-grub2 fixed it.

Note: This is for 9.10 etc where Grub2 is in use, and not Legacy grub. - I think directions for earlier versions might be slightly different.

---

### Post by shp.jc on 2009-12-24
Hi I'm trying to install Ubuntu 9.10 on an old Dell Latitude C400 laptop and an Optiplex desktop.
 
After 4 different CD writing attempts I have a CD that will let me run the OS from CD.
 
**On the laptop**, install is almost finished when I get an I/O error that recommends, among other things, that I perform the operation some where colder.
 
Reboot. Can't find a bootable OS on the HD. Try CD again, run from CD, install again....the partition step says that the hard drive is already Ubuntu (rather than XP). Since then I have not been able to get the "install" option or the "run from CD" option to run again.
 
Also when I try to just boot from the HD the system reports no bootable device.
 
No clue what's wrong.
 
**Great news**: I got the laptop installed and booting.  Going into the advanced tab during install I configured the boot install to "sda" rather than the default and it worked.  Now the only problem with the laptop is that Ubuntu can't read from the CD Rom drive.  Even wireless networking worked with the NDISWrapper.  It took two days' of effort but I'm impressed that brand new Ubuntu works on a 10 year old laptop.  You couldn't say the same for Vista or Windows 7.
 
The same step did not help the desktop unfortunately.  
 
**On the Optiplex**, install goes fine. But when I reboot the machine I get...
 
GRUB loading...
error: out of disk
grub rescue>
 
I've seen the post to read the link on Grub and rescue mode, but aside from "ls" none of the commands listed work.
 
when I enter ls I get
(hd0) (hd0,1) (fd0)
error: no such disk
grub rescue>
 
Note I am not trying to run dual boot (just Ubuntu) so I also tried the advanced option not to include dual boot but have the same problem.  And I tried the "sda" trick I mentioned above but no joy.  
 
Note in order to get the system to boot from CD I have to disable the HD as a boot option in the BIOS. Then I go back and reenable the HD option. I have no idea why, but both Dells ignore the CD if I don't disable the HD. I don't know if the problem is that "hd0" is changing.
 
Any ideas how to solve these problems?
 
I know *nothing* about Linux and have been all Windows for 20 years (except for a brief OS/2 daliance in 95 but I was young). I can't even use a Mac because I can't get over that it's missing a mouse button. So I really need some help here.
 
Thanks

---

### Post by shane.wilkins on 2009-12-31
Ok, I was having the same problem I think a few of the rest of you were too. I was trying to install 9.10 on my eeePC 901 with a liveUSB, but it kept kicking me back to the GRUB rescue screen. 

I was creating the liveUSB using the command ```
dd . . . 
``` in my terminal on Mac OS X 10.6. *However*,  if you create the liveUSB, from the dd command you have to be burning the USB off of an .img file, rather than an .iso file. 

Curiously, there is no .img file available for 9.10, so what I did was downloaded the old .img for 9.04 and burned that with dd and now installation is working just fine, no grub menu freakouts. 

Don't know if this is what your issues were, but this worked for me.

---

### Post by Paul Stone on 2010-01-07
> **etomar said:**
> Please! I can't boot Ubuntu or Windows... No one knows what I could do??

I guess it's too late to be of any help, but you can fix the Windows boot by using FIXBOOT and FIXMBR, which are available from the Windows installation CD.

You should be able to google on those terms and find instructions on how to go about getting Windows booting again.

I found this information by Microsoft:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

It may be possible that by getting Windows to fix its own boot, you will then be able to boot Ubuntu with the LiveCD, but I wouldn't count on it.

---

### Post by mihaimm on 2010-02-18
After a lot of trying... I solved my initial problem with a... BIOS update. Don't see why this would solve it or how was the BIOS related to grub... but... in my case, it did fix all problems I had with grub2.

---

### Post by sameer.walgude on 2010-03-12
Try this at grub rescue> prompt....

grub rescue> set prefix=(hd0,x)/boot/grub
grub rescue> insmod (hd0,x)/boot/grub/normal.mod
rescue:grub> normal

(here x represents the partition number where ubuntu is installed...)
(try ls at prompt to know your existing partitions...)

If still fails...boot up live cd...

at terminal...
sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub /dev/sda

substitute /media/{kubuntu9.10partition} with actual partition :)

If you get error message,(mapping fails), do this..

sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub -m 
/media/{kubuntu9.10partition}/boot/grub/device.map /dev/sda

All the best!

Thanks & Regards
Sameer J Walgude
[email]sameer.walgude@aol.in[/email]
+91 98191 15533

---

### Post by sameer.walgude on 2010-03-12
Try this at grub rescue> prompt....

grub rescue> set prefix=(hd0,x)/boot/grub
grub rescue> insmod (hd0,x)/boot/grub/normal.mod
rescue:grub> normal

(here x represents the partition number where ubuntu is installed...)
(try ls at prompt to know your existing partitions...)

If still fails...boot up live cd...

at terminal...
sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub /dev/sda

substitute /media/{kubuntu9.10partition} with actual partition :)

If you get error message,(mapping fails), do this..

sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub -m 
/media/{kubuntu9.10partition}/boot/grub/device.map /dev/sda

All the best!

Thanks & Regards
Sameer J Walgude
[email]sameer.walgude@aol.in[/email]
+91 98191 15533

---

### Post by akxiii on 2010-05-03
> **lmarmisa said:**
> May be you could try to reinstall grub2.

Start the system with a LiveCd.

Open a terminal and type:

**fdisk -l**

Take note of the Linux partition (I'll suppose that it's /dev/sda1 but change it if neceesary)

[B]mount /dev/sda1 /mnt
mount --bind /dev /mnt/dev
chroot /mnt
install-grub /dev/sda
update-grub2
[/B]
That is all.

Best regards,

Luis

I got "install-grub: command not found"
Am I right in thinking that I should be trying this from the livecd?

---

### Post by tomihasa on 2010-05-29
First I tried to install Windows 2000 and then Ubuntu 10.04 LTS Desktop Edition and I got (only ls command works in grub rescue):

```
grub rescue> ls
(hd0) (hd0,1) (fd0)
```

Then I tried to install only Ubuntu and I got:

```
error: out of disk.
grub rescue> ls
(hd0) (hd0,1) (fd0)
```

Then I used Mandriva installation disc to find out that Ubuntu didn't remove the old partitions and they were invisible to Ubuntu installation disc, but not to Mandriva installation disc. Could it be my approximately 10 year old BIOS causing the problems as hinted by someone else on this topic?

Also, after installing Ubuntu I get many lines like these, but I see them only once after installation:

```
[ 1409.827253] end_request: I/O error, dev sr0, sector 505896
[ 1409.830711] end_request: I/O error, dev sr0, sector 505904
[ 1409.834133] end_request: I/O error, dev sr0, sector 505904
...
```

---

### Post by factorialpython on 2010-07-01
out of disk grub rescu, same problem on home pc, cannot get into grub rescue if i press restart (i was told to hold tab during boot), anywho after cmos check, goes straight to that error, anything i type gives reply "no such command":confused:

---

### Post by drs305 on 2010-07-01
> **factorialpython said:**
> out of disk grub rescu, same problem on home pc, cannot get into grub rescue if i press restart (i was told to hold tab during boot), anywho after cmos check, goes straight to that error, anything i type gives reply "no such command":confused:

If youa re trying to get to the grub menu, you hold down the SHIFT key. But in your case it probably is still going to leave you at the prompt. For determining what the problem is the best course would be to post the results of the boot info script found here:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by mamamia88 on 2010-07-31
not even getting grub rescue script anymore.   thinking of just waiting to build a new system based around the ssd

---

### Post by tom_pm on 2010-08-09
I installed ubuntu recently on an old PC, worked perfectly until I connected it to internet and downloaded the last updates. when I rebooted it I could'nt get further the "error: out of disk   
 grub rescue> "
I looked up my system with the "ls" command and when I arrived to "ls (hd0,1)/boot" I got the error: out of disk again
 
little detail, I cannot boot linux from a live cd as my computer don't have enough RAM for it.

---

### Post by kallavin on 2010-08-13
I have found the fix for this error. If you try to reinstall Ubuntu on a previously installed harddisk, the installer will not delete the partition. I have a windows xp disc and I used its Partitioner to delete everything on my harddisk. Then I reinstalled Ubuntu again.

---

### Post by mrguga on 2010-10-19
Well, i guess i was lucky on solving this... I had recently changed some configuration in BIOS... and when i installed 10.10 i got this error out of disk.
The configuration i changed was something about Sata Mode. It was set to AHCI. When i set back to IDE mode (not raid) it booted ok!

Maybe the bios update some user did to solve just reset bios to default values and set it to IDE mode again.

Hope it works for you guys!

---

### Post by weisbm on 2010-11-09
I had the same problem, and the most consistent symptom I found was that it was happening on HP laptops.  (weird!)

My "fix" was to create a partition of no more than 8 GB, and designate it as "/boot", allocate all but the last 4 GB of the drive as "/" and the last 4 GB as swap.  

I seem to remember somewhere, a long time ago, that older BIOS's could not load a kernel from above the 8 GB line.

Anyone have a better answer?  I tried playing with the BIOS settings, but didn't get any good results.

Thanks,

Michael

---

### Post by ogre_lawless on 2010-11-12
> **weisbm said:**
> I had the same problem, and the most consistent symptom I found was that it was happening on HP laptops.  (weird!)

My "fix" was to create a partition of no more than 8 GB, and designate it as "/boot", allocate all but the last 4 GB of the drive as "/" and the last 4 GB as swap.  

I seem to remember somewhere, a long time ago, that older BIOS's could not load a kernel from above the 8 GB line.

Anyone have a better answer?  I tried playing with the BIOS settings, but didn't get any good results.

Thanks,

Michael

Thanks a million for posting this. I just ran into this dropping Ubuntu 10.10 onto a rather old but still serviceable machine and this appears to have solved my instance of this same problem.  I notice GRUB still throws errors on boot but it proceeds OK after that.

---

### Post by baksoy08 on 2010-12-31
I installed ubuntu in "D" with **Wubi** (Windows 7 Ultimate). Then I updated and restarted.
I had
[B]error: no such device: 4261f085-4ce8-4dff-9214-dfed58457dd0
grub rescue>[/B]

I tried;
[B]grub rescue>ls
(hd0) (fd0) (fd1)
grub rescue> set prefix=(hd0,1)/boot/grub[/B] and
**grub rescue> set prefix=(hd0,0)/boot/grub** and
**grub rescue> set prefix=(hd0,2)/boot/grub** and
**grub rescue> set prefix=(hd1,0)/boot/grub**
[B]grub rescue> set root=(loop0)
grub rescue> set
prefix=(hd0,1)/boot/grub
root=loop0
grub rescue> ls /boot
error: no such disk.[/B]

Please Help!  :(

Thanks,
Bahad&#305;r.

---

### Post by baksoy08 on 2010-12-31
I installed ubuntu in "D" with **Wubi** (Windows 7 Ultimate). Then I updated and restarted.
I had
[B]error: no such device: 4261f085-4ce8-4dff-9214-dfed58457dd0
grub rescue>[/B]

I tried;
[B]grub rescue>ls
(hd0) (fd0) (fd1)
grub rescue> set prefix=(hd0,1)/boot/grub[/B] and
**grub rescue> set prefix=(hd0,0)/boot/grub** and
**grub rescue> set prefix=(hd0,2)/boot/grub** and
**grub rescue> set prefix=(hd1,0)/boot/grub**
[B]grub rescue> set root=(loop0)
grub rescue> set
prefix=(hd0,1)/boot/grub
root=loop0
grub rescue> ls /boot
error: no such disk.[/B]

Please Help!  :(

Thanks,
Bahad&#305;r.

---

### Post by drs305 on 2010-12-31
baksoy08,

Welcome to the Ubuntu forums. Forum member *Rubi1200* has written a very comprehensive guide to solving Wubi boot problems. Take a look here:
[Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by BigMoose on 2011-01-19
> **weisbm said:**
> I had the same problem, and the most consistent symptom I found was that it was happening on HP laptops.  (weird!)

My "fix" was to create a partition of no more than 8 GB, and designate it as "/boot", allocate all but the last 4 GB of the drive as "/" and the last 4 GB as swap.  

I seem to remember somewhere, a long time ago, that older BIOS's could not load a kernel from above the 8 GB line.

Anyone have a better answer?  I tried playing with the BIOS settings, but didn't get any good results.

Thanks,

Michael

Could you provide the details of how you did this? I am not that tech savy when its comes to OS's and disk partitioning so I would appreciate steps for someone like me to do. Thanks.

---

### Post by BigMoose on 2011-01-19
> **weisbm said:**
> I had the same problem, and the most consistent symptom I found was that it was happening on HP laptops.  (weird!)

My "fix" was to create a partition of no more than 8 GB, and designate it as "/boot", allocate all but the last 4 GB of the drive as "/" and the last 4 GB as swap.  

I seem to remember somewhere, a long time ago, that older BIOS's could not load a kernel from above the 8 GB line.

Anyone have a better answer?  I tried playing with the BIOS settings, but didn't get any good results.

Thanks,

Michael

Could you provide the details of how you did this? I am not that tech savy when its comes to OS's and disk partitioning so I would appreciate steps for someone like me to do. Thanks.

---

### Post by cordoval on 2011-02-05
Please provide details
I got an hp dv2125la and it suddently gave 
error: hd0,msdos1 out of disk

ls returns:
(hd0) (hd0,msdos5) (hd0, msdos1)

when I do:
set prefix=(hd0,msdos1)/boot/grub
insmod (hd0,msdos1)/boot/grub/normal.mod

I get the error: hd0,msdos1 out of disk

... trying to think what else to do,

when I try a liveCD I get the same thing, it would not boot from it

Please any help?

also I have noticed on the BIOS that the hard disk is not being recognized, however on the boot I can see the folders

with 

ls (hd0,msdos1)/

however when I try to go inside one of the directories it just fails and gives the error

please help

thanks

---

### Post by cordoval on 2011-02-05
> **tom_pm said:**
> I installed ubuntu recently on an old PC, worked perfectly until I connected it to internet and downloaded the last updates. when I rebooted it I could'nt get further the "error: out of disk   
 grub rescue> "
I looked up my system with the "ls" command and when I arrived to "ls (hd0,1)/boot" I got the error: out of disk again
 
little detail, I cannot boot linux from a live cd as my computer don't have enough RAM for it.

I have the same problem, but it seems like it is not the RAM
I do have 2GB of RAM!!!

I think that is enough to boot, don't you think?

Any help please, how were you able to solve it?

thanks

---

### Post by wojox on 2011-02-05
Have you read the thread in my signature?

---

### Post by Andri33 on 2011-04-22
Hi. I'm having a grub problem as well. Could anyone help me. I looked around the forum and I found some stuff that is similar to what happened to my computer but all that I tried did not work. It's about ubuntu 10.04 which has grub 2 if I'm not mistaking. 

I have a computer with windwos xp on it and I installed ubuntu 10.04 along to give it a try. I didn't even got the chance to enter windows or ubuntu because I got the "grub rescue>" message after restarting.

Running ubuntu from the cd works, I can mount the windows partitions and access the data. I tried to see if I can reinstall windows but it tells me that it can't access the hard drive as if it's not there.

I also tried to reinstall ubuntu but I get stuck at the part when it asks me to partition the space. It says the root system file is not defined or smt like that. 
I tried the commands in this thread and some of them work like "set prefix=(hd0,x)/boot/grub" but when I get to the "insmod" command  it says out of disk.

Another thing I tried was to fix the windows boot by running windows cd. The command fixmbr works but not fixboot, so I can't finalize. Can you please help me. Thanks

---

### Post by smallispowerful on 2011-08-04
When in rescue, I typed ls and got hd0 and hd0,msdos1.

I think the problem here may be that ubuntu install disk for 11.04 does not properly remove previous partitions correctly (I had done a complete install selecting ubuntu as my only OS), and so my outdated bios was trying to boot multiple drives.

My solution was to use the UBCD and completely wipe the hard drive (after i had removed all valuables by running ubuntu from the usb boot) and do a complete fresh start. Trying now and will post results

---

### Post by BigD77 on 2011-09-05
> **drs305 said:**
> If youa re trying to get to the grub menu, you hold down the SHIFT key. But in your case it probably is still going to leave you at the prompt. For determining what the problem is the best course would be to post the results of the boot info script found here:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")


I tried loading Lubuntu 11.04 in a dual boot with XP:

```

                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x88928892

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   233,571,163   233,571,101   7 NTFS / exFAT / HPFS
/dev/sda2         233,572,350   488,396,799   254,824,450   5 Extended
/dev/sda5         233,572,352   487,088,127   253,515,776  83 Linux
/dev/sda6         487,090,176   488,396,799     1,306,624  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        325879C55879887D                       ntfs       
/dev/sda5        b2689d1a-f3f5-4bb9-9f90-662117ef2588   ext4       
/dev/sda6        354e0bb8-196b-4e8b-85a2-d32602658a6e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/b2689d1a-f3f5-4bb9-9f90-662117ef2588 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sr0         /cdrom                   iso9660    (rw)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=5

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

--------------------------------------------------------------------------------

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root b2689d1a-f3f5-4bb9-9f90-662117ef2588
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root b2689d1a-f3f5-4bb9-9f90-662117ef2588
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=b2689d1a-f3f5-4bb9-9f90-662117ef2588 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=b2689d1a-f3f5-4bb9-9f90-662117ef2588 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 325879C55879887D
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b2689d1a-f3f5-4bb9-9f90-662117ef2588 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=354e0bb8-196b-4e8b-85a2-d32602658a6e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-8-generic               2
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  55 45 20 66 61 69 6c 65  64 20 69 6e 20 69 66 6f  |UE failed in ifo|
00000010  5f 72 65 61 64 2e 63 3a  31 35 39 39 20 2a 2a 2a  |_read.c:1599 ***|
00000020  0a 2a 2a 2a 20 66 6f 72  20 63 5f 61 64 74 2d 3e  |.*** for c_adt->|
00000030  63 65 6c 6c 5f 61 64 72  5f 74 61 62 6c 65 5b 69  |cell_adr_table[i|
00000040  5d 2e 63 65 6c 6c 5f 69  64 20 3e 20 30 20 2a 2a  |].cell_id > 0 **|
00000050  2a 0a 0a 0a 2a 2a 2a 20  6c 69 62 64 76 64 72 65  |*...*** libdvdre|
00000060  61 64 3a 20 43 48 45 43  4b 5f 56 41 4c 55 45 20  |ad: CHECK_VALUE |
00000070  66 61 69 6c 65 64 20 69  6e 20 69 66 6f 5f 72 65  |failed in ifo_re|
00000080  61 64 2e 63 3a 31 36 30  31 20 2a 2a 2a 0a 2a 2a  |ad.c:1601 ***.**|
00000090  2a 20 66 6f 72 20 63 5f  61 64 74 2d 3e 63 65 6c  |* for c_adt->cel|
000000a0  6c 5f 61 64 72 5f 74 61  62 6c 65 5b 69 5d 2e 73  |l_adr_table[i].s|
000000b0  74 61 72 74 5f 73 65 63  74 6f 72 20 3c 20 63 5f  |tart_sector < c_|
000000c0  61 64 74 2d 3e 63 65 6c  6c 5f 61 64 72 5f 74 61  |adt->cell_adr_ta|
000000d0  62 6c 65 5b 69 5d 2e 6c  61 73 74 5f 73 65 63 74  |ble[i].last_sect|
000000e0  6f 72 20 2a 2a 2a 0a 0a  0a 2a 2a 2a 20 6c 69 62  |or ***...*** lib|
000000f0  64 76 64 72 65 61 64 3a  20 43 48 45 43 4b 5f 56  |dvdread: CHECK_V|
00000100  41 4c 55 45 20 66 61 69  6c 65 64 20 69 6e 20 69  |ALUE failed in i|
00000110  66 6f 5f 72 65 61 64 2e  63 3a 31 35 39 37 20 2a  |fo_read.c:1597 *|
00000120  2a 2a 0a 2a 2a 2a 20 66  6f 72 20 63 5f 61 64 74  |**.*** for c_adt|
00000130  2d 3e 63 65 6c 6c 5f 61  64 72 5f 74 61 62 6c 65  |->cell_adr_table|
00000140  5b 69 5d 2e 76 6f 62 5f  69 64 20 3e 20 30 20 2a  |[i].vob_id > 0 *|
00000150  2a 2a 0a 0a 0a 2a 2a 2a  20 6c 69 62 64 76 64 72  |**...*** libdvdr|
00000160  65 61 64 3a 20 43 48 45  43 4b 5f 56 41 4c 55 45  |ead: CHECK_VALUE|
00000170  20 66 61 69 6c 65 64 20  69 6e 20 69 66 6f 5f 72  | failed in ifo_r|
00000180  65 61 64 2e 63 3a 31 35  39 39 20 2a 2a 2a 0a 2a  |ead.c:1599 ***.*|
00000190  2a 2a 20 66 6f 72 20 63  5f 61 64 74 2d 3e 63 65  |** for c_adt->ce|
000001a0  6c 6c 5f 61 64 72 5f 74  61 62 6c 65 5b 69 5d 2e  |ll_adr_table[i].|
000001b0  63 65 6c 6c 5f 69 64 20  3e 20 30 20 2a 2a 00 fe  |cell_id > 0 **..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 58 1c 0f 00 fe  |...........X....|
000001d0  ff ff 05 fe ff ff 02 58  1c 0f 00 f8 13 00 00 00  |.......X........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by drs305 on 2011-09-05
BigD77,

The Grub 2 menus look correct but this part of RESULTS.txt indicates there is a problem finding the Grub file locations:
> 
=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-8-generic               2
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================



You could try reinstalling Grub2 from the LiveCD. Do not include the partition number in the second command:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```
Reboot. If you still get a grub rescue prompt, run the following commands to determine if Grub can see your Grub files.

```
ls (hd0,5)/boot # Should see your 'vmlinuz' and 'initrd.img' files.
ls (hd0,5)/boot/grub # Should see a lot of *.mod files, and grub.cfg
```

---

### Post by BigD77 on 2011-09-05
Thanks.  I am trying with a new fresh start.  I was trying to load it from a flash drive using pendrive linux.  Just formatted the whole drive, re-installed XP, now formatted the USB drive and downloading Lubuntu 11.04 amd creating a new pendrive file.  

Spent most of last night playing with this.  The first time I tried installing it, I got the "Minimal BASH" error.  The next timeI first ran Lubuntu from the drive like a Live CD, and installed it from there, and got "Out of disk grub rescue".  Maybe it's something I did wrong.  But running it from the USB drive like a live CD runs fine.  :confused:

---

### Post by drs305 on 2011-09-05
> **BigD77 said:**
> Thanks.  I am trying with a new fresh start.  I was trying to load it from a flash drive using pendrive linux.  Just formatted the whole drive, re-installed XP, now formatted the USB drive and downloading Lubuntu 11.04 amd creating a new pendrive file.  

Spent most of last night playing with this.  The first time I tried installing it, I got the "Minimal BASH" error.  The next timeI first ran Lubuntu from the drive like a Live CD, and installed it from there, and got "Out of disk grub rescue".  Maybe it's something I did wrong.  But running it from the USB drive like a live CD runs fine.  :confused:

The steps I listed were leading to the possibility that your BIOS isn't recognizing the full drive size. If your system still ends up at the grub rescue prompt after the installation we can do the troubleshooting to setermine of that might be causing it...

Good luck with the fresh install; hopefully it will work.

---

### Post by BigD77 on 2011-09-05
> **drs305 said:**
> The steps I listed were leading to the possibility that your BIOS isn't recognizing the full drive size. If your system still ends up at the grub rescue prompt after the installation we can do the troubleshooting to setermine of that might be causing it...

Good luck with the fresh install; hopefully it will work.

Nope. It didn't.  I set it up with XP getting 112 GB space, and Lubuntu getting the rest.  That worked with Ubuntu 9.10. 

I tried the steps you suggested previously.  I got this:
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.

Not able to boot.  Then I tried:

ubuntu@ubuntu:~$ ls (hd0,5)/boot #
bash: syntax error near unexpected token `('
Also:
ubuntu@ubuntu:~$ ls (hd0,5)/boot 
bash: syntax error near unexpected token `('

I also tried:
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x88928892

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13559   108908519    7  HPFS/NTFS
/dev/sda2           13559       30402   135288833    5  Extended
/dev/sda5           13559       30320   134634496   83  Linux
/dev/sda6           30320       30402      653312   82  Linux swap / Solaris

Disk /dev/sdb: 8021 MB, 8021606400 bytes
247 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a7524

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1023     7833080    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(1023, 246, 62) logical=(1022, 246, 62)
And tried:

root@ubuntu:~# ls (hd0,5)/boot #
bash: syntax error near unexpected token `('

---

### Post by drs305 on 2011-09-05
BigD77,

The "ls" commands are to be run at the grub rescue prompt after a failed boot. 

If the BIOS isn't recognizing the part of the disk with the Grub/boot files, the "ls" commands won't find them. If the commands do provide valid returns, the BIOS and Grub are able to see the boot files and there is some other issue.

It can be a bit deceiving because once the system boots the OS can see the entire disk and all the files. It's just the BIOS (and Grub) that cannot see them during the boot process (if that is the problem).

---

### Post by BigD77 on 2011-09-05
> **drs305 said:**
> BigD77,

The Grub 2 menus look correct but this part of RESULTS.txt indicates there is a problem finding the Grub file locations:


You could try reinstalling Grub2 from the LiveCD. Do not include the partition number in the second command:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```
Reboot. If you still get a grub rescue prompt, run the following commands to determine if Grub can see your Grub files.

```
ls (hd0,5)/boot # Should see your 'vmlinuz' and 'initrd.img' files.
ls (hd0,5)/boot/grub # Should see a lot of *.mod files, and grub.cfg
```


I did a fresh install of XP again and re-loaded Lubuntu 11.04 from a USB drive.  I used 100 GB for XP, the rest for Lubuntu (The BIOS sees 137 GB).  Got the same result.

Tried the above suggestions.  When I tried the ls commands, I got "bad file name" on both.
grub rescue> ls (hd0,5) /boot #
error: bad file name.

---

### Post by drs305 on 2011-09-05
There shouldn't be a space in the command "ls (hd0,5)/boot", but if that isn't the problem, the next thing to check is to enter the BIOS setup during boot and find out the reported drive size.

If it is reporting a drive size of 137GB (or less), it means your BIOS cannot see any further than that on the drive. Your options are to update the BIOS, shrink your partitions so Ubuntu is within the first 137GB of the drive, or create a separate boot partition either on the same drive (within the first 137GB) or on another drive.

---

### Post by BigD77 on 2011-09-05
> **drs305 said:**
> There shouldn't be a space in the command "ls (hd0,5)/boot", but if that isn't the problem, the next thing to check is to enter the BIOS setup during boot and find out the reported drive size.

If it is reporting a drive size of 137GB (or less), it means your BIOS cannot see any further than that on the drive. Your options are to update the BIOS, shrink your partitions so Ubuntu is within the first 137GB of the drive, or create a separate boot partition either on the same drive (within the first 137GB) or on another drive.

The BIOS reports 137 GB.  I used 100 GB for XP, the rest for Lubuntu.  That setup worked for Ubuntu 9.10, the last Ubuntu install that worked.

---

### Post by drs305 on 2011-09-05
> **BigD77 said:**
> The BIOS reports 137 GB.  I used 100 GB for XP, the rest for Lubuntu.  That setup worked for Ubuntu 9.10, the last Ubuntu install that worked.

Ok, I think the solution should be simple enough. If you shrink the Lubuntu partition to around 30GB you should solve your problem. That will ensure the /boot and Grub files are all within the area seen by BIOS/GRUB. You can use the extra space as a data partition. Be sure to back up any important data files before doing any partitioning work.

You will have to shrink the Ubuntu partition from the LiveCD, as the Lubuntu partition (and swap partition which you will have to unmount via Gparted after booting the CD) must be unmounted when you shrink it.

---

### Post by BigD77 on 2011-09-05
> **drs305 said:**
> Ok, I think the solution should be simple enough. If you shrink the Lubuntu partition to around 30GB you should solve your problem. That will ensure the /boot and Grub files are all within the area seen by BIOS/GRUB. You can use the extra space as a data partition. Be sure to back up any important data files before doing any partitioning work.

You will have to shrink the Ubuntu partition from the LiveCD, as the Lubuntu partition (and swap partition which you will have to unmount via Gparted after booting the CD) must be unmounted when you shrink it.

This sounds almost complicated.  (I just again did a fresh install of XP, thanks Norton Ghost).  So I then re-install Lubuntu, leaving roughly 100 GB for XP, (And the rest will go to Lubuntu).  Then go back using the live USB stick and use Gparted to shrink the Lubuntu to 30GB or less?

---

### Post by drs305 on 2011-09-05
> **BigD77 said:**
> This sounds almost complicated.  (I just again did a fresh install of XP, thanks Norton Ghost).  So I then re-install Lubuntu, leaving roughly 100 GB for XP, (And the rest will go to Lubuntu).  Then go back using the live USB stick and use Gparted to shrink the Lubuntu to 30GB or less?

If you haven't already reinstalled Lubuntu, I would use the Windows partitioner to make a new 30GB partition, and then during the Lubuntu installation use the manual partitioning option to install Lubuntu into that partition. You would select the partition, then also designate / as the mountpoint on the same page.

If you have already installed Lubuntu: You use Gparted and a LiveCD, you just shrink the Ubuntu partition ( move the right border of the partition to the left) to make it less than 35GB or so. This will ensure all it's files are within, and remain within, the first 137GB of the disk.

If I'm not making myself clear just keep asking for clarification.  :-)

---

### Post by BigD77 on 2011-09-05
> **drs305 said:**
> If you haven't already reinstalled Lubuntu, I would use the Windows partitioner to make a new 30GB partition, and then during the Lubuntu installation use the manual partitioning option to install Lubuntu into that partition. You would select the partition, then also designate / as the mountpoint on the same page.

If you have already installed Lubuntu: You use Gparted and a LiveCD, you just shrink the Ubuntu partition ( move the right border of the partition to the left) to make it less than 35GB or so. This will ensure all it's files are within, and remain within, the first 137GB of the disk.

If I'm not making myself clear just keep asking for clarification.  :-)

Thanks.  I am already in the process of re-installing Lubuntu.  Sometimes people don't get my sense of humour.

---

### Post by BigD77 on 2011-09-05
Well, that worked, but now the screen is all screwed up.  I am getting almost a duplicate screen 2/3 of the way down, and 2/3 of the screen from left to right.  And screen resolution of 640x480 and not adjustable.  How can that be fixed?

---

### Post by drs305 on 2011-09-06
> **BigD77 said:**
> Well, that worked, but now the screen is all screwed up.  I am getting almost a duplicate screen 2/3 of the way down, and 2/3 of the screen from left to right.  And screen resolution of 640x480 and not adjustable.  How can that be fixed?

I'll offer one possibility but screen displays are not my area of expertise. You can two things:
1. Try booting the recovery mode and selecting the failsafe graphic mode.  If it works, add your video card driver.

2. Try adding "nomodeset" to the 'linux' line of the menuentry. 
At the Grub menu, press 'e' to edit the desired selection. 
Cursor to the end of the 'linux' line and delete 'quiet splash' and whatever else is there. 
Add **nomodeset**
CTRL-x to boot.
If it boots to a normal screen, try to add your video card's driver via "Additional Drivers".

If neither of those work, I'd recommend opening a new thread with a more applicable title. You will get more views, and the viewers will be more likely to be able to answer your questions.

---

### Post by BigD77 on 2011-09-06
> **drs305 said:**
> I'll offer one possibility but screen displays are not my area of expertise. You can two things:
1. Try booting the recovery mode and selecting the failsafe graphic mode.  If it works, add your video card driver.

2. Try adding "nomodeset" to the 'linux' line of the menuentry. 
At the Grub menu, press 'e' to edit the desired selection. 
Cursor to the end of the 'linux' line and delete 'quiet splash' and whatever else is there. 
Add **nomodeset**
CTRL-x to boot.
If it boots to a normal screen, try to add your video card's driver via "Additional Drivers".

If neither of those work, I'd recommend opening a new thread with a more applicable title. You will get more views, and the viewers will be more likely to be able to answer your questions.

Thanks for all the help!

I'll have to give that a try when I get home.  What baffles me is that the screen, resolution and all work fine when running off the Live USB drive.  And it works great on that 2001 vintage H-P Pentium 3 desktop I loaded Lubuntu on.

---

### Post by drs305 on 2011-09-06
> **BigD77 said:**
> Thanks for all the help!

I'll have to give that a try when I get home.  What baffles me is that the screen, resolution and all work fine when running off the Live USB drive.  And it works great on that 2001 vintage H-P Pentium 3 desktop I loaded Lubuntu on.

The 'nomodeset' option prevents some modules from loading. Since the video works when booting the LiveUSB, I'm thinking that a driver is loading at boot that wouldn't otherwise. So disabling the option until you can investigate it may work. 

Note that editing the Grub menu at boot is not persistent. The edit won't be present on the next boot unless you actually modify the boot files after successfully booting. Of course, if you fix the drivers you may not need the 'nomodeset' option...

---

### Post by BigD77 on 2011-09-07
Once again, thanks!

I tried that, was able to get full screen by deleting the "quick flash" in the logon menu, but made a mistake and deleted it in the grub cfg.  So I removed Lubuntu and installed Ubuntu 10.10, and so far, everything's good.  ):P

---

### Post by MayKee on 2011-09-09
i've same problem but i don't have a live cd and i create a liveUSB but when i reboot my machine i didnt see anythng( like try or install) , opening OS selection page but when i choose ubuntu saying minimal bash error, on the other hand my second OS win7 is workin normlly ...

---

### Post by dragen427 on 2011-12-01
> **drs305 said:**
> Ok, I think the solution should be simple enough. If you shrink the Lubuntu partition to around 30GB you should solve your problem. That will ensure the /boot and Grub files are all within the area seen by BIOS/GRUB. You can use the extra space as a data partition. Be sure to back up any important data files before doing any partitioning work.

You will have to shrink the Ubuntu partition from the LiveCD, as the Lubuntu partition (and swap partition which you will have to unmount via Gparted after booting the CD) must be unmounted when you shrink it.

I did this (above) shrinking the Linux partition to just under 40GB.  It booted up right away with no error messages.

I installed Mythbuntu 11.10 on a PIII 1.0MHz machine with a 320GB hard drive.  Not sure how well it's going to work yet, but it's running the OS fine.

---

### Post by Agrapha on 2012-01-10
I had ubuntu running onj my Satellite-1955 laptop. It crashed. I repaired it with "fsck" but the drive is the original 40 gig drive and it was finally giving up... The drive kept re-reading sectors/tracks and after a third or fourth manual fsck from a live CD, I was forced to buy a new HD.
 
The new PATA WD 250 was expensive but I liked that laptop. I downloaded 11.01 and watched it epically fail saying the media was bad or my new hard drive failed. After trying for 48 hours I was made a believer. I returned it for a new drive, with the same model and type. However, again Media fail. Burned a new CD at S L O W S P E E D as the helpful ubuntu error recomended. Same error.
 
Next I grabbed a 10.04 LTS iso and tried it. No Error but failed to boot with "OUT OF DISK." and the *grub rescue>* prompt. My last version was 9.X and it installed ok. It occured to me my last drive was formated ext3. So again fdisk from live CD shell. Manually click advanced and reprovisioned the drive into 
/ ext3 0 - 249000
and swap linux swap 1024
 
Yes I know this setup is madness but ...
 
it installed perfect and booted with only a momentary pause of "OUT OF DISK" but continued to boot. Logged in and I'm up. 1 gig memory.
 
I'll try and reinstall grub-install tonight and see if that works too.
 
Just my 2c

---

### Post by Agrapha on 2012-01-11
Reinstalled Grub loader with 
grub-install /dev/sda
 
and updated with 
update-grub
 
after reboot I get a very nice menu driven grub request asking which one of about 4 ubuntu roots I'd like to start. I picked the first one. It seems to work great but I'm a bit concerned about the 4-8 other roots it offered to start. Could those other roots but the failed installs that also failed to delete even after a fdisk?
 
Let me know how I should remove those entries with out messing up my working partition.

---

### Post by drs305 on 2012-01-12
Agrapha,

Those additional entries are most likely other kernels. You can use Ubuntu Tweak to remove them if you wish, but it's usually best to keep at least one older kernel that works. The easiest way to clean up the menu is with Ubuntu Tweak.

I've written a guide about removing older kernels which you can review. The link follows, but note that I can't be sure from your post that these menu items are older kernels.  If you read the post, let Ubuntu Tweak take a look, and are not sure this is what you are looking at on your Grub menu please ask for more clarification.

[HOWTO: Remove Older Kernels via GUI ]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by Agrapha on 2012-01-12
Ok I'm trying to get ubuntu-tweaks installed but the installer says there is a dependency missing called   python-aptdaemon.gtk3widgets which I tried also tried to install but that required python2.7 but my system has 2.65 installed on this box.

Not sure how to install this tweak.

Error: Dependency is not satisfiable: python2.7

---

### Post by Agrapha on 2012-01-12
> **Agrapha said:**
> Ok I'm trying to get ubuntu-tweaks installed but the installer says there is a dependency missing called   python-aptdaemon.gtk3widgets which I tried also tried to install but that required python2.7 but my system has 2.65 installed on this box.

Not sure how to install this tweak.

Error: Dependency is not satisfiable: python2.7


Let me just say if I had actually read the instructions posted on the page I probably would have had this installed already. Second time around I realized there was already a build for 10.04 I could download. Yes it installed just fine after I fixed my dependencies with
 apt-get install -f

that straightened me out and yes I have tweaks installed.

---

### Post by ray13z on 2012-01-14
[COLOR=#000000][FONT=Arial]Hi, sorry for posting in this thread again. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I  have a Dell Inspiron 17R. There's a 640GB HDD (the entire chunk  recognised by BIOS) and I have a dual booted system (WIn 7 + Ubuntu).[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I  installed 11.10 a few days back via a USB and it completed  successfully. However when I boot now, I get the same 'error: hd0 out of  disk.' followed by a grub rescue prompt. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I can see all partitions using 'ls' and even located my Ubuntu partition with the /boot and /boot/grub files all intact. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]While  recovering using the commands, the 'set prefix' and 'set root' work  fine, but when I run 'insmod linux' I get the same infamous 'error: hd0  out of disk.'[/FONT][/COLOR]

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

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
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 30580 of /dev/sdb1 for its 
                       second stage. According to the info in the boot 
                       sector, sdb1 starts at sector 0. But according to the 
                       info from fdisk, sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2    *        206,848    20,686,847    20,480,000   7 NTFS / exFAT / HPFS
/dev/sda3          20,686,848   146,512,799   125,825,952   7 NTFS / exFAT / HPFS
/dev/sda4         146,516,894 1,250,258,943 1,103,742,050   f W95 Extended (LBA)
/dev/sda5         146,516,896   461,085,600   314,568,705   7 NTFS / exFAT / HPFS
/dev/sda6         910,532,133 1,225,100,834   314,568,702  83 Linux
/dev/sda7       1,225,101,312 1,245,100,031    19,998,720  83 Linux
/dev/sda8       1,245,102,080 1,246,259,199     1,157,120  83 Linux
/dev/sda9       1,246,261,248 1,250,258,943     3,997,696  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8021 MB, 8021606400 bytes
247 heads, 62 sectors/track, 1023 cylinders, total 15667200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62    15,666,221    15,666,160   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       56087728-a73b-47f8-8351-cb37d065c7bc   ext3       
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        925E68275E680677                       ntfs       RECOVERY
/dev/sda3        18B4B7BBB4B799A8                       ntfs       OS
/dev/sda5        DC8E5B128E5AE514                       ntfs       
/dev/sda6        46383ce0-8048-493f-a02b-cf735f25e087   ext4       
/dev/sda7        fbb6d681-c518-4eb0-9890-ca2f2a9a43b6   ext4       
/dev/sda8        df7c7d3b-a86d-486e-8cfb-8487566e58ad   ext4       
/dev/sda9        9fc11554-ab75-4335-a30c-93c9702552b3   swap       
/dev/sdb1        49A4-13CA                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root fbb6d681-c518-4eb0-9890-ca2f2a9a43b6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root fbb6d681-c518-4eb0-9890-ca2f2a9a43b6
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root fbb6d681-c518-4eb0-9890-ca2f2a9a43b6
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=fbb6d681-c518-4eb0-9890-ca2f2a9a43b6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root fbb6d681-c518-4eb0-9890-ca2f2a9a43b6
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=fbb6d681-c518-4eb0-9890-ca2f2a9a43b6 ro recovery nomodeset 
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root fbb6d681-c518-4eb0-9890-ca2f2a9a43b6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root fbb6d681-c518-4eb0-9890-ca2f2a9a43b6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 925E68275E680677
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=fbb6d681-c518-4eb0-9890-ca2f2a9a43b6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=46383ce0-8048-493f-a02b-cf735f25e087 /home           ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=9fc11554-ab75-4335-a30c-93c9702552b3 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 586.505111694 = 629.755068416  boot/grub/core.img                             1
 586.505119324 = 629.755076608  boot/grub/grub.cfg                             1
 585.683799744 = 628.873191424  boot/initrd.img-3.0.0-12-generic               2
 590.461338043 = 634.003034112  boot/vmlinuz-3.0.0-12-generic                  1
 585.683799744 = 628.873191424  initrd.img                                     2
 590.461338043 = 634.003034112  vmlinuz                                        1

============================= sda8/grub/grub.cfg: ==============================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set aa717fbb-6e41-4a33-8f98-731e6ef64ca0
if loadfont /usr/share/grub/ascii.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set df7c7d3b-a86d-486e-8cfb-8487566e58ad
    linux    /vmlinuz-2.6.35-22-generic root=UUID=aa717fbb-6e41-4a33-8f98-731e6ef64ca0 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set df7c7d3b-a86d-486e-8cfb-8487566e58ad
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=aa717fbb-6e41-4a33-8f98-731e6ef64ca0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set df7c7d3b-a86d-486e-8cfb-8487566e58ad
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set df7c7d3b-a86d-486e-8cfb-8487566e58ad
    linux16    /memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 593.859283447 = 637.651550208  grub/core.img                                  1
 593.861331940 = 637.653749760  grub/grub.cfg                                  1
 593.859260559 = 637.651525632  initrd.img-2.6.35-22-generic                   1
 593.843387604 = 637.634482176  vmlinuz-2.6.35-22-generic                      1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  a2 ba 44 56 63 23 e7 e8  b9 d5 28 c9 91 b4 33 43  |..DVc#....(...3C|
00000010  ba 1c 5e e5 56 cb 6a bb  21 f7 74 ac 23 4d bc 94  |..^.V.j.!.t.#M..|
00000020  a4 92 a6 9f 92 75 a6 05  f5 95 7e a6 ea bc 9b a6  |.....u....~.....|
00000030  53 65 87 5c 3f 4e ea a8  8d 89 15 d4 ea 93 45 6c  |Se.\?N........El|
00000040  83 5d a7 73 4a 26 27 0a  ae b1 ae 5a a6 99 26 6e  |.].sJ&'....Z..&n|
00000050  ba d2 39 82 5b 46 97 64  d1 2c b0 e0 49 d4 59 f5  |..9.[F.d.,..I.Y.|
00000060  06 4e 47 07 99 d8 59 cf  b2 07 12 70 fa 54 e8 11  |.NG...Y....p.T..|
00000070  ad cc cf 4c ca 65 ab 7a  b3 4b 95 d9 d6 78 20 9b  |...L.e.z.K...x .|
00000080  3c 4d c3 d7 64 3b 29 22  10 4c c5 f1 6d 43 4b 11  |<M..d;)".L..mCK.|
00000090  09 2e 21 ed f1 da 6d 40  6b f2 5e 72 67 0f da 4d  |..!...m@k.^rg..M|
000000a0  82 d3 31 77 20 c6 9e c2  7b 0e ed 04 3b 77 43 cf  |..1w ...{...;wC.|
000000b0  50 a9 20 42 6c c8 86 8e  ce 42 42 ec 71 7a ec 6b  |P. Bl....BB.qz.k|
000000c0  02 b4 99 08 3a 38 dd 05  24 71 da f7 1d 5e 08 10  |....:8..$q...^..|
000000d0  e6 b1 17 d5 07 92 ab 3c  52 95 51 d8 88 f1 b3 8c  |.......<R.Q.....|
000000e0  44 9a 81 97 84 13 9e cd  e6 8e cc 92 31 30 a1 ab  |D...........10..|
000000f0  25 b1 43 aa e6 02 c4 25  b1 26 5b 8e d0 fc b5 c4  |%.C....%.&[.....|
00000100  12 4b af 77 b5 98 4a 36  1e 45 ce 95 51 bc 47 e2  |.K.w..J6.E..Q.G.|
00000110  58 45 8d 6d 51 d4 8a cc  ab 45 9f 5e 2b bc b9 72  |XE.mQ....E.^+..r|
00000120  90 74 73 94 91 68 22 88  d9 60 33 24 a2 6a 6a 3c  |.ts..h"..`3$.jj<|
00000130  9c d0 38 89 31 7a d4 93  48 fb 2e 75 d6 aa 49 46  |..8.1z..H..u..IF|
00000140  82 be d2 d7 b4 a8 fd bd  48 9d 4d 26 06 06 3b 42  |........H.M&..;B|
00000150  b4 31 12 b6 22 56 ed 21  e2 8e 25 86 b1 12 32 a9  |.1.."V.!..%...2.|
00000160  a1 e9 45 14 ac 3b 1a d5  28 06 0b 47 39 db 89 65  |..E..;..(..G9..e|
00000170  12 0d c7 13 59 ff fd b0  00 89 65 67 56 67 66 66  |....Y.....egVgff|
00000180  54 55 45 45 92 44 ca 48  90 00 00 00 00 00 00 00  |TUEE.D.H........|
00000190  0a aa a2 aa aa a2 ea aa  aa 51 45 d7 85 da 24 a6  |.........QE...$.|
000001a0  ca 63 92 2a 28 a2 8a a8  aa 8b 31 b2 9a ec b2 ba  |.c.*(.....1.....|
000001b0  ec ae fc 6c b6 aa ad ce  75 0b f0 6a 51 a7 00 fe  |...l....u..jQ...|
000001c0  ff ff 07 fe ff ff 02 00  00 00 01 f0 bf 12 00 fe  |................|
000001d0  ff ff 05 fe ff ff 48 f2  89 2d 3d f0 bf 12 00 00  |......H..-=.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by drs305 on 2012-01-14
ray13z,

Thanks for posting your attempts to solve this. Without them, it would tend to point toward a BIOS limitation. What you have found should rule that out.

Your sda7 files all look correct. However, your sda8 Grub files point to UUID *aa717fbb-6e41-4a33-8f98-731e6ef64ca0* which no longer appears to exist. I suspect that this might be part of the problem.

The first thing I'd try is the Boot Repair tool since it can analyze things and may find something completely different that needs fixing. Generally it does a very good job of correcting Grub problems. There is a link to it in my signature line.

The initial lines of the RESULTS.txt don't show which partition Grub is looking for. You will notice the partition is missing in the "is looking for" sentence in the first section, so we can't be sure it's looking at sda7.

I'm not sure why manually loading the modules didn't work for you, assuming the correct modules are installed in /boot/grub. Sometimes I find using the format "insmod (hd0,7)/boot/grub/linux.mod" works when a shorter command doesn't.

If Grub is still 'confused' about sda7 / sda8, you could try reinstalling Grub to make sure the MBR is pointing to the sda7 installation. Use an 11.10 LiveCD and boot to the Desktop, then:```

sudo mount /dev/sda7 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```
That should ensure that the MBR points to sda7's Grub files.

If you get it to boot normally, don't forget to run "sudo update-grub" to ensure the grub.cfg file is updated.

---

### Post by ray13z on 2012-01-14
Hey, thanks for the quick reply.

Ok so here's what all I tried from your post and in this order:

1. Booted up a Live CD and ran ```
sudo mount /dev/sda7 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```
It completed successfully. However on reboot same 'error: hd0 out of disk.' message with the grub rescue>

2. At Grub rescue I used the long form of insmod as you stated, but that gave the same response as the insmod linux.

3. Tried Boot-repair. It did a lot of stuff for quite a while. Then rebooted, I was super happy to find my grub 2 menu again but sadly on clicking 'Ubuntu, with 3.0.0-12-generic' I get the following message after about 2 minutes of a blank purple screen: error: couldn't read file
error: you need to load the kernel first.

So at the grub prompt I tried to boot the system, and the insmod command runs successfully. However I hit a bump at 'linux /vmlinuz root=/dev/sdXY ro' with the following error: couldn't read file.

My Boot-repair pastebin URL is [here]("http://paste.ubuntu.com/804034/").

Any ideas?

(Also, Windows boots perfectly from Grub2 menu)

---

### Post by drs305 on 2012-01-14
> **ray13z said:**
> 
So at the grub prompt I tried to boot the system, and the insmod command runs successfully. However I hit a bump at 'linux /vmlinuz root=/dev/sdXY ro' with the following error: couldn't read file.
Any ideas?


I'll assume you used "linux /vmlinuz root=/dev/sda7 ro" in the above?

Since the system doesn't seem to be able to read/load the system, the remaining solution that might work would be to reinstall the kernel. You would do this from the LiveCD and the chroot procedure.

Mount sda7 and chroot using the procedures in the 'chroot' link in my signature line (or other guide of your choice). You don't need to follow the commands to purge/reinstall Grub (at least I wouldn't until the following attempt failed).

Once into the 'chroot', you could try:
```
apt-get update
apt-get install --reinstall linux-image
```
While the second command runs, make sure it regenerates the initrd image. If it doesn't, I'd also run this command:
```
update-initramfs -k all -u
update-grub
```

The only other thing you might do while sda7 is still mounted is manually edit the grub.cfg file and remove the 'search' line entirely and change the root reference in the linux line to *root=/dev/sda7*.

---

### Post by ray13z on 2012-01-14
> **drs305 said:**
> 
Once into the 'chroot', you could try:
```
apt-get update
```

I got an error right here: ```
root@ubuntu:/# apt-get update
E: Opening configuration file /etc/apt/apt.conf.d/01autoremove - ifstream::ifstream (5: Input/output error)

```I had seen this I/O error earlier too. Can't recollect when! Mostly while trying to re-install grub from the LiveCD during earlier attempts. 

Could my HDD itself have a problem? Dell Diagnostics seems to say so. Is there any script/app that could confirm/reject an HDD problem?

---

### Post by ray13z on 2012-01-15
> **drs305 said:**
> Your sda7 files all look correct. However, your sda8 Grub files point to UUID *aa717fbb-6e41-4a33-8f98-731e6ef64ca0* which no longer appears to exist. I suspect that this might be part of the problem.


Turns out this was the problem. This was an old /boot partition that my dad used to use. Since there's only one distro, I only needed a / and a /home. I expected Grub to handle that but for some reason my partitions weren't going down well with it (I still can't figure out why!)

Deleted the old /boot and tried. Still 'out of disk'. Then I deleted all the linux partitions including the swap and tried again. 

I finally have a working 11.10 now. But it really irritates me that the earlier partitions weren't holding. In fact, been doing the same thing (only formatting my /) for years. This is the first time it failed.

---

### Post by Kkweit on 2012-04-11
Hi,

I have the same out of disk error with a grub rescue prompt.
here is the result of the of the bootinfo script

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   155,205,631   155,203,584  83 Linux
/dev/sda2         155,207,678   160,835,583     5,627,906   5 Extended
/dev/sda5         155,207,680   160,835,583     5,627,904  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5350d6db-466e-4f84-a8dd-90043b108be4   ext4       
/dev/sda5        769796c5-d571-4326-ae9f-e8deb8196217   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5350d6db-466e-4f84-a8dd-90043b108be4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=769796c5-d571-4326-ae9f-e8deb8196217 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------




```

in the grub rescue prompt when i run the following command:
```

ls (hd0,5)/boot 

```
it returns me 
```

error: hd0,1 out of disk.

```

Ubuntu was working fine on this computer. I got this problem since since a reboot and don't know how to fix it.

Does anybody have a clue ?

---

### Post by drs305 on 2012-04-11
> **Kkweit said:**
> Hi,

I have the same out of disk error with a grub rescue prompt.
here is the result of the of the bootinfo script

in the grub rescue prompt when i run the following command:
```

ls (hd0,5)/boot 

```
it returns me 
```

error: hd0,1 out of disk.

```

Ubuntu was working fine on this computer. I got this problem since since a reboot and don't know how to fix it.

Does anybody have a clue ?

Your command lists hd0,5 but the return mentions hd0,1. I'll assume you actually were checking hd0,1...

An out of disk error sometimes means there is a BIOS limitation which prevents the BIOS from seeing the entire drive. The most common limit is 137GB for older BIOS's. 

The system could run fine for a long time, but an update could move critical Grub or boot files outside the first 137GB of the drive and Grub can't find them.

Only part of the boot info script was posted so we are missing some of the results which might help pinpoint the problem.

*If it is a BIOS limitation*, you may have a setting for LBA or large drives you can update in BIOS. You could also try updating your BIOS (if it is older) or shrink the Ubuntu partition to about 130 GB to ensure the boot files remain where the BIOS can see them. You could also create a separate /boot partition early in the disk. (Shrinking would be easiest, but backup critical files first).

By the way, Maverick has reached it's End of Life and will no longer get security updates. You might want to consider upgrading to 11.04 or to 12.04 when it comes out in a few weeks.

---

### Post by oldfred on 2012-04-11
@Kkweit
Welcome to the forums.

You install does not look complete. You do have grub2's boot loader installed to the MBR, but no grub.cfg in the / partition. Script also does not show the kernel(s). Did you cut it off script listing, or were they not found also.

While it may be possible to chroot into your system and repair, if it is a new install with nothing to salvage a new install may be easier.

---

### Post by Kkweit on 2012-04-11
@drs305 & oldfred: Thanks both of you for your response.

I didn't cut the result of the boot info script. It sur^prise me too i did run it two times but that's the only result i get.

I will check the bios configuration.

Just in case do you have for shrinking ubuntu's partition.

for now a new install is the last option that i would like to consider so if could help me fix my problem it would be great

---

### Post by drs305 on 2012-04-11
You may need only to reinstall Grub if the rest of your system files are intact.

You can do this from a LiveCD using the 'chroot' procedure. It's described here:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by oldfred on 2012-04-11
drs305 has posted instructions on grub uninstall & reinstall. 

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You should also run these while chrooted to make sure you have all the updates and a kernel.
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
sudo apt-get install linux-image
sudo update-grub

It almost looks like you had a /boot partition with the grub.cfg & kernels and it now is missing?

---

### Post by Kkweit on 2012-04-12
Hi,

I checked my BIOS configuration and I do have LBA setting enabled.

I was about to use the chroot procedure from a liveCD but in order to be sure that my /boot partition is in different partition than linux i did run a fdisk -l from the LiveCD.

it returns me:
```

ubuntu@ubuntu:~S sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c0996

   Device  Boot  Start      End      Blocks  Id   System
**/dev/sda1    *       1     9662    77601792  83   Linux**
/dev/sda2         9662    10012     2813953   5   Extended
/dev/sda5         9662    10012     2813952  82   Linux swap / Solaris
ubuntu@ubuntu:~S

```
which means that i don't have a separate /boot partition.

On the grub rescue prompt when i run:
```

ls (hd0,1)/

```
I can see the /boot directory but impossible to see what's in it. 
It returns an error when i try to as i said previously.

Do you have any clue of what i could do or test ?

---

### Post by drs305 on 2012-04-12
> **Kkweit said:**
> Hi,

I checked my BIOS configuration and I do have LBA setting enabled.

I was about to use the chroot procedure from a liveCD but in order to be sure that my /boot partition is in different partition than linux i did run a fdisk -l from the LiveCD.

it returns me:
```

ubuntu@ubuntu:~S sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c0996

   Device  Boot  Start      End      Blocks  Id   System
**/dev/sda1    *       1     9662    77601792  83   Linux**
/dev/sda2         9662    10012     2813953   5   Extended
/dev/sda5         9662    10012     2813952  82   Linux swap / Solaris
ubuntu@ubuntu:~S

```
which means that i don't have a separate /boot partition.

On the grub rescue prompt when i run:
```

ls (hd0,1)/

```
I can see the /boot directory but impossible to see what's in it. 
It returns an error when i try to as i said previously.

Do you have any clue of what i could do or test ?

We still don't have a clear picture of what happened, but with the limited amount of information we do have I would agree with the possibility proposed by *oldfred*

There is a good chance your /boot directory was deleted, moved, or corrupted. Using "ls (hd0,1)/boot" should display the kernel and initrd files, and if they are missing your system isn't going to boot.

I suggest booting a LiveCD (make sure it's the same version as you installed), chrooting into your sda1 partitition, and then install the kernel and grub-pc. Installing the kernel should rebuild your /boot folder, and installing grub-pc should put the correct files into /boot/grub.

All the commands you need are in the chroot link and, for installing the kernel, in *oldfred's* post.

---

### Post by Kkweit on 2012-04-16
Hi,

Since i can't have an internet connection on that machine i'm looking for a way to re-install the kernel

---

### Post by Kkweit on 2012-04-16
Hi,

Using ubuntu server liveCD trying chroot failed.
it returns me /bin/sh: chroot: Input/output error.
Same error message when i run "upgrade-grub2".

It's starting driving me crazy. If you could help me it would me great. From the liveCD i can see the /boot and /proc directory but can't see what's in it seems like they are corrupt since i can see what's in other directory.
Isn't there a way to download manually all the necessary package (from another computer since i can't get a internet connection on this one) and install all of them to make this server running fine ?

---

### Post by oldfred on 2012-04-16
If it is a server CD it is not a liveCD, but just an installer CD. Do not know if that works or not. 
Also the normal instructions for chroot are for typical desktops, again not sure which (if any) other system partitions if separate partitions may have to be also mounted to get an update to run.

From synaptic you can set CD as source for updates, but I do not know how to do that from command line for a server. I assumed it is some editing of the sources file to be CD.

Some info on sources:
Best command to reset apt sources to distro release defaults?
[http://ubuntuforums.org/showthread.php?t=1858451](http://ubuntuforums.org/showthread.php?t=1858451)

Offline Updates:
[http://keryxproject.org/](http://keryxproject.org/)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)
Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

Before changing sources:
cp /etc/apt/sources.list ~/sources.list.backup

---

### Post by Corpel on 2012-04-27
I installed ubuntu 12.04 yesterday and this morning it took me several attempts before I can boot.
 I could read this; error: out of disk. grub rescue>
 I read everything written here and then I reinstalled grub2 with the terminal.
 Problem solved.

 Amazing all the help we find for linux.
 Incidentally, I am with linux for only about 3 weeks but my main pc is still with windows for now.

 Linux, how beautiful discovery.

 Thank you all for your help and good luck to kkweit.

---

### Post by tilt2kngiht on 2012-05-11
Hi I came to this forum with the same problem and read the reboot idea. I tried to open the cd tray to put the boot disk in and the whole unit came out. I then put it back without the CD, taped the power button and it restarted with no issues. So it may be a loose CD USB drive.

---

### Post by vidmantasdd on 2012-06-11
hi,
I had same problem,and sorted out with next way:
booted from  ubuntu live usb(cd) , go to places-computer-file system and find file /boot/grub/menu.lst open file menu.lst and copy everything.
Next- go to your drive where is your not working ubuntu , and look in /boot/grub/menu.lst 
on my computer,this file was missing,so with sudo gedit in terminal, i opened new text editor, pasted copy of /boot/grub/menu.lst from live usb and saved file in /boot/grub/  where is not working ubuntu. And reboot computer.
And - my crashed Ubuntu working normal now :)
As well, make sure you got same ubuntu system on live usb ( for example,my was ubuntu 10.04 64bit on hdd and same on live usb)
Let me know ,if it works for you:)
bye......

---

### Post by oldfred on 2012-06-11
Some old systems that have been update may still have grub legacy with menu.lst.

But Since 9.10 grub2 has been the standard and it does not use menu.lst.

---

### Post by paccamura on 2012-07-23
Hi,

I just upgraded from 11.10 to 12.04 and I have the same problem:
error: out of disk
grub rescue 

using a live CD I tried some of the solution proposed here:
I followed this [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) but it didnt work.
I also tried to use Boot-repair but without success.

I m not expert at all, so maybe I have done something wrong... can somebody give me some tip

thanks for your help 

I got this
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00089d9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   612853759   306425856   83  Linux
/dev/sda2       612855806   625141759     6142977    5  Extended
/dev/sda5       612855808   625141759     6142976   82  Linux swap / Solaris


```

and 
```

Boot Info Script 0.61      [1 April 2012]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 

Finished. The results are in the file "mario"
located in "/home/ubuntu/".

```

```

 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   612,853,759   612,851,712  83 Linux
/dev/sda2         612,855,806   625,141,759    12,285,954   5 Extended
/dev/sda5         612,855,808   625,141,759    12,285,952  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        10f46005-5d95-4cda-8807-54282693b1df   ext4       
/dev/sda5        8b644e91-7e61-44f1-ad97-3b88bc4fdce7   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/10f46005-5d95-4cda-8807-54282693b1df ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 10f46005-5d95-4cda-8807-54282693b1df
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 10f46005-5d95-4cda-8807-54282693b1df
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
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 3.2.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 10f46005-5d95-4cda-8807-54282693b1df
    linux    /boot/vmlinuz-3.2.0-26-generic root=UUID=10f46005-5d95-4cda-8807-54282693b1df ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 10f46005-5d95-4cda-8807-54282693b1df
    echo    'Loading Linux 3.2.0-26-generic ...'
    linux    /boot/vmlinuz-3.2.0-26-generic root=UUID=10f46005-5d95-4cda-8807-54282693b1df ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-26-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 10f46005-5d95-4cda-8807-54282693b1df
    linux    /boot/vmlinuz-3.0.0-23-generic root=UUID=10f46005-5d95-4cda-8807-54282693b1df ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.0.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 10f46005-5d95-4cda-8807-54282693b1df
    echo    'Loading Linux 3.0.0-23-generic ...'
    linux    /boot/vmlinuz-3.0.0-23-generic root=UUID=10f46005-5d95-4cda-8807-54282693b1df ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 10f46005-5d95-4cda-8807-54282693b1df
    linux    /boot/vmlinuz-2.6.38-15-generic root=UUID=10f46005-5d95-4cda-8807-54282693b1df ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-2.6.38-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 10f46005-5d95-4cda-8807-54282693b1df
    echo    'Loading Linux 2.6.38-15-generic ...'
    linux    /boot/vmlinuz-2.6.38-15-generic root=UUID=10f46005-5d95-4cda-8807-54282693b1df ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-15-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 10f46005-5d95-4cda-8807-54282693b1df
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 10f46005-5d95-4cda-8807-54282693b1df
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
# Commented out by Dropbox
# UUID=10f46005-5d95-4cda-8807-54282693b1df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8b644e91-7e61-44f1-ad97-3b88bc4fdce7 none            swap    sw              0       0
UUID=10f46005-5d95-4cda-8807-54282693b1df / ext4 errors=remount-ro,user_xattr 0 1
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-15-generic              2
               =                boot/initrd.img-3.0.0-23-generic               2
               =                boot/initrd.img-3.2.0-26-generic               3
               =                boot/vmlinuz-2.6.38-15-generic                 1
               =                boot/vmlinuz-3.0.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-26-generic                  1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


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

```

---

### Post by drs305 on 2012-07-23
paccamura,

At the grub rescue prompt, if you run the folloiwng commands do you get the results after the # symbol:

```
ls (hd0,1)/  # vmlinuz and initrd.img
ls (hd0,1)/boot # the kernel and initrd.img with versions
ls (hd0,1)/boot/grub # Lots of mod files
```

If GRUB cannot see all those files, your BIOS may be limited to viewing only the first part of the drive. Let us know and we can tell you how to proceed. Or review this site for more information:
[https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk]("https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk")

---

### Post by paccamura on 2012-07-25
> **drs305 said:**
> paccamura,

At the grub rescue prompt, if you run the folloiwng commands do you get the results after the # symbol:

```
ls (hd0,1)/  # vmlinuz and initrd.img
ls (hd0,1)/boot # the kernel and initrd.img with versions
ls (hd0,1)/boot/grub # Lots of mod files
```

If GRUB cannot see all those files, your BIOS may be limited to viewing only the first part of the drive. Let us know and we can tell you how to proceed. Or review this site for more information:
[https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk]("https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk")


Hi,

I followed the instructions in the link. the problem was solved creating a boot partition.
thank you very much!

---

### Post by mkhuda on 2012-08-21
> **sameer.walgude said:**
> Try this at grub rescue> prompt....

grub rescue> set prefix=(hd0,x)/boot/grub
grub rescue> insmod (hd0,x)/boot/grub/normal.mod
rescue:grub> normal

(here x represents the partition number where ubuntu is installed...)
(try ls at prompt to know your existing partitions...)

If still fails...boot up live cd...

at terminal...
sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub /dev/sda

substitute /media/{kubuntu9.10partition} with actual partition :)

If you get error message,(mapping fails), do this..

sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub -m 
/media/{kubuntu9.10partition}/boot/grub/device.map /dev/sda

All the best!


its worked for me 
thanks ! =)

---

### Post by ookooboontoo on 2012-09-02
Just a quick note to this thread, I was facing the same dilemna as those others above however I had changed my RAM about a bit and although back in its original place, I must have not returned it exactly. I have had 24 hours of the grub rescue prompt only to fin that prior to switching on I toook out and put back the same RAM again and this time it booted fine.
My suggestion if other things fail, try a memory test if you can :)

A

---

### Post by lokihound on 2012-09-04
> **drs305 said:**
> paccamura,

At the grub rescue prompt, if you run the folloiwng commands do you get the results after the # symbol:

```
ls (hd0,1)/  # vmlinuz and initrd.img
ls (hd0,1)/boot # the kernel and initrd.img with versions
ls (hd0,1)/boot/grub # Lots of mod files
```

If GRUB cannot see all those files, your BIOS may be limited to viewing only the first part of the drive. Let us know and we can tell you how to proceed. Or review this site for more information:
[https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk]("https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk")



I am also getting the same "out of disk" error.  I entered the above commands and for the first, get a bunch of sub-directories - /., /.., /boot, etc.

On both the second and third commands I just "get out of disk". So it's not able to find them.

I just installed Ubuntu on an old Toshiba Sattelite with a brand new hard drive.  I heard somewhere that it was finnicky about larger hard drives, but I got the replacement from Toshiba itself as the recommended replacement (320G).  

So should I follow the suggestions about making a small separate boot partition?  I have no experience yet with Linux, but have partitioned drives - and could follow the directions from the above link...

---

### Post by drs305 on 2012-09-04
> **lokihound said:**
> I am also getting the same "out of disk" error.  I entered the above commands and for the first, get a bunch of sub-directories - /., /.., /boot, etc.

On both the second and third commands I just "get out of disk". So it's not able to find them.

I just installed Ubuntu on an old Toshiba Sattelite with a brand new hard drive.  I heard somewhere that it was finnicky about larger hard drives, but I got the replacement from Toshiba itself as the recommended replacement (320G).  

So should I follow the suggestions about making a small separate boot partition?  I have no experience yet with Linux, but have partitioned drives - and could follow the directions from the above link...

Yes, a separate /boot partition may help. Even though the drive may be a recommended replacement, it's the BIOS that has the limitation. Before you make a separate /boot partition, you might check to see if there is an update to your BIOS. Since you bought the hard drive from Toshiba, I would think their tech support might be able to assist you in determining if your current BIOS can support the new drive, and if not, how to proceed.

---

### Post by lokihound on 2012-09-05
I have the BIOS updated to the latest, but it's still a 2001 version!  I was running Windows 2000 on the machine before and it worked fine.  I am not sure it's the new drive, or just an old machine that is the problem.  I thought Linux was supposed to be easy!

However, I am having a hard time booting to the "Try Ubuntu" part.  It goes past a certain amount, then seems to get lost - it keeps accessing the CD, and the screen goes from blank, to blank with a cursor, to a sort of graphical interface - with a bar at the top, with a cursor.  I've left it go for more than an hour, then canceled it.  I'm trying again now, but it's doing it again.

Am I lost here?

I have Acronis Disk Director and can partition there on my Windows Machine via a USB to the disk... Then reinstall.  Not sure that would help?

---

### Post by drs305 on 2012-09-05
lokihound,

As far as the trouble you are having booting from the CD, it may be a video driver issue. There are options you can invoke as the CD boots which can help if that is the problem. 

Here is the Ubuntu community documentation:
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")
I'd start with the 'nomodeset' option.

---

### Post by lokihound on 2012-09-05
> **lokihound said:**
> I have the BIOS updated to the latest, but it's still a 2001 version!  I was running Windows 2000 on the machine before and it worked fine.  I am not sure it's the new drive, or just an old machine that is the problem.  I thought Linux was supposed to be easy!

However, I am having a hard time booting to the "Try Ubuntu" part.  It goes past a certain amount, then seems to get lost - it keeps accessing the CD, and the screen goes from blank, to blank with a cursor, to a sort of graphical interface - with a bar at the top, with a cursor.  I've left it go for more than an hour, then canceled it.  I'm trying again now, but it's doing it again.

Am I lost here?

I have Acronis Disk Director and can partition there on my Windows Machine via a USB to the disk... Then reinstall.  Not sure that would help?

I fixed it.  I pre-partitioned the disk to have a 1 gig primary with Acronis Boot disk - though this may not be necessary - though removing the partitions that already existed may have been helpful with the rest.  Then I reinstalled - this time with XUbuntu because it seemed to be smaller (though I don't think that is true).  

Worked through the partition part of the install, and figured out how to put the boot part in the small partition, and the rest in the second partition.  Put in a third just for good measure, and added a swap as well.  

Boots up - seemingly fine.

Could use a little more info on the partitioning manual stuff - it was pretty hard to figure out - even though I've done many other OS partitioning. I gathered some info from the info about repartitioning in the above link (but could not boot the CD - or just was not patient to wait for the boot - if it takes as long as the install - I had not waited long enough!

Now I just have to figure out the network stuff.  Isn't seeing my wireless network - though I don't even know how to start this!  First is to see if my main computer sees it and that it's still working and putting out a signal, as I don't use the wireless that much.  Once I have that and can connect to the internet on the Linux machine I'll be set!

---

### Post by lokihound on 2012-09-05
> **drs305 said:**
> lokihound,

As far as the trouble you are having booting from the CD, it may be a video driver issue. There are options you can invoke as the CD boots which can help if that is the problem. 

Here is the Ubuntu community documentation:
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")
I'd start with the 'nomodeset' option.

Not sure on this one.  I WAS able to see some things - pretty well actually, then it would go and get more things off the CD... It was never really locked, just seemingly really slow. I may just not have been patient.  Though if it does take this long (more than 30 minutes) to boot, it would not be a good option for emergencies.

---

### Post by drs305 on 2012-09-05
> **lokihound said:**
> Not sure on this one.  I WAS able to see some things - pretty well actually, then it would go and get more things off the CD... It was never really locked, just seemingly really slow. I may just not have been patient.  Though if it does take this long (more than 30 minutes) to boot, it would not be a good option for emergencies.

If you are seeing the complete desktop (eventually) then it's not the video driver. On one of my older machines, it takes about 10 minutes to boot to the Desktop.

It's possible to boot the ISO directly from a hard drive if you have GRUB installed and make some modifications. You could also try making a bootable USB to see if that boots more quickly.

---

