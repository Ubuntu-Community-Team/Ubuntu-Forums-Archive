---
title: "ati graphics drivers don't appear to work?"
date: 2010-08-18
forum: General Help
---

### Post by one2fwee on 2010-08-18
While trying live usb versions of different gnome and kde distributions, i noticed very unusable performance, however since i read that live media versions of linux did not perform well, i merely assumed that was the reason.

The sad thing is though, i installed ubuntu 10.4 x64 and i am still having the same problems. The only way to get the system slightly usable is to completely disable desktop effects. However, even then, it sort of feels like windows xp before you have installed graphics drivers - like it's not using the hardware at all.

Even the little fish screensaver is basically unrunnable.

My graphics card is an ati radeon x1950 pro AGP version. I read on their site that they only support up to x-org 11.4 and i heard that the linux distributions as of now are beyond that - so i cannot install the official drivers for it (whether they are any good anyway?). I saw in the package manager there are radeonhd drivers also, but i didn't really know what these are and this card is before ati started making their hd series.

So basically, i don't really know what to do or where to turn to in regards to this.

Some other small, unrelated questions are:

How can i increase the amount scrolled with each click of my scroll wheel so it's equivalent to windows? it seems to be one line at the moment, where as in windows i think it is something like 3 - whatever the case, it seems painfully slow.

Also, of my 5 button intellimouse explorer, strangely, the extra forward and back buttons seem to work, but the middle click button doesn't - or at least, holding it in and dragging the mouse to scroll doesn't seem to work - or should it be used for something different in linux?

Sorry if any of these questions are silly, as i don't really know anything about linux.
Thanks for your time.

---

### Post by clhsharky on 2010-08-18
one2fwee

I  have a ATI Radeon X1650 card and don't suffer from any desktop effects or screensaver(OSS supports 2D & 3D acceleration). I suspect that your AGP card is causing a problem with KMS in Lucid.
It is fixable though, Agp is a pain with new KMS(kernel mode setting). It a known issue and will be solved.

Radeon is the correct driver for your OSS(open source stack), hope you dident try to install fglrx on your legacy card.

Fresher OSS PPA is here
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)

The latest kernels have some fixes for AGP with KMS.
The drivers are easy, add ppa and update your system.
The kernel is a little more fussy, your kernel image and headers must match. Ask for help if needed.
Configuring your xorg.conf file could also correct or help your problem. Its a little more detailed to do in Lucid.

My card works out of the box, but I use fresher OSS and kernel for performance and testing.

Do not do anything you don't understand, ask and research.

Sharky

---

### Post by one2fwee on 2010-08-19
Ok, thanks :)

What exactly is ppa?
Could you perhaps guide me through this install process as the stuff in the link seems a bit over my head in that i'm not quite sure exactly what i'm trying to do, or even how to do it.

Thanks for your help.

---

### Post by Lolo Uila on 2010-08-20
@clhsharky,

For the Radeon X1950 Pro the driver should be ReadeonHD. According to the description in Synaptic, xserver-xorg-video-radeonhd is the driver for the R5xx/R6xx series cards, which the RV570 X1950 is part of. However, that driver is not being installed or used by default.

I am in the same boat as the OP. I also have an AGP Radeon X1950 Pro video card, which is not being used, even though the output of "inxi -Gx" says it is (Direct Rendering = yes). Graphics performance is terrible. Even a simple operation like opening a window and dragging it causes the system to hang momentarily.

I have read a lot of cryptic info on KMS but still don't understand how to change drivers using that. Is there a clear explanation to be found somewhere (nothing I found with google was useful, it all seemed incomplete).

I have also read that xorg.conf can be used if you disable KMS, but again the info I found didn't have a clear explanation on how to do that.

Any help would be greatly appreciated!

Thanks.

---

### Post by one2fwee on 2010-08-24
I added the 2 lines to my sources and then ran an update through the update manager - that's what i assume you are meant to do?
Then i restarted and it had made no difference :S

I have found that turning off kms creating a file called "radeon-kms.conf" in etc/modprobe.d , with the contents:
options radeon modeset=0
seems to help a bit.

However i still get massive freezing when changing background image, or when enabling compiz blur or suchlike.
I have no idea if the ppas have installed since i don't really have much idea what i'm doing.

---

### Post by one2fwee on 2010-08-25
Erm is anybody there?

---

### Post by avengerxp on 2010-10-06
well clhsharky,

after researching, performing 3 fresh installs of ubuntu 10.04 (which i end up ruining every time i try to install VGA drivers), i guess i have found a place with a much detailed answer and a member who seems to know things ...

my system uses a x1950 VGA card as well. 

can anyone provide a detailed walk through on how to install and enable drivers for ATI (unsupported cards) in ubuntu 10.04 LTS.

while researching i found out that a lot of users have this issue..and it's diappointing to see that no fix is being posted as at now.

