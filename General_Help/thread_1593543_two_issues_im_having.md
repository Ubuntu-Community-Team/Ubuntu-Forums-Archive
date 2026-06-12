---
title: "two issues im having"
date: 2010-10-11
forum: General Help
---

### Post by TimEnid on 2010-10-11
I had these issues since the previous version (10.4), i thought they would go away with 10.10.

1 - After booting up my pc, sometimes it loads, and then my mouse freezes and i am unable to do anything at all. keyboard doesnt work either. Causing me to do a restart

2 - when starting my pc, i get the ubuntu splash screen and then it jumps to a black screen with:

"desktop login"
after i out in my log in it asks for the password, i put that in and get 
"Weclome to Ubuntu...............etc.........." (forgot all the words, but its some statement welcoming me to ubuntu.
The i get

"tim@tim-desktop: $"

but this is all on a black screen. Only way to get past this is to reboot my pc. and then it loads properly.

---

### Post by Peter09 on 2010-10-11
Difficult to diagnose this,
it may be a graphics card issue, can you post the specs of your hardware.

---

### Post by TimEnid on 2010-10-11
here are the specs of the graphics card. my hardware is in my sig. thanks
GB GDDR5 memory 
ATI Eyefinity technology with support for up to three displays(1) 
ATI Stream technology(2) 
Designed for DirectCompute 11 and OpenCL 
Accelerated Video Transcoding (AVT)(2,5) 
Compliant with DirectX® 11 and earlier revisions 
Supports OpenGL 3.1 
Dual-mode ATI CrossFireX&#8482; technology support for highly scalable performance(6) 
ATI Avivo&#8482; HD video and display technology(3,7) 
Dynamic power management with ATI PowerPlay&#8482; technology(7) 
DL-DVI, DL-DVI, DisplayPort, HDMI 
PCI Express® 2.0 support

---

### Post by Rubi1200 on 2010-10-11
Here are two links that I hope will help you diagnose the problems:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)
[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

---

### Post by TimEnid on 2010-10-16
> **Rubi1200 said:**
> Here are two links that I hope will help you diagnose the problems:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)
[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)
this didnt help. here is a pic of the screen i sometimes get
[IMG]http://i54.tinypic.com/20ho5eu.jpg[/IMG]

---

### Post by TimEnid on 2010-10-18
any help with this?

---

### Post by Rubi1200 on 2010-10-18
After you see the login prompt, type in your username and password and then try either or both of these commands:

```
sudo startx

sudo service gdm start
```

Report any errors.

---

### Post by TimEnid on 2010-10-20
> **Rubi1200 said:**
> After you see the login prompt, type in your username and password and then try either or both of these commands:

```
sudo startx

sudo service gdm start
```Report any errors.

thanks. it happens randomly, so next time it happens, i will report back.

any help with the freezing issue. that link didnt seem to help me out.

---

### Post by TimEnid on 2010-10-30
another issue i keep running into:

when i boot up my pc, sometimes i get this pink screen (see pic)

then it freezes. so i restart, and instead of getting this screen, i get the screen that shows my kernels. i dont get the kernel screen on the first boot. anyone know why this is?

---

### Post by TimEnid on 2010-10-31
Anyone?

---

### Post by coreyscx on 2010-10-31
its a gpu issue i used to have it, if you run startx it will reopen ubuntu, x is failing..to be honest, i dunno how to fix it all i know is i got a new card and it hasent happened ever since, goodluck :)

---

### Post by TimEnid on 2010-10-31
> **coreyscx said:**
> x is failing..

what do you mean?

a new graphics card? would that also be the cause of the freezing?

is there an app that will let me check if something is wrong with my current graphics card?

---

### Post by Peter09 on 2010-11-02
Hi,
can you post the output of the terminal command
 
```
lshw -C video
```
 
This is not a bad card - but the card driver is incompatible.

---

### Post by matt_symes on 2010-11-02
Hi

Also, when it freezes can you shutdown gracefully using alt + SysRq + reisub.

[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

If you can then it would suggest to problem with x is causing both your first 2 issues as your kernel has not crashed.

Kind regards

---

### Post by TimEnid on 2010-11-02
> **Peter09 said:**
> Hi,
can you post the output of the terminal command
 
```
lshw -C video
```
 
This is not a bad card - but the card driver is incompatible.

this is what i get
> WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: Juniper [Radeon HD 5750 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:75 memory:d0000000-dfffffff memory:fbbc0000-fbbdffff ioport:b000(size=256) memory:fbba0000-fbbbffff

---

### Post by Peter09 on 2010-11-03
Looking on the web this appears to be a problem for others, with various symptoms and resolutions. 
 
Just as a sanity check have you done
 
```
sudo apt-get update && sudo apt-get upgrade
```
 
of late, just to ensure you have the latest drivers kernel etc.
 
Just wondering, many people fail to do this when they cannot get to a graphical login. Often the problem has been resolved through an update.

---

### Post by TimEnid on 2010-11-03
> **Peter09 said:**
> Looking on the web this appears to be a problem for others, with various symptoms and resolutions. 
 
Just as a sanity check have you done
 
```
sudo apt-get update && sudo apt-get upgrade
```of late, just to ensure you have the latest drivers kernel etc.
 
Just wondering, many people fail to do this when they cannot get to a graphical login. Often the problem has been resolved through an update.

yes i have done this recently. i am running 10.10, but had these problems since 10.4.

---

### Post by TimEnid on 2010-11-14
> **Rubi1200 said:**
> After you see the login prompt, type in your username and password and then try either or both of these commands:

```
sudo startx

sudo service gdm start
```

Report any errors.

i am still having this issue. it just took me about 10 minutes to log on. i tried the above and all i get is a black screen. this is becoming annoying, and unless i can fix it within it the next week, i may have to go back to windows 7. everytime i start my pc, im presented with something different, from the "all black log in screen", to the mouse freeze, to pink screen in the pic attached, or the list of kernels. Something is obviously wrong. And i need some help.

---

### Post by TimEnid on 2010-11-22
for anyone who may experience this issue. it was a video card issue. i thought i had been upgrading thru the methods mentioned above, but when i went to the radeon website, there was a new software version for 10.10 and 10.4, which i obviously didnt have. so i upgrade thru their site, and i have not seen these issues in a week. thanks everyone.

---

