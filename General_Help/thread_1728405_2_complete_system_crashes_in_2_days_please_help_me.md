---
title: "2 complete system crashes in 2 days please help me find the cause"
date: 2011-04-13
forum: General Help
---

### Post by metalf8801 on 2011-04-13
My laptop running Ubuntu 10.10 had suddenly go to a dark gray screen that will not take any kind of input other than holding to power button down for 5 seconds. I'm not running any new or odd programs just Firefox, Openofice writer, and Pidgin. When I turn the computer back on I do not see any kind of an error message. I'm looking for any advice that will help me find the cause of the problem. 

Thank you
Dan

---

### Post by earthpigg on 2011-04-13
let's conjecture that the system isn't locking up, only everything graphical is locking up.

(ctrl+alt+f7 will bring you back to were you are at now)

try pressing ctrl+alt+f5 right now.

once there, login and type "top".  see that CPU% column?

next time it locks up, do that, and gander what is listed at 100% or (if multicore CPU) 200%.

my guess would be firefox on some poorly designed flash-heavy web page or web pages. (don't want to get overly personal, but if that 2 times in 2 days was when you had several porn tabs open in firefox... that's the cause. flash sucks on linux, unfortunately, and poorly implemented flash found on many porn websites multiplies the problem.)

---

### Post by metalf8801 on 2011-04-13
> **earthpigg said:**
> let's conjecture that the system isn't locking up, only everything graphical is locking up.

(ctrl+alt+f7 will bring you back to were you are at now)

try pressing ctrl+alt+f5 right now.

once there, login and type "top".  see that CPU% column?

next time it locks up, do that, and gander what is listed at 100% or (if multicore CPU) 200%.

my guess would be firefox on some poorly designed flash-heavy web page or web pages. (don't want to get overly personal, but if that 2 times in 2 days was when you had several porn tabs open in firefox... that's the cause. flash sucks on linux, unfortunately, and poorly implemented flash found on many porn websites multiplies the problem.)

I tried using ctrl+alt+anything including F1 through F7, Delete and Backspace none of which worked when the screen went grey. Also the Caps Lock key would not turn the Caps Lock LED on but the volume keys did work because audio from the video I was watching went into a loop of what had just been said in the last few seconds and I was able to mute and unmute that. 

Does anyone know of anything I can run in the background that will collect information that could help me? I'm will to try anything other than bug-buddy because bug-buddy was causing my computer to crash when I tried to use Suspended or Hibernate. 

There is a good chance that flash is the problem. At least for the crash that happened today because I was watching a video on TV.com which does use flash heavily. However, I do not think I was yesterday watching anything on TV.com yesterday when I had what appeared to be the same problem. 

I'm not sure if this matters but 
The laptop is a Lenovo Thinkpad T60 
GPU 
VGA compatible controller
/0/100/1/0

product: Radeon Mobility X1400 [1002:7145]
vendor: ATI Technologies Inc [1002]
bus info: pci@0000:01:00.0
version: 00
width: 32 bits
clock: 33MHz
capabilities:
	Power Management,
	PCI Express,
	Message Signalled Interrupts,
	vga_controller,
	bus mastering,
	PCI capabilities listing,
	extension ROM
configuration:
	driver: radeon
	latency: 0
resources:
	irq: 47
	memory: d8000000-dfffffff
	ioport: 2000(size=256)
	memory: ee100000-ee10ffff
	memory: ee120000-ee13ffff

Thank you 
Dan

---

### Post by metalf8801 on 2011-04-13
I've enabled apport by opening a terminal
sudo nano /etc/default/apport

and changing enabled from "0" to "1". then closing and saving nano. So hopefully if this happens again it will generate a report that will help me understand what's causing the problem. 

I'm still very open to any ideas if anyone has one.

---

### Post by K_45 on 2011-04-13
It may be your GPU driver, can you boot a live CD and then try switching to a terminal with Ctrl+Alt+F5? What happens?

---

### Post by earthpigg on 2011-04-13
> **metalf8801 said:**
> I tried using ctrl+alt+anything including F1 through F7, Delete and Backspace none of which worked when the screen went grey.

it works otherwise though, right? when the screen isn't greyed out?

