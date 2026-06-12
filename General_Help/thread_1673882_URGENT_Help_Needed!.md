---
title: "URGENT Help Needed!"
date: 2011-01-23
forum: General Help
---

### Post by rcfreak339 on 2011-01-23
Hello all! Tonight for the first time I tried to use Linux (Ubuntu). I installed it on to a small 100gb external HDD that I had just laying around. I thought I could do this without impacting my internal hard drive. I thought I could run Windows 7 normally when it wasn't plugged in and chose between Windows 7 or Ubuntu when it was. I installed it correctly (or atleast I thought). It worked fine but I then noticed I could only boot into Ubuntu or Windows 7 when it was plugged in. Having a laptop and going everywhere with it I could not tolerate it. When I tried to boot the system without the External HDD plugged in I would always get a "GRUB Rescue-No such Device" error and a white command line.

Confused I looked up how to uninstall Ubuntu, I got a windows recovery disc and deleted the partion off the External HDD. I then changed the BIOS settings so the CD would be booted first, well for whatever reason I get the same GRUB Error. It seems like I cannot boot into any CD Rom. Neither a recovery disc nor a Live CD. I got so frustrated I tried to system restore but it appears like the key command for that is also not working...so now I'm stuck.

I can't boot into anything and I'm stuck with the same Grub error. Im so confused and frustrated...I'm thinking about taking It to a pro and paying them to get it fixed or just calling it quits. I have no idea what I can do if Ibcan't boot from any CDs or any OSs....

Any help? I have no knowledge of the Ubuntu lingo...so don't confuse me!

Thanks!

---

### Post by Quackers on 2011-01-23
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by rcfreak339 on 2011-01-23
There's a problem...I can't boot with a CD, I've tried for hours.

---

### Post by Quackers on 2011-01-23
You're going to need to boot from a cd to fix the mbr of the drive.
What is happening when you try?
Have you tried resetting the bios to default settings and starting again? Sometimes bioses can trip themselves up.

---

### Post by rcfreak339 on 2011-01-23
What exactly is a Ubuntu Live CD?

---

### Post by Sylos on 2011-01-23
THe Live CD is the installation CD - but it is "LIVE" as it allows booting from the CD without installation - running from the RAM rather than a HDD. Usually the CD you download to install will be live and will give you the option to "Try without installing" amongst other options when booting. This is what you want to use.

It sounds from your original post that the GRUB boot loader has installed onto the external drive - hence why you can only boot into either OS when that drive is plugged in. I think Quackers knows more than me about this but the first step is definitely to try the boot info script he mentioned and see what it looks like.

---

### Post by rcfreak339 on 2011-01-23
It simply will not do a thing. Correct BIOS settings and everything...is there a setting I'm forgetting about? Everytime I try to boot from a CD I get the same exact GRUB error. I can press F12 to select be there isn't  a CD option. 

Is my computer screwed if I can't boot from a CD?

Also, I CAN'T run anything on my external hard drive anymore. Since I went ahead and deleted the partions on it.

---

### Post by rcfreak339 on 2011-01-23
Anyone? I need to have this computer back fast!

---

### Post by Quackers on 2011-01-23
If your cd/dvd drive is not an option in your bios something is wrong. I don't even know why that might be, unless the actual drive is not being seen by the bios.

---

### Post by rcfreak339 on 2011-01-23
I give up! I've been at this for days and it's driving me up a wall! Once I get Windows 7 to work again I'm done with multiple OS's. I just want my system to work again and every possible solution I had is busted. Even my computer wont boot to a CD...it's screwed. I NEED this computer fixed incredibly bad and I have ZERO idea how to do it if I can't boot into anything. There's no way I screwed up this badly!

Please...help. If like to do a full system restore if I have to.

---

