---
title: "Computer sleeps but will not wake up after some time"
date: 2011-02-08
forum: General Help
---

### Post by dbldown768 on 2011-02-08
I wasn't sure what forum to ask this question in but recently, my computer will not wake up using the remote after some time has passed. This seems to have started just recently and might just be a coincidence that I updated xbmc around the same time.

I have the power options set to sleep. If i power off my htpc with my remote, it will sleep fine. I can power it back on without any problems if it is done soon after the pc goes to sleep. If some time passes (few hours or more) the remote no longer wakes up the computer. I can press the power button and the computer doesn't respond either.

The only way I can get the computer to turn back on is, flip the power switch on the back of the box, press the power button, turn the power switch back on, and press the power button once again.

Ubuntu Intrepid 8.10: Motherboard P5N7A-VM, E8400 C2D 3.0 processor. NVIDIA 9300 graphics card

---

### Post by epooch on 2011-03-05
[FONT=Arial]I had a similar problem, but my suspend never worked right.  It would suspend correctly once, wake, and then it would not work the second time.[/FONT][FONT=Arial]
[/FONT]
 [FONT=Arial]Enter into the terminal:[/FONT]
  ```
lshal | grep P5N7A
``` [FONT=Arial]
[/FONT] 
 [FONT=Arial]if you get:[/FONT]
 ```
system.board.product = 'P5N7A-VM'  (string)
``` [FONT=Arial]
[/FONT] 
 [FONT=Arial]you can try editing:[/FONT]
 [FONT=Arial]/usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-asus.fdi
and inserting: [/FONT]
```
   <match key="system.board.product" prefix="P5N7A">
       <merge key="power_management.quirk.s3_bios" type="bool">true</merge>
       <merge key="power_management.quirk.vbemode_restore" type="bool">true</merge>
   </match> 
```[FONT=Arial]
after the existing line:
<!-- Board with broken system.hardware.* fields. Use system.board.* instead -->
reboot and try suspending again. 

You could also try entering the command:
[/FONT]```
lshal | grep primary_video 
```[FONT=Arial]
and entering the product (mine is 0x86c) after:  
<match key="system.hardware.primary_video.product" int_outof=[/FONT][FONT=Arial]

in:
[/FONT][FONT=Arial]21-video-quirk-nvidia.fdi[/FONT][FONT=Arial]
I don't know if the 2nd option will work, but the first fixed all of my suspend problems.[/FONT]
 [FONT=Arial]
[/FONT] [FONT=Arial]For details check out:[/FONT]
 [[FONT=Arial]http://hal.freedesktop.org/quirk/quirk-suspend-try.html[/FONT]]("http://hal.freedesktop.org/quirk/quirk-suspend-try.html")
 [FONT=Arial]
[/FONT]

---

### Post by epooch on 2011-03-07
I just upgraded my XBMC and now I am having the same problem!  It works fine for short suspends, but the fans turn on and I can't wake it after long suspends.  It is definitely related to upgrading xbmc.

---

### Post by dbldown768 on 2011-05-15
This issue is still a problem.  I just bought new ram to try and see if that was the problem, but that didnt seem to help.  In addition, i now have 11.04, 8.10 and Windows 7 partitioned on my hard drive and all of them create the same issue where the PC doesnt wake after an extended period of time. 

Do you think this is a motherboard issue? PSU issue? There isn't much left to swap out?  The PC runs find when it is booted - no freezes etc?

---

### Post by dino99 on 2011-05-15
those issues are related to acpi settings (or bugs :()

[http://wiki.xbmc.org/index.php?title=Ubuntu_Suspend_/_Wake](http://wiki.xbmc.org/index.php?title=Ubuntu_Suspend_/_Wake)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642091](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642091)

---

### Post by dbldown768 on 2011-05-15
I would hope that you are correct, but the problem is my 8.10 installation never had these problem until recently.  I used to work just perfectly.  In addition, the fact that windows 7 exhibits the same problem leads me to believe it is not a software issue.  On other reason is, i built the exact same PC for my brother (hardware / software imaged (ubuntu)) and he has not had the same problem.

I would hope your suggestion works, but you can see why I am a bit apprehensive.  Does the above 'bug' apply to wireless/wired keyboards and mice? Even if i hit the power button on the pc, it doesnt wake up.

---

### Post by dino99 on 2011-05-15
so if your config is borked now, try to clean it (autoremove, autoclean, bleachbit) and run fsck on next boot (sudo shutdown -r now) and watch logs of course

as swap is used to suspend/hibernate, it needs at least 4 Gb and you can reformat its partition in case it have to be blamed (then run update-grub as the uuid is regenerated)

---

### Post by dbldown768 on 2011-05-15
Pardon my ignorance, but I dont understand fully what you are suggesting? fsck is going to check the hard disk correct?  Not sure what autoremove, autoclean and blechbit do or how to execute them?  Shutdown -r should just reboot the pc correct? But what logs should I be watching? How do these logs relate to waking from sleep.

---

### Post by dbldown768 on 2011-05-16
Just got off the phone with asus support, and they suggested to try a bios update and replacing the cmos battery.  His thought was the battery isnt lasting long enough to keep the shadow memory together which is causing the motherboard to 'panic' and not wake up.  I guess its worth a try to spend $3 on a new battery before RMA'ing the motherboard.

Just doesnt make complete sense seeing that i do not see any checksum errors and the bios settings are retained.  in addition, i have pc's that are much older than 2 years that still have original cmos battery and they wake from sleep mode just fine.

---

