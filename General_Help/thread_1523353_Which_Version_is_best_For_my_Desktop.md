---
title: "Which Version is best For my Desktop"
date: 2010-07-03
forum: General Help
---

### Post by Honey_HR on 2010-07-03
[SIZE=5][B]I am new to Ubuntu, I Just want to know,
Which Ubuntu Version is Best for my Desktop ??  Currently I am using Latest LTS 10.04 and i am facing some problems with it related Graphic and Sound and Many Other,
[COLOR=Red]HELP ME PLEASE[/COLOR]

My PC is,

Intel Celeron 1.7 MGH
DDR 1GB[/B][/SIZE]

---

### Post by DJYoshaBYD on 2010-07-03
well, first, you will need to tell us alot more about your computer.. what type of motherboard/chipset? what issues are you having?

please be alot more concise with the issues that you are having.. For me, EVERYTHING worked right out of the box.. wireless, sound, video, etc etc etc etc..

but, you may be missing a driver/module, you may have unsupported hardware.... lots of things..

please tell us exactly WHAT is happening, and more about your computer..

PS.. you dont have to make the font that big.. we can see it :)

---

### Post by SmokeyThePanda on 2010-07-03
I agree with the above statement, we need more information about your system. However, by what you have shown us already, the normal Ubuntu should run just fine..

---

### Post by Honey_HR on 2010-07-03
> **DJYoshaBYD said:**
> well, first, you will need to tell us alot more about your computer.. what type of motherboard/chipset? what issues are you having?

please be alot more concise with the issues that you are having.. For me, EVERYTHING worked right out of the box.. wireless, sound, video, etc etc etc etc..

but, you may be missing a driver/module, you may have unsupported hardware.... lots of things..

please tell us exactly WHAT is happening, and more about your computer..

PS.. you dont have to make the font that big.. we can see it :)

Oh come on Guys I am newbie, I don't know how to see full PC configuration on Ubuntu

---

### Post by roger_1960 on 2010-07-03
Hi

If you post the output from > sudo lshw when entered in terminal to the forum (you will be asked for your password which wont appear as you type it) and describe your problems in a little detail, then perhaps someone can help.

---

### Post by stlsaint on 2010-07-03
Please DO NOT post the entire output of the command lshw into a post. Copy and paste the output into a file and attach that file to the post.

---

### Post by DJYoshaBYD on 2010-07-03
> **Honey_HR said:**
> Oh come on Guys I am newbie, I don't know how to see full PC configuration on Ubuntu

its ok.. lol.. i didnt know you were a n00b.. haha.. just new to linux..

did you buy your computer, or build it?

im assuming you bought it ;)

if so, what is the make and model of your PC, so we can check specs..

Really, it doesnt matter.. You can choose any of the following:

Ubuntu 10.04
Kubuntu 10.04
Xubuntu 10.04
UbuntuStudio

and pretty much anything else.. you should be just fine.. :)

just run the 32-bit version, as you cannot handle the 64-bit version on your system

Welcome to Linux :D

---

### Post by DJYoshaBYD on 2010-07-03
oh yeah.. i almost forgot..

if you still want to send your specs, you can use the following command to generate it on your desktop..... if you are using Ubuntu, of course

```
sudo lshw > ~/Desktop/specs.tx
```

Just put in your password, and it will just generate that file, which is just a list of all the hardware on the system

---

### Post by Honey_HR on 2010-07-04
> **DJYoshaBYD said:**
> oh yeah.. i almost forgot..

if you still want to send your specs, you can use the following command to generate it on your desktop..... if you are using Ubuntu, of course

```
sudo lshw > ~/Desktop/specs.tx
```

Just put in your password, and it will just generate that file, which is just a list of all the hardware on the system

