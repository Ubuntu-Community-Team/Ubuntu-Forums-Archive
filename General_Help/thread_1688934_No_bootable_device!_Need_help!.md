---
title: "No bootable device! Need help!"
date: 2011-02-16
forum: General Help
---

### Post by Brennan9082 on 2011-02-16
Ok, i just got ubuntu using wubi on my laptop, during installation i only gave it like 3 or 4 gigs of space not know that's all the hard disk space it was gonna get.  so i installed and messed iwth ubuntu for 5 hours, getting a crap load of addons like the sphere and getting wine so i could run steam games and all this other stuff.  was seriously considering to remove windows and go full ubuntu.  but suddonly it told me i only had 170 mb left on the harddrive!  i went and looked and realized i had only given it a maximum of like 4 gigs that i had filled up already.  so i did some googling and found GParted.  i downloaded it and read 4 forums with people saying to basically just click one of the drives and it'll remove all from it.  i thought this'd be alright saying that i wanted to remove all the files on windows and start from scratch as if it were a new computer using ubuntu.  so i click one that said 12 gigs and click partition or something... then it instantly said "error partitioning the device" i was like "that's weird"  so i exited it and did some youtube surfing and stuff, got bored so reset computer and WABOOOOM "No bootable device -- please insert device and press any key"  i instantly knew what happened, i opened the bios resetting the computer over and over changing the boot order to try to make it run from different disks and stuff with no luck at all.  i've probably removed something epicly vital to booting up, what's sad is im really computer smart and i just did this without even thinking, i might as well have just fried my harddrive in boiling water UGH! can someone give me some other option besides taking it to the Geek Squad? quick answers would be EPICCC :p

---

### Post by requeth on 2011-02-16
I apologise in advance, but I may sound a bit condescending here and it's not my intent, since I've done this exact same thing before.

A) as far as I know you can't fry your BIOS by using gpart.
B) Did you write down the error message you received?
C) Did you use a live CD to Gpart your drives or did you override the failsafe and do it while running your Ubuntu install? If you did, don't do it again, trust me, it doesn't work the next time either.

If the next part doesn't work, reply with answers to the above.

When you Gpart a drive, a really annoying step gets missed. Your Master Boot Record doesn't get updated, which if Gpart moves the primary blocks (which happens fairly often) then you get the 'no bootable device' readout, because your BIOS goes to the MBR and says "oh good, I grab from sector 147" It goes to sector 147 and instead of finding byte 1 of Ubuntu, it finds something random like your firefox link and rejects the data. Use instructions at your own risk, I have done this before and I made notes when I did it, which I'm posting below, but I'm not a master of it:

Run an Ubuntu Live CD or Live Flash drive on the machine.

Mount Root Partition from your hard disk. I'm assuming in the next line that the drive is labeled sda.
Run:dd if=/media/sda/mbr.bin of=/dev/sda bs=446 count=1
Reboot and load your computer instance of Ubuntu. NOT the live CD, NOT Windows.
Re-config Grub by typing 'sudo grub-mkconfig' into the command line. This will fix your partition locations in the MBR.
Reboot.
Try both Ubuntu and Windows.

---

### Post by Rubi1200 on 2011-02-16
Hi and welcome to the forums :-)

You need to do the following please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

We need to see the results to be able to help you sort this out.

Thanks.

---

### Post by requeth on 2011-02-16
Actually, scratch that. That'd be to fix your drives to keep data. If you want to wipe everything throw the live CD in and just run a fresh install of Ubuntu, when you get to partitions remove all partitions and then allow the installer to allocate space.

---

### Post by Brennan9082 on 2011-02-16
One problem with all these suggestions is, i didn't install ubuntu on a cd that i can place in my disk drive, i installed it onto my harddrive itself.  idk what a live cd is.  the only thing i could imagine to do is download ubuntu and use Wubi to install it on a blank cd from the computer im using right now, then insert that cd into my computers cd drive and go to the BIOS and set my cd drive to boot.  but from there i don't know what i should do.

---

### Post by Rubi1200 on 2011-02-16
On the Ubuntu downloads page there are instructions on how to create a bootable LiveCD or LiveUSB.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Click on Show Me How to get more information.

There is also information on how to try Ubuntu, which is what I would like you to do first.

After that follow the instructions I posted previously.

If you need more help, just ask.

I want to point out that we can probably help you repair any problems, but we need the results of the script to do so.

---

### Post by Brennan9082 on 2011-02-16
im working on using ubuntu off of my USB drive on the laptop, but it shows the ubuntu loading screen but now the screen is just black, i'll figure it out, but i have to go to a basketball game in a bit so i'll have to finish it tonight.

---

