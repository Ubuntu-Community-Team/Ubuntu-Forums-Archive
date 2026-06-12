---
title: "Problems after upgrading to 12.04"
date: 2012-05-14
forum: General Help
---

### Post by martenclark on 2012-05-14
I upgraded to Ubuntu 12.04 and ever since doing so i cant get anything other than a complete white screen on load up, if i start in recovery mode as i am running now , i can see and use everything but if i boot normally once loaded i only get white screen with bar on top saying Ubuntu desktop but if i open any app its as if its hidden behind this white screen, please help im new to all this and by no means as clever as most of you out there

---

### Post by kc1di on 2012-05-14
We need a little more information, what you discribe sounds to me like a video card issue.  so lets start with that. 

in recovery mode can you get to a terminal? if you can would you type the following command and post the out put here.

```
lspci
```

the l is a lower cased L not # 1.

then we will see if we can help.

---

### Post by mörgæs on 2012-05-14
Welcome to the fora.

Next time please use a more informative thread title.

---

### Post by martenclark on 2012-05-14
sorry Dave im not that clever with all this i will try find a terminal to type command in but dont really understand the process, sorry i did say im old and useless haha, i will try

---

### Post by martenclark on 2012-05-14
dougal@dougal-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation NV34GL [Quadro FX 500/600 PCI] (rev a1)
02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
dougal@dougal-desktop:~$ 

not sure if i did that right

---

### Post by kc1di on 2012-05-14
Hi again martenclark,
Welcome to Ubuntu. 
As I suspected your video card is an Nvidia and there have been some problems with some nivida card in 12.04.  I'm not sure yours is one of them. Your is 01:00.0 VGA compatible controller: **NVIDIA Corporation NV34GL [Quadro FX 500/600 PCI]** (rev a1)

It should work with the opensource driver but there must be a problem.  

another question when you boot in the regualar mode do you see the login screen?  Or is that blanked out also? if you can see it you
can try ubuntu 2d instead of 3d , you can do that by 
clicking on the little ubuntu Icon in the upper right corner of the login block and selecting 2d from the menu.

try that first if you can.  and we will go from there.

I'm old along with you by the way :)

---

### Post by martenclark on 2012-05-14
Many thanks Dave i will try that now, sorry to be so useless, i was weened onto Linux from microcrap and love it just not that good with it yet haha , oh and yes i get login screen fine it just all goes wrong after that. will try now and report

---

### Post by martenclark on 2012-05-14
Dave i like your suggestions :P  I tried the 2d option and everything booted up as normal if a little slow but all seems normal in 2d, 
If this problem is likely to persist is there a way i can re-install the previous version of Ubuntu ?? 
I tried selecting previous versions on grub screen with no luck, and lastly many many thanks for your help Dave  and thanks for your paitence with me

---

### Post by kc1di on 2012-05-14
> **martenclark said:**
> Dave i like your suggestions :P  I tried the 2d option and everything booted up as normal if a little slow but all seems normal in 2d, 
If this problem is likely to persist is there a way i can re-install the previous version of Ubuntu ?? 
I tried selecting previous versions on grub screen with no luck, and lastly many many thanks for your help Dave  and thanks for your paitence with me

Now lets see if we can get the 3d to work also.
Go to the system settings The Icon on the left panel with gear and wrench. The click on additional drivers.  see if it offers you any different drivers?

---

### Post by martenclark on 2012-05-14
Tried that it says '  no proprietary drivers are in use on this system '

---

### Post by kc1di on 2012-05-14
> **martenclark said:**
> Tried that it says '  no proprietary drivers are in use on this system '

Ok for now I'd stick with the 2d version unless there is some compelling reason why you need the 3d version..
cheers!
enjoy,

dave

---

### Post by bogan on 2012-05-14
Hi!, **All**,

The Nvidia FX  series video cards require the 173. driver and it is not compatible with the 12.04 Xorg!!

This is a different problem to the bug in the 295.40 driver; which in any case does not support the FX cards. .

Some people report they cannot even get Unity 2D or Gnome Classic to work. 

So, yes, stick to what works for you!

Chao!, **bogan**.

Edit: PS. Bet I'm even older!!  87, &  still counting.

---

### Post by martenclark on 2012-05-14
thanks again for your help Dave it has been invaluable to me,

---