### Post by derklempner on 2011-01-23
I'd wager a guess that when you did the initial installation GRUB2 was installed on the MBR of your internal HD, not the external HD.  You may need to simply [_[COLOR="Red"]uninstall GRUB2[/COLOR]_]("https://help.ubuntu.com/community/Grub2#Uninstalling GRUB 2") to solve your problem.

---

### Post by rcfreak339 on 2011-01-23
> **Quackers said:**
> If your cd/dvd drive is not an option in your bios something is wrong. I don't even know why that might be, unless the actual drive is not being seen by the bios.

It IS an option in the BIOS, just not when I press the F12 key command.

This sucks.

---

### Post by rcfreak339 on 2011-01-23
> **derklempner said:**
> I'd wager a guess that when you did the initial installation GRUB2 was installed on the MBR of your internal HD, not the external HD.  You may need to simply [_[COLOR="Red"]uninstall GRUB2[/COLOR]_]("https://help.ubuntu.com/community/Grub2#Uninstalling GRUB 2") to solve your problem.

I can't boot into a Live CD....this is my main problem. But that does sound correct.

---

### Post by derklempner on 2011-01-23
> **rcfreak339 said:**
> I can't boot into a Live CD....this is my main problem. But that does sound correct.
If you can't boot from CD, then the problem is with your BIOS configuration.  Enter the BIOS config and change the boot order to boot from CD-ROM **before** booting from the hard drive.  If there isn't an option to boot from CD-ROM on your boot selection screen, then this would be the only way to make sure the computer boots from CD-ROM.

---

### Post by rcfreak339 on 2011-01-23
> **derklempner said:**
> If you can't boot from CD, then the problem is with your BIOS configuration.  Enter the BIOS config and change the boot order to boot from CD-ROM **before** booting from the hard drive.  If there isn't an option to boot from CD-ROM on your boot selection screen, then this would be the only way to make sure the computer boots from CD-ROM.

I did just that and still nothing! I moved "USB CD-Rom" to the front of the boot order. 

I'm just amazed as to why this isn't working. I hate this.

---

### Post by crewkid89 on 2011-01-23
> **rcfreak339 said:**
> I did just that and still nothing! I moved "USB CD-Rom" to the front of the boot order. 

I'm just amazed as to why this isn't working. I hate this.

If you have the external usb drive plugged in when you do this, then it will probably boot from the usb drive.  Try booting from cd when the external is NOT plugged in.  I had this same problem with the 10.10 installer, I didn't notice that it was installing grub to my hackintosh drive and it ruined my os x install.  Make sure it installs grub to the external drive next time by using the manual partition tool in the installer.

---

### Post by derklempner on 2011-01-23
> **rcfreak339 said:**
> I did just that and still nothing! I moved "USB CD-Rom" to the front of the boot order. 

I'm just amazed as to why this isn't working. I hate this.
To be honest, it sounds like a hardware issue.  Try unplugging the USB CD-ROM and plugging it back in, or try plugging it in to a different USB port.  If you were able to boot from it before, then it's either died, it's not being noticed by the computer, or you need to change the boot order to try and boot from a USB device other than "USB CD-ROM".

Alternately, you could create a bootable USB flash drive with Ubuntu on it (on another computer, naturally) and boot from that instead.

---

### Post by Quackers on 2011-01-23
Are you using a usb cdrom? Or is it built-in?

---

### Post by rcfreak339 on 2011-01-23
> **Quackers said:**
> Are you using a usb cdrom? Or is it built-in?

I feel like an idiot...Im using a internal CD drive. Then I am wrong....I have no clue why my CD drive isnt showing up in the BIOS. Odd.

---

### Post by Quackers on 2011-01-23
We all make mistakes! It's easily done.
DId your cd drive work ok for playing cd's and dvd's the last time you used it?

---

### Post by rcfreak339 on 2011-01-23
> **Quackers said:**
> We all make mistakes! It's easily done.
DId your cd drive work ok for playing cd's and dvd's the last time you used it?