OKay here is full detail 
 please HELP ME guys:(

---

### Post by kimikrishna on 2010-07-04
You can "hardinfo" to find system specs (it's in software center)

You may want to install Drivers to get graphics work properly

---

### Post by Honey_HR on 2010-07-04
> **kimikrishna said:**
> You can "hardinfo" to find system specs (it's in software center)

You may want to install Drivers to get graphics work properly

Thanks sir,But where to get drivers sir, I just see gigbytes site but there is no any drivers for linux or Ubuntu. What to do,?? I am very Upset:popcorn:

---

### Post by philinux on 2010-07-04
> **Honey_HR said:**
> Thanks sir,But where to get drivers sir, I just see gigbytes site but there is no any drivers for linux or Ubuntu. What to do,?? I am very Upset:popcorn:

System>admin>hardware drivers.

Tell us if it offers to install activate any graphics drivers or others.

---

### Post by Honey_HR on 2010-07-04
> **philinux said:**
> System>admin>hardware drivers.

Tell us if it offers to install activate any graphics drivers or others.
[SIZE="3"][SIZE="3"]Hello Sir I did it, System>admin>hardware drivers   then hardware windows appear on screen but it shows nothing, No require drivers nothing,
I NEED GRAPHIC DRIVERS FOR [COLOR="Red"]"gigabyte 8I845GVMRZ"[/COLOR], and also need AUDIO drivers for [COLOR="red"]"C-Media-PCI AUDIO CM8738"[/COLOR][/SIZE][/SIZE]

---

### Post by cascade9 on 2010-07-04
81845 would be a intel 845 chipset. You dont need to download and install drivers for the intel 845 chipset, everything works out of the box. 

Same for the cmedia 8738.

---

### Post by philinux on 2010-07-04
Op,

What exactly is the graphics problem. Stick to one problem at once or it will get confusing.

---

### Post by Honey_HR on 2010-07-04
> **philinux said:**
> Op,

What exactly is the graphics problem. Stick to one problem at once or it will get confusing.

Graphics are not good, it take some time to open up new window, or anything, same with the sound its not working at all, there is no sound in system

---

### Post by philinux on 2010-07-04
> **Honey_HR said:**
> Graphics are not good, it take some time to open up new window, or anything, same with the sound its not working at all, there is no sound in system

System>prefs>desktop effects. Set to none.

Also run these commands from a terminal. Apps>Access>terminal

```
top

then 

free -m
```

See if any app is maxing your cpu or memory.

---

### Post by Honey_HR on 2010-07-04
> **philinux said:**
> System>prefs>desktop effects. Set to none.

Also run these commands from a terminal. Apps>Access>terminal

```
top

then 

free -m
```

See if any app is maxing your cpu or memory.

Thanks for support sir i fix audio myself its working perfectly,
But still problems with graphics, 
I did it, top then free-m
its shows this, i don't know what is this:
> * A: PID        = Process Id              u: nFLT       = Page Fault count
* E: USER       = User Name               v: nDRT       = Dirty Pages count
* H: PR         = Priority                y: WCHAN      = Sleeping in Function
* I: NI         = Nice value              z: Flags      = Task Flags <sched.h>
* O: VIRT       = Virtual Image (kb)    * X: COMMAND    = Command name/line
* Q: RES        = Resident size (kb)
* T: SHR        = Shared Mem size (kb)  Flags field:
* W: S          = Process Status          0x00000001  PF_ALIGNWARN
* K: %CPU       = CPU usage               0x00000002  PF_STARTING
* N: %MEM       = Memory usage (RES)      0x00000004  PF_EXITING
* M: TIME+      = CPU Time, hundredths    0x00000040  PF_FORKNOEXEC
  b: PPID       = Parent Process Pid      0x00000100  PF_SUPERPRIV
  c: RUSER      = Real user name          0x00000200  PF_DUMPCORE
  d: UID        = User Id                 0x00000400  PF_SIGNALED
  f: GROUP      = Group Name              0x00000800  PF_MEMALLOC
  g: TTY        = Controlling Tty         0x00002000  PF_FREE_PAGES (2.5)
  j: P          = Last used cpu (SMP)     0x00008000  debug flag (2.5)
  p: SWAP       = Swapped size (kb)       0x00024000  special threads (2.5)
  l: TIME       = CPU Time                0x001D0000  special states (2.5)
  r: CODE       = Code size (kb)          0x00100000  PF_USEDFPU (thru 2.4)
  s: DATA       = Data+Stack size (kb)


---

### Post by philinux on 2010-07-04
free-m

Should be free -m with a space between.

---

### Post by Honey_HR on 2010-07-04
> **philinux said:**
> free-m

should be free -m with a space between.

its shows this,

> honey@honey-desktop:~$ free -m
             total       used       free     shared    buffers     cached
mem:           994        607        386          0        102        326
-/+ buffers/cache:        178        815
swap:          934          0        934


---

### Post by philinux on 2010-07-05
Honey_HR,

```
honey@honey-desktop:~$ free -m
total used free shared buffers cached
mem: 994 607 386 0 102 326
-/+ buffers/cache: 178 815
swap: 934 0 934

```

That looks fine.

Shows zero swap in use. If it needs it, it will use it. I'd leave it as it is set up.

---

### Post by Honey_HR on 2010-07-06
OKies Thanks

---

