---
title: "Get Windows Stuff..."
date: 2006-02-18
forum: General Help
---

### Post by mofomikeman on 2006-02-18
How do I recover stuff, my windows installation is screwed...  Its NTFS.

---

### Post by cilynx on 2006-02-18
Is the machine dual booting Windows and Linux or are you looking to use a Live CD as a rescue disc?

What are you looking to accomplish?

Details are good things =)

---

### Post by mofomikeman on 2006-02-18
LOL Dual Boot.  I need to get my stuff back, i g2g, ill check this thread tommorow, please dont ask a dumb question lol, i want the answer in the morning :KS

---

### Post by cilynx on 2006-02-18
Well, aren't we demanding... =)

Generally speaking, Ubuntu lets you pick somewhere to mount your Windows partition during the installation process.  Mine is at /media/hda1/.

```

rcw@pyth:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2             22359424   7728768  13494864  37% /
varrun                  257716       116    257600   1% /var/run
varlock                 257716         4    257712   1% /var/lock
udev                    257716       112    257604   1% /dev
devshm                  257716         0    257716   0% /dev/shm
/dev/hda1             15116836  10104032   4244900  71% /media/hda1
rcw@pyth:~$

```

If your 'df' doesn't show your Windows partition as mounted, you may have to do it yourself.

Assuming your Windows partition was on hdb1, you could do:

```

mount -t ntfs /dev/hdb1 /mnt

```

After that, your whole Windows partition should be available under /mnt

Good Luck

---

### Post by Protex on 2006-02-18
You know, for someone who is asking the help of others, you really are quite impatient.

---

### Post by Cesium on 2006-02-19
[QUOTE=Protex]You know, for someone who is asking the help of others, you really are quite impatient.[/QUOTE]
According to urbandictionary.com: 
**MOFO**="Short for mo*#&@ f%^^er. A person who thinks they are the s&#t, dressed down with sagging pants, a high need for a belt, too much gold to make the national reserve jealous, and an attitude that stems from not having parents who knew how to refrain from the use of crack cocaine." :D

---

