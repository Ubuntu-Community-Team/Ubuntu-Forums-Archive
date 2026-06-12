---
title: "Ubuntu Keeps Crashing!"
date: 2006-06-14
forum: General Help
---

### Post by L2wis on 2006-06-14
Fairly soon after installing Ubuntu as a solo OS on my computer i've found it to keep crashing and requiring a power cycle! It seems fairly random so far it's happened during:

[LIST]
[*]Browsing via Firefox
[*]Emailing via Thunderbird
[*]During Screensaver
[*]Looking at a Files properties
[*]Listening to music via XMMS
[/LIST]

I can still move the mouse around but nothing happens. Anyone else had this problem? My system is as follows:

3200+ Athlon,
9800pro Radeon,
Audigy 4,
1 gig of RAM,

---

### Post by Rui Pais on 2006-06-14
Hi, you need to be more specific and give more information.

If you say you can move the mouse that means that what crashs was not the computer (the OS), but that the X server froze. 
Seems like a agp support problem or something related with your Radeon (usually a bad creature to live under linux)

whats the output of:```
cat Xorg.0.log | grep EE
```?  

can you post too the Section "Device" of /etc/X11/xorg.conf?

---

### Post by sarhento_lobo on 2006-06-14
I would also suggest to check that all pluggable stuff are plugged in nice and tight, specifically the video card. Something like this happened to me too and I almost pulled my hair out trying to find out what it was, only to find that my video card was already coming loose.

Cheers,
sarhento_lobo

---

### Post by zeus77 on 2006-06-14
had a similar problem, but when it hung the HD would crank nonstop.  strangely, i found that my swap partition wasn't working, and i've seen a few other posts related to this problem.  it's mysterious.  try typing 'top' to see how much swap is available.  if it's zero, then that's most likely your problem.  assuming a swap partition exists, but just isn't active, do the following:

```
sudo fdisk -l
```

