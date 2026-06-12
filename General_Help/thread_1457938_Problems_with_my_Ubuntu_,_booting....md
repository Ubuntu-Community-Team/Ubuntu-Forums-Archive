---
title: "Problems with my Ubuntu , booting..."
date: 2010-04-19
forum: General Help
---

### Post by kasabia on 2010-04-19
Hello, and welcome to this thread *:)*... I hope i haven't posted in the wrong section... anyway i have a problem with my ubuntu ( i am a newb with this OS, i just want to get rid of windows becauses it starts to stress me a lot! windows fails , linux is the future :lolflag:)
 
So the problem is that my ubuntu doesn't boot, i've tried :
-reinstalling
-changed the partitions
-repair a broken OS
-check disk
Nothing worked, i even tried something i found on other posts but same...
i really don't know what to do.
 
My computer spec:
ASUS P5P800-VM Motherboard
Intel DUal core (3.0GHZ)(x2)
3GB ram DDR400
Ati RADEON SAPPHIRE 3850HD AGP (512mb)
2 HDD's (1st 80GB, 2nd 250GB)
Monitor: As you can see in the videos below, it's a samsung TV
_[COLOR=#810081][http://www.youtube.com/watch?v=T1oKzzpsAUk](http://www.youtube.com/watch?v=T1oKzzpsAUk)[/COLOR]_
[http://www.youtube.com/watch?v=C50ibjT0t5U](http://www.youtube.com/watch?v=C50ibjT0t5U)
(where i stopped the movies, in those "places" ubuntu stops loading, (you know it doesn't boot anymore) 
 
PS: I tried to install Xubuntu, Kubuntu, even the alternative CD of Ubuntu, they all did the same, even changed some settings in Bios but still the same.
 
Thank you, and sorry for my bad english, if i had some grammar problems.

---

### Post by klemes on 2010-04-19
I am sorry I cannot watch the videos you provided because I have no broadband where I am right now(just using my cell phone for internet connectivity and there is no 3G here also).
My only remark regarding your hardware specification is that they are relatively modern and as such you should choose a distro with the latest kernel.I would go with Ubuntu 10,4 LucidLynx beta2 if I were you instead of trying anything else.
But if you choose not to go this way then somethings you could try although it is doubtful if they succeed is when booting into grub (when you see the menu with the available Linux kernels and other OS's in your machine) is to highlight with the arrow keys of your keyboard a kernel and then hit the 'e' key in your keyboard .This way you will be able to edit the line.So scroll back at the very end of this line and type (try one at a time):

acpi=off
noapic
nolapic

and then hit ENTER and then the 'b' key so you can boot.
If something of the above works and you are finally able to boot into Ubuntu consider adding it permanently in your /boot/grub/menu.lst or your /boot/grub/grub.cfg accordingly depending if you have grub or grub2.
As a last resort you should also try perform a BIOS update but only if you are familiar with the procedure.

---

### Post by linden940 on 2010-04-19
best thing I can think of would be FIRST check the hardware list here

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

once you did that and find out all is good and all should run ubuntu then we can mark that off the list once thats marked off the list then you should do a bench test if you dont know what that means read bottom of post.

after doing a bench test we will know alittle bit more then now...I BET all your hardware IS supported BUT I have had hardware that WAS not support (just my luck) and I never thought to check it..until HRS later and...well lets say I never did need that hair cut LMAO

[CENTER]Bench testing[/CENTER]

since you KNOW your computer will turn on there will be no need for you to take the "guts" out of your computer an put on a cardboard box...BUT do this...take out everything of your computer BUT the bare bones...ONE ram chip NO video card ONE HDD mouse and key-bored ONE cd drive...all other drives unplug them...thats all...what you what to find out is....will it work then?

and by the way...when you do this...unplug the computer before you do anything and when you turn it on put the live cd in the cd tray and go at it

---

### Post by kasabia on 2010-04-19
tried the things you suggested , and i did something i found on the net... to delete "quiet" thingy... done that this is what it sais:
 
...
Begin: loading essential drivers... ...
Done.
Begin: Running /scripts/init-premount ...
done
begin: mounting root file system
begin: running /scripts/local-top
done.
begin: running /scripts/local-premount
done
begin Running /scripts/local-bottom
done 
done
begin: running /scripts/init-bottom
begin: starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 3.5
done.
done. 
 
and it gets stuck...
i'll go buy a cd and burn version 10 on it maybe it might work.. i hope ( btw can u update from the version that is now to the new one that will be out soon without reinstalling and stuff? (sry for the stupid question but i am new with linux :D i used old versions of linux and then switched to windows... )(now it makes me really angry just to see it ... windows 7 is a little better but still fails, you install something on it then the registries get fkd up... and in like 4-5 months u need to reinstall it *sighs*.

---

### Post by linden940 on 2010-04-19
ooo and forgot to say....before to power on the computer when your doing the bench testing clear your cmos either by the jumpers or by the bat thats in there...if by the jumpers...power cord needs to be plug in...if by the bat...(from what i hear) the plug needs to be unplug 

to know the settings of the cmos look in your motherborad user guide

---

### Post by kasabia on 2010-04-19
> **linden940 said:**
> ooo and forgot to say....before to power on the computer when your doing the bench testing clear your cmos either by the jumpers or by the bat thats in there...if by the jumpers...power cord needs to be plug in...if by the bat...(from what i hear) the plug needs to be unplug 
 
to know the settings of the cmos look in your motherborad user guide
 
 
the mother board user guide... lost... my motherboard is really old :p

---

### Post by linden940 on 2010-04-19
lol well....you cant take this to the bank...but (use this info at your own risk) cmos on most motherboards is called Jbat1 it will look like 3 pegs that come up from the motherboard with a small little clip that's only sits on two of the pegs and one having nothing on it....take that small clip (pull up on it very ezly) and move move it down....it would look something like this


[o] [o] o

^^before you change anything the [ ] is the clip o being the "peg"

then to clear cmos do this

o [o] [o] 

^^clearing cmos (name on board is Jbat1) wait a few mins then move it back to

[o] [o] o


if have it in o [o] [o] the computer WONT boot...so if the computer is not booting then you need to check to make sure you moved the clip back to where it should be

the CMOS (jbat1) job is to keep data of system configuration so when you clear it...if there WAS a problem in the system configuration that was keeping Ubuntu for booting up...when you clear it and install Ubuntu..it will redo that system configuration data

---

### Post by kasabia on 2010-04-19
got the cd burned ubuntu 10.04 still the same, tried the thingy with the 
[o] [o] o
same... problem... i think my system is anti linux or wtf :lolflag:

---

### Post by XelNagah on 2010-05-06
Hey, any luck with this?

I have two computers here at office with the same motherboard, and none of them is able to boot Ubuntu Karmic 9.10.
Not even live.

I was able to boot knoppix 5.0 though. Writing from it.
I'm suspecting these are unsupported motherboards. Any idea?

lshw output for motherboard:

```
  *-core
       description: Motherboard
       product: P5P800-VM
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890

```

---

### Post by kasabia on 2010-07-12
You may be right XelNagah... but this is just uncool...

---

### Post by XelNagah on 2010-07-14
> **kasabia said:**
> You may be right XelNagah... but this is just uncool...

Just as a note, I was able to boot Ubuntu Karmic 9.10 to these particular motherboards using a USB pendrive with uNetBootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)). Probably some module issue with CD-ROM.

At first I thought it was a badly burnt cd but later I tried with two other recently burned and had the same problems.

So for those of you having problems booting Ubuntu Karmic 9.10 into this particular hardware, try creating a bootable pendrive with uNetBootin.

That did the trick for me. -_-

---