every new user stepping into Linux is not a tech guru. :(

---

### Post by mastablasta on 2010-10-06
as it was mentioned before you can't use the graphics drivers from ATI. they won't work on new X system that newer linux distributions are using. now you could install older linux distro and then use them or you can use opensource. open source drivers are sitll being developed and as you can feel they sometimes not work as they should.
 
you could try with a newer open soruce driver as mentioned above, by installing it through PPA.

---

### Post by phredbull on 2010-10-06
Here's a thread w/lots o' info on ATI & Linux:
[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)
follow the instructions in the opening post where it says "Ubuntu stuff";
I'm using a Radeon 7500 on Lucid w/2.6.35 kernel.
3d works and I can use Compiz, but it gets a bit sluggish, so I turn it off.

---

### Post by avengerxp on 2010-10-06
thank you for the feed back, i will try these and post the feed back.

it's sad to find out that ubuntu has poor support for hardware..:confused:

---

### Post by mastablasta on 2010-10-06
> **avengerxp said:**
>  ubuntu has poor support for hardware..:confused:
 
Actually it's the other way arround. hardware has poor support for Ubuntu. because all they care about is supporting windows.
 
But it's getting better and better. and open source drivers are also getting better.

---

### Post by clhsharky on 2010-10-06
avengerxp

phredbull pointing to handy"s thread is very good.

The Radeon open source stack drivers is correct driver for Radeon X1xxx chips.
> while researching i found out that a lot of users have this issue..and it's diappointing to see that no fix is being posted as at now.
I see no issue, you cant use the wrong driver on a chip, no matter what one wants.

I use the xorg-edgers PPA , for updated driver stack and kernel all in one place.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

The .35 kernel and the now default G3D driver(Gallium) in this ppa should help your performance in Lucid.

The latest OSS is more stable than fglrx ever was on this chip.


Sharky

---

### Post by avengerxp on 2010-10-06
ok, sorry for troubling.

how to get this done

> Add the xorg-edgers PPA ([https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)), update, upgrade.

what should i download?

command line?

upgraded to kernal 2.6.35 as per handys instructions... I dont want to go ahead without knowing what to do exactly on installing the edgers ppa... (am afraind i'll end up screwing this installation as well)

---

### Post by clhsharky on 2010-10-06
avengerxp

Go to site 
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
instructions on how to add ppa is down near package listings, read the hole page.
It tells you far more than I can, and its updated regularly.
add
```
ppa:xorg-edgers/ppa
```
to your system's Software Sources

Once ppa is added, use update manager or package manager to update.

You can also use package manager to install the newer .35 kernel for lucid.
You can use terminal but not necessary,I use Synaptic package manager.

Sharky

---

### Post by FahadMKS on 2010-10-06
> **clhsharky said:**
> one2fwee

I  have a ATI Radeon X1650 card and don't suffer from any desktop effects or screensaver(OSS supports 2D & 3D acceleration). I suspect that your AGP card is causing a problem with KMS in Lucid.
It is fixable though, Agp is a pain with new KMS(kernel mode setting). It a known issue and will be solved.

Radeon is the correct driver for your OSS(open source stack), hope you dident try to install fglrx on your legacy card.

Fresher OSS PPA is here
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa]("https://edge.launchpad.net/%7Exorg-edgers/+archive/ppa")

The latest kernels have some fixes for AGP with KMS.
The drivers are easy, add ppa and update your system.
The kernel is a little more fussy, your kernel image and headers must match. Ask for help if needed.
Configuring your xorg.conf file could also correct or help your problem. Its a little more detailed to do in Lucid.

My card works out of the box, but I use fresher OSS and kernel for performance and testing.

Do not do anything you don't understand, ask and research.

Sharky

That is absolutely right. The AGP (Accelerated Graphics Port) is an old model Card and it can cause issues even with the windows.

---

### Post by avengerxp on 2010-10-06
Feed back.

Updated kernal to 2.6.35 (when i boot i see it. :)

added the lines manually to software sources

> deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main 

updated using update manager.

still when i check system>admini>hardware drivers it does not show any specific driver being used. the list is empty.

[B]now i don't see artifacts around cursor.
Movies can be played and now watchable with VLC.
<thanks for the guidelines> [/B]

still unable to set desktop effects. (still at none)

---

### Post by clhsharky on 2010-10-06
avengerxp


> still when i check system>admini>hardware drivers it does not show any specific driver being used. the list is empty.
Will not be showing any for your card, as system>admin>hardware drivers will only show proprietary drivers not open source drivers.

In terminal
```
glxinfo|grep render
```
Will give info about 3D driver
```
dmesg|grep radeon
```
Will give info on radeon driver, that you need to use.


Sharky

---

### Post by avengerxp on 2010-10-07
Done! Thanks sharky!

now it seems much stable ....thanks...

> desktop:~$ glxinfo|grep render
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
desktop:~$ dmesg|grep radeon
[   16.072447] [drm] radeon defaulting to kernel modesetting.
[   16.072453] [drm] radeon kernel modesetting enabled.

---

### Post by clhsharky on 2010-10-07
avengerxp

> OpenGL renderer string: Software Rasterizer
This is problem, your 3D will be slow.
I do not know your hardware configuration/installation that is making 
Software Rasterizer fallback. Search or goggle Software Rasterizer might point to some solutions.
Apologizes for not being more help.


Sharky

---

### Post by avengerxp on 2010-10-08
so, does this software rasterizer needs to be changed to hardware rasterizer?

my system is

AMD athlon64
ATI x1950 pro VGA (r570 chipset)
ubuntu 10.04.1 LTS (kernal updated to 2.6.35

I am googling at the moment for this... didnt found any fix yet.

thanks a lot for the help and guidelines.

---

### Post by phredbull on 2010-10-08
If I enable KMS, then I get
```
OpenGL renderer string: Software Rasterizer                      
```If I disable KMS, then I get
```
OpenGL renderer string: Mesa DRI R100 (RV200 4C57) 20090101 AGP 4x x86/MMX/SSE2 TCL
```but either way, I don't notice a difference in performance.

---

