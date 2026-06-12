---
title: "Fresh install and can only get 800x600 screen res"
date: 2012-07-28
forum: General Help
---

### Post by typos1 on 2012-07-28
Recently got another pc, putting a fresh install of 12.04 on my old pc so I can sell it, but there is only 800x600/4:3 resolution available.

I remember when I first installed ubuntu on this pc, there was  a similar problem, so I ve looked back to my first few posts and tried to do what ppl on here told me to do then to correct it (basically edit xconfig and alter xandr), but not only do they not work, now the install wont boot -  after 5 mins of a blank screen, some terminal type text comes up and then it just hangs. I ve tried typing re boot but nothing happens.

Firstly anyone know how I can get it to boot now ? 

And secondly anyone know how I can get more resolutions listed in "display" ?

Thanks

---

### Post by TheFu on 2012-07-28
You need to know the graphics chips used and the  resolutions that the monitor supports. Pushing either to unsupported resolutions is a bad idea.

Running **xrandr** alone without any options on the PC (not remote) should show the supported resolutions from the GPU.

Then you can use something like this (from a netbook):
```
$ xrandr --output LVDS1 --mode 1024x600 --rate 60 --primary
```to set the mode you want.  Be certain the output device matches what **xrandr** says you have exactly.

Here's the output for a VM on a different laptop:
```
$ xrandr 
Screen 0: minimum 64 x 64, current 1920 x 1140, maximum 32000 x 32000
VBOX0 connected 1920x1140+0+0 0mm x 0mm
   1920x1140      60.0*+
   1440x1050      60.0  
   1280x960       60.0  
   1024x768       60.0  
   800x600        60.0  
   640x480        60.0  
```If this doesn't work, it is time for the big guns.  Use 'lshw' to figure out your GPU, then look up the supported resolutions and bit depths.  Looking up the resolutions supported by the monitor works fine for YOUR monitor, but not so much for the person buying the PC. I'd assume a safe resolution of 1280x800 or 1024x768.

If you the PC has either an nVidia or ATI GPU, loading those proprietary drivers would be good, then you'd want to use their specific programs to manage the resolution and refresh rates.

For nVidia those programs are:
```
sudo /usr/bin/nvidia-xconfig
sudo /usr/bin/nvidia-settings
```
I don't know what ATI drivers use, sorry.

As to the boot issue, you'll need to determine some Grub options, probably related to the video settings, that will let it boot. What those options need to be will depend on your specific PC or motherboard or GPU or southbridge or all sorts of other things. We need more data about the machine to be more helpful.  If it is a pre-built PC, searching for that model on the internet with "ubuntu install boot" should help.

---

### Post by typos1 on 2012-07-28
Ok, I dont know why what I did 3 years ago to sort it doesnt work now, other than things have changed in subsequent ubuntu versions. It does clearly show there is a problem with this type of pc and ubuntu when it comes to screen res, though.

I ll try the things you suggest . . . when I manage to get things booting properly  !

Its an Acer Aspire T-180 UB7Z, AMD 64X2 3800+, 2 Gb RAM, Nvidia onboard graphics, connecting to a 1680x1050 screen. (I also enabled upgraded Nvidia drivers on it)

---

### Post by TheFu on 2012-07-28
> **typos1 said:**
> I also enabled upgraded Nvidia drivers on it)

That was probably your mistake.  If a GPU driver is working for you, don't change it.  Go back to the driver installed by the package system, not directly from the GPU vendor. This ain't MS-Windows.

Often "newer" doesn't mean "better" when it comes to GPU drivers under Linux.
Since 11.04, Ubuntu has assumed 2D accelerated video was the standard for most systems. If your machines are like mine - they don't have that capability.  Loading Lubuntu 12.04 instead might be easier.

I'm not going to google for "install ubuntu 12,04 " and your Acer model. You can do that.

---

### Post by typos1 on 2012-07-28
No, it WASNT my mistake - the GPU driver WAS NOT "working" for me because it only offered one (800x600) resolution. 

I have had this same problem before on this pc, but what sorted it out before (on 9.04 which I then upgraded all the way up to 12.04) does not sort it now on this fresh install of 12.04 on the same pc (this is my old pc which I want to sell).

