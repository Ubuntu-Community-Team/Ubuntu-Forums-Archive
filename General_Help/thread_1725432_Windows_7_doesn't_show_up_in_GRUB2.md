---
title: "Windows 7 doesn't show up in GRUB2"
date: 2011-04-09
forum: General Help
---

### Post by CedricAnne97 on 2011-04-09
So, as the title says Windows 7 doesn't show up in GRUB2's selection menu, but it does show my Windows XP professional option that I had before Linux and then reinstalled.
After searching very long for the problem in Linux and GRUB2 I decided to boot into XP, witch gave me the option for Windows 7 or older versions of Windows -> so I eventually can boot to it!
So here is the real question: How can I make an entry for Windows 7 and for Windows XP? This is because I'd like to use a theme for GRUB and it would be to stupid to make GRUB look nice if I then come to a stupid screen of the Windows loader!

PS: I'm a total noob to this, so if you could explain everything very precise, I would very much appreciate that! :P
PS2: Please don't mind my spelling, I'm only 13 and Belgian! (I really tried :P)

Already a BIIIG thank you for anybody that has a solution, thanx!

---

### Post by wilee-nilee on 2011-04-09
So if you choose the XP line in grub it takes you to a choice of XP or W7 and they both boot correct?

If this is the case, or if you don't have XP booting but W7 does be exact here also do this.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Your going to need a recovery disc for W7 or a install disc, if some adjustment needs being done, and for any future problems you may have, here is a recovery disc download for W7.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by techunit on 2011-04-09
I problem is likely do to the presence of old boot configs located in some partition on your harddrive.

Because you can essentially side load Windows 7 it appears you have somehow managed to install grub to your Ubuntu partition leaving the Windows Boot Loader in place.

The good thing is everything is working the way it should so you may just want to ignore the problem, as the solution to the problem can require some patience and the use of the terminal.

I am not a expert on this but you may want to take a look at some GRUB related threads here on the forum. You can get started with the one below.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Your best bet is to try reinstalling GRUB but I would see if other people on the forum come to the same conclusion I did.
Best regards hope you get this resolved.

---

### Post by techunit on 2011-04-09
> **wilee-nilee said:**
> So if you choose the XP line in grub it takes you to a choice of XP or W7 and they both boot correct?

If this is the case, or if you don't have XP booting but W7 does be exact here also do this.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Your going to need a recovery disc for W7 or a install disc, if some adjustment needs being done, and for any future problems you may have, here is a recovery disc download for W7.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Wilee-Nilee

Are you thinking that he has preserved the MS Boot Menu? This would explain why gets further options.
Also would his best course of action be to fix the MS Boot Menu first or Reinstall GRUB which would wipe out the MS boot config.

Thanks Good Luck. I'll check back later.

---

### Post by CedricAnne97 on 2011-04-09
Thanks for the very fast reply's, I'll be sure to try it tomorow!
Thanx again!

---

### Post by wilee-nilee on 2011-04-09
> **techunit said:**
> Wilee-Nilee

Are you thinking that he has preserved the MS Boot Menu? This would explain why gets further options.
Also would his best course of action be to fix the MS Boot Menu first or Reinstall GRUB which would wipe out the MS boot config.

Thanks Good Luck. I'll check back later.

Just wanted to get the script up really that will tell what is up. I'm the side of if it is a chain-loaded XP-W7 with grub as the bootloader I would leave it as is.

If the XP is a old and deactivated then this can be dealt with, sounds like a dual MS install though.

---

### Post by CedricAnne97 on 2011-04-10
> **wilee-nilee said:**
> So if you choose the XP line in grub it takes you to a choice of XP or W7 and they both boot correct?

If this is the case, or if you don't have XP booting but W7 does be exact here also do this.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Your going to need a recovery disc for W7 or a install disc, if some adjustment needs being done, and for any future problems you may have, here is a recovery disc download for W7.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
I don't really think I need that live cd or your recovery cd for windows, because I have a working Linux installation and I have the installation dvd of Windows 7 Ultimate (via torrent+WAT remover, does that change anything?) is that correct, or do I need to boot from live cd?
And also: both XP and Windows 7 boot, 7 a bit slower, because it's an old computer, but it boots. As you say, I think that it is the windows bootloader that comes after the grub2 (if this is incorrect, please correct me-as I said in the first post, I'm a noob :P )

---

### Post by CedricAnne97 on 2011-04-10
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Schijf /dev/sda: 80.1 GB, 80060424192 bytes
255 koppen, 63 sectoren/spoor, 9733 cilinders, totaal 156368016 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    22,669,311    22,669,249   7 HPFS/NTFS
/dev/sda2         132,261,888   156,366,847    24,104,960   5 Extended
/dev/sda5         132,263,936   156,014,591    23,750,656  83 Linux
/dev/sda6         156,016,640   156,366,847       350,208  82 Linux swap / Solaris
/dev/sda3    *     22,669,312    65,060,863    42,391,552   7 HPFS/NTFS


blkid -c /dev/null:
```
there it is! If you know anything let me know!

---

### Post by Quackers on 2011-04-10
If you go to System > Admin > Synaptic package manager then enter into the search box "os-prober"  (without quotes), the package os-prober should appear in the main window. Does it have a green box on its left? In other words is it installed - it should be. If not, please install it, then run sudo update-grub in a terminal and watch as grub.cfg is run to see whether the Windows Loader is picked up.
If it is, reboot and you should get a grub menu with Windows on it.

---

### Post by CedricAnne97 on 2011-04-10
Thanks for all your help, but it just got fixed => I was running an update of Ubuntu 10.10 and it magically showed 2 windows options (both windows 7, but I don't really care about that -- the option says Windows 7 but it also says /dev/sda1 or 3 so it should boot xp and 7 only tried 7 yet--)
Only one question: how can I apply a theme to grub2? I already tried one with burg manager and buc -> it didn't look nice - it looked the same as always- how can I solve this?
Again thanks and sorry to start about something else, but I thought I could just ask it here :P
PS: If you've got any tips about how to add an entry ... please let me know, cause I think I'm gonna add another OS :P

---

