---
title: "What am I doing wrong???"
date: 2011-06-20
forum: General Help
---

### Post by JASONFUSARO on 2011-06-20
[SIZE=3]**[COLOR=Red]I want to get into this directory which I can get into in file manager but can't in terminal? Why?[/COLOR]**[/SIZE]

[COLOR=Blue]root@PartedMagic:~# cd /media/sdb1/dosemu
sh: cd: /media/sdb1/dosemu: **[COLOR=Red]No such file or directory[/COLOR]**[/COLOR]

**[COLOR=Red]so I try all these[/COLOR]**

root@PartedMagic:~# ls
clamav/           media@            readme.txt
Desktop/          Network_Settings/

root@PartedMagic:~# cd media@
sh: cd: media@: No such file or directory

root@PartedMagic:~# cd media

root@PartedMagic:~/media# ls
cdrom@  cdrom1@ sda2/   sda3/   sda5/   sda6/   sdb1/   sr0/
root@PartedMagic:~/media# cd sdb1

finally
[B]BUT YET, here it is??

[/B]root@PartedMagic:~/media/sdb1# ls
7zip/                         mbrdrive2.bin*
7-Zip/                        mbrdrive3.bin*
Assembler/                    mbrfix/
Assem_Installers/             mbrtool/
DIY DataRecovery MBRtool 2/   mkbt20.zip*
[COLOR=Red]**DOSEMU/    **[/COLOR]                   pebuilder3110a/
downloadinstallers/           Program Files/
hl2270dwlpr-2.1.0-1.i386.deb* Ruby192/
HxD/                          salix64-fluxbox-13.37.iso*
HxDSetupEN/                   testdisk/
LINUX_DOWNLOADS/              testdisk-6.12.win/
makeboot.bat*                 VB/
Make_IT_BOOT/                 winhex/
manual.pdf*                   WorkinMBR/
mbrdrive1.bin*
[COLOR=Red][B]
BUT then it's not?[/B][/COLOR]

root@PartedMagic:~/media/sdb1# cd dosemu
sh: cd: dosemu: No such file or directory

[COLOR=Red]**so I try all these**[/COLOR]

root@PartedMagic:~/media/sdb1# cd /dosemu
sh: cd: /dosemu: No such file or directory
root@PartedMagic:~/media/sdb1# cd dosemu/
sh: cd: dosemu/: No such file or directory
root@PartedMagic:~/media/sdb1# cd .dosemu
sh: cd: .dosemu: No such file or directory
root@PartedMagic:~/media/sdb1# cd Jason/dosemu
sh: cd: Jason/dosemu: No such file or directory
root@PartedMagic:~/media/sdb1# cd ~/dosemu
sh: cd: /root/dosemu: No such file or directory

[COLOR=Red]**maybe it's not there, so I check one more time and YEP it is there??**[/COLOR]

root@PartedMagic:~/media/sdb1# ls
7zip/                         mbrdrive2.bin*
7-Zip/                        mbrdrive3.bin*
Assembler/                    mbrfix/
Assem_Installers/             mbrtool/
DIY DataRecovery MBRtool 2/   mkbt20.zip*
**[COLOR=Red]DOSEMU/     [/COLOR]**                  pebuilder3110a/
downloadinstallers/           Program Files/
hl2270dwlpr-2.1.0-1.i386.deb* Ruby192/
HxD/                          salix64-fluxbox-13.37.iso*
HxDSetupEN/                   testdisk/
LINUX_DOWNLOADS/              testdisk-6.12.win/
makeboot.bat*                 VB/
Make_IT_BOOT/                 winhex/
manual.pdf*                   WorkinMBR/
mbrdrive1.bin*

[COLOR=Red]**so I google some more and maybe these will get me in**[/COLOR]


root@PartedMagic:~/media/sdb1# cd ~/dosemu
sh: cd: /root/dosemu: No such file or directory
[COLOR=Red][B]
NOPE[/B][/COLOR]

root@PartedMagic:~/media/sdb1# cd ~/media/sdb1/dosemu
sh: cd: /root/media/sdb1/dosemu: No such file or directory

[COLOR=Red]**NOPE**[/COLOR]

root@PartedMagic:~/media/sdb1# 
[SIZE=3][COLOR=Blue][B]

AND PLAYING HIDE AND SEEK SUCKS

HELP PLEASE!![/B][/COLOR][/SIZE]

---

### Post by idoitprone on 2011-06-20
Mac and Linux are case-sensitive, but not windows

```
cd DOSEMU
```

---

### Post by mastablasta on 2011-06-20
is the cd mounted in terminal?

---

### Post by smithk on 2011-06-20
Did you combine using MAC and LINUX?
This was a sensitive One...

---

### Post by idoitprone on 2011-06-20
> **smithk said:**
> Did you combine using MAC and LINUX?
This was a sensitive One...

case-senstive

mac and linux
```
ls

Dog ant lIon LION

cd dog
No such file exist
cd Dog
pwd
/Dog
cd ant
pwd
/ant
cd lion
no such file exist
cd Lion 
no such file exist
cd LION
pwd
/LION
```


windows
```
dir
Dog ant lIon


cd Dog
pwd
\Dog
cd ant
pwd - dont know windows equivelent
\ant
cd LION
pwd
\lion
```

---

### Post by JASONFUSARO on 2011-06-20
after a good nights sleep and presto!!


root@PartedMagic:~/media/sdb1/DOSEMU# ls
bisonpp.pl*                 freedos/
BUGS*                       INSTALL*
ChangeLog*                  install-sh*
ChangeLog.ancient*          install_systemwide*
ChangeLog.old*              Makefile*
compiletime-settings*       Makefile.conf.in*
compiletime-settings.devel* man/
compiletime-settings.help*  mkkeytables*
configure*                  mknewyear*
configure.ac*               mkpluginhooks*
COPYING*                    NEWS*
COPYING.DOSEMU*             QuickStart*
\ /)
(O.o)
(> <)
default-configure*          README*
dist/                       README.bindist*
doc/                        rebuild*
dosemu-1.4.0/               set-permissions*
dosemu-1.4.0-1.i386.rpm*    setup/
dosemu-1.4.0.tgz*           setup-dosemu*
dosemu-freedos-bin.tgz*     src/
dosemu.spec.in*             THANKS*
etc/                        VERSION*
FDchange.log*               ViewDocs*
root@PartedMagic:~/media/sdb1/DOSEMU# 


YEP there she is, well a great many thnaks to sir Mr. idiotprone!!!!
this thank you comes with many bows to you sir

all my hours of typing, staring at the screen looking for inadvertent periods, googling links and to think it was so simple!!!
Hold this gun for me while I pull the trigger, and make sure it stays aimed at my forehead please


but wait don't leave me now, assist me with my other problems please, I went to bed after I ran an install of Fluxbox which died when it started to download each file, now I have something else to clean off my harddrive!!!

Check out my thread Stuck in Limbo please, I really need the help, Maybe there are others out there experiencing my bad dream to?? I should have installed DreamLinux instead!!

thank you

---

