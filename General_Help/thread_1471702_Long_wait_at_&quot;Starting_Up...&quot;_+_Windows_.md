---
title: "Long wait at &quot;Starting Up...&quot; + Windows Load Problem"
date: 2010-05-03
forum: General Help
---

### Post by jschille on 2010-05-03
Installed 10.04 last night and started to have some troubles with the computer.

On the Ubuntu side my start-up speed has increased by quite a bit.
I get a long pause after I select 10.04 from my grub screen 
"Starting up..." takes a while.

Someone mentioned something about having Grub 2 vs Grub 1?
Forgive me, I am very new and have no idea how to check which version of Grub I have.

It does say Grub Loading Stage 1.5 as it starts up...

Someone else mentioned something about drivers
System -> Admin -> Hardware Drivers
Three drivers appear.
1) NVIDIA accelerated graphics driver (version 173)
2.) Broadcast STA wireless driver
3) NVIDA accelerated graphics driver (version current) [Recommended]
The third one is activated, so that feels right.

And then, on the Windows side of things.
Right after I installed 10.04 and then tried to select my window's partition it would not load.  It just got stuck in a never ending loop of "Starting Windows...". Had to force shut down and then Windows made me go through this long process of trying to revive it to an older point....

Has anyone else this problem with the Window's load and the long load into Ubuntu. 
Doubt this matter's but the new loading screen for Ubuntu (UBUNTU with the red and white dots under it) is not the greatest resolution, quite pixelly...

Thanks for your help.

---

### Post by jschille on 2010-05-03
/bump for love

---

### Post by oldfred on 2010-05-03
If it says loading stage 1.5 it is grub legacy or 0.97. To check:
Grub version:
grub-install -v
lsb_release -a
dpkg -l 'grub*'

Did you see instruction on installing grub to all the MBR but also installed it to all the partitions overwritting the windows boot loader in the windows partition boot or PBR? (Many have) 

This fixes it for most, some seem to have additional problems:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I installed the recommended Nvidia driver and it worked just fine.

---

### Post by jschille on 2010-05-03
Thank you for the response Oldfred.

Typed in your commands and this is what it spit out for me.

jb@jb-laptop:~$ grub-install -v
grub-install (GNU GRUB 0.97)
jb@jb-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04 LTS
Release:    10.04
Codename:    lucid
jb@jb-laptop:~$ dpkg -l 'grub*'
Desired=Unknown/Install/Remove/Purge/Hold
|  Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  grub           0.97-29ubuntu6 GRand Unified Bootloader (Legacy  version)
ii  grub-common    1.98-1ubuntu5  GRand Unified Bootloader, version 2  (common 
un  grub-coreboot  <none>         (no description available)
un  grub-doc       <none>         (no description available)
un  grub-efi       <none>         (no description available)
un  grub-efi-amd64 <none>         (no description available)
un  grub-efi-ia32  <none>         (no description available)
un  grub-emu       <none>         (no description available)
un  grub-ieee1275  <none>         (no description available)
un  grub-legacy-do <none>         (no description available)
un  grub-linuxbios <none>         (no description available)
un  grub-pc        <none>         (no description available)
un  grub2          <none>         (no description available)


How does that look?
In regards to the long load, any idea?
It sits on the Starting Up for about 14 seconds.

I'll follow the steps in your link and let you know what happens.

Thanks Fred.

EDIT: Do I need to upgrade GRUB?

---

### Post by jschille on 2010-05-03
In Reply to the Link - 
Windows is booting now. Thank you Fred.
Still long load for Ubuntu to start up though.

Any more secrets for me Fred?

---

### Post by tmt345 on 2010-05-03
I don't know if this is related to this but I hope so... I noticed that the underscore blinks for a fairly long time during startup. Here's what I got when I entered that command:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  grub           <none>         (no description available)
ii  grub-common    1.98-1ubuntu5  GRand Unified Bootloader, version 2 (common 
un  grub-coreboot  <none>         (no description available)
un  grub-doc       <none>         (no description available)
un  grub-efi       <none>         (no description available)
un  grub-efi-amd64 <none>         (no description available)
un  grub-efi-ia32  <none>         (no description available)
un  grub-emu       <none>         (no description available)
un  grub-ieee1275  <none>         (no description available)
un  grub-legacy    <none>         (no description available)
un  grub-legacy-do <none>         (no description available)
un  grub-linuxbios <none>         (no description available)
ii  grub-pc        1.98-1ubuntu5  GRand Unified Bootloader, version 2 (PC/BIOS
un  grub2          <none>         (no description available)

I have a new computer so I think I should be able to get this new "10 second boot" but it just ain't happening :(

---

### Post by oldfred on 2010-05-03
I did a clean install of Karmic so I went thru the conversion to grub2 and learned the differences ( a lot).  

A few systems seem not to work or work well with grub2. I not sure if users just gave up and went back or had problems. There are some HP & Dell's with software that overwrites parts of grub2 and causes problems.

Grub2 has worked fine for me on two systems.

---

### Post by micheledm on 2010-05-03
Maybe I'm affected from the same problem. The boot time is 63 secs for me, it hangs around 20 secs from grub to the splash screen and the remaining time is to get to the login menu.
This is my bootchart.

[[IMG=http://img140.imageshack.us/img140/3074/micheledmlaptoplucid201.png][/IMG]](http://img140.imageshack.us/i/micheledmlaptoplucid201.png/)

I've got a Dell 1330m, i heard about a bug caused by the ghost floppy enabled from the bios, but i can't find any way to disable from there.

---

### Post by oldfred on 2010-05-03
I do not know how to read boot charts and they usually are too small for my eyes, even the one I ran once.

I look in the log files system, administration, log file viewer. I look for errors, warnings and some logs show times for long delays (time diff) to try to narrow down where a problem may be. I think Karmic takes about 1 minute on my portable but my test install of Lucid is very quick. I am sure as I add some things it may get slower.

---

### Post by Usabent on 2010-05-03
They could  have released ubuntu 10.04 a little bit later there are so many bugs! On the rc none at all! What the heck? Now im getting worried if i should install ubuntu or not...

---