Yes, I have never had problems with it before...

I'm about to try and burn it onto a USB stick in a few to see if I can boot from that.

Thanks Quackers and everyone trying to help! Means a ton!

---

### Post by crewkid89 on 2011-01-23
if all else is failing you could also try to make a usb installer.  the program for it is built into ubuntu, or you can use unetbootin in windows.  you need a 1gb+ usb stick and an ubuntu .iso file.

---

### Post by Quackers on 2011-01-23
Ok, good luck with that.
It's sure strange about the cd drive though.

---

### Post by rcfreak339 on 2011-01-24
Success! Here you go!
> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

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
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855    25,382,699       208,845   7 HPFS/NTFS
/dev/sda3          25,382,700   488,395,119   463,012,420   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2045 MB, 2045771776 bytes
63 heads, 62 sectors/track, 1022 cylinders, total 3995648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             64     3,995,647     3,995,584   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        108C70D38C70B4B6                       ntfs       PQSERVICE                     
/dev/sda2        38C07170C071356A                       ntfs       SYSTEM RESERVED               
/dev/sda3        4E08727D0872643D                       ntfs       Acer                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B8CF-C7B1                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 01 00  |.X.SYSLINUX..@..|
00000010  02 00 02 00 00 f8 f4 00  3f 00 ff 00 40 00 00 00  |........?...@...|
00000020  c0 f7 3c 00 00 01 29 b1  c7 cf b8 4e 4f 20 4e 41  |..<...)....NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc f0 7b 8e d9 b8  00 20 8e c0 fc bd 00 7c  |....{.... .....||
00000050  38 4e 24 7d 24 8b c1 99  e8 3c fa fc 31 c9 8e d1  |8N$}$....<..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 09 02 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by rcfreak339 on 2011-01-24
Bump!

---

### Post by rcfreak339 on 2011-01-24
Sorry for bumping so much! I just need my Windows 7 back!

---

### Post by rcfreak339 on 2011-01-24
Hello?

---

### Post by rcfreak339 on 2011-01-24
Im thinking I just need to restore the MBR?

Do I just have to put in a Windows recovery disk and run the "fixmbr" command in the terminal?

---

### Post by Quackers on 2011-01-24
You appear to have installed via wubi, not in a separate partition, yes?
What is the problem?

---

### Post by rcfreak339 on 2011-01-24
Yes, I did.

The problem is still the same, I can't boot into Windows. I can only boot into Ubuntu on my flash drive. 

If  don't I get a GRUB error "No such device found".

---

### Post by Quackers on 2011-01-24
Ok, got you.
You now have Ubuntu installed "inside" Windows, but you have grub2 installed in the mbr of the drive, so it's trying to find files that aren't now there.
You need to boot from the Windows repair disc (or installation disc) and run the startup repair from the recovery console. It may need running more than once to reapir it.

---

### Post by rcfreak339 on 2011-01-24
^Okay thats what I thought, thanks Quackers.

Is that all I'll need to do?

I need to find a way to do that via USB flash drive, but I could probably find that out with some Google magic.

---

### Post by Quackers on 2011-01-24
I haven't done it, but one or two have, I believe.
Have a look through oldfred's posts for yesterday. He detailed how he made one.

---

### Post by Trublue on 2011-01-25
Make sure you do not have your external hdd plugged in when you try to boot as I find if I have my external hdd plugged in the pc goes no where. Have to boot then plug in.Also have found once that a usb flash drive did the same.

---

### Post by rcfreak339 on 2011-01-25
FIXED!! :D

I booted into a Windows recovery disk via flash drive, I then just went into Command Prompt and used the boot.exe/fixmbr and rebooted. Problem solved.

Pretty easy fix, it was figuring out why computer wouldn't boot into a CD.

Thanks to everyone!

---

### Post by Quackers on 2011-01-25
Excellent :-)  Enjoy!
You're welcome.

---

