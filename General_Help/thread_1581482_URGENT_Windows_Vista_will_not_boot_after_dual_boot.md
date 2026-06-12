---
title: "URGENT Windows Vista will not boot after dual boot install"
date: 2010-09-25
forum: General Help
---

### Post by rhoparkour on 2010-09-25
Hello, 

I have recently installed Ubuntu 10.04 on a Compaq Presario V3000.

To prepare the install, I freed about 15 GB of space, booted from an USB. I chose "use largest continous free space" when it got to that point and then proceeded with the rest.

Now when I choose vista it will not load properly, here's what happens:

1.Windows says loading windows files.

2.After a while, I have to choose a language.

3.Windows looks for operating systems to repair.

If I choose not to, it will take me to a menu where I can choose to fix boot problems, command line, etc...

Linux is running very well, vista is the problem here, I have a recovery disk*, but I wanted to ask you guys if that is the correct move. I really need to keep windows to run some windows only apps.

*This disk was burnt on another computer, an HP from a friend who has the same vista edition. Will this work? This computer's burner is broken....

Thank you in advance for the help dudes!

PS. Background story: This is actually something for my gf, she has an account on my computer(only ubuntu on it) and uses it often (Mendley, Zotero, and sciency things in general). She loved it and asked me to install a dual boot with her win system. She use SPSS for whatever kind of statistical analysis it does and she likes ms office better then open office, and I would like to leave her with the choice....

---

### Post by rhoparkour on 2010-09-25
By the way, almost forgot to post the boot_info_script055 output:

