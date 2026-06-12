---
title: "ubuntu 11.04 suspend problem"
date: 2011-05-05
forum: General Help
---

### Post by Jordanbadangayon on 2011-05-05
hello everybody. I have a big problem with suspend. Everytime i hit it, my laptop goes to suspend (the screen goes blank then my laptop runs on low power mode) but when i wake it up, it actually boots up, not wake up. i meant boot up because it starts from grub then goes to the bootsplash screen before the desktop. this also means that all the open applications before suspend are closed. I use a vaio VGN-NW20EF dual booted with windows 7. can anybody help please?? or at least explain what is going on. i don't think it has something to do with the swap because I alloted 4Gb to it and i have a 3gb RAM.  :confused: thank you...

---

### Post by bhatbhai on 2011-05-05
I also have the same problem, and I have a Vaio VGN-NW as well. I made a topic about it a while ago, you can take a look at the answers and see if they help you, because they didn't work for me.

[http://ubuntuforums.org/showthread.php?t=1740457](http://ubuntuforums.org/showthread.php?t=1740457)

---

### Post by hkdbb on 2011-05-05
Same problem here on a Sony Vaio. I am not dual booting though. 10.04 did not give me this problem.

---

### Post by 0_irishboy_0 on 2011-05-05
I have the same problem with an Asus G73 also dual booting with Windows 7.  Has anyone had any luck fixing it?  I'm wondering if a fresh install might help.

---

### Post by Quackers on 2011-05-05
I have a Vaio too and your symptoms only occur on mine if I choose to hibernate. Suspend works ok most of the timre. Occasionally waking from suspend gives me no display so I have to reboot but using hibernate always gives me the same symptoms you have.

---

### Post by Jordanbadangayon on 2011-05-05
> **bhatbhai said:**
> I also have the same problem, and I have a Vaio VGN-NW as well. I made a topic about it a while ago, you can take a look at the answers and see if they help you, because they didn't work for me.

[http://ubuntuforums.org/showthread.php?t=1740457](http://ubuntuforums.org/showthread.php?t=1740457)
thanks for replying :). i tried the solutions posted on your thread but with no luck. I did not bother changing my kernel version because i actually had the same problem in 10.10. since i only used 10.10 for about 3 weeks, i had hoped that this problem will be fixed in 11.04.

---

### Post by Jordanbadangayon on 2011-05-05
> **0_irishboy_0 said:**
> I have the same problem with an Asus G73 also dual booting with Windows 7.  Has anyone had any luck fixing it?  I'm wondering if a fresh install might help.
Did you have this problem in 10.10. I actually did a fresh install for 11.04 but still have the same problem...

---

### Post by hkdbb on 2011-05-07
> **Jordanbadangayon said:**
> Did you have this problem in 10.10. I actually did a fresh install for 11.04 but still have the same problem...

I can't answer for him, but I did a fresh install. No dual booting. I was using 10.04 and had no problems. This only started after a clean install of 11.04. Also getting the message that /dev/mapper/cryptswap1 is not present or ready at boot. I've waited for some kind of answer or fix to these problems but no luck. I'm moving on to something else. A shame really, I actually liked Ubuntu until now.

---

### Post by mijodo on 2011-05-10
Possible solution...

I have a similar issue: my laptop goes into suspend mode correctly but when I try to wake it, it does a full reboot instead of resuming.

After hunting around on the web and trying several solutions, I found one that works for my PC.

The following solution was intended for 10.10, but it also works for me in 11.04:

[http://www.michali.org/ubuntu/sony-vaio-fw490j/73-suspendresume-on-ubuntu-1010](http://www.michali.org/ubuntu/sony-vaio-fw490j/73-suspendresume-on-ubuntu-1010)

Note: you must do a full reboot after running update-grub before suspend will start working.

Note: while this fixes suspend on my PC, it does *not* fix hibernate.

Note: I have a Sony Viao VGN-SR21M, running 11.04, 64 bit, alternate installer.

---

### Post by Jordanbadangayon on 2011-05-11
> **mijodo said:**
> Possible solution...

I have a similar issue: my laptop goes into suspend mode correctly but when I try to wake it, it does a full reboot instead of resuming.

After hunting around on the web and trying several solutions, I found one that works for my PC.

The following solution was intended for 10.10, but it also works for me in 11.04:

[http://www.michali.org/ubuntu/sony-vaio-fw490j/73-suspendresume-on-ubuntu-1010](http://www.michali.org/ubuntu/sony-vaio-fw490j/73-suspendresume-on-ubuntu-1010)

Note: you must do a full reboot after running update-grub before suspend will start working.

Note: while this fixes suspend on my PC, it does *not* fix hibernate.

Note: I have a Sony Viao VGN-SR21M, running 11.04, 64 bit, alternate installer.
Can you give me a step by step procedure on how to do this exactly?? I did not quite understand the instruction from the link.. ;). And I'm afraid that I might not do it right. I don't want to screw up grub... :D

---

### Post by mijodo on 2011-05-11
> **Jordanbadangayon said:**
> Can you give me a step by step procedure on how to do this exactly?? I did not quite understand the instruction from the link.. ;). And I'm afraid that I might not do it right. I don't want to screw up grub... :D

Sure, here's what you need to do:

1) Save a copy of the grub settings file, just in case:

