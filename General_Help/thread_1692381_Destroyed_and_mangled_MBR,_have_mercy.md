---
title: "Destroyed and mangled MBR, have mercy"
date: 2011-02-21
forum: General Help
---

### Post by GnoitAll on 2011-02-21
Hey everyone. I'd like to describe how I mangled and destroyed my MBR and partition table (it would seem). I'm sure the extent to which I've gone to ensure it's completely destroyed is unrivaled. Here's the background:

I installed vista, it had some problems cause by a faulty uninstall of acronis, which meant it didn't aways boot properly. This will be important later in the story.

Now, I decided that I wanted to dual boot ubuntu, since there was some softward not available for Vista. So I proceded to install it via Wubi, the first transformation of my MBR. I installed it on a 2nd drive, so I'm not sure what that did to the original MBR, but whatever it did, it now booted from drive 2.

It worked well for some months.

The 2nd transformation came after an update that forced me to restart the computer, now the acronis problem comes back in, and I can't boot into Vista. Woe is me! What to do? Well, I had set up Plop boot manager to install from boot, and decided it was a good time to install it, what could go wrong? Besides, it'd be handy booting from USB (I didn't think to check, but my motherboard boots from USB anyway).

So now I have plop, and what should happen, but windows and ubuntu do not appear on the boot list. That's funny. So what now, the logical thing would be to uninstall it, but... Here comes transformation #3, I decide, running on a live USB, to install Lilo boot manager to see if that will recognise my OSes. It doesn't. It's just blank, with a blinking cursor.

Here's what I've tried:
Vista DVD - doesn't work, with the acronis problem, it would hang and never start. Now I've got the drive hooked in via USB, but it doesn't recognize Windows
Plugging into other computers - freezes, BSOD, causes plug & play errors
Prayer - progress, but no definitive answer
Transformations 1-3

What I haven't tried:
fdisk /mbr (from a dos CD)
testdisk (considering using this next)
uninstalling lilo/restoring Plop (don't know how to do this)
Uninstalling plop (need to restore first)

To make matters worse, when I type 'fdisk -l' on the live USB, it tells me the hard drive partitions do not end on cylinder boundaries, which I suspect means the partition table is hosed.

I *suspect* the cleanest way is to restore from lilo, but don't know how to do it (I tried sbin/lilo -u /dev/sda, I get some error about "Fatal: cannot open: /etc/lilo.conf")

Please help! Ignorance has lead me this far, and I'm hoping knowledge can pull me out.

---

### Post by oldfred on 2011-02-21
We need to see exactly where you are at:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by srs5694 on 2011-02-21
Follow oldfred's suggestion. I'll also add this:

The Master Boot Record (MBR) contains two things: The partition table (which defines where partitions begin and end, and some additional metadata about them) and the primary boot loader (which is a key part of the boot process). Nothing you've said makes me believe that your partition table is damaged. The fdisk warning about partitions not beginning on cylinder boundaries is unimportant -- it has to do with the old-style (cylinder-aligned) vs. new-style (1 MiB alignment) layout of partitions, which is irrelevant to modern OSes. What you've got is a boot loader issue, possibly confounded with other stuff, like your Acronis installation. (I'm not familiar with Acronis, so I don't know whether it might do anything to interfere with boot loader setups.)

Also, be aware that WUBI installations of Ubuntu are not very highly regarded; they tend to be trouble-prone and limited. If you're serious about using Linux, it's probably best to plan on deleting the WUBI installation and starting again with a conventional side-by-side dual-boot configuration. You might need to do this down the road, though, if you first need to remove files from the WUBI installation or use the WUBI installation to assist in recovering your Windows installation to bootability. So don't do anything about this just yet; post the Boot Info Script's RESULTS.txt file and wait for advice. I just want you to be aware that there may be advice to reconfigure WUBI coming in a while.

---

### Post by GnoitAll on 2011-02-21
Alright, thanks guys. Good to know my partition table's probably OK. I figured the error I was getting about the cylinder heads and the crashing in various ways was related to that.

I found out WUBI was a problem after all this hullabaloo, and I'll certainly be moving to a normal dual-boot scenario after this.

Here's the result of the script. The 320gb hard drive is drive 1, on which I installed Vista originally. I've temporarily disconnected the IDE with the WUBI bootloader (disk 2). The last 4 drives listed is a multi-card reader, the 4000mb drive is the ram. Let me know if you want me to connect the IDE drive and re-run the test.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
1 heads, 63 sectors/track, 9922896 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4000 MB, 4000317440 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7813120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,813,119     7,813,057   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F80F-0522                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/VistaPE           iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 84 04  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c1 37 77 00 be 1d 00 00  00 00 00 00 02 00 00 00  |.7w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 22 05 0f f8 4e  4f 20 4e 41 4d 45 20 20  |..)"...NO NAME  |
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
00000100  7d 00 66 b8 08 40 00 00  66 ba 00 00 00 00 bb 00  |}.f..@..f.......|
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


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by srs5694 on 2011-02-21
Your /dev/sda partition table appears to be damaged, since there are no partitions listed on that disk. Therefore, you may need to use TestDisk to recover those partitions.