### Post by mofomikeman on 2006-02-19
Well Here is what i see in /dev/
(the hd's)
hda
hda1
hdb
hdb1
hdb2
hdb3
hdb5
hdc
hdd

Their all harddrive icons with an X in the top right corner.

mounted are the following:
```
mofomikeman@mikeslinuxsystem:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdb2             20809632   4913612  14838944  25% /
tmpfs                   387520         0    387520   0% /dev/shm
/dev/hdb1            134215008  48105284  86109724  36% /mnt
```

And sorry for sounding demanding yall, but I've been looking for an answer for ever.

---

### Post by mofomikeman on 2006-02-19
Oh and this:
```
mofomikeman@mikeslinuxsystem:~$ mount
/dev/hdb2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/hdb1 on /mnt type ntfs (rw)
/dev/hda1 on /mnt type ntfs (rw)

```

---

### Post by kaamos on 2006-02-19
Try this:
```
sudo umount /dev/hda1
sudo mkdir /media/hda1
sudo chmod 555 /media/hda1
sudo mount /dev/hda1 /media/hda1 -t ntfs -o nls=utf8,umask=0222
```
and
```
sudo umount /dev/hdb1
sudo mkdir /media/hdb1
sudo chmod 555 /media/hdb1
sudo mount /dev/hdb1 /media/hdb1 -t ntfs -o nls=utf8,umask=0222
```
Now you should be able to access them from your desktop.

---

### Post by mofomikeman on 2006-02-19
It takes forever to load the drives now... it took a little time before, but I'm still loading hda1...

---

### Post by mofomikeman on 2006-02-19
[QUOTE=kaamos]Try this:
```
sudo umount /dev/hda1
sudo mkdir /media/hda1
sudo chmod 555 /media/hda1
sudo mount /dev/hda1 /media/hda1 -t ntfs -o nls=utf8,umask=0222
```
and
```
sudo umount /dev/hdb1
sudo mkdir /media/hdb1
sudo chmod 555 /media/hdb1
sudo mount /dev/hdb1 /media/hdb1 -t ntfs -o nls=utf8,umask=0222
```
Now you should be able to access them from your desktop.[/QUOTE]
Yeah, cool, but how do I make it not take an hour (I have a gig of RAM, P IIII, why does it lag?).

Oh and its still not open...

---

### Post by mofomikeman on 2006-02-19
[QUOTE=mofomikeman]Yeah, cool, but how do I make it not take an hour (I have a gig of RAM, P IIII, why does it lag?).

Oh and its still not open...[/QUOTE]
and its open. oh, when i weant to this window it went white again, great..

---

### Post by kaamos on 2006-02-19
Calm down man, this not a paid tech support service for your company or anything!!

What happens when you open a terminal and type "cd /media/hda1 && ls -la" ?

---

### Post by mofomikeman on 2006-02-19
```
total 1404700
dr-xr-xr-x  1 root root      32768 2006-02-15 14:22 .
drwxr-xr-x  7 root root       4096 2006-02-19 13:19 ..
dr-xr-xr-x  1 root root          0 2005-11-27 11:34 15_skins_lolz
-r-xr-xr-x  1 root root      10606 2004-05-23 00:26 1649.txt
dr-xr-xr-x  1 root root          0 2005-11-26 22:45 640hud7
dr-xr-xr-x  1 root root          0 2005-10-18 10:50 addons
dr-xr-xr-x  1 root root       4096 2005-11-19 12:11 Adminmod
-r-xr-xr-x  2 root root     236904 2005-11-08 21:07 aim_night-dust.bsp
dr-xr-xr-x  1 root root          0 2005-11-15 16:15 aiord
dr-xr-xr-x  1 root root          0 2006-02-02 20:46 Akira
-r-xr-xr-x  1 root root     135731 2006-02-02 20:50 Akira.zip
dr-xr-xr-x  1 root root       4096 2005-11-05 10:56 AMX Mod X
dr-xr-xr-x  1 root root          0 2005-12-22 10:23 arcade
-r-xr-xr-x  1 root root          0 2005-08-08 18:54 AUTOEXEC.BAT
dr-xr-xr-x  1 root root          0 2005-11-29 20:00 awp_arena
-r-xr-xr-x  1 root root     921654 2005-12-08 16:04 blackout.bmp
dr-xr-xr-x  1 root root       8192 2005-12-06 15:55 blog mod
-r-xr-xr-x  1 root root        186 2005-11-05 12:04 BOOT.BKK
-r-xr-xr-x  1 root root        219 2005-11-15 15:53 boot.ini
dr-xr-xr-x  1 root root       4096 2005-12-06 16:57 CashMod223
dr-xr-xr-x  1 root root       4096 2005-10-28 19:33 composer
dr-xr-xr-x  1 root root          0 2006-02-14 10:20 Config.Msi
-r-xr-xr-x  1 root root          0 2005-08-08 18:54 CONFIG.SYS
dr-xr-xr-x  1 root root      36864 2006-01-26 19:00 converted
dr-xr-xr-x  1 root root      12288 2005-11-13 13:23 Converted HLSS Wavs
dr-xr-xr-x  1 root root          0 2006-01-26 18:58 Converted Music
dr-xr-xr-x  1 root root          0 2006-01-20 15:31 ConverterOutput
dr-xr-xr-x  1 root root      20480 2005-12-06 16:29 cs
dr-xr-xr-x  1 root root          0 2005-12-09 16:11 cs-hacked.com-ecstaticcheatv737
dr-xr-xr-x  1 root root          0 2005-12-25 15:49 css hacks
dr-xr-xr-x  1 root root          0 2005-11-22 15:55 cstrike shizzle
-r-xr-xr-x  1 root root    6368287 2005-11-23 10:11 cstrike.zip
-r-xr-xr-x  1 root root      53248 2006-02-15 14:21 cygwid.exe
dr-xr-xr-x  1 root root          0 2005-11-23 09:53 deagle_18
dr-xr-xr-x  1 root root       4096 2005-11-12 15:11 DELL
dr-xr-xr-x  1 root root          0 2005-12-24 15:57 Dell720
dr-xr-xr-x  1 root root          0 2005-08-26 15:05 Digidesign Databases
dr-xr-xr-x  1 root root       4096 2006-02-15 14:25 Documents and Settings
dr-xr-xr-x  1 root root       4096 2005-11-18 16:49 Download
dr-xr-xr-x  1 root root       4096 2006-02-04 11:22 Downloads
-r-xr-xr-x  2 root root      28672 2006-02-15 14:20 drsmartload1.exe
dr-xr-xr-x  1 root root       4096 2005-12-06 16:50 easymod
dr-xr-xr-x  1 root root       4096 2005-11-26 17:45 forum
dr-xr-xr-x  1 root root       4096 2005-12-16 13:49 Fraps
dr-xr-xr-x  1 root root          0 2005-12-28 16:10 Games
-r-xr-xr-x  2 root root      36864 2006-02-15 14:22 gimmygames.exe
dr-xr-xr-x  1 root root     258048 2005-12-15 17:41 girl
-r-xr-xr-x  1 root root     327294 2005-12-15 17:38 girl.bmp
dr-xr-xr-x  1 root root       4096 2005-12-22 16:41 GoldBullion
dr-xr-xr-x  1 root root          0 2005-11-15 16:00 GunZ
dr-xr-xr-x  1 root root          0 2005-12-16 15:22 hack
dr-xr-xr-x  1 root root          0 2005-11-19 14:29 hawkaa
dr-xr-xr-x  1 root root          0 2005-12-16 16:13 higrow
dr-xr-xr-x  1 root root       8192 2005-11-05 07:57 hlserver2
dr-xr-xr-x  1 root root      12288 2005-11-27 10:20 hlserver3
dr-xr-xr-x  1 root root       8192 2006-02-15 13:20 hlserver4
dr-xr-xr-x  1 root root          0 2005-10-18 17:01 hlss
dr-xr-xr-x  1 root root       4096 2005-10-19 15:30 hl s s
dr-xr-xr-x  1 root root          0 2005-12-01 15:37 HSF
dr-xr-xr-x  1 root root      24576 2005-12-04 17:17 icytower1.2
-r-xr-xr-x  2 root root       4096 2006-02-15 14:20 inst_0004.exe
-r-xr-xr-x  2 root root     578560 2006-02-15 14:22 Installer.exe
-r-xr-xr-x  2 root root     422912 2006-02-15 14:21 installerus.exe
-r-xr-xr-x  1 root root          0 2005-08-08 18:54 IO.SYS
-r-xr-xr-x  1 root root       6095 2006-02-12 14:45 iPod_log.txt
-r-xr-xr-x  1 root root         14 2006-01-03 17:35 klttd323.dll
dr-xr-xr-x  1 root root          0 2005-11-18 15:04 metapad
dr-xr-xr-x  1 root root       4096 2005-12-10 13:03 mexican_motor_mafia_kg_nowa
dr-xr-xr-x  1 root root       4096 2005-12-10 16:27 monkey
dr-xr-xr-x  1 root root       4096 2005-12-06 16:35 mother
-r-xr-xr-x  1 root root          0 2005-08-08 18:54 MSDOS.SYS
-r-xr-xr-x  2 root root      25105 2006-02-15 14:21 MTE3NDI6ODoxNg.exe
dr-xr-xr-x  1 root root       4096 2005-11-19 17:33 MY FOLDER
dr-xr-xr-x  1 root root          0 2005-10-18 10:30 New Folder
dr-xr-xr-x  1 root root          0 2005-11-22 16:44 New Folder (2)
-r-xr-xr-x  2 root root     266240 2006-02-15 14:22 NNSCAA638.EXE
-r-xr-xr-x  1 root root      47580 2003-07-16 15:39 NTDETECT.COM
-r-xr-xr-x  1 root root     233632 2003-07-16 15:39 ntldr
dr-xr-xr-x  1 root root          0 2005-12-25 11:06 NVIDIA
-r-xr-xr-x  1 root root 1207959552 2006-02-15 09:54 pagefile.sys
dr-xr-xr-x  1 root root       4096 2006-01-08 12:16 PeN15
-r-xr-xr-x  1 root root      11736 2005-11-26 17:06 pldecal.wad
dr-xr-xr-x  1 root root       4096 2006-02-04 19:00 podbotwaypoints
dr-xr-xr-x  1 root root      73728 2006-02-15 14:25 POOP
-r-xr-xr-x  1 root root       2190 2005-12-11 17:45 poop.htm
-r-xr-xr-x  2 root root         20 2005-12-11 17:22 poop on you.txt
dr-xr-xr-x  1 root root      49152 2006-02-15 14:22 Program Files
dr-xr-xr-x  1 root root          0 2005-11-04 14:03 RECYCLER
-r-xr-xr-x  1 root root         26 2005-12-22 16:47 register.js
-r-xr-xr-x  1 root root          0 2006-01-05 20:09 report.htm
-r-xr-xr-x  1 root root       2035 2005-11-15 17:46 rsdl.xpi
-r-xr-xr-x  2 root root       1209 2005-11-15 17:46 rs-ff-install.html
-r-xr-xr-x  2 root root        237 2005-12-15 15:33 runescape.txt
dr-xr-xr-x  1 root root       4096 2005-11-19 11:51 script
dr-xr-xr-x  1 root root          0 2005-11-06 10:53 Sierra
dr-xr-xr-x  1 root root          0 2005-11-26 22:51 spriteexplorer_v20
-r-xr-xr-x  1 root root     129204 2006-02-15 14:22 SS1001.exe
-r-xr-xr-x  2 root root      14848 2006-02-15 14:21 stub_113_4_0_4_0.exe
dr-xr-xr-x  1 root root       4096 2005-11-26 22:42 stuff
-r-xr-xr-x  2 root root   52320619 2005-12-16 20:19 Stunt GP.zip
dr-xr-xr-x  1 root root       4096 2005-11-26 18:01 subSilver
dr-xr-xr-x  1 root root       4096 2006-02-15 14:11 superspray
dr-xr-xr-x  1 root root          0 2005-12-14 19:50 superswitch
-r-xr-xr-x  2 root root  146600448 2005-12-14 19:48 superswitch.avi
dr-xr-xr-x  1 root root    1241088 2005-12-08 14:09 surf demo
-r-xr-xr-x  2 root root    5876736 2005-12-08 14:28 surf demo.avi
dr-xr-xr-x  1 root root          0 2005-11-20 20:37 surf_ski
dr-xr-xr-x  1 root root       4096 2005-11-04 14:02 System Volume Information
dr-xr-xr-x  1 root root          0 2006-01-21 11:21 Temp
dr-xr-xr-x  1 root root      32768 2005-12-16 13:34 to convert
dr-xr-xr-x  1 root root          0 2005-11-28 16:32 tutorial
-r-xr-xr-x  2 root root     517168 2006-02-15 14:22 ucmoreiex.exe
-r-xr-xr-x  1 root root     467968 2006-02-15 14:21 visfx500.exe
dr-xr-xr-x  1 root root          0 2005-12-28 15:57 vmex
-r-xr-xr-x  1 root root        480 2006-02-13 13:45 win32.sys
dr-xr-xr-x  1 root root      73728 2006-02-15 14:22 WINDOWS
-r-xr-xr-x  1 root root   12756992 2005-12-14 19:23 yeah.avi
-r-xr-xr-x  2 root root        375 2006-02-02 20:50 ZANZER.COM.AKIRA.README.TXT
```

---

### Post by mofomikeman on 2006-02-19
NOTE: only does it on hda1.  different hdd that this one.  the other drive works fine.

---

### Post by mofomikeman on 2006-02-19
How do I make a drive writeable?  I tried chmoding it and it said its a read-only drive.

sorry for being pissy, ive been working on this for like a month (i suck at linux)

---

### Post by kaamos on 2006-02-19
You can't (safely) write to ntfs from linux. Thank Microsoft for not releasing the specs for ntfs. Use fat32 if you want to have a drive you can write to from both windows and linux.

---

### Post by mofomikeman on 2006-02-19
Heres the problem:  I have about, oh, 130 gig of data on that drive.  It has about 30 gig of space left, which is about what I need to back up.  I have no dvd burner.  So how do I (unsafely) write to it?

---

### Post by kaamos on 2006-02-19
Kind of a bad idea to use a method that potentially corrupts the filesystem to back up data. If you really want to, using google should get you started. I rather suggest you get for example an external usb hd and copy the data there from the ntfs drive with ubuntu.

---

### Post by mofomikeman on 2006-02-19
[QUOTE=kaamos]Kind of a bad idea to use a method that potentially corrupts the filesystem to back up data. If you really want to, using google should get you started. I rather suggest you get for example an external usb hd and copy the data there from the ntfs drive with ubuntu.[/QUOTE]
What is a drive known to be compatible with ubuntu and windows?

---

### Post by kaamos on 2006-02-19
Just about all usb devices that mount as disk drives are. I have a Lacie usb hdd and it came formatted with fat32 and works just perfectly with ubuntu.

---

### Post by mofomikeman on 2006-02-19
I decided to **** it...  I'm just gonna format.  How come I can't format  that partition in the Disks Manager?

---

