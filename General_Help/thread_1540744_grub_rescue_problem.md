---
title: "grub rescue problem"
date: 2010-07-28
forum: General Help
---

### Post by rupertismydog on 2010-07-28
hi,:(
 
 
I have used 'wubi' to dual boot my computer with windows vista home premuim and ubuntu 10. I was updating everything on ubuntu including GRUB,for the first time, and then I rebooted my computer 
 
then it read ...
 
"error no such device "(then a load of numbers and letters)" " (followed by on the next line)
 
"grub rescue>"
 
 
now I cannot even go onto windows , it does not give me the option to.
 
I tried system restore "shift + f10" and nothing happens...
 
 
I have an acer aspire 5720 laptop dual booted with ubuntu 10 and windows vista home premuim
 
 
 
can somebody please help me to fix this problem or restore my computer to defualt settings,
 
 
 
 
THANKS!!!:p

---

### Post by bcbc on 2010-07-28
> **rupertismydog said:**
> hi,:(
 
 
I have used 'wubi' to dual boot my computer with windows vista home premuim and ubuntu 10. I was updating everything on ubuntu including GRUB,for the first time, and then I rebooted my computer 
 
then it read ...
 
"error no such device "(then a load of numbers and letters)" " (followed by on the next line)
 
"grub rescue>"
 
 
now I cannot even go onto windows , it does not give me the option to.
 
I tried system restore "shift + f10" and nothing happens...
 
 
I have an acer aspire 5720 laptop dual booted with ubuntu 10 and windows vista home premuim
 
 
 
can somebody please help me to fix this problem or restore my computer to defualt settings,
 
 
 
 
THANKS!!!:p

You need to reinstall the windows bootloader. There is a bug in grub that's been overwriting the drive MBR lately.
Either boot a windows repair CD/DVD and reinstall the bootloader (bootrec.exe /fixmbr) or boot an ubuntu live CD, and run:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by rupertismydog on 2010-07-28
[FONT=Georgia][SIZE=4]thanks,but ubuntu live does not work (same error message) I was wondering if I bought windows 7 when I install it off the disk would it clean everything and install? so no GRUB or anything would be left behind???[/SIZE][/FONT]
[FONT=Georgia][SIZE=4][/SIZE][/FONT] 
[FONT=Georgia][SIZE=4][COLOR=darkred](windows 7 profesional)[/COLOR][/SIZE][/FONT]
[FONT=Georgia][SIZE=4][/SIZE][/FONT] 
[FONT=Georgia][SIZE=4][/SIZE][/FONT] 
[FONT=Georgia][SIZE=4]THANKS FOR ALL OF YOUR HELP SO FAR THOUGH[/SIZE][/FONT]:KS

---

### Post by rupertismydog on 2010-07-28
[FONT=Comic Sans MS][SIZE=3][COLOR=royalblue]all help is greatly appreciated but I am 12 and do not really understand complex stuff as I am a complete beginner,so if you were to break down explanations well sort of...[/COLOR][/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=3][COLOR=royalblue]it would be greatly appreciated.[/COLOR][/SIZE][/FONT]
[SIZE=7]THANKS!:KS:KS:KS:KS[/SIZE]

---

### Post by bcbc on 2010-07-28
You don't need to reinstall. When your computer starts, the first thing it does it look for something to boot, in your case, it's your internal hard drive. Then it looks for the master boot record on the drive (where the bootloader is stored). 

What is happening now is that ubuntu replaced your windows bootloader with grub2. That's all (no other damage). And all you need to do is replace it.

In order to do this, you have to boot off some other device. In your case, the CD ROM. But you need to tell the computer to do this.

Two ways - most modern computers have a Boot Options key (it's F12 on my computer). When you first turn it on a screen briefly flashes and shows two things - a key to enter BIOS and a key for boot options. If you can get the boot options key, then it will give you a menu, and you select to boot off the CD/DVD. That's the easiest. 

Once you're booting from your Ubuntu CD, select "Try without installing". Then once it loads the desktop, Click on Applicatios, Accessories, Terminal. This gets you to the command line.
Then run:
```
sudo apt-get install lilo
```
You'll see a popup with some info, tab to OK and hit enter. You can ignore the info - that refers to a different use of Lilo than what you'll be using.
Then install the lilo bootloader in a form that is equivalent to Windows. 
```
sudo lilo -M /dev/sda mbr
```

That should be it, "exit" from terminal, shutdown, removing CD, and reboot.

If you want more explanation, just ask.

---

### Post by rupertismydog on 2010-07-29
would fedora or something do the trick also as the ubuntu live usb does not work,It gets to the menu ok but when you click try without installing it shows the same error message!?

---

### Post by bcbc on 2010-07-29
> **rupertismydog said:**
> would fedora or something do the trick also as the ubuntu live usb does not work,It gets to the menu ok but when you click try without installing it shows the same error message!?

that's strange. Did the live USB ever work?

I haven't used fedora. You should be able to repace your bootloader using any system that can install lilo, or any windows repair cd. 

But the commands to install lilo may be different if it's not debian based, and if it doesn't use sudo you'll have to run it as root.

---

### Post by jokes_finder on 2010-07-29
well, thanks bcbc for the explanation.. very clear, so thanks
I had the same problem but couldn't figure out what's happening so i re-installed Ubuntu and formatted my HDD :( without meaning that..

---

### Post by rupertismydog on 2010-07-29
thanks for help so far:D
 
 
does anyone know of any other debien linux distrobutions apart from ubuntu because
ubuntu does not seem to work...

---

### Post by rupertismydog on 2010-07-29
:KS:KSubuntu now working...
 
got to terminal typed code it installed lilo,
 
then typed the other code
 
more text then closed terminal reebooted and nothing happened...:(:(:(:(:(
 
HAVE I NOT DONE THE PROCESS RIGHT????

---

### Post by bcbc on 2010-07-29
> **rupertismydog said:**
> :KS:KSubuntu now working...
 
got to terminal typed code it installed lilo,
 
then typed the other code
 
more text then closed terminal reebooted and nothing happened...:(:(:(:(:(
 
HAVE I NOT DONE THE PROCESS RIGHT????

Boot the live USB and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). Post the results back (instructions in link)

---

### Post by alenn on 2010-07-29
just reinstall ubuntu and everything will be fine, I had the same problem.

---

### Post by bcbc on 2010-07-29
> **alenn said:**
> just reinstall ubuntu and everything will be fine, I had the same problem.
No, read the thread again. Everything will not be fine,

Computer doesn't boot. Ubuntu installed with WUBI from inside windows.

---

### Post by alenn on 2010-07-30
> **bcbc said:**
> No, read the thread again. Everything will not be fine,

Computer doesn't boot. Ubuntu installed with WUBI from inside windows.

yeah, but don't install ubuntu inside windows, make dual boot, and GRUB will be fixed.

---

### Post by rupertismydog on 2010-07-30
thanks here are results of bootloader....

---

### Post by Jahid65 on 2010-07-30
[FONT=Verdana]@rupertismydog, this happens because of installing via wubi. You should install ubuntu in separate partition. Wubi has some demerits. It installs ubuntu in windows partition. If your windows get crashed, Ubuntu will also crash. Even if you don't shutdown your windows properly, there is possibility of crashing grub in wubi installation. But with separate partition this will not happen.
[/FONT]

---

### Post by rupertismydog on 2010-07-30
[SIZE=7]here are the results of boot info...     [/SIZE]           Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


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
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    24,563,384    24,563,322  27 Hidden HPFS/NTFS
/dev/sda2    *     24,563,712   168,792,063   144,228,352   7 HPFS/NTFS
/dev/sda3         168,792,064   312,578,047   143,785,984   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders, total 1974271 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,974,270     1,974,208   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       18c7ad2a-8a2c-46c6-9b50-cd255c46826c   ext4                                     
/dev/sda1        A288CA59E49BED2A                       ntfs       PQSERVICE                     
/dev/sda2        B898B25F98B21BB6                       ntfs       ACER                          
/dev/sda3        B23EEECD3EEE89A5                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9CDA-7294                              vfat       SAM USB                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

---

### Post by bcbc on 2010-07-30
grub2 is still on your drive MBR. Please try again to install lilo, and this time note what the response is (report any error, it should say 'lilo successfully installed' or something similar.

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

I've also noticed that your root.disk has some issues. Can you tell me if anything strange happened when you ran the lastest updates? Did you have to do a forced shutdown of your computer?

---

### Post by rupertismydog on 2010-07-30
[SIZE=5][COLOR=Magenta][COLOR=Yellow][FONT=Times New Roman][COLOR=DarkRed]here is a log of what I do when I type the code...
Is it as it should be?[/COLOR][/FONT]
[/COLOR]
[COLOR=Red](in purple is what I typed)[/COLOR]

ubuntu@ubuntu:~$ sudo apt-get install lilo[/COLOR][/SIZE]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 413kB of archives.
After this operation, 1,315kB of additional disk space will be used.
Do you want to continue [Y/n]? [SIZE=5][COLOR=Magenta]y[/COLOR][/SIZE]
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main mbr 1.1.10-2 [23.0kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main lilo 1:22.8-8ubuntu1 [390kB]
Fetched 413kB in 0s (508kB/s)
Preconfiguring packages ...
Selecting previously deselected package mbr.
(Reading database ... 129816 files and directories currently installed.)
Unpacking mbr (from .../archives/mbr_1.1.10-2_i386.deb) ...
Selecting previously deselected package lilo.
Unpacking lilo (from .../lilo_1%3a22.8-8ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-8ubuntu1) ...

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian


[SIZE=5][COLOR=Magenta]ubuntu@ubuntu:~$ sudo lilo -m/dev/sda mbr[/COLOR][/SIZE]
usage: lilo.real [ -C config_file ] -q [ -m map_file ] [ -v N | -v ... ]
       lilo.real [ -C config_file ] [ -b boot_device ] [ -c ] [ -g | -l | -L ]
            [ -F ] [ -i boot_loader ] [ -m map_file ] [ -d delay ]
            [ -v N | -v ... ] [ -t ] [ -s save_file | -S save_file ]
            [ -p ][ -P fix | -P ignore ] [ -r root_dir ] [ -w | -w+ ]
       lilo.real [ -C config_file ] [ -m map_file ] -R [ word ... ]
       lilo.real [ -C config_file ] -I name [ options ]
       lilo.real [ -C config_file ] [ -s save_file ] -u | -U [ boot_device ]
       lilo.real -A /dev/XXX [ N ]        inquire/activate a partition
       lilo.real -M /dev/XXX [ mbr | ext ]    install master boot record
       lilo.real -T help             list additional options
       lilo.real -X                internal compile-time options
       lilo.real -V [ -v ]            version information

ubuntu@ubuntu:~$ 
[SIZE=6][COLOR=DarkRed]

still not working...[/COLOR][/SIZE]:(:(:(:(:(

---

### Post by bcbc on 2010-07-30
> **rupertismydog said:**
> 
[SIZE=5][COLOR=Magenta]ubuntu@ubuntu:~$ sudo lilo -m/dev/sda mbr[/COLOR][/SIZE]
Linux is case sensitive. It's a capital M and there is a space between the M and the /. Cut and paste if you are not sure.

```
sudo lilo -M /dev/sda mbr
```

---

### Post by rupertismydog on 2010-07-30
[SIZE=5]It's a miracle![/SIZE]
[SIZE=6][COLOR=SandyBrown]
[COLOR=Yellow]It's such a relief to see my computer now fixed![/COLOR][/COLOR][/SIZE]
[SIZE=7][COLOR=DarkOliveGreen]
thanks bcbc![/COLOR][/SIZE]

---

### Post by bcbc on 2010-07-30
> **rupertismydog said:**
> [COLOR=DarkOliveGreen]
thanks bcbc![/COLOR]

You're very welcome :)

---

### Post by doron387 on 2010-10-16
worked for me also
thanks a lot
doron387

---

### Post by elender on 2010-11-10
din't work for me. i've got the error: lilo is not available anymore

---

### Post by bcbc on 2010-11-10
> **elender said:**
> din't work for me. i've got the error: lilo is not available anymore

lilo is available in the universe repositories. Check your sources (in 10.10 go to System, Administration, Update Manager, Settings; in 10.04 go to System, Administration, Software Sources).

---