```

rho@Verde:~/Downloads$ cat RESULTS.txt 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   188,514,838   188,514,776   7 HPFS/NTFS
/dev/sda2         218,419,740   234,436,544    16,016,805   7 HPFS/NTFS
/dev/sda3         188,516,350   218,419,199    29,902,850   5 Extended
/dev/sda5         188,516,352   217,069,567    28,553,216  83 Linux
/dev/sda6         217,071,616   218,419,199     1,347,584  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A2E2F499E2F472C1                       ntfs                                     
/dev/sda2        2C88743C8874071C                       ntfs       PRESARIO_RP                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        9defec7f-50e5-4477-b9e5-09965f467fa7   ext4                                     
/dev/sda6        05c7c5db-6da2-4ff6-a7e2-db7a5f00c069   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 9defec7f-50e5-4477-b9e5-09965f467fa7
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 9defec7f-50e5-4477-b9e5-09965f467fa7
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9defec7f-50e5-4477-b9e5-09965f467fa7
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=9defec7f-50e5-4477-b9e5-09965f467fa7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9defec7f-50e5-4477-b9e5-09965f467fa7
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=9defec7f-50e5-4477-b9e5-09965f467fa7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9defec7f-50e5-4477-b9e5-09965f467fa7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9defec7f-50e5-4477-b9e5-09965f467fa7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=9defec7f-50e5-4477-b9e5-09965f467fa7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=05c7c5db-6da2-4ff6-a7e2-db7a5f00c069 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 101.0GB: boot/grub/core.img
  99.0GB: boot/grub/grub.cfg
 101.0GB: boot/initrd.img-2.6.32-24-generic
 101.0GB: boot/vmlinuz-2.6.32-24-generic
 101.0GB: initrd.img
 101.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  91 a0 32 15 1d 7b 2d ee  80 21 8a 30 18 ed 23 b2  |..2..{-..!.0..#.|
00000010  4d 73 66 c1 2b 67 9a d5  0d 87 30 d2 7d a0 d9 b9  |Msf.+g....0.}...|
00000020  02 e8 cc a5 f0 15 16 21  c1 5f 60 7c 81 15 a9 63  |.......!._`|...c|
00000030  1e 81 7c 63 09 13 89 78  07 44 da c0 ae 95 ef 0b  |..|c...x.D......|
00000040  d0 c9 7a 81 55 57 88 e0  53 2a cb 3e b9 26 c8 43  |..z.UW..S*.>.&.C|
00000050  2e af 9f e3 1d e6 7a 88  f1 af ac ae 11 97 99 b1  |......z.........|
00000060  04 80 71 1f 49 79 af af  d8 33 3e a7 70 75 40 b4  |..q.Iy...3>.pu@.|
00000070  0c ac c9 02 90 d1 f3 2c  bf 82 15 89 de ec 84 15  |.......,........|
00000080  75 e3 32 4e f7 5c 6c a8  7e a3 b1 84 3e 7c 53 b5  |u.2N.\l.~...>|S.|
00000090  40 86 be 78 00 59 1e 92  96 9a 7b 37 09 0e 0c 88  |@..x.Y....{7....|
000000a0  fd 34 09 aa 47 a3 78 a0  23 6e 5d 53 28 27 0e eb  |.4..G.x.#n]S('..|
000000b0  19 e0 2b d9 79 f4 49 d2  eb b3 e8 52 27 7c 78 a9  |..+.y.I....R'|x.|
000000c0  4b 0f d9 28 2c 86 fa 26  8d a1 1c 10 9a ba 22 46  |K..(,..&......"F|
000000d0  d9 4e 10 63 ba 7e c3 cc  72 29 b7 6c 01 e2 43 fd  |.N.c.~..r).l..C.|
000000e0  db 24 f1 0c c5 95 c0 60  f3 4b ab 7d 88 af da b8  |.$.....`.K.}....|
000000f0  5d fc 00 ca 9f 4f 62 8f  0e ad 8b 7a 66 12 a5 6a  |]....Ob....zf..j|
00000100  40 c9 85 06 3a 50 87 58  aa a7 ba a6 6e ab 8b 5d  |@...:P.X....n..]|
00000110  fa e6 c9 19 f5 6b dc 2a  6a ec fb 4c 2e f5 c0 7a  |.....k.*j..L...z|
00000120  d5 eb 0e f5 c4 2a 72 92  df 08 5d 36 28 79 bd 77  |.....*r...]6(y.w|
00000130  bc ed ff 47 09 ac f1 a7  e0 d5 78 d0 bd fe ec 9a  |...G......x.....|
00000140  05 f8 49 96 0f 9a 1d 9c  3f 14 16 a9 1d a3 d1 c6  |..I.....?.......|
00000150  a0 ed c6 f6 c4 cf 55 fc  b4 ba 6e e3 09 ba 83 db  |......U...n.....|
00000160  d8 a7 e5 cd 73 4d 11 ff  a7 4b 40 07 6d 74 58 b6  |....sM...K@.mtX.|
00000170  10 ec c2 33 78 e5 28 90  d9 b1 01 7b 8e 20 bb af  |...3x.(....{. ..|
00000180  f6 33 9d ab 9b af 96 26  f4 70 f6 9c b1 be b1 1d  |.3.....&.p......|
00000190  f5 50 37 3d be 26 5d 78  97 b6 10 af c7 6b a2 73  |.P7=.&]x.....k.s|
000001a0  27 09 39 2e a0 8e e3 db  0b 98 74 b8 79 91 fe f8  |'.9.......t.y...|
000001b0  f5 2c e8 97 a0 2a 9b 96  6f 06 8a 7d b9 77 00 fe  |.,...*..o..}.w..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b0 b3 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff ca b2  b3 01 38 95 14 00 00 00  |..........8.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Well, I'll be digging around the forums! (not that I haven't done so for a while now...)

---

### Post by rhoparkour on 2010-09-25
UPDATE:

Windows is working fine as far as I can tell, if I go to the command line after all the screaming it does and run:

```

bootrec.exe /fixboot
bootrec.exe /fixmbr

```

then reboot windows will, after asking for safe or normal mode, boot normally.

If I happen to recover grub using:

```

sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /media/sda5
sudo grub-install --root-directory=/mnt/sda5 /dev/sda

```

Now Ubuntu will boot and vista is lost.

I have also noticed that I cannot mount the windows partition from Ubuntu, it will give the same error as the beginning of the bootscript output I posted. I can´t mount from either the live cd or the hard drive install (same error on both).

I have now left the computer with the windows bootloader, until I can:

a) Figure out a way to mount the windows partition from Ubuntu (I have a feeling this is the root of everything).
b) Have windows boot from grub (or whatever it boots from after selecting it at the grub start screen).

I mean, there is no point in running Ubuntu on a measly 15 GB if I can´t store the data on the windows partition (which is about 70 GB). I was planning to just have the ubuntu stuff on the ubuntu partition and the actual ¨personal files¨ (documents ,music, etc...) on the windows partition.

I would be happy to get some advice :) and I thank you again in advance.

---

### Post by Quackers on 2010-09-25
I followed this post by drs305, which sorted my boot problems out.
[http://ubuntuforums.org/showpost.php?p=9836539&postcount=5](http://ubuntuforums.org/showpost.php?p=9836539&postcount=5)

---

### Post by rhoparkour on 2010-09-25
Well, I seem to have a very firrefent problem than him. So what I did is (again):
 
```

sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt/sda5
sudo grub-install --root-directory=/mnt/sda5 /dev/sda
sudo reboot  #computer reboots, boot into ubuntu no prob
#I also hve the option to go into vista (loader), but before that open a terminal
sudo update-grub

```
 
I get that grub has found everything:
 
```

generating grub.cfg
found linux image: /boot/vmlinuz-2.6.32-24-generic
found initrd image: /boot/initrd.img-2.6.32-24-generic
found memtest86+ image: /boot/memtest86+.bin
found windows vista (loader) on /dev/sda2
done

```
 
After this, I reboot, grub is well nd fine, I have the option of Vista and Ubuntu (as I`ve always had), but the same problem arises, vista does not boot properly. Vista leads me after some time to the recovery menu, or whatever it is called, where I choose to go into command line. I run /fixboot and /fixmbr through bootrec.exe to recover the windows install.
 