```
$ sudo cp /etc/default/grub /etc/default/grub.bak
```2) Edit the grub settings file:
[FONT=Courier New]
[/FONT]```
$ sudo gedit /etc/default/grub
```3) Locate the following line (line 12 on my installation):

```
GRUB_CMDLINE_LINUX=""
```[FONT=Courier New]
[/FONT]and change it to:

```
 GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"
```[FONT=Courier New]
[/FONT]4) Save the file and exit.

5) Run update-grub. This reads the contents of [FONT=Courier New]/etc/default/grub[/FONT] and builds a new grub config file [FONT=Verdana]in [/FONT][FONT=Verdana][FONT=Courier New]/boot/grub/[/FONT]:
[/FONT] 
```
$ sudo update-grub
```6) Reboot your PC, for the changes to take effect.

Note: As mentioned above, this only fixes the suspend mode, not hibernate (at least on my PC).

---

### Post by Jordanbadangayon on 2011-05-11
> **mijodo said:**
> Sure, here's what you need to do:

1) Save a copy of the grub settings file, just in case:

```
$ sudo cp /etc/default/grub /etc/default/grub.bak
```2) Edit the grub settings file:
[FONT=Courier New]
[/FONT]```
$ sudo gedit /etc/default/grub
```3) Locate the following line (line 12 on my installation):

```
GRUB_CMDLINE_LINUX=""
```[FONT=Courier New]
[/FONT]and change it to:

```
 GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"
```[FONT=Courier New]
[/FONT]4) Save the file and exit.

5) Run update-grub. This reads the contents of [FONT=Courier New]/etc/default/grub[/FONT] and builds a new grub config file [FONT=Verdana]in [/FONT][FONT=Verdana][FONT=Courier New]/boot/grub/[/FONT]:
[/FONT] 
```
$ sudo update-grub
```6) Reboot your PC, for the changes to take effect.

Note: As mentioned above, this only fixes the suspend mode, not hibernate (at least on my PC).
Thank you so much for this. Works like a charm. :).  

By the way, I'm using a Vaio VGN-NW20EF.

---

### Post by Jordanbadangayon on 2011-05-11
It also fixed my Hibernate :D.... But then again, it may not be for everybody....

---

### Post by Jordanbadangayon on 2011-05-25
> **Jordanbadangayon said:**
> Thank you so much for this. Works like a charm. :).  

By the way, I'm using a Vaio VGN-NW20EF.
also worked on Vaio VPCCW1S1E.. :)

---

### Post by Willynux on 2011-05-28
Also works on Vaio VGN-FW270AE  :popcorn:

Thx bro

---

### Post by Novacaptain on 2011-05-31
The fix doesn't resolve the issue for dell studio 1747. Neither hibernate nor suspend works, though both worked flawlessly in kernel 2.6.35.
In fact, just installing the older kernel and selecting it in grub gives back this functionality, but breaks a bunch of other stuff (such as the touchpad behavior).

---

### Post by fari81 on 2011-07-24
nice. thanks. it worked perfectly. can't live without suspend.

vaio VGN-SR220J

---

### Post by lads on 2011-07-27
Hello everyone,

Just to inform that the procedure provided by mijodo also solves the Suspend issue on a Sony Vaio VGN-FW31ZJ.

Note: I had to upgrade to GRUB 2 first, which was easy following this [guide]("http://www.unixnewbie.org/how-to-easily-upgrade-grub-2/").

Best.

---

### Post by AntBlair on 2011-08-02
The fix also works for Sony Vaio VGN-NW180J. Thanks for the help!

:guitar:

---

### Post by Flopply on 2011-09-09
Thanks for everybody's efforts. It's not working for me on my Amilo Li2727. Oh well. I've just set mine to blank the screen when I shut the lid.

---

