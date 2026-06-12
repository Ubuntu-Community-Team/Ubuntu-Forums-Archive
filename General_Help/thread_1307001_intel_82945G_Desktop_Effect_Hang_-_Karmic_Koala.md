---
title: "intel 82945G Desktop Effect Hang - Karmic Koala"
date: 2009-10-30
forum: General Help
---

### Post by luqeliverpudlian on 2009-10-30
I just installed Karmic Koala on my Desktop, and when i try to enable the Desktop Visual Effect to Normal or Extra, my desktop hangs and can't do anythyn...any ideas to solve it???:(:(

---

### Post by Mike08857 on 2009-10-31
I am having the same problem.  I have a MPC allin one computer and it has a 

Intel 82945G Express Chipset an if I try to Try to change the Visual Effects to NORMAL or above My computer Freezes! 

Does anyone have a solution for this ?? or a Possible Workaround ?

I Love Ubuntu But if I can't get this to work properly I will have to move on the some other Distro or even back to Dreaded M$

---

### Post by Mike08857 on 2009-10-31
xf86-video-intel 2.9.1 Driver is available is this the one included in 9.10 ??

I can enable Extra Effects then as soon as I move a window it freezes.

I have to do a hard reboot and carefully change it back to NONE to use the system.

I used Compiz-Check is a script and got the following info.

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


So I should be able to run compiz fine. 

