---
title: "Black screen with blinking marker top-left-corner"
date: 2011-01-11
forum: General Help
---

### Post by Veltia on 2011-01-11
Recently, I installed Ubuntu in order to find out if it was something I liked. I followed instructions step-by-step and everything, made a 2GB USB stick for installing and mounted the ISO in Daemon Tools.

I liked it so much that I decided to not just use the trial version, but the full version, so last night I asked it to install the "real" ubuntu and using the chance to get it to delete all the old junk that I didn't need on the computer (I had taken a back-up of the things I need). :)

The first 5 steps in the install went perfect, however when the installing itself began, I headed to bed. When I woke up a few hours late the process bar hadn't moved at all, not even a pixel. I canceled the install procress and thought of the usual Windows (I used to use windows before deciding to switch) tip: Reboot. So I got the computer to reboot, and the USB remained in computer. :o

Next thing I know is that **after the Asus logo, the screen turns black with a marker (or underscore, you know: _ ) in the top left corner blinking**. Even waiting does nothing unless the waiting includes _extreme_ long periodes, because I am not that much of a patient man. Pressing any bottom does not work, I've tried Esc, Enter, Space and holding left-shift while booting up.

[COLOR=Red]*I assume that the install process managed to empty the harddisc, but haven't filled it up again with Ubuntu, so how would I logically solve this problem installing Ubuntu on a computer with no OS already installed?*[/COLOR] :(


[LIST]
[*]Booting with the USB doesn't work.
[*]I have no CD-drive, so I can't write the ISO files to a CD and ask it to start up from that. (I have considered getting an external CD-drive if all else fails just to try). I have no Daemon Tools to mount ISO files with anymore.
[*]I don't know any Linux/Ubuntu commands since I am extremely new to Ubuntu (I've heard about it, but haven't ventured far into it yet, other than open-source software), but even if the commands couldn't work, I am not even sure if the computer responds to my pressing the keyboard.
[*]Pressing Ctrl+Alt+Delete (in desperation) causes a reboot.
[*]Rebooting doesn't work either.
[/LIST]

So I am pretty doomed. I hope I have written this in a language that you can understand. Here is some info that might help:


[LIST]
[*]Computer: Asus UL20A (Netbook)
[*]Practical experience with Ubuntu: None (something I hoped to do something about by switching to)
[*]I have used the search function but didn't manage to find something that I could understand that could help me.
[/LIST]

If you have any questions that might help me, feel free to ask, I really hope I will be able to use Ubuntu soon. :)

Thanks in advance

---

### Post by Quackers on 2011-01-11
To stand a chance of getting anything running (including Windows) you really need to get the usb flash drive booting. Is the bios set to boot the flash drive first? If you can get the flash drive booting please select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Veltia on 2011-01-11
Thank you for your contribution Quackers, but I think you won't be able to use this as much as *I'm right now using a different computer than the one with the issue*, as the one described in the opening post is nothing but a flashing "_",nevertheless I complied, who knows - I am the rookie here so you might find what you need. Thanks :)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2020 MB, 2020904448 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3947079 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,935,924     3,935,862   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7A0CADF10CADA919                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0BDC-1437                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  76 0e 3c 00 fd 0e 00 00  00 00 00 00 02 00 00 00  |v.<.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 37 14 dc 0b 4e  4f 20 4e 41 4d 45 20 20  |..)7...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
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
00000100  7d 00 66 b8 22 1e 00 00  66 ba 00 00 00 00 bb 00  |}.f."...f.......|
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


```As I said: I hope this helps, but I doubt it seeing that it states the OS of the computer to be Windows XP (which is the OS of the computer I'm being lend = The computer I'm using right now) while the computer with the issue had Windows 7. :)

---

### Post by Veltia on 2011-01-12
I do not know if bumping is generally allowed on these boards, but I'm bumping the thread now, in the hopes someone is able to help me. :)

---

### Post by rikdeek on 2011-01-12
Hi Veltia,

Try this:

- Press delete (sometimes a function key) whilst booting the computer to get into the bios and find the boot priority. Make the computer boot from USB first and make sure that booting from USB is enabled.
- Restart the computer with the USB stick plugged in. This should bring up a main menu with an Ubuntu logo.
- If you do not get to a menu, confirm that the usb drive mounts on another machine. Put it in another computer and boot it to see if you can get to the menu (make sure this computer is set to boot from USB first in the bios settings).

Let me know how you get on.
Cheers.

---

### Post by Veltia on 2011-01-12
Actually, I tried to follow one of my friends advice, he told me that when booting a computer there should usually be some text or something saying "press *bottom* to boot" or something. When I saw my girlfriends computer boot, I noticed that text was under the Acer logo, so I tried to shut down the computer and reboot it again a couple times, everytime pressing either: f1, f2, f3, f4, f5, f6, f7, f8, f9, f10, f11, f12, backspace, left shift and finally escape. When I pressed escape something happened and it just worked, it has Ubuntu on it now. So I am happy. Thanks for your support though Quacker and rikdeek. :)

---

### Post by Quackers on 2011-01-12
Glad you got things working :-)

---

