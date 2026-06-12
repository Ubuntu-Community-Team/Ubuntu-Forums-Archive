---
title: "Problem with nVidia"
date: 2009-10-09
forum: General Help
---

### Post by Sondeckis on 2009-10-09
Hi there,
Today I installed fresh ubuntu 9.04. Installed nvidia drivers 180 made a restart. After boot when mouse should appear I see just nothing(i think at that moment it should use nvidia drivers...) after few secs my monitor turns to power saving mode. In recovery mode I disable video card drivers and ubuntu starts up without any problems.
Tried 180,173,96 none of them works for me ;/. 
Have an idea what's the problem?

---

### Post by jeremyswalker on 2009-10-09
Could you post the output of the following command:
```
lspci | grep VGA
```

---

### Post by Sondeckis on 2009-10-09
omg so fast :D, got to switch to ubuntu to check it
EDIT: 
> 01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)


---

### Post by jeremyswalker on 2009-10-09
Hmmm... That card should be supported with the latest version of the driver from what I can tell.

Could you post the output of:
```
less /var/log/Xorg.0.log | grep EE
```

---

### Post by Sondeckis on 2009-10-09
> 	(ww) warning, (ee) error, (ni) not implemented, (??) unknown.
(ii) loading extension mit-screen-saver
 1

---

### Post by jeremyswalker on 2009-10-09
How did you install the drivers? Did you use System > Administration > Hardware Drivers?

From what I see, the newest version available in the repositories for 9.04 should be from the 180.* branch. You didn't list that with the drivers you tried, though.

---

### Post by Sondeckis on 2009-10-09
Mistake i used 180 then tried 173 and at the last time 96
Installed with hardware drivers.

---

### Post by jeremyswalker on 2009-10-09
I am kind of at a loss, at the moment. Although, I forgot you said you disabled the driver and got it to start.
One last thought. Run the following command and see if there are multiple logs:
```
ls /var/log | grep -i Xorg
```

Now, if there are multiple entries (which I imagine there are) run the following for each entry and post the output: (Replace "Xorg.0.log" with each entry from the previous output, one at a time)
```
less /var/log/Xorg.0.log | grep -i EE
```

---

### Post by Sondeckis on 2009-10-09
1.
> Xorg.0.log
Xorg.0.log.old
2.1
> 	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension XFree86-DRI
(II) NV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(II) NV(0): Year: 2009  Week: 23
(II) NV(0): Sync:  Separate  SyncOnGreen
(II) NV(0): redX: 0.641 redY: 0.334   greenX: 0.301 greenY: 0.608
(II) do I need RAC?  No, I don't.
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Indirect CPU to Screen color expansion
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(**) USB Mouse: (accel) keeping acceleration scheme 1

2.2
> 	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension XFree86-DRI
(II) NV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(II) NV(0): Year: 2009  Week: 23
(II) NV(0): Sync:  Separate  SyncOnGreen
(II) NV(0): redX: 0.641 redY: 0.334   greenX: 0.301 greenY: 0.608
(II) do I need RAC?  No, I don't.
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Indirect CPU to Screen color expansion
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(**) USB Mouse: (accel) keeping acceleration scheme 1

Going to sleep.

---

### Post by jeremyswalker on 2009-10-09
Ok. I have to get going for a little while. However, when you get around to it, I would recommend ensuring that you have the 180 driver installed. Then, possibly try the following recommendation:
> If you have a problem where, after enabling the nvidia drivers via the Resricted Drivers Manager, X will no longer start, a possible workaround may be to remove and reinsert the nvidia kernel module by rmmod nvidia && modprobe nvidia. Symptoms include:

    * syslog contains entries like the following:

         NVRM: RM/client version mismatch!!
         NVRM:    aborting to avoid catastrophe!

      Xorg.0.log contains entries like the following:

         (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!

      lsmod | grep nvidia reports that the nvidia kernel module is loaded. If removing and reinserting the nvidia kernel module allows X to go ahead and start, it is possible to accomplish this at system start by making this the first command under the start) case in the gdm (or other display manager) init script, like so:
          

                 case "$1" in
                 start)
                    ##hack to deal with broken nvidia km not loading right###
                    rmmod nvidia && modprobe nvidia

      Another way of fixing this is to add
          

                 RUN+="/sbin/modprobe nvidia"

      to /etc/udev/rules.d/90-modprobe.rules 
From:     [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by Sondeckis on 2009-10-10
Truly i don't have any idea what to do by using that quote you gave...
I have just installed nVidia 180 drivers... Made restart, xfix'ed. Booted up:
[[IMG]http://v7.lt/out.php/t13226_Screenshot1.png[/IMG]](http://v7.lt/out.php/i13226_Screenshot1.png)
> mynde@Sondeckis:~$ less /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

> mynde@Sondeckis:~$ less /var/log/Xorg.0.log.old | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***


Oh forgot to ask:right now ubuntu looks very slow, even xp is faster... Would video drivers speed up ubuntu?
Specs: 1.4GHz Athlon
RAM 512MB
Video Card: GeFroce 6200 AGP8x 256MB

---

### Post by Sondeckis on 2009-10-10
*BEEP* Sorry for double post, it's just for bringing this thread to front from 'n' page...

---

### Post by Sondeckis on 2009-10-12
*BEEP* Tripleposting this time(for the last) I really care of using ubuntu, but some problems is changing my mind.

---