### Post by Brennan9082 on 2011-02-16
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files/dirs:   /etc/fstab

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
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



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
124 heads, 62 sectors/track, 1021 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *              1     1,945,600     1,945,600   6 FAT16
/dev/sdb2           1,945,601     3,891,200     1,945,600  82 Linux swap / Solaris
/dev/sdb3           3,891,201     5,836,800     1,945,600  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1977 MB, 1977614336 bytes
64 heads, 63 sectors/track, 957 cylinders, total 3862528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                 135     3,858,623     3,858,489   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        543B-B06E                              vfat       PENDRIVE                      
/dev/sdb3        b7aef57c-de3d-4397-a538-cb3a0ecbb63a   ext3       C-ROOT                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        6130-3235                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb3        /media/C-ROOT            ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/6130-3235         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sdb1/boot/grub/grub.cfg: ===========================


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

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg

=============================== sdb3/etc/fstab: ===============================

# UNCONFIGURED FSTAB FOR BASE SYSTEM

=================== sdb3: Location of files loaded by Grub: ===================


   2.8GB: boot/initrd.img
   2.8GB: boot/initrd.img-2.6.30-chromeos-intel-menlow
   2.9GB: boot/vmlinuz
   2.9GB: boot/vmlinuz-2.6.30-chromeos-intel-menlow
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 20 04 00  |.X.SYSLINUX.. ..|
00000010  02 00 02 00 00 f8 ee 00  3f 00 ff 00 01 00 00 00  |........?.......|
00000020  00 b0 1d 00 80 00 29 6e  b0 3b 54 4e 4f 20 4e 41  |......)n.;TNO NA|
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
00000100  7d 00 66 b8 00 02 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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
```


here's what came up, im going to basket ball game here soon be back later this afternoon.  thank you for all this help

---

### Post by bcbc on 2011-02-16
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Boot live cd, install testdisk  - use it to recover your partition table etc. It's probably all there and will work after fixing.

```
sudo apt-get install testdisk
sudo testdisk /dev/sda
```

Follow the menu, something like:
no log
intel
analyze
etc.

It's usually pretty good at fixing these sorts of problems.

---

### Post by Brennan9082 on 2011-02-16
> **bcbc said:**
> [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Boot live cd, install testdisk  - use it to recover your partition table etc. It's probably all there and will work after fixing.

```
sudo apt-get install testdisk
sudo testdisk /dev/sda
```

Follow the menu, something like:
no log
intel
analyze
etc.

It's usually pretty good at fixing these sorts of problems.

I'm not at home right now to test this, but i read the wiki link u sent me and it was quite a bit confusing, please give me step by step instructions for my specific problem.  When it comes to partitions and harddrives i don't know much.

---

### Post by bcbc on 2011-02-16
> **Brennan9082 said:**
> I'm not at home right now to test this, but i read the wiki link u sent me and it was quite a bit confusing, please give me step by step instructions for my specific problem.  When it comes to partitions and harddrives i don't know much.

Well... I think you are going to have to study that link. It's your data and I can't see from here what's going on - at each point in the process you'll have to read what testdisk finds.

But if it goes well it should be:
sudo testdisk /dev/sda
Intel
Analyze
Quick search
Yes/no (search for partitions created under vista)
Enter to proceed
If it looks like testdisk found everything then Write it, otherwise select Deeper search.

That should do it. It also looks like you might need to reinstall the windows bootloader - since bootinfoscript didn't find it. 

But first see if you can get back your partitions.

---

### Post by Brennan9082 on 2011-02-16
im trying to install testdisk, and i put in ```
sudo alien /home/ubuntu/Downloads/testdisk-6.11.3-1.i386.rpm
```  then it says .deb created it creates testdisk_6.11.3-2_i386.deb . so then i type ```
sudo dpkg -i testdisk_6.11.3-2_i386.deb
```  and it says there's no such directory.  i searched to try to find that file on the computer at all and it couldn't find it, i tried using alien to install the program directly from the .rpm and it wouldn't work.  any help?
EDIT:i had to get 
**testdisk_6.1-1_amd64.deb**

which just so happens to not work with my computer, it says it's not available for this computer.  i'll try to find out how to make it work.  i need help getting testdisk to work

---

### Post by bcbc on 2011-02-17
```
sudo apt-get install testdisk
```

---

### Post by Brennan9082 on 2011-02-17
IDK how to set this thread to [SOLVED] but if someone can please do so.  i put ubuntu on a USB and just installed ubuntu onto my harddrive and one of the options was to format my disk and make it empty, idk if this would fix the partitions, but i can now boot up onto ubuntu and it says i have 137 gigs out of 160 open, and when i installed windows when i got this computer i only had 134 gigs.  so as far as i can tell it works.  thx for all the help, but one thing that sucks is i no longer have my itunes library D:

---