In my experience of Ubuntu, your advice "if a GPU driver is working for you, dont change it" is simply not correct, I have always upgraded my drivers on ubuntu and this is the first problem I ve had. And on top of that, if you install a graphics card, you SHOULD upgrade the driver otherwise it wont work properly.

I m fully aware it ISNT MS Windows, and thank god for that !!-  I tried re-installing XP as well (thought I would have more chance of selling it then) on the pc as well and I ve spent 10 days on it I ve lost count of the errors I ve got - it simply wont install properly, in the end I gave up and decided to sell it as Ubuntu only, not dual boot. Not used Windows for 3 years and after all the problems I got with it, I can see why I stopped using it - its cr*p !

---

### Post by cwsnyder on 2012-07-28
You are right, what worked in 9.04 will _not_ work in 12.04 to change your resolution.

In 9.04 your changed /etc/X11/xconf to add the resolution.

In 10.04 and later, you must use xrandr.  There is a pretty good article on setting your resolution using xrandr at [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html) which I have used even for resolutions for which the EDID of the monitor was read incorrectly.

---

### Post by TheFu on 2012-07-29
> **typos1 said:**
> No, it WASNT my mistake - the GPU driver WAS NOT "working" for me because it only offered one (800x600) resolution. 

Sorry, I misunderstood.  Not working and failing to show higher resolutions are definitely different issues.
> 
I have had this same problem before on this pc, but what sorted it out before (on 9.04 which I then upgraded all the way up to 12.04) does not sort it now on this fresh install of 12.04 on the same pc (this is my old pc which I want to sell).
 I assume you've done those updates over the years, not all in a few weeks, right?  I have done a massive update myself, all in 1 week from 6.xx to 8.04. It wasn't fun.  Since then, I've stayed on LTS releases for my main systems and only touched the intermediate releases for testing purposes.
> 
In my experience of Ubuntu, your advice "if a GPU driver is working for you, dont change it" is simply not correct, I have always upgraded my drivers on ubuntu and this is the first problem I ve had. And on top of that, if you install a graphics card, you SHOULD upgrade the driver otherwise it wont work properly.
  Let's just say that we've had very different experiences. 3 times I've attempted to use the non-package manager GPU drivers and I've been burned every time. Fortunately, I'm comfortable with a remote ssh connection and was able to roll back to previous drivers.
> 
I m fully aware it ISNT MS Windows, and thank god for that !!-  I tried re-installing XP as well (thought I would have more chance of selling it then) on the pc as well and I ve spent 10 days on it I ve lost count of the errors I ve got - it simply wont install properly, in the end I gave up and decided to sell it as Ubuntu only, not dual boot. Not used Windows for 3 years and after all the problems I got with it, I can see why I stopped using it - its cr*p !

So after all this, did **randr** get you to the higher resolutions? 
Is the PC booting into a GUI interface or just stuck at a CLI?

We'd still like to help.

---

### Post by typos1 on 2012-07-30
No probs.  :)

Yeah, did the updates over 3 years.

Just updated nVidia drivers, again with no probs.

Everything is sorted - I did a fresh install as I couldnt get it to boot properly and after the re-install I got 10 or 12 res options, compared to just one before !

The only thing different was that I changed the vga lead - I ve put my graphics card with DVI out, in my new pc, no DVI out on my old one, so only way to connect to monitor was with vga, had no cable so brought a Belkin one. 

Prior to re-installing I took it back and got a cheapo one from Asda (Wallmart's UK arm) for half the price and with this lead I got all the resolution options ! 

Proves the old adage "you get what you pay for" is nonsense put about by companies to try and justify taking more money off you for stuff ! Bit like Microsoft and Windows really, why pay loads of cash for a cr*p OS when ubuntu is free AND far better ?

---

### Post by Grenage on 2012-07-30
> **cwsnyder said:**
> In 10.04 and later, you must use xrandr.

Lol, oh? I use xorg.conf.  If it exists, it will be honoured.

---

### Post by cwsnyder on 2012-08-03
My xorg.conf which I had used from 7.04 to 9.10 broke with 10.04, specifically used because my Etronix 1701B monitor EDID wasn't read properly and I was limited to a maximum of 800x600 pixels.  Probably I wasn't able to figure out how to fix the broken state.

I was able to get the 1280x1024 display mode using xrandr and have used that method since.

---

### Post by cwsnyder on 2012-08-03
:-)

---