:(

---

### Post by itsjustarumour on 2009-11-01
Plus one for problems with Karmic and the Intel display driver (on my laptop - don't have details of the driver version to hand at the mo) :(  

I was just setting up Compiz, things were working OK, but then all I did was enable the "Reflection" plugin and the whole thing locked up.  Had to do a hard reboot... now I can't even load the full desktop without it hard locking again.  I've tried dropping down to a console and uninstalling (and later reinstalling) compiz etc, but no joy, my whole system appears to be completely b*ggered  :(


EDIT:  My tech details - Intel Corporation Mobile GME965/GLE960 Integrated graphics, i915 driver

---

### Post by ZarathustraDK on 2009-11-02
1+ in the Intel graphics driver problem. Card: Intel GMA 3100.

Compositing works with the default drivers, but is very slow (slow as in "running around Dalaran with 512mb ram" in WoW-speak).

Is there a fix out there, or is it possible to downgrade to 2.4 in karmic somehow?

---

### Post by Mago on 2009-11-02
there is a way to donwgrade to xserver-xorg-video-intel-2.4 ( [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) )but it wont help, you get a white screen after enabling compiz.

The system doesn't just completely hang. You can still use alt+print screen+"R" and then alt+print screen+"E" to recover keyboard control, then switch to another console with crt+alt+f1, login and reboot sytem.
Just restarting gdm won't do.

all flavours of xserver-xorg-video-intel-2.7 to 2.9 end up freezing the system after some time (less than a minute usualy) once compiz is enabled.

the best way to test this is by enabling compiz with "compiz --replace &" from gnome-terminal. The system will hang once compiz kicks in (at least this way it won't hang seconds after reboot).

---

### Post by Mike08857 on 2009-11-04
:confused:

Anyone have any ideas on how to fix this ???
No reply's on how to correct this problem!?

---

### Post by scontin on 2009-11-05
I have same problem.
When my Intel X3100 lock up (Gigabyte GA-G33M-DS2R), dmesg shows

 render error detected, EIR: 0x00000010
[  506.887756] page table error
[  506.887758]   PGTBL_ER: 0x00100000
[  506.887761] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[  506.887767] render error detected, EIR: 0x00000010
[  506.887769] page table error
[  506.887771]   PGTBL_ER: 0x00100000

So, it's an HW lock.
Compiz bencmark shows 59-60 (vs 130-150 Jaunty with Intel 2.7 and kernel 2.6.30)
Without compiz with metacity compositing enbled, it seems all OK.

---

### Post by scontin on 2009-11-11
@Mago: Compiz problem is related to uxa. in Karmic, only using Accel Mode Uxa make Compiz working.
Today I tested xserver-xorg-video-intel_2.7.0-1ubuntu2_i386.deb.
Now, Compiz benchmark shows 149-150 Frames/sec.
So, it seems a regression in Intel drivers from 2.8 with Compiz.
I'm testing now stability, kernel 2.6.31-14-generic-pae

---

### Post by Peneus on 2009-11-11
I am having  problem with my koala as well. What if I uninstalled compiz.  will tha solve the problem? I will try it tomorrow.

---

### Post by scontin on 2009-11-18
Now, I'm sure problem is UXA.
With Exa, rock solid video.

With Intel drivers 2.7, xorg.conf's options "AccelMethod" "exa", "EXAOptimizeMigration" "true","MigrationHeuristic""greedy", and
downgrade of libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa mesa-utils at Jaunty version (7.4), Compiz is running at 150-160 Frames/sec with EXA acceleration mode.

So, all problems of GMA965 and X3100 are related to the new accel method UXA :popcorn:

---

### Post by budiyanto on 2009-11-19
I also have 82945G display chip, my work around is this:
put this: nolapic nomodeset  at the end of your kernel line in /boot/grub/grub.cfg ,restart. If you can get the desktop fine, no hang. Then run your compiz using : compiz --replace --indirect-rendering. Hope it works!;)

---

### Post by scontin on 2009-11-20
@ budiyanto

I tried your solution.
Perhaps it works (I tested one day), but the performances loss on my Intel Q9550s is absolutely unacceptable.

---

### Post by aasami on 2009-11-24
> **Mike08857 said:**
> xf86-video-intel 2.9.1 Driver is available is this the one included in 9.10 ??

Not yet.[http://www.nanowrimo.org/fr/node/3373197](http://www.nanowrimo.org/fr/node/3373197)

You can find out which version you have installed by typing:
```
apt-cache policy xserver-xorg-video-intel
```

And list currently used module with:
```
grep "LoadModule: \"intel\"" /var/log/Xorg.0.log -A5
```

I don/t know how stable the 2.9.1 driver is, but you can [try it out wit this howto]("http://www.nanowrimo.org/fr/node/3373197").

If you decide to take the rocky road, feel free to share your experiences here.
I wish you luck.

---

### Post by Kaiyusn on 2009-11-24
I have the same problem. Can anyone help me??

---

### Post by Chillawowa on 2009-11-30
Tested the 2.9.1 version of the xserver-xorg-video-intel driver, but the display still freezes when starting xrandr (dual screen). However, this is with Kubuntu 9.10. The composition works(Kwin) at a good speed. 
The graphics card is a GM965 (X3100).

However, by switching off the kernel mode setting (KMS) in GRUB, the problem is fixed, but there is a slight flicker when booting up.

Moritz

---

### Post by Kaiyusn on 2009-12-01
> **Chillawowa said:**
> Tested the 2.9.1 version of the xserver-xorg-video-intel driver, but the display still freezes when starting xrandr (dual screen). However, this is with Kubuntu 9.10. The composition works(Kwin) at a good speed. 
The graphics card is a GM965 (X3100).

However, by switching off the kernel mode setting (KMS) in GRUB, the problem is fixed, but there is a slight flicker when booting up.

Moritz
Could you tell me how to do it? thx

---

### Post by adirea on 2009-12-29
Hi, I recently published the solution to this in [http://picotea.com/](http://picotea.com/) in group GNU/Linux.

Thank you very much, regards.

---

### Post by adirea on 2009-12-29
> **luqeliverpudlian said:**
> I just installed Karmic Koala on my Desktop, and when i try to enable the Desktop Visual Effect to Normal or Extra, my desktop hangs and can't do anythyn...any ideas to solve it???:(:(
Resolve
----------

Hi, I recently published the solution to this in [http://picotea.com/](http://picotea.com/) in group GNU/Linux.

Thank you very much, regards.

---

### Post by Nico666 on 2009-12-29
[QUOTE=adirea;8577485]Hi, I recently published the solution to this in [http://picotea.com/](http://picotea.com/) in group GNU/Linux.


Well, I singed up in that site, just for the solution, and I couldn't find it. Why you not post it just here? Are you promoting that website?

This sounds like spam!

---

### Post by adirea on 2009-12-29
Im sorry but the solution is a very long and the post put it over there.

Regards,

---

### Post by Nico666 on 2009-12-29
> **adirea said:**
> Hi, I recently published the solution to this in [http://picotea.com/](http://picotea.com/) in group GNU/Linux.

Thank you very much, regards.

This is just Pictoea Spammer. Is absolutely unfair use the Ubuntu community in this way. You can't force us to registry in a service to look for a solution, no way!!

For the reasons above I will publish his solution here, and then you don't have to registry in picotea:

1) After install, work in a tty (Control + Alt + F1). and remove the following

```

$ sudo aptitude remove compiz compiz-core 

```

2) After that, reinstall/install the followings

```

sudo apt-get install compiz compiz-core fusion-icon emerald simple-ccsm

```

3) Back to the graphic environment (Ctrl + Alt + F7) and run Compiz Fusion Icon (Apps -> System tools -> Compiz Fusion Icon.

4) The compiz fusion icon should appear in your notification bar, there, right click -> Compiz options -> Indirect Rendering

5) Select Window Manager -> Compiz<

6) Run compiz icon at the start-up: 

System -> Preferences -> Start up apps -> Add
Name: Compiz Fusion Icon
Command: fusion-icon -f
Comment:

7) Reboot

8) Once again in the desktop compiz should work properly. Configure it with

```

$ simple-ccsm

```

as is showed here [http://isopenisfree.wordpress.com/2009/11/29/configurador-simple-de-compiz-fusion/](http://isopenisfree.wordpress.com/2009/11/29/configurador-simple-de-compiz-fusion/) (in Spanish)

Source: [http://picotea.com](http://picotea.com) because **REGISTRATION IS REQUIRED** I published this content here, but I'm not the author.

---

### Post by Nico666 on 2009-12-29
> **adirea said:**
> Im sorry but the solution is a very long and the post put it over there.

Regards,

It is too long to put it here, but not long enough to put it in "Picotea" split in small sections of 160 characters each one?? No way!

I don't want to be unpolite, but for me that was just spam to force people to join in it.

---

### Post by adirea on 2009-12-29
Hi again. As it's required to register to write here, it's required to register to write in Picotea, but you can read the solution without join in. If you search "picotea linux" in google you will arrive to this page [http://picotea.com/es/grupos/gnu-linux-bf05](http://picotea.com/es/grupos/gnu-linux-bf05) and you will be able to see the solution.

It's just another tool to communicate like this. You can consider it as spam, but users there dont't consider spam when I put this address to solve issues about Ubuntu. I appreciate that you have written my blog address in the solution. Regards.

---

### Post by lmivan on 2010-06-10
Thank you for the solution. It woks for me :-D

Regards, Iván.

---

### Post by caith_sit on 2010-07-25
It seems to be working for me too... 

It froze after 30 seconds, it never worked more than that... and now its worked for 1 hour!!!  finally!!!

Thanks!!

---

### Post by tech_freak on 2011-02-20
HURRAY it worked for me too. (same problem of freezing with lucid)
It even worked on Lucid Lynx.
You can check out my thread here=>
			 			[(Lucid Lynx) 10.04 LTS freezes constantly,  only runs stable on failsafeX mode]("http://ubuntuforums.org/showthread.php?t=1690829").

---

