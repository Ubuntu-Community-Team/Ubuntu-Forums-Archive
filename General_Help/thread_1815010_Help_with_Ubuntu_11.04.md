---
title: "Help with Ubuntu 11.04"
date: 2011-07-30
forum: General Help
---

### Post by The New Guy on 2011-07-30
Hello everyone this is my first thread since a couple of years ago when I completely stopped using Ubuntu, to be honest with u I kind of missed it but now I know why I stopped using for one of the reasons Im about to explain,but anyways here is whats happening.

Well firs of all the last version of Ubuntu I used was Ubuntu 8.04 and going from that to the new Unity desktop is a big difference but Im getting used to it. I think my computer is pretty powerful to run Ubuntu without any problems.

My Specs
Motherboard : G41M-ES2H
CPU         : Intel(R) Core(TM)2 Duo CPU E8200 @ 2.66GHz
Memory RAM  : Patriot 4GB
Video Card  : GeForce 9500 GT 1GB 
Hard Drive  : SATA Maxtor 6L200M0 200GB
Monitor     : ASUS ML238 23"

1. - The first thing is my monitor is HDMI and Ubuntu will not work on HDMI but it does work with the VGA cable but I would love to see the HDMI resolution with Ubuntu. My question is if there is anyway to fix this problem?

2.- I enabled transparency in Unity's top panel and when I go to change compiz effects the panel automatically disable the transparency also the launcher on the left when it hides it leaves a dark spot on the back is like if was there but instead is a black rectangle  down across the screen. 

3.- An the biggest issue that I have is when I play youtube videos the computer starts to lag especially when I minimize firefox or chrome. 
Also when I go into full screen on the video (because of compiz) it opens it like if it was a new window and I would like to fix it to where it would just go into full screen normally. 

I hope I make enough sense for u guys to help me with this, thanks before hand. Cheers!!

---

### Post by mikewhatever on 2011-07-30
1. I've tested 11.04 on a laptop with Geforce 9300 GM and there was no problem with HDMI video output. You should elaborate a lot more: what driver do you use, what exactly do you do and what happens. Otherwise, the problem remains vague.

2. Could it have something to do with the changed you made to compiz?

3. That makes no sense. How do you watch flash videos full screen with Firefox or Chrome minimized?

---

### Post by The New Guy on 2011-07-30
> **mikewhatever said:**
> 1. I've tested 11.04 on a laptop with Geforce 9300 GM and there was no problem with HDMI video output. You should elaborate a lot more: what driver do you use, what exactly do you do and what happens. Otherwise, the problem remains vague.

2. Could it have something to do with the changed you made to compiz?

3. That makes no sense. How do you watch flash videos full screen with Firefox or Chrome minimized?

I apologize if I confused u. This is exactly what haappens

1.- In my monitor I have to outputs vga and hdmi both of them are pluged to the tower. When I was using windows it always used the hdmi I know this because when I first logged into the system and the desktop would come up on the top left hand corner would tell you "HDMI". Also my monitor has an option on the menu to switch from VGA to HDMI. 

I said all that to say this when I first boot up Ubuntu LiveCD ny screen was blank that was because it was on hdmi output so I switched it to vga output and there it was I had image, so I installed the system and update it and activated the nvidia driver hoping that it would let me switch to hdmi output but it did not so this is what exactly happens with this. 

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: XFX Pine Group Inc. Device 400a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at c000 [size=128]
	[virtual] Expansion ROM at f3000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-173, nvidia-current, nouveau, nvidiafb

I hope this helps.

2.- Well the I tried to use the less effects as possible and it actually happened when I was disabling some effects, I was thinking if it has less efects it would run better.

3. - You miss understood me here I go to youtube play a video and it plays it fine but then when I have to minimize the window it lags for a second and it freezes for a lil while. The other thing is when I play the video full screen the actual video skips a little. 

I hope I made more sense now, thanks!!!

---

### Post by mikewhatever on 2011-07-30
When trying Ubuntu from a CD, HDMI output doesn't work because the open source driver doesn't support it. The proprietary driver, however, should work, in fact, Nvidia does arguably the best job with hdmi support.

Flash on Linux is an ongoing problem. It's slow, unstable, and is a major resource hog. Do you know what version of flash you use? If not, check with the following:
```
dpkg -l | grep flash
```

...also, do you have a 32 or a 64 bit Ubuntu installed?

---

### Post by The New Guy on 2011-07-30
> **mikewhatever said:**
> When trying Ubuntu from a CD, HDMI output doesn't work because the open source driver doesn't support it. The proprietary driver, however, should work, in fact, Nvidia does arguably the best job with hdmi support.

Flash on Linux is an ongoing problem. It's slow, unstable, and is a major resource hog. Do you know what version of flash you use? If not, check with the following:
```
dpkg -l | grep flash
```

...also, do you have a 32 or a 64 bit Ubuntu installed?

I have a 32bit

and this is the flash player I have

 adobe-flash-properties-gtk            10.3.181.34-0natty1                        GTK+ control panel for Adobe Flash Player plugin version 10
ii  adobe-flashplugin                     10.3.181.34-0natty1                        Adobe Flash Player plugin version 10
rc  flashplugin-installer                 10.3.181.34ubuntu0.11.04.1                 Adobe Flash Player plugin installer

---