FINAL SATUS:
 
So now vista has taken over and runs properly. 
 
At no point can I mount the vista partition in ubuntu, which is now disabled (I can´t mount the main vista one from linux, but I can mount the small 8GB recovery partition at all times from linux).
 
I should point out that grub does detect a vista loader and it is on the menu, but it sends me to vista recovery when chosen.
 
Again, I have left the computer with vista taken over.
 
Thanks Quackers, but I seem to have a very different problem than what is described on the post you linked.

---

### Post by Quackers on 2010-09-25
It appears to me that grub is not identifying your Windows partition (sda1) it is recognising and pointing to your Windows Recovery Partition (sda2 for some reason) which is, I think, called Presario_RP) and consequently when you choose the Windows boot option you are actually booting the Presario Recovery Environment.
For some reason grub is not properly recognising the proper Windows partition.

---

### Post by Lateralis on 2010-09-25
Stupid question.  The script suggests running chdsk \f.  You have done that, right? 

Also, do you have a recovery partition?  When I first installed Jaunty on my (then newish) laptop it actually picked up the Vista recovery partition, not the Vista OS partition.  (At the time of installing I had no idea I had a recovery partition installed!  Only when I inadvertantly booted into it through Grub did I realise I had one...)  It meant I had to *manually* add a menu entry in my menu.lst.  

Of course, that was with Grub legacy, not Grub 2 so I will assume the situation is different/better.  But I thought I would throw it out there as a possible...



Edit: Too slow to post... curse you Quackers!

---

### Post by Quackers on 2010-09-25
Lol. Quack Quack!
I was cursing grub2 for picking up both my Windows partition and the Recovery Partition. I now see that there are worse problems.

---

### Post by Lateralis on 2010-09-25
Oh, as another thought, how did you partition that hard drive up?  I think Vista has built in partitioning tools.  Did you use those (if they exist - perhaps you could remind me?!) or did you use Gparted?  