With that done, you may need to use a Windows emergency recovery CD to restore Windows to bootability, unless the LILO installation on /dev/sda happens to have working Windows options. I'm not an expert on restoring Windows to bootability (I usually just re-install it, since the references I find generally don't help when I get in such situations). Certainly the FDISK /MBR command is one possibility, although I'm not sure if that will be very useful with Vista.

---

### Post by bcbc on 2011-02-22
> **GnoitAll said:**
> So I proceded to install it via Wubi, the first transformation of my MBR. I installed it on a 2nd drive, so I'm not sure what that did to the original MBR, but whatever it did, it now booted from drive 2.

Wubi doesn't do anything with the MBR. It's also not possible that it could alter the order BIOS boots. Wubi boots from the windows boot manager via a call to grub4dos and, except for one grub-related bug, it cannot affect the MBR (and that bug results in the computer not booting at all ==> grub rescue prompt - not the symptoms you describe).

So... wubi isn't perfect, but in this case, something else has "mangled your MBR"

---

### Post by GnoitAll on 2011-02-22
I'll try TestDisk and see what happens. Is there anything destructive that could come of that? So far, every fix I've tried has made things worse, and I don't want to approach it the same way and cause worse problems (not that I can think of any).

Regarding Wubi, it did change the mbr in some way, since before installing wubi, it was booting from disk 1 (just Vista), and after installing wubi, it booted from disk 2, or maybe the mbr on disk 2 just pointed to disk 1, which would then boot normally. I'm pretty sure it was Plop boot manager that pushed it over the edge, though.

---

### Post by oldfred on 2011-02-22
Wubi would not have changed boot order. BIOS controls that. But plop may have changed something as it is set up to chainboot devices that do not normally boot.

Lilo is like windows & will boot windows in the MBR, as it just looks for a boot flag and jumps to additional boot code in the partition boot sector. Lilo will also let you directly boot XP in a logical partition. Windows will not boot the logical as it does not recognize the boot flag on a logical partition.

---

### Post by GnoitAll on 2011-02-23
OK, I ran TestDisk, and it fixed my partition table, and with the help of a SATA to USB connector (Vista would hang if connected via SATA) I managed to restore the MBR from the Vista DVD. So, now I'm back to my original starting place, trying to figure out why Vista won't boot (it hangs at crcdisk.sys in safemode, and in normal mode it gives me a quick BSOD (can't see it, too quick), and then restarts).

One last question, that may help me point myself in the right direction: I've noticed if I connect the drive via USB to Windows (XP, though I suspect it's the same on others), then it will give me a "plug_and_play" error, saying something about a bad/corrupt driver and force a restart, but on Ubuntu, it has no problem opening the disk and using it. Does this provide any clues as to what may be the problem? Perhaps HD drivers?

Thanks,
-Julian

---

### Post by srs5694 on 2011-02-23
I'm far from an expert on Windows recovery, so I can't help you with your Windows boot problems. My recommendation would be to either ask for help on a Windows forum or re-install Windows.

---

### Post by GnoitAll on 2011-02-24
OK, thanks again for your help. I'll take my issue to another forum now and see if I can resolve it...

To recap, in case anyone else has this problem, I simply ran TestDisk, which restored the partition table, and then restored the boot manager by using the Vista DVD. Whereas the DVD would crash if I connected the drive via SATA, when I connected through a USB adapter (I got this one: [http://www.newegg.com/Product/Product.aspx?Item=N82E16812816111&cm_re=sata_to_usb-_-12-816-111-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16812816111&cm_re=sata_to_usb-_-12-816-111-_-Product)), the Vista DVD loaded, and recognized the windows installation. It didn't recognize it before running testdisk.

Testdisk can be gotten here: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I may just backup and reinstall, but recalling back to how much of a pain that is, I might still consider a few options.
-Julian

---

### Post by ronparent on 2011-02-24
You seem to have four disks and all of them damaged? Is it possible that they were configured in some kind of a four disk raid array? That suggests a raid10 perhaps. In that case attempting to install to one disk (ie sda) of a four disk raid would trash your partition table. That would be also be possible if your raid level were not supported by dmraid and the raid wasn't recognized during install.

---

### Post by GnoitAll on 2011-02-24
No, nothing like that. It's just a single 320gb drive. I think the reason it showed 4 'partitions' is that the partition table was broken. Why 4? It might have something to do with Plop bootloader, with which I was playing with many settings.

Unless you're referring to this:
```
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf
```
Which is simply a multi-card reader, I believe.

---