and note which partition is the swap (we'll call it hdaX).  then, make sure there's a corresponding line in /etc/fstab that says

```
/dev/hdaX   none   swap   sw   0 0
```

then type 

```
sudo mkswap /dev/hdaX
sudo swapon -a
```

---

### Post by matrooswolf on 2006-06-14
I have this same hanging problem.
this is the output from sudo fdisk -l
```

Schijf /dev/hda: 81.9 GB, 81964302336 bytes
255 koppen, 63 sectoren/spoor, 9964 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1   *           1        9305    74742381    7  HPFS/NTFS
/dev/hda2            9306        9962     5277352+   f  W95 Ext'd (LBA)
/dev/hda5            9306        9961     5269288+   b  W95 FAT32
/dev/hda6            9962        9962        8001   82  Linux-swap / Solaris

Schijf /dev/hdb: 122.9 GB, 122942324736 bytes
255 koppen, 63 sectoren/spoor, 14946 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hdb1               2       14946   120045712+   f  W95 Ext'd (LBA)
/dev/hdb5               2       11730    94213161    7  HPFS/NTFS
/dev/hdb6           11731       14943    25808391   83  Linux
/dev/hdb7           14944       14946       24066   82  Linux-swap / Solaris

Schijf /dev/sda: 257 MB, 257949696 bytes
16 koppen, 32 sectoren/spoor, 984 cylinders
Eenheden = cylinders van 512 * 512 = 262144 bytes

```
and this is my /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,umask=0000        0       0
/dev/hda5       /media/hda5     vfat    defaults,umask=0000        0       2
/dev/hdb5       /media/hdb5     ntfs    defaults,umask=0000        0       0
/dev/hda4       none            swap    sw              0       0
/dev/hdb6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     ntfs   defaults,umask=0000     0       0       $

```
something is wrong I think, it looks all mixed up to me, but do you know how I should fix it? (I am a bit chicken when it comes to partitions ;)

---

### Post by ????? on 2006-06-14
Have you tried restarting X? (ctrl-alt-backspace)

---

### Post by Turgon on 2006-06-14
I have the same problem on two of my ubuntu systems. Don't even think I can move the mouse. Hope someone can solve this!

---

### Post by nix4me on 2006-06-14
Mine is doing it too.  Mostly overnight when the screensaver is running.

Anyone filed a bug?

nix4me

---

### Post by Rui Pais on 2006-06-14
> **matrooswolf]something is wrong I think, it looks all mixed up to me, but do you know how I should fix it? (I am a bit chicken when it comes to partitions  said:**
> 

Hi matrooswolf,
something is deeply wrong with those outputs you post. 
Nothing seems to be correct, as an example your fdisk says:
> /dev/hdb7           14944       14946       24066   82  Linux-swap / Solaris

but your fstab says:
[QUOTE]/dev/hdb7       /               ext3    defaults,errors=remount-ro 0       1
 your apparently are mounting your root filesystem at a linux swap.
After give a look i guess you have been deleting some partitions, and whatever you use forget to update partition numeration.
try to do:
```
sudo fdisk /dev/hda
x (enter)
f (enter)
w (enter)
sudo fdisk /dev/hdb
x (enter)
f (enter)
w (enter)

```
and reboot

---

### Post by matrooswolf on 2006-06-14
[QUOTE=Rui Pais]
 your apparently are mounting your root filesystem at a linux swap.
After give a look i guess you have been deleting some partitions, and whatever you use forget to update partition numeration.
[/QUOTE]

Hi Rui Pais.
Thanx!  Yes that what I thought too.  

I think the problem is I once changed my partitions in Windows with partitionmagic (added a fat32), and recently I resized the linux partition (bigger) also with partitionmagic.  I didn't know that would affect the partition numbers.

I am going to look into it tomorrow, and try the fdisk, thanks for the suggestion, but first I need to get some sleep, and I am going to make some backups in case I totally mess up.

---

### Post by Rui Pais on 2006-06-14
I was betting with myself that you used partitionmagic or at least some Windows tools (like MS fdisk or presizer). Thats they signature, an entended partition occupying an entire harddisk and all partitions as logical ones ;)

don't worry with using the f flag with fdisk, is plain inoffensive anf hard to fail (but make backups is an excellent approach).

have a good night sleep.

---

### Post by L2wis on 2006-06-15
**Re: whats the output of: cat Xorg.0.log | grep EE**

Current Operating System: Linux l2wis-Linux 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

**Re: can you post too the Section "Device" of /etc/X11/xorg.conf?**

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	VideoRam	131072
EndSection

[B]Re: I would also suggest to check that all pluggable stuff are plugged in nice and tight.
[/B]
I will check this next in 5 minutes :)

**Re: Try typing 'top' to see how much swap is available.**

I've typed that Top command and I'm not to sure which column is displaying the swap memory being used. But I presume it's Virt, in which case there are numbers in that column.

**Re: Command Fdisk -l:**

Returned this result:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9351    75111876   83  Linux
/dev/hda2            9352        9729     3036285    5  Extended
/dev/hda5            9352        9729     3036253+  82  Linux swap / Solaris

I'm guessing that thats all okay?

**Re:Have you tried restarting X? (ctrl-alt-backspace)**

Yes I have tried this, it doesn't have any effect on the system :(

Guys thanks so much for all the responce so far, i have a feeling this should be fixed soon. Then we can all enjoy ubuntu -stress :D

Thanks in advance.

---

### Post by zeus77 on 2006-06-15
[QUOTE=L2wis]**Re: Try typing 'top' to see how much swap is available.**

I've typed that Top command and I'm not to sure which column is displaying the swap memory being used. But I presume it's Virt, in which case there are numbers in that column.[/QUOTE]

Existence of a swap partition (confirmed via fdisk) is not sufficient evidence for a working swap space.  If 'top' gave you ambiguous results, try typing 

```
cat /proc/swaps
```

which should return the size of your swap if it's working...

---

### Post by L2wis on 2006-06-15
Filename
/dev/hda5

Type:
partition

Size:
3036244   

Used:
0

Priority:
-1

Is the result of that command.

---

### Post by Rui Pais on 2006-06-15
hi L2wis,
sorry i can not help much, i don't have a Radeon for almost 2 years... 
I give up on them cause i got your problem a lot of times (and across several distros).

The only way i managed to get them work then (note that my experiences was with much older kernels and drivers) was compiling agpgart and drm support always as modules and play around with the following options at Device section:
> Option "UseInternalAGPGART" "no"
and/or
> Option "NoAGP" "0" 
(i don't remember exactly which combination...)

Other Options that can control AGP are:
 Option  "KernelModuleParm" "agplock=0"   ## AGP locked user pages
 Option  "AGPFastWrite"  "yes"   ## "no"
 Option  "AGPMode"  "4"   ## "4" means 4x

maybe twicking, turn on/off some of those may get some results. 
I don't know whats defaults right now, [here is a wiki]("http://www.thinkwiki.org/wiki/Additional_options_for_the_radeon_driver") with information about it.

Another suggestion is checking Ati site for the newest drivers possible. Maybe they have some updates that work better then the ones on ubuntu restricted modules.

Check too the suggestion of sarhento_lobo. I never installed a video card that work at first. I need to insert them several times until they decided to work. Agp slots seems to be a little to sensitive... maybe use, fans vibration and box movements may have make your card to be a little loose (is that the term? sorry my english) on the slot.

Another thing, you seems to have a problem with /dev/wacom. Thats the controller for some input device you have. It seems that it fails on you. Searching around i find people with problems even to start an X session with that problem. Maybe is the guilty one for you.
Check [this]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-s3/+bug/40560") and [this thread]("http://www.ubuntuforums.org/showthread.php?t=185930&page=2") from post #9 and ahead.

Good luck.

---

### Post by matrooswolf on 2006-06-15
[QUOTE=Rui Pais]I was betting with myself that you used partitionmagic or at least some Windows tools (like MS fdisk or presizer). Thats they signature, an entended partition occupying an entire harddisk and all partitions as logical ones ;)

don't worry with using the f flag with fdisk, is plain inoffensive anf hard to fail (but make backups is an excellent approach).

have a good night sleep.[/QUOTE]
Thank you, I had (more or less).

I am still hesitating to do the fdisk thing though.

What will fdisk x f and w do?  

And how will fdisk in Ubuntu influence my windows partitions (I still need them, all my music, pictures, etc are on them).  

Wouldn't it be safer to simply change my fstab so it reflects the fdisk output?

The problem is I really don't know enough about partitions, and I don't like to mess around with something so vital if I'm not knowing what I'm doing ...

:confused:

---

### Post by Rui Pais on 2006-06-15
[QUOTE=matrooswolf]Thank you, I had (more or less).

I am still hesitating to do the fdisk thing though.

What will fdisk x f and w do?  

And how will fdisk in Ubuntu influence my windows partitions (I still need them, all my music, pictures, etc are on them).  

Wouldn't it be safer to simply change my fstab so it reflects the fdisk output?

The problem is I really don't know enough about partitions, and I don't like to mess around with something so vital if I'm not knowing what I'm doing ...

:confused:[/QUOTE]

Hi,
the fdisk options:
x -> pass to expert mode, f -> fix order partition, w -> write partition table and exit. 
I used a lot of times and never had any problem or ever see someone who had it, but who knows, there is nothing that is 100% safe. It only change partition numbers, wont move it on disk or even touch anything on it.

I don't think change fstab would be simpler, expecially if you later change again your partition scheme... but, at this point it could be considered safer.
At least you can do it and reboot to see if everything works good and stable. And later on fix the partition order when you feel more secure. 
Note that what is now wrong is that fstab are not according to your partition table. Is not a problem having partition numbering all twisted and out of order. The kernel managed those things completly; it's for you, to make it easier to understand your disks and partition schemes (errors tend to be human or started/induced by our human actions, computers are just the tool that exist to us to blame :lol:)

Anyway, as soon as your Ubuntu is work normaly, give a try to gparted. 
It's an excellent GUI for partitions (and a little like partitionmagic) and will make you feel more confortable dealing with partitions.

---

### Post by matrooswolf on 2006-06-15
[QUOTE=Rui Pais]Hi,
the fdisk options:
x -> pass to expert mode, f -> fix order partition, w -> write partition table and exit. 
I used a lot of times and never had any problem or ever see someone who had it, but who knows, there is nothing that is 100% safe. It only change partition numbers, wont move it on disk or even touch anything on it.

I don't think change fstab would be simpler, expecially if you later change again your partition scheme... but, at this point it could be considered safer.
At least you can do it and reboot to see if everything works good and stable. And later on fix the partition order when you feel more secure. 
Note that what is now wrong is that fstab are not according to your partition table. Is not a problem having partition numbering all twisted and out of order. The kernel managed those things completly; it's for you, to make it easier to understand your disks and partition schemes (errors tend to be human or started/induced by our human actions, computers are just the tool that exist to us to blame :lol:)

Anyway, as soon as your Ubuntu is work normaly, give a try to gparted. 
It's an excellent GUI for partitions (and a little like partitionmagic) and will make you feel more confortable dealing with partitions.[/QUOTE]
Hi Rui, thank you for your help.

I decided to change my fstab for the moment.  If its not a problem for my computer that my partition numbers are mixed up, and only a problem for my human understanding, then I can live with that (there is so much that I don't understand, so a little bit more or less ;))

This is my new fstab, still a mess, but everything mounted right now, and working.```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,umask=0000        0       0
/dev/hda5       /media/hda5     vfat    defaults,umask=0000        0       2
/dev/hdb5       /media/hdb5     ntfs    defaults,umask=0000        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdb7       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     ntfs   defaults,umask=0000     0       0	  

```

This fixed my swap not being available problem, and hence the crashes, (top says it is being used), and I have no crashes for the moment, not even with vmware :-D .

I will give a try to gparted some other time, I will probably be rearranging all my partitions in the near future, (I still have a lot on Ntfs, but I am switching more and more to Linux.)

In the mean time: Muito Obrigado! 

(no, don't get too enthousiastic, that is about all the Portugese I know ;))

---

### Post by Rui Pais on 2006-06-15
matrooswolf, glad to know its working :)
You know little portuguese but at least your pronounce of the "b"s is excellent :lol: joking... Até à vista (see you around)

---

### Post by L2wis on 2006-06-15
[QUOTE=Rui Pais]compiling agpgart and drm support always as modules and play around with the following options at Device section:

and/or

(i don't remember exactly which combination...)

Other Options that can control AGP are:
 Option  "KernelModuleParm" "agplock=0"   ## AGP locked user pages
 Option  "AGPFastWrite"  "yes"   ## "no"
 Option  "AGPMode"  "4"   ## "4" means 4x

maybe twicking, turn on/off some of those may get some results.
[/QUOTE]
I'm not sure how to do either of those ideas :S
[QUOTE=Rui Pais]Another suggestion is checking Ati site for the newest drivers possible. Maybe they have some updates that work better then the ones on ubuntu restricted modules.
[/QUOTE]
I've installed the latest drivers, it's said at the end to save my X window configuration file? 
**How do i do that?**
[QUOTE=Rui Pais]Check too the suggestion of sarhento_lobo. I never installed a video card that work at first. I need to insert them several times until they decided to work. Agp slots seems to be a little to sensitive... maybe use, fans vibration and box movements may have make your card to be a little loose (is that the term? sorry my english) on the slot.
[/QUOTE]
I've ensured it's pluged in firmly, i don't think this is the problem :(
[QUOTE=Rui Pais]Another thing, you seems to have a problem with /dev/wacom. Thats the controller for some input device you have. It seems that it fails on you. Searching around i find people with problems even to start an X session with that problem. Maybe is the guilty one for you.
Check [this]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-s3/+bug/40560") and [this thread]("http://www.ubuntuforums.org/showthread.php?t=185930&page=2") from post #9 and ahead.

Good luck.[/QUOTE]
I'll check these in 5 mins.

---

### Post by L2wis on 2006-06-16
Double post i know appoligues in advance but this problem seems to have been solved =D

After installing the latest ATI drivers (straight over the top of the old ones) I've not yet had a crash, and the screensaver has been coming on and off too =D So anyone else with this problem if you've not tried already do what i did. I didn't save any X file btw.

Thanks

---

### Post by cleggton on 2006-07-05
Guys, 

I also have a problem with Dapper crashing.  Mostly the session stops responding with the mouse still active.  This often happens during the screensave, but also happens during standard use.  Trying to kill the xserver is also futile.   

I am unsure wether this is a swap problem as I am using LVM (i am new to LVM and haven't completely got to grips with it yet).  Top suggests I have 3gb swap free and none used (I have 1gb RAM).  MAybe when swap is being used it is crashing, but my system monitor is showing no usage and I haven caugth it with top running in a terminal.

Down the graphics card route I have an Nvidia geforce4 mx4000.  I have the Nvidia drivers installed.

I have trawled every log that I can think of to find the cause but there seems to be nothing out of the ordinary.

I have also removed all usb hardware to try and get to a base system to avoid any hardware related crashes.
  
Any more suggestions?

---

### Post by cleggton on 2006-07-05
I tell a lie.  I have been working for a couple of hours andchecked top again and my swap is being used.  So I can rule that out.

---

### Post by dspivey on 2006-07-05
here's another post regarding the same issues that contains lots of information, but there's no resolution yet.  This might save you some testing time.

[http://www.ubuntuforums.org/showthread.php?t=193283](http://www.ubuntuforums.org/showthread.php?t=193283)

---

### Post by Rui Pais on 2006-07-05
Hi,
That is usually a problem of the agpgart kernel module and some nvidia/ati video cards/drivers.
Regrettably thats not easy to prevent agpgart to load (blacklist it in most cases is useless).

Maybe trying the latest drivers, they keep trying to solve the problems and later drivers don't seems to be so affected (Nvidia cards, i mean).
Check tseliot's [how-to]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") and [thread]("http://ubuntuforums.org/showthread.php?t=139264").
Check also the Problems Section point 4) 

Setting 
```
Option "RenderAccel" "Off"
Option "NvAGP" "0" 
```
sometimes is enough to solve it for some driver/kernel version combination.

hope that helps

---

### Post by Tails on 2006-07-05
ya... mine using ATI seems to crash almsot every time it went to screensaver..... may be i should disable the screensaver....

---

### Post by dspivey on 2006-07-06
Again, I'll point you to this link:

[http://www.ubuntuforums.org/showthread.php?t=193283](http://www.ubuntuforums.org/showthread.php?t=193283)

Most of your theories have been tested there already and could save you a lot of time.  Everyone sees that xorg is eating up memory, but no one has found the reason just yet.  However, disabling screensavers hasn't resolved, and there are lots of people seeing these problems who don't have ATI or nVidia cards/drivers.

---

### Post by L2wis on 2006-07-06
updating the drivers fixed my computer :D

---

### Post by cleggton on 2006-07-06
The plot thickens.  I wanted to of this was a complete system(kernel) lock or wether it was isolated to Xorg.  Installed SSHD and waited for the inevitable crash.  Whic according to the clock on gnome looks like it happened around 9 this morning.  

Tried to ssh into the machine.  Shock horror, it allowed me to.  Ran top.  most of the memory was used (but i think most of this looks to be used as cache, even running fine it looks well commited on memory) and swap was harly used.  The shocker was the processor use was maxed out at 96-100% - the culprit, Xorg of course.  There does seem to be some life in there. 

I decided that I would try and kill X from top to save another reboot and more potential lost data.  Tried to kill, no luck.  Tried shutdown now,  this seemed to start reducing runlevels and terminated my ssh session, but the x session died badly and looks like it stopped the halt.  

Will check logs now to see if I can find any more info.  This seems to point to X as the weakest link to me.

---

### Post by cleggton on 2006-07-06
Sorry a double post again.

I have tried changing these settings in Xorg as suggested by the howto.

> Option "NvAGP" "0" 
Option "RenderAccel" "Off" 
Option "IgnoreDisplayDevices" "DFP,TV" 
Option "NoRenderExtension" "Off" 
Option "AllowGLXWithComposite" "Off"

I will see how I get on with this.  Does anyone know what the actual result is of these options.

---

### Post by Rui Pais on 2006-07-06
[QUOTE=cleggton]Tried to ssh into the machine.  Shock horror, it allowed me to.  Ran top.  most of the memory was used (but i think most of this looks to be used as cache, even running fine it looks well commited on memory) and swap was harly used.  The shocker was the processor use was maxed out at 96-100% - the culprit, Xorg of course.  There does seem to be some life in there. 

I decided that I would try and kill X from top to save another reboot and more potential lost data.  Tried to kill, no luck.  Tried shutdown now,  this seemed to start reducing runlevels and terminated my ssh session, but the x session died badly and looks like it stopped the halt. [/QUOTE]

Hi,
that's exactly a typical symptom. The box/kernel/Environment is not dead. Just X. Badly frozen.

That's a problem related with kernel agp support and video cards drivers. 
Usually the bad guy of the movie is agpgart module. That, as i said, usually ignore the backlist and get loaded giving that frozes. 
The Option "NvAGP" "0" is exactly to try to workaround that. It tries make video card work ignoring agpgart. Sometimes work. Sometimes a simple "NvAGP" "1" (using internal-from the card- agpgart) is enough. Sometimes no luck with neither (and eventually the only solution is manually compile a kernel without agpgart).

Btw, what driver version are you using? the ones on restricted modules always seems to give more problems that the latest from Nvidia site. Do you followed the tseliot's how-to?

I can find more detailed and technical information searching nvidia forum:
[http://www.nvnews.net]("http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14")



**@dspivey**
That thread, as you said, don't point any solution or special information. A lot of people even use XGL. That, besides experimental, is a full source of problems, not related (at least directly) with this one that can only agravate things. 
Anyway, the only way i finded (and saw others found) was trying different and several approachs. 
There isn't a unique solution (or even ***a*** solution :() So others experiments can only serve to give clues and ideas to try ourselves. In this cases only trying, even when it fails on others, one get a proper way of get out of that hell.

---

### Post by cleggton on 2006-07-06
I checked TS's howto and it looked similar to the procedure that I carried out.  I am using the nvidia-glx from synaptics 1.0.8762  looks like the version number.  I will try these options and report back.  This doesn't seem like an uncommon problem.

---

### Post by cleggton on 2006-07-08
Does look like this has fixed it.  Thankyou so much.

---

