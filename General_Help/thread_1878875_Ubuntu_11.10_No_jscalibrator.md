---
title: "Ubuntu 11.10 No jscalibrator?"
date: 2011-11-10
forum: General Help
---

### Post by 0LinuxUser on 2011-11-10
I have a USB gamepad that I'd like to use with some games, but I can't install jscalibrator. Whenever I try to run this command:

```
sudo apt-get install jscalibrator
```I get an error that Ubuntu cannot find jscalibrator.

Is there some other gamepad setup program I need to run in Ubuntu 11.10, so that I can configure my USB controller?

Any help is appreciated.

---

### Post by satanselbow on 2011-11-10
```

sudo apt-get joystick

```

includes ye olde jscalibrate (and a force-feedback tool) I believe ;)

---

### Post by 0LinuxUser on 2011-11-10
Ok, so... is there a way to make this work in a GUI environment? I don't believe joystick can do that... perhaps I'm wrong?

---

### Post by Grumbel on 2012-02-07
> **0LinuxUser said:**
> Ok, so... is there a way to make this work in a GUI environment? I don't believe joystick can do that... perhaps I'm wrong?
The jscal that comes with Ubuntu is console only, no GUI. I don't think there is any GUI tool that ships with Ubuntu. But there is:

[http://pingus.seul.org/~grumbel/jstest-gtk/](http://pingus.seul.org/~grumbel/jstest-gtk/)

Which might have packages available as PPA.

Anyway, all that said, you don't need to calibrate your joystick and most games will ignore that calibration anyway, as SDL doesn't use the joystick device, but evdev.

---

### Post by Geezanansa on 2012-04-06
Dunno if op has a working controller for games.

jstest is now available through software centre in oneric.  i cannot get this to see my razer onza te so try xboxdrv can get xboxdrv to see but am struggling to remap due to joydev permission probs or not clearing xpad .  i dunno 

surely there is a guide on how to xbox360 controller that works somewhere or a workaround if i can work out what is what

i too like op cannot install or use jscalibrator

Any help would be appreciated

---

### Post by Grumbel on 2012-04-06
> **Geezanansa said:**
> i cannot get this to see my razer onza te so try xboxdrv can get xboxdrv to see but am struggling to remap due to joydev permission probs or not clearing xpad
What error message do you get from xboxdrv? "rmmod xpad" and running xboxdrv as root or adding your user to the root group should be all that is needed.

> i too like op cannot install or use jscalibrator
Debian and Ubuntu dropped gtk1, they only ship gtk2 and gtk3. jscalibrator happens to be victim of that as it is a gtk1 application and thus dropped as well. But as said, jscal and jstest do the same thing without graphics, jscalibrator is not needed.

---

### Post by Geezanansa on 2012-04-06
I installed xboxdrv as ppa/repository and have found manpage online but can not find readme file.

i can get xboxdrv running with no errors by running sudo xboxdrv

using this thread as guide[ http://ubuntuforums.org/showthread.php?t=825464]("http://http://ubuntuforums.org/showthread.php?t=825464") but cannot load uinput module and struggling to find relevant workaround or how to for ubuntu 11.10

i will start new thread

Thanks in advance

---

### Post by Grumbel on 2012-04-06
> **Geezanansa said:**
> I installed xboxdrv as ppa/repository and have found manpage online but can not find readme file.
All the info you need is in the manpage. The README is at:

/usr/share/doc/xboxdrv/README

> i can get xboxdrv running with no errors by running sudo xboxdrv
Then it should work. If uinput wouldn't be loaded, xboxdrv would complain about it being missing.

---

### Post by Geezanansa on 2012-04-06
Good to know Grumbel just need to spend more time familiarising myself with xboxdrv(and ubuntu):popcorn:

Just used readme (10.10) to use software centre to install all required packages.  It is becoming clearer.  make updated to scons etc etc 
thanks for help Grumbel.

---

### Post by binsky734 on 2012-08-26
Here is where you can find jscalibrator [http://packages.ubuntu.com/hardy/jscalibrator](http://packages.ubuntu.com/hardy/jscalibrator)

---

