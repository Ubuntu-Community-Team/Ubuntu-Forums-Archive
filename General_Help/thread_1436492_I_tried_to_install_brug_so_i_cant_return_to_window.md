---
title: "I tried to install brug so i cant return to windows 7 need help serious"
date: 2010-03-22
forum: General Help
---

### Post by ballot on 2010-03-22
hi guys i tried to install brug theme so i cant return to windows 7 which files should i paste here for able to you help me ?

when i click to windows 7 option in grub boot menu it just returns me "GRUB" and nothing help me please :( :( :( my father will kill me

---

### Post by blueridgedog on 2010-03-22
Can you elaborate more on what happened?  What worked before and what is broken now?  Could you boot into windows 7 and Ubuntu at one time?

What version of Ubuntu do you have?

---

### Post by howefield on 2010-03-22
> **ballot said:**
> hi guys i tried to install brug theme so i cant return to windows 7

Is this the alternative theme for Grub2 ?

Easiest way of fixing is probably to reinstall Grub2 using the directions here,...
 (this assumes that you are using Grub2, yes ?)

[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

It is easier than it sounds, have a read a that link, and if you have any questions, post back.

---

### Post by ballot on 2010-03-22
win7 and ubuntu was working fine before 

i was trying to install a theme by burg and it did happened so 

now i am accessing by live cd gurb has died as total :D it just says "GURB" and no menu i can see ow .. :(

please help me guys i beg you :(

---

### Post by blueridgedog on 2010-03-22
I agree that you should just reinstall grub while booted from the LiveCD.

Section 13 on this site goes over the process:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Read the process and post any questions you have in this thread and we will be glad to help you.

---

### Post by ballot on 2010-03-22
> **blueridgedog said:**
> I agree that you should just reinstall grub while booted from the LiveCD.

Section 13 on this site goes over the process:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Read the process and post any questions you have in this thread and we will be glad to help you.

ok i will check i cant beleive to there are still humans to help to others for humanity :p

---

### Post by ballot on 2010-03-22
> **ballot said:**
> ok i will check i cant beleive to there are still humans to help to others for humanity :p

[HTML]
ubuntu@ubuntu:~$ sudo su root
root@ubuntu:/home/ubuntu# sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69b83c25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       18552   148915516    7  HPFS/NTFS
/dev/sda3           18553       86700   547398810    7  HPFS/NTFS
/dev/sda4           86701      121601   280342282+   f  W95 Ext'd (LBA)
/dev/sda5           86701      116502   239376384    7  HPFS/NTFS
/dev/sda6          116503      121601    40957686   83  Linux
root@ubuntu:/home/ubuntu# sudo mount /dev/sda6 /mnt
mount: /dev/sda6 already mounted or /mnt busy
mount: according to mtab, /dev/sda6 is already mounted on /mnt
root@ubuntu:/home/ubuntu# sudo mount /dev/sda6 /mnt/boot
mount: /dev/sda6 already mounted or /mnt/boot busy
mount: according to mtab, /dev/sda6 is already mounted on /mnt/boot
root@ubuntu:/home/ubuntu# sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
root@ubuntu:/home/ubuntu# 
[/HTML]


can u check where i am wrong i think i could mount but couldnt reinstall

oww forget it and i did 
sudo umount /mnt
and im going to restart be here pls :(

---

### Post by howefield on 2010-03-22
> **ballot said:**
> Installation finished. No error reported.

Why do you think that ? It thinks everything went well.

Reboot and see what happens.

Edit:
See your edit now... good luck.

---

### Post by ballot on 2010-03-22
now i could back to my linux but when i try to return to windows 7 it says

GRUB Loading.
and returns to main menu 

if i can back to win7 i will donate to ubuntu :(

---

### Post by howefield on 2010-03-22
Try opening a terminal and type

```
sudo update-grub
```

Press enter, put in your password if asked. Let it do its stuff and try rebooting.

---

### Post by ballot on 2010-03-22
> **howefield said:**
> Try opening a terminal and type

```
sudo update-grub
```

Press enter, put in your password if asked. Let it do its stuff and try rebooting.

tontonq@Tontonq:~$ sudo su root
[sudo] password for tontonq: 
root@Tontonq:/home/tontonq# sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
root@Tontonq:/home/tontonq# 

im going to restart

---

### Post by ballot on 2010-03-22
> **ballot said:**
> tontonq@Tontonq:~$ sudo su root
[sudo] password for tontonq: 
root@Tontonq:/home/tontonq# sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
root@Tontonq:/home/tontonq# 

im going to restart


it restarts my pc when i choose win7 option  :(

---

### Post by howefield on 2010-03-22
> **ballot said:**
> tontonq

Ahaaa.. I refused your msn request a few minutes ago. Sorry about that, but you really should ask first.

---

### Post by ballot on 2010-03-22
> **howefield said:**
> Ahaaa.. I refused your msn request a few minutes ago. Sorry about that, but you really should ask first.

:( sorry can i add you please? may be u can help better and we dont waste forum

---

### Post by howefield on 2010-03-22
> **ballot said:**
> it restarts my pc when i choose win7 option  :(

Probably because Windows 7 isn't located on sda1 which is where it thinks it is.

What partition is Windows installed on ?

---

### Post by blueridgedog on 2010-03-22
> **howefield said:**
> Try opening a terminal and type

```
sudo update-grub
```

Press enter, put in your password if asked. Let it do its stuff and try rebooting.

Just to clarify...that is a terminal from the on-disk Ubuntu, not a LiveCD...

---

### Post by ballot on 2010-03-22
> **howefield said:**
> Probably because Windows 7 isn't located on sda1 which is where it thinks it is.

What partition is Windows installed on ?

### END /etc/grub.d/40_custom ###
root@Tontonq:/boot/grub# sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bayt
255 heads, 63 sectors/track, 121601 cylinders
Units = silindir of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69b83c25

   Ayg&#305;t Aç&#305;l&#305;&#351;    Ba&#351;lang&#305;ç     Biti&#351;  BlokSay&#305;s&#305; Kml Sistem
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
1. disk bölümü silindir s&#305;n&#305;r&#305;nda bitmiyor.
/dev/sda2              13       18552   148915516    7  HPFS/NTFS
/dev/sda3           18553       86700   547398810    7  HPFS/NTFS
/dev/sda4           86701      121601   280342282+   f  W95 Ext'd (LBA)
/dev/sda5           86701      116502   239376384    7  HPFS/NTFS
/dev/sda6          116503      121601    40957686   83  Linux
root@Tontonq:/boot/grub# ^C
root@Tontonq:/boot/grub# cd /dev/sda2/
bash: cd: /dev/sda2/: Not a directory
root@Tontonq:/boot/grub# ^C
root@Tontonq:/boot/grub# 


ahh i see my files in here :?

root@Tontonq:/media/B8FCF347FCF2FF06# ls
AppServ                    GamersFirst          Recovery
AppServ-Backup-2007-02-20  hiberfil.sys         $Recycle.Bin
ASUS.000                   Intel                RHDSetup.log
ASUS.SYS                   MSOCache             Server
ATI                        pagefile.sys         splash.idx
CMLoader.log               PerfLogs             System Volume Information
dfinstall.log              Persi0.sys           temp
Documents and Settings     ProgramData          Users
dvmexp                     Program Files        version
dvmexp.idx                 Program Files (x86)  Windows
Fraps                      RaidTool
root@Tontonq:/media/B8FCF347FCF2FF06#

---

### Post by ballot on 2010-03-22
no anyone will help me ? :(

---

### Post by andrewthomas on 2010-03-22
> **ballot said:**
> no anyone will help me ? :(
Post the output of this in your next reply.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ballot on 2010-03-22
> **andrewthomas said:**
> Post the output of this in your next reply.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


[http://pastebin.com/xJQVkQPr](http://pastebin.com/xJQVkQPr)

---

### Post by Mark Phelps on 2010-03-22
Your system is messed up big time -- probably from all the hacking that you've done to it.

Win7 installs by default to two partitions: (1) a boot partition (containing the boot loader files and recovery files), and (2) the OS partition containing everything else.

When GRUB2 runs its scripts, it looks for boot loaders -- and it found the one for Win7 in your sda1 volume, thus, it added a line for that to the menu.

But, in looking at what you posted, I noticed two problems: (1) the boot folder appears to be missing from sda1 -- not a good sign, and (2) /grldr IS in sda1.  But grldr is used by GRUB4DOS -- which is ONLY installed into an NTFS partition when you do a Wubi install.

AND, when you have a Wubi install, it is NOT using the standard GRUB -- and installing that will only hose up your machine -- which you've apparently done.

You can't repair the Win7 boot loader from Ubuntu; you have to use MS Windows utilities to do that.  So, if you want Win7 boot restored, you will need to boot from a Win7 Install DVD or a Win7 repair CD and run  Startup Repair three times.

If you don't have a Win7 Install DVD or a Win7 Repair CD, you can download and burn an ISO image of a repair CD from the following location:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

Once you get Win7 restored, we can deal later with restoring Ubuntu access.  But, stop installing GRUB!

---

### Post by ballot on 2010-03-22
> **Mark Phelps said:**
> Your system is messed up big time -- probably from all the hacking that you've done to it.

Win7 installs by default to two partitions: (1) a boot partition (containing the boot loader files and recovery files), and (2) the OS partition containing everything else.

When GRUB2 runs its scripts, it looks for boot loaders -- and it found the one for Win7 in your sda1 volume, thus, it added a line for that to the menu.

But, in looking at what you posted, I noticed two problems: (1) the boot folder appears to be missing from sda1 -- not a good sign, and (2) /grldr IS in sda1.  But grldr is used by GRUB4DOS -- which is ONLY installed into an NTFS partition when you do a Wubi install.

AND, when you have a Wubi install, it is NOT using the standard GRUB -- and installing that will only hose up your machine -- which you've apparently done.

You can't repair the Win7 boot loader from Ubuntu; you have to use MS Windows utilities to do that.  So, if you want Win7 boot restored, you will need to boot from a Win7 Install DVD or a Win7 repair CD and run  Startup Repair three times.

If you don't have a Win7 Install DVD or a Win7 Repair CD, you can download and burn an ISO image of a repair CD from the following location:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

Once you get Win7 restored, we can deal later with restoring Ubuntu access.  But, stop installing GRUB!

thank for your helps i pray to god for able to recover my windows xD

can u check these  screenshots too
[http://i39.tinypic.com/21157de.png](http://i39.tinypic.com/21157de.png)
[http://i44.tinypic.com/2s6pjcl.png](http://i44.tinypic.com/2s6pjcl.png)

---

### Post by ballot on 2010-03-23
i was having more fun while in ubuntu than trying to repair the pc by rescue disk it's loading takes 5-6 minutes than it says 


Windows has encountered a problem communicating with device connected yo your computer.

This error can be caused by unplugging a removable storage device such as an external USB drive while the device is in use, or by faulty hardware such as a hard drive or CD ROM diver that is failing. Make sure any removable storage is properly connected and then restart your computer.

If you continue to reciver this error message , contact the hardware manufacturer.

|Status : 0x00000e9
Info: an unexpected I/0 error has occured


and keeps retrying to load the cd and fails again :p

---

### Post by ballot on 2010-03-23
> **ballot said:**
> i was having more fun while in ubuntu than trying to repair the pc by rescue disk it's loading takes 5-6 minutes than it says 


Windows has encountered a problem communicating with device connected yo your computer.

This error can be caused by unplugging a removable storage device such as an external USB drive while the device is in use, or by faulty hardware such as a hard drive or CD ROM diver that is failing. Make sure any removable storage is properly connected and then restart your computer.

If you continue to reciver this error message , contact the hardware manufacturer.

|Status : 0x00000e9
Info: an unexpected I/0 error has occured


and keeps retrying to load the cd and fails again :p


is really ubuntu for humanity :S i think its more evil then the windows trojans 

root@Tontonq:/home/tontonq# sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@Tontonq:/home/tontonq# 


now it doesnt show my windows 7 too dont know what should i,i spend my 12 hours (00-12) just for nothing like a nobb wasted my pc

---

### Post by ballot on 2010-03-23
wont anyone help i still didnt sleep from last night

---

### Post by ballot on 2010-03-23
> **ballot said:**
> wont anyone help i still didnt sleep from last night

bump :(

---

### Post by Mark Phelps on 2010-03-23
I know you're frustrated, but posting 5-6 times in a row is NOT going to get you responses faster.  We're all volunteers here and most of us have other obligations that prevent us from being available 24 hours a day.  So, show some patience!!

Looking at your screenshots, it looks like you are running Win7 64-bit.  

So, did you download and burn the 64-bit Win7 Repair CD images like I suggested?

Did you then boot from that Repair CD and choose Startup Repair?

If so, what error messages did you get?

Also, running GRUB utilities in Ubuntu is NOT going to restore your Win7 boot.  Running the Startup Repair from the Repair CD is what is needed.

---