---

### Post by metalf8801 on 2011-04-13
> **earthpigg said:**
> it works otherwise though, right? when the screen isn't greyed out?
Yes I have checked to make sure that Alt+Ctrl+F5 and then Alt+Ctrl+F7 works 

Thank you earthpigg

---

### Post by metalf8801 on 2011-04-13
> **K_45 said:**
> It may be your GPU driver, can you boot a live CD and then try switching to a terminal with Ctrl+Alt+F5? What happens?
Yes I can try that but can you please explain why? I'm not a complete noob. 

Thank you

---

### Post by earthpigg on 2011-04-13
> **metalf8801 said:**
> Yes I can try that but can you please explain why? I'm not a complete noob. 

Thank you

i think he misunderstood your earlier statement, as i did (hence my clarification question).

what video card are you using, and what drivers, and where did you get them from?

---

### Post by metalf8801 on 2011-04-13
> **earthpigg said:**
> i think he misunderstood your earlier statement, as i did (hence my clarification question).

what video card are you using, and what drivers, and where did you get them from?

I'm using the Open Source X.Org X server -- AMD/ATI Radeon display driver
Version: 1:6.13.1-1ubuntu5
they are just the default drivers that Ubuntu comes with for my Video card and I no longer have the option of using the propriety drive from ATI because it no longer works with current versions of Ubuntu. However, I do have full 3D support from the open source drive.

GPU
VGA compatible controller
/0/100/1/0

product: Radeon Mobility X1400 [1002:7145]
vendor: ATI Technologies Inc [1002]
bus info: pci@0000:01:00.0
version: 00
width: 32 bits
clock: 33MHz
capabilities:
Power Management,
PCI Express,
Message Signalled Interrupts,
vga_controller,
bus mastering,
PCI capabilities listing,
extension ROM
configuration:
driver: radeon
latency: 0
resources:
irq: 47
memory: d8000000-dfffffff
ioport: 2000(size=256)
memory: ee100000-ee10ffff
memory: ee120000-ee13ffff

I did do the test with the live CD (I didn't know then that I didn't need to) I also checked my systems memory while I was using the live CD.

Thank you again for your help

---

### Post by K_45 on 2011-04-13
Did the livecd boot or did you get a dark gray screen?

---

### Post by metalf8801 on 2011-04-13
> **K_45 said:**
> Did the livecd boot or did you get a dark gray screen?

It booted just fine. In case it's a problem I used a live Kubuntu 10.10 CD because that's what I had laying around, but I'm using the standard Gnome version of Ubuntu 10.10. 

I was also able to enter TTY using Alt+Ctrl+F5 and back to the graphical desktop by pressing Alt+Ctrl+F8.

---

### Post by K_45 on 2011-04-13
Load up Ubuntu again and enter

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

to jumpstart Xorg.

---

### Post by metalf8801 on 2011-04-13
> **K_45 said:**
> Load up Ubuntu again and enter

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

to jumpstart Xorg.
OK but Xorg is running right now. The grey screen hasn't come back since I restarted the computer. I'm just trying to figure out what is causing my laptop to crash.

---

### Post by earthpigg on 2011-04-13
couple things we can do dig a bit deeper and find out.

would you be willing to try using chromium or opera for a few days? if the crashes suddenly stop, we have our answer. this is just my general skepticism of FF still expressing itself.

and: would you be willing to keep htop running in a small terminal visible while you use your computer? maybe a spike in CPU usage of something immediately preceding a lockup will give us a clue. (sudo apt-get install htop, then htop in a terminal)

---

### Post by metalf8801 on 2011-04-13
> **earthpigg said:**
> couple things we can do dig a bit deeper and find out.

would you be willing to try using chromium or opera for a few days? if the crashes suddenly stop, we have our answer. this is just my general skepticism of FF still expressing itself.

and: would you be willing to keep htop running in a small terminal visible while you use your computer? maybe a spike in CPU usage of something immediately preceding a lockup will give us a clue. (sudo apt-get install htop, then htop in a terminal)

Yeah I'll switch to Chromium for awhile and I'll run htop 

Thank you for all of your help 
Dan

---

