---
title: "After updating 10.10 to 11.04 Ubuntu won't lounch"
date: 2011-04-29
forum: General Help
---

### Post by coffeholikas on 2011-04-29
Just updated Ubuntu 10.10 to 11.04, after reboot the 11.04 loading screen opened, there was purple background, ubuntu logo, and 5 red loading dots. It stays like that for ever...
Please help me.

---

### Post by teknic111 on 2011-04-29
I'm having a similar problem.  I'm pretty sure it's due to Unity.  What are your hardware specs?

---

### Post by nicknormal on 2011-04-29
similar situation here, on 2nd reboot. First boot in told me I didn't have the hardware to run Unity, not it just hangs after logo screen.

---

### Post by teknic111 on 2011-04-29
What's the minimal hardware requirements for Unity?  I'm using an Nvidia Go 7200, which ran Compiz just fine.

---

### Post by Samloops on 2011-04-29
Exact same situation as well after upgrading today from 10.10 on my P4 desktop.  First boot after upgrading gave a vertical black and white banded screen on my Cornerstone p1500 but this was expected.  I've always had to manually edit Xorg.conf in order to set up that monitor after a major upgrade.  So switched to another monitor, rebooted, and have the five red dots as described above.  I'm using an Nvidia 6200 and had the proprietary Nvidia driver installed in 10.10.  My goal right now is to get 11.04 to boot...any driver, any monitor.

Is there someway to turn off the splash screen in grub so that I can see where it is hanging?  

Thanks

Sam
Kamloops, BC

---

### Post by Samloops on 2011-04-29
OK...

I did make some progress.  I guess the right Shift key during boot does not get you to the grub menu... only the left Shift.  OK.  Don't think I ever read that anywhere though.  With that I was able to boot successfully into failsafe graphics mode and as noted above also received the message that I did not have the minimum hardware to run Unity, and so it defaulted to the "Classic" desktop.  The hardware thing is nutty and so I assume that message pops up in error when one is in failsafe mode.  Hopefully I can work out the graphics issues from here.  At least I've got something to work with.

---

### Post by dino99 on 2011-04-29
try without "splash" on the boot line (edit from grub menu, then x to boot)

then to make it permanent: sudo gedit /etc/default/grub

and: sudo update-grub

---

### Post by coffeholikas on 2011-04-29
Intel Quad processor
GeForce 9800GT or smth like that
4Gb RAM
750GB HDD
Good PC. :)

Maybe I should try "clean" install?

---

### Post by ivanovnegro on 2011-04-29
> **Samloops said:**
> 

Is there someway to turn off the splash screen in grub so that I can see where it is hanging?  

Thanks

Sam
Kamloops, BC

You can also type "Esc" while booting the system when you see the splash screen to get into text mode, to see what actually happens.

> **coffeholikas said:**
> Intel Quad processor
GeForce 9800GT or smth like that
4Gb RAM
750GB HDD
Good PC. :)

Maybe I should try "clean" install?

Yup! :)

---

### Post by Samloops on 2011-04-30
Thanks for the hints there.  I was asking because originally I couldn't get into the grub menu and thought there might be some new way to change boot parameters.  I've since found that I need to be using a keyboard with a PS2 plug instead of my normal WIRED USB keyboard, otherwise keystrokes are not accepted during the boot phase.  It's interesting in that I can ESC out of the initial memory check during boot with the USB keyboard, but once grub starts, the keyboard is ignored.  Haven't seen this issue before as I've installed Ubuntu in the past on computers that didn't even have a PS2 port! ???

Anyway, true to form, boot issues were related to Nvidia graphic card driver installation problems. I was able to get things up and running (with 3D acceleration) by following instructions in this thread [http://ubuntuforums.org/showthread.php?t=1742952](http://ubuntuforums.org/showthread.php?t=1742952) .  Purging the Nvidia drivers also deleted ubuntu-desktop however and even reinstalling that has not successfully brought up a Unity desktop.  So I'm working with a Ubuntu Classic. I'll probably redo the whole process again, but instead of loading the driver downloaded from Nvidia, will sudo apt-get install nvidia-current and see if that makes any difference in the end.  

At least Ubuntu is launching now.

Thanks again.

---

### Post by .bashrc on 2011-04-30
I am having this problem as well. Looking at the verbose startup, it appears to be cycling through the same commands and then reporting a failure at "Stopping automatic crash report generation." Any help would be greatly appreciated.

---

### Post by heisters on 2011-04-30
Followed the link above and found an easier solution. Posted my solution in the other thread: [http://ubuntuforums.org/showthread.php?p=10747631&posted=1#post10747631](http://ubuntuforums.org/showthread.php?p=10747631&posted=1#post10747631)

---