Resizing, moving and shrinking NTFS partitions used by Vista and Win 7, particularly their OS partitions (their root if you will) using Gparted or other Linux tools isn't fool proof and can lead to problems.  Aside from the fact that NTFS support in Linux isn't fool proof anyway (that's a different story for a different thread) Win 7 and Vista can get very uppity if their partitions are fondled with without them knowing.


Addendum: Quackers is right.  I didn't look at the bootinfo script output, but the menu entry is pointing to the recovery partition, not the Vista OS partition.  Try adding a new menu entry which points to sda1 and see if that works.  

Now, that being said, the boot info in sda1 looks borked to me.  Is there a way you can get the recovery partition to reinstall the Windows boot shizzle to sda1 and not reinstall the whole Windows bootloader to the MBR?

---

### Post by rhoparkour on 2010-09-25
About my partitioning: 
 
I used the vista partition tool to set up the ubuntu parttion, Ieven booed into win a few times to check it was ok and did a hard drive check (or whatever it is called), no problems.
 
I had ubuntu use the largest cont. free space, it ceated a partition for itself and a small swap in that free space.
 
About my recovery partition:
 
Quackers is very right indeed, /dev/sda2 IS the recovery partition, /dev/sda1 is the windows partition. How can I make grub point to the right `booter`?
 
 And no, I didn`t run chdisk \f, do I run this in the command line of the recovery partition? Or where should I run it? What does it do? Will it remove anything?
 
It seems I will have to do what you suggest, Lateralis.

---

### Post by Lateralis on 2010-09-25
OK, good that you used the Vista tools to do the partitioning. =)  

[This HP link]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00809678&product=18703#CheckPCFiles") seems to suggest how you can do it (chkdsk) through the recovery partition.  Unfortunately I've never had to do anything like this before so I can't be of much help.  chkdsk \f should though check for inconsistencies and fix them.  It should also be fairly simple how to check either the primary Vista OS partition or the recovery partition.  I would personally check both of them, even though it looks like the recovery partition is fine.  
 

Whilst you're in the recovery partition, I would also see if you can install the Vista boot info again to sda1.  From reading your earlier post 

```

/fixboot

```

is probably what you want, NOT fixmbr - that will wipe grub.  You should also have the option of pointing /fixboot to sda1, but again I'm unsure of the details.  

As for getting the additional menu entry, I've never done that in Grub 2.  There is a link in my signature pointing to the Grub 2 wiki - I would read that.  What I think you need to do is make a new template and run update-grub after that.  DO NOT edit grub.cfg manually; it is not meant to be edited, like menu.lst was.

---

### Post by Quackers on 2010-09-25
The only thing I can think of as to why your main Windows partition is not being properly recognised by grub2 is that maybe some files are missing or damaged. I'm not sure how that could have happened if you used the Windows tools. (Unless you ran bootrec /fixboot or /fixmbr using partition 2). This is a possibility, as the recovery partition should be partition 1 not 2. This happened with my system a while ago. As a last resort you could try the fixboot and fixmbr or rebuildbcd on the other partition then Grub2 may boot the proper partition.

---

### Post by rhoparkour on 2010-09-25
Ok, I am a little confused.
 
Should I run /fixboot inside the system recovery boot or on the command promp of the usual win system (the on you would use normally)? It seems you are implying that doing it from the recovery partition is a bad idea, so I should it in the normal win session?
 
Also, this laptop is a compaq (I`m posting from another one), but I don`t think the instructons from your link should change.
 
So in summary:
 
I sould run chdisk on normal win session, then recover grub, it should now be able to detect sda1 as the win booter and bot into windows and hopefully windows will boot normally. And also, I would hopefully be able to mount the windows partition.
 
If I`m wrong pleae correct me, this is NOT my computer, I`m doing a favor. Otherwise I would just keep Ubuntu and let vista die!
 
EDIT: I have read the grub2 wiki, thisis where I got the instructions to recover grub. Will read again.

---

### Post by Quackers on 2010-09-25
When you ran fixboot or fixmbr did you use Diskpart? Selecting disk 0 then selecting partition 1? Or partition 2? I would suggest running the same command on the other partition (which as we now know grub has labelled wrongly). Then see if windows will boot.

---

### Post by rhoparkour on 2010-09-25
What is diskpart? I have no idea if I used it or not.... I really don`t think I did. Also I have no idea what you mean by partition 0,1 or 2. Interms of sda which would these be? 
 
Anyway, I think running chdisk on the normal windows partition should do the trick and repair what it should.

---

### Post by Lateralis on 2010-09-25
> **rhoparkour said:**
> Ok, I am a little confused.
 
Should I run /fixboot inside the system recovery boot or on the command promp of the usual win system (the on you would use normally)? It seems you are implying that doing it from the recovery partition is a bad idea, so I should it in the normal win session?


I think you can do it from the recovery console.  My understanding is that you cannot do /fixboot from within Windows Vista normally because, well, if you could boot normally there's no need to /fixboot or /fixmbr!  

You also said earlier on in the thread that you had done /fixboot then /fixmbr from within the recovery console.  So I was suggesting that you should do the same thing, just without the fixmbr step.  

