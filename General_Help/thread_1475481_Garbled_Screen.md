---
title: "Garbled Screen"
date: 2010-05-06
forum: General Help
---

### Post by mleonard2012 on 2010-05-06
I really hope this isn't a duplicate post of any kind, but it's a little hard for me to read some of the text on my screen so I may have missed one.  Anyway, my problem is that the graphics on my screen, using either metacity or compiz, become garbled and unreadable after a short while of using my netbook.  It is a gateway netbook with an athlon 64 processor and ati x1270 graphics.  I am using the open source drivers that were installed along with Ubuntu.  I uploaded a few screenshots to give you an idea of what happens, but it gets quite a bit worse than what I've shown.

---

### Post by longanduselessname on 2010-05-06
Well this is most likely a graphics driver problem. I suggest you post the driver version you are running. 

IIRC ATI Linux support for some cards was dropped... but I don't know where I am remembering that from. Generally rough times with ATI but hopefully you can get it up and going.

---

### Post by alexpwnsn00b2 on 2010-05-06
same here
[http://www.uluga.ubuntuforums.org/showthread.php?t=1471701](http://www.uluga.ubuntuforums.org/showthread.php?t=1471701)

i think we may have the same netbook

---

### Post by mleonard2012 on 2010-05-07
It turns out that we do have the exact same netbook.  And I'm sorry, but I have not used any linux distribution for quite a while, due to issues that are very similar to this one.  So how would I go about finding which driver version I am running?

---

### Post by Tricast on 2010-05-08
Count me in on that problem. Have a Packard bell with the same hardware as in your Gateway machine. Amd L110 cpu + x1270. Unusable system with Ubuntu 10.04. Ubuntu 9.10 works like a charm though.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/574321](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/574321)

---

### Post by Catharsis on 2010-05-08
Are you running Lucid (10.04)? If so, try this from the Release Notes:
[http://www.ubuntu.com/getubuntu/releasenotes/1004#Window%20corruption%20with%20older%20ATI%20graphics%20cards](http://www.ubuntu.com/getubuntu/releasenotes/1004#Window%20corruption%20with%20older%20ATI%20graphics%20cards)

---

### Post by Catharsis on 2010-05-08
It also might be an issue with KMS. Try:

1) Hold down Shift as you boot to enter the GRUB menu.
2) Hit 'e' to edit the kernel boot parameters.
3) Add "nomodeset" after "quiet splash".
4) Ctrl+x to boot.

---

### Post by physic.dude on 2010-05-08
Try to turn off your "Motion Blur" setting in Compiz.

---

### Post by Tricast on 2010-05-08
> **Catharsis said:**
> It also might be an issue with KMS. Try:

1) Hold down Shift as you boot to enter the GRUB menu.
2) Hit 'e' to edit the kernel boot parameters.
3) Add "nomodeset" after "quiet splash".
4) Ctrl+x to boot.

Thanks Catharsis! The "nomodeset" fixed the problem for me.

For those with similar problem i added a screenshot of /etc/default/grub file where the change was made.

---

### Post by mleonard2012 on 2010-05-09
Wow guys, that really helped.  So far, the problem has no occured.  Now I'll be able to use Ubuntu full time on my netbook

---

### Post by mleonard2012 on 2010-05-09
Well, I lied.  The problem just took longer to occur than usual.  Any other suggestions?

---

### Post by Tricast on 2010-05-10
> **mleonard2012 said:**
> Well, I lied.  The problem just took longer to occur than usual.  Any other suggestions?

Did you update grub after adding "nomodeset" to it?

sudo update-grub

---

### Post by heizenberg on 2010-05-17
Happening to me of late. I tried upgrading from 9.10 to 10.04 and that didn't help. Then I added "nomodeset" to grub and ran update-grub. Didn't work either.

When I login, it seems fine... then after a while it turns into this garbled stuff. I have no effects running on my desktop either (no compiz decorations).

Any ideas?

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="nomodeset"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


---

### Post by rodspi on 2010-05-23
I have a gateway LT3103u with a x1270 graphic chip. I may have found a fix.  Mint 9 is my OS.  I had the same graphic issues as the others have discussed in this thread and others. I tried reinstalling twice. The problem persisted.  In those three attempts when would select recovery mode (Failsafe X Session)on boot screen, the OS would boot to the maximum resolution 1366x768 (weird) not the scaled down 1024x768 resolution.  I then did another reinstall.  After the reinstall, I booted to recovery first.  Inserted the <GRUB_CMDLINE_LINUX="nomodeset"> in the grub config file as other in this thread suggested. Issued the grub update command then rebooted.  I selected normal OS selection.  I then open programs to try to see if the glitch would occur.  It didn't.  I rebooted to recovery mode(Failsafe X Session) and the typical 1024x768 resolution was now present. No issues in the last two days I hope the glicth does come back.  Also I have been install and update my system in the failsafe X session of recovery mode.

---

### Post by Tricast on 2010-05-24
> **heizenberg said:**
> When I login, it seems fine... then after a while it turns into this garbled stuff. I have no effects running on my desktop either (no compiz decorations).

Any ideas?

Do you have any screen smoothing effects in some other applications activated? When i run epsxe with smoothing effects (anti-aliasing) the garbage screen comes back. Even if i use the "nomodeset" parameter.

Any change if you deactivate subpixel smoothing for fonts in "Appearance preferences/Fonts"?

---

### Post by rodspi on 2010-05-25
Tricast,

I haven't ran any emulators on my netbook.  I mainly use it for work so the software I use is more more focused on office productivity. In a couple of week when I have some free time on the weekend I'm going to backup my system and load XBMC.  This program produced the graphic glitch almost immediately.

I think the key is:

1. fresh install of OS
2. immediately reboot to recovery mode and select a failsafe X graphic sessions
3. insert the command into the grub.cfg file and run update grub command
4. reboot to the standard os
5. reboot to failsafe X graphic sessions to see if the graphics are scaled down failsafe graphics.  For some reason when I installed the os the first three times the failsafe X graphic sessions was in normal resolution not failsafe. I get the same row of dots on boot without the linux mint logo that I get on my desktop system with a NVIDIA graphic card with restricted drivers enabled.  I didn't get that on the previous three installs

I used my netbook all day at work today with no issues.  Firefox and Opera would typically cause the glitch after 3 to 4 minutes uses and I did a lot of browsering today.  I did lock my kernel updates in synaptic to try to prevent a recurrence.

---

### Post by heizenberg on 2010-06-17
Well, I figured my problem out.

When I finally noticed that my graphics cards (I was having problems on two separate machines - one had garbled graphics and one had a non-responsive UI) were running hot, I decided to swap them to see if that would make a difference.

Turned out that both the cards had a bunch of blown out capacitors... probably from a power surge that may have happened during a thunderstorm a few weeks ago.

Replacing the cards solved both the problems.

Apparently when capacitors blow out this way, they can still function at part capacity - which is why I still had partly functioning displays on both machines.

---