> **rhoparkour said:**
> 
Also, this laptop is a compaq (I`m posting from another one), but I don`t think the instructons from your link should change.


Ah!  My mistake.  I thought you had a HP, but that's another person's problem in a different thread!  


In principle, you should be able to do the same from the recovery partition.  I stress again that I'm very hazy on the details as I've (fortunately) never found myself in a position where these sorts of steps are necessary.  

I think I recall seeing people post download links to the chkdsk program.  Whether you can download the program and some how boot to it I don't know.  I'm shooting from the hip at the minute. :P  


> **rhoparkour said:**
> 
So in summary:
 
I sould run chdisk on normal win session, then recover grub, it should now be able to detect sda1 as the win booter and bot into windows and hopefully windows will boot normally. And also, I would hopefully be able to mount the windows partition.


I would see if you can run the chkdsk utility from within the Windows recovery partition and have the utility point to sda1 and sda2.  This will check both drives for consistency and errors. 

Then, see if you can point /fixboot to sda1 from within the recovery partition in order to reinstall the necessary boot files for Windows Vista.  If you go /fixmbr then it will reinstall the Windows boot loader and wipe Grub.  That isn't an insurmountable problem though.
 
> **rhoparkour said:**
> 
If I`m wrong pleae correct me, this is NOT my computer, I`m doing a favor. Otherwise I would just keep Ubuntu and let vista die!


Hehe!  Die Vista!  Die a horrible and painful death!  (At least Vista isn't as bad as [Windows ME]("http://xkcd.com/323/"). :rolleyes:)

> **rhoparkour said:**
> 
EDIT: I have read the grub2 wiki, thisis where I got the instructions to recover grub. Will read again.

[This]("https://wiki.ubuntu.com/Grub2#User-defined%20Entries") is the section that you probably want to take a look at.  Also have a look [here]("https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries").

---

### Post by Quackers on 2010-09-25
Ok, from the beginning.
You installed Ubuntu and Grub2. Grub2 overwrote the mbr for Windows so it wouldn't boot. You presumably ran fixboot or fixmbr from the system disc so that windows would then boot. When I did that I entered the command line and ran Diskpart, selected disk 0, then selected partition 1 and ran the fixboot command. 
I am suggesting that when you ran that command you ran it on partition2 (which would be normal), but we now know that grub2 has labelled the windows partition and the windows recovery partition wrongly. So those commands should have been run on partition 1 not partition 2. This is why when you choose windows from grub2 you are actually booting the recovery partition. This happened to me a while back.
If you do what you did before to get windows booting but do it on the other partition, windows should boot.
This is what I suspect.

---

### Post by Lateralis on 2010-09-25
> **rhoparkour said:**
> What is diskpart? I have no idea if I used it or not.... I really don`t think I did. Also I have no idea what you mean by partition 0,1 or 2. Interms of sda which would these be? 
 
Anyway, I think running chdisk on the normal windows partition should do the trick and repair what it should.

A partition is a chunk of a hard drive.  Windows incorrectly labels partitions as "drives".  So "drive" c and d may in fact be two partitions on the same physical disk. 

In Linux, we properly talk about disks and partitions.  The convention is the sdXY, where X labels a drive and Y a partition.  X is a letter starting from '**a**' and Y is a number starting from 1.  sda1 is therefore partition 1 on disk 1.  sdc5 is partition 5 on disk 3.  So on and so forth.  

Also, chkdsk will only look for errors.  It looks like there are errors on the drive, but whether that will fix your problem or not I don't know.  I suspect you may also have to do /fixboot and point that at sda1.

---

### Post by rhoparkour on 2010-09-25
Ok ok, I´ll try that later, I need to go now...

And yes, if I enter a password, Hitler starts his speech.

Oh, and another question, how do I get /fixboot or whatever to ¨point¨ to the partition I want? And how would I be able to tell which one is the right one? Wouldsomething in the lines of:

```

bootrec.exe /fixboot C:/

```

work? Well, thank you Quackers and Lateralis for the great help so far!

It´s been really helpfull ans I really appreciate it. 

XKCD FTW. I have not met a singleperson who does not like it, even if just slightly computer literate.

---

### Post by Quackers on 2010-09-25
Oh, and another question, how do I get /fixboot or whatever to ¨point¨ to the partition I want?
By running fixboot on the right partition. I suspect you have run it on the wrong partition - but it's only wrong because grub2 has labelled it wrongly.

---

### Post by rhoparkour on 2010-09-26
Ok, I have convinced the owner that the best for this would be a clean only ubuntu insall. I mean choosing `use entire hard drive` on the installation menu. All data is backed up already (she has an account on my comp, withe everything on it, and the new things are on a small 2GB usb).
 
Do you think this will work? Considering the error on the BIG winows partition that doesn`t let me mount it, will the fresh Ubuntu intall fix this on that space? To see what I mean by `the error` look at my bootinfo script at the beginning of the thread...

---

### Post by rhoparkour on 2010-09-27
So... yeah! We have decided to kill Vista and do a clean Ubuntu install (the computer on Ubuntu is noticeably faster than with vista).

Will this fix the problem with mounting the windows partition (the one on the bootinfo script)? I mean, could this be a hardware fault (I can't mount the win partition from Ubuntu)? Or will it be fixed when Ubuntu creates new partitions for itself on a clean install?

---

