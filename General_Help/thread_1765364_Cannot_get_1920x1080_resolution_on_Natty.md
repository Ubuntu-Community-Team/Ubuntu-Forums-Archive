---
title: "Cannot get 1920x1080 resolution on Natty"
date: 2011-05-23
forum: General Help
---

### Post by Jadzia Dax on 2011-05-23
Hi All, 

I really hesitated before opening this thread.  I read many threads with the same issue, followed them, and none seem to solve my problem, so, finally, here i am. 

I installed Natty about a month ago.  First time i installed, i got this same problem.  Installation pendrive works on 1920x1080, and the first time it boot it was lovely.  I did all the recommended installs, including ATI / AMD proprietary FGLRX Drivers, and the second time my machine boot, it came on 1600x1200.  I did some troubleshooting with xrandr, and was able to get HD resolution again, until i rebooted, and then i couldn't even get it with Xrandr.  

This is really driving me nuts.  I was able to get it fixed by going into recovery mode, and running ubuntu in low graphics mode, i was choosing reconfigure and it worked sometimes, but now i'm stucked with 1600x1200 and i hate it. 

I don't want to go back to windows, and i really followed every trhead i found with solutions and can't get it to work.  ](*,)

I forgot to mention that i have an Ati Radeon 4670 video card.  Also i am a total n00b on linux, i am good at following instructions though :P

Any help will be highly appreciated, 

Thanks in advance.

---

### Post by linuxinstalledfromhdd on 2011-05-23
I have always had trouble with ATI graphic cards and Ubuntu. 

Make and model of computer please?

---

### Post by Jadzia Dax on 2011-05-23
Motherboard is Asus P5QC, Video Card is Ati Radeon HD 4670

---

### Post by linuxinstalledfromhdd on 2011-05-23
I was hoping it was a MB with a on-board video port you could switch back to for the moment.  Hmmm.  Wait a while and let's bump this message and see if anyone knows.

BUMP

---

### Post by Jadzia Dax on 2011-05-23
haha thanks. 

Another thing, i was checking xrandr now

jadzia@jadzia:~$ xrandr
Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 1600 x 1600
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0*+
   1400x1050      60.0  
   1280x1024      60.0     47.0     43.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       60.0  
   1152x864       60.0     47.0     43.0  
   1280x768       59.9     56.0  
   1280x720       60.0     50.0  
   1024x768       60.0     43.5  
   800x600        60.3     56.2     47.0  
   720x480        60.0  
   640x480        60.0  
jadzia@jadzia:~$ 

Seems like its seeing my LCD monitor as CRT? Not sure if that's what it means, but just in case i paste it, it may help.

---

### Post by Hedgehog1 on 2011-05-23
When I boot my office PC (with ATI video) from my Natty install on a USB stick (full install), I get the full resolution of the monitor (1920x1200 in my case) and Unity/Compiz all **without using the proprietary ATI driver**.  The generic support in the Kernel seems to handle many ATI cards just fine.

As a quick experiment, could you try removing the proprietary driver and see if you get full resolution and working Unity/Compiz?

I have a sneaking suspicion that many folks with ATI cards should not be using the proprietary drivers any more in Natty.

***The Hedge***

:KS

p.s. Is **Jadzia Dax** from Deep Space Nine?

---

### Post by Jadzia Dax on 2011-05-23
Hi! 

Yes, Jadzia dax from DS9, i always use this as my nick name hehe.

I did remove the driver earlier today, at least i think i did, and when i rebooted, i got only 1024x768, then i re-installed it and ended up with 1600 again.

I hate to be stucked with this resolution :(

---

### Post by Hedgehog1 on 2011-05-23
> **Jadzia Dax said:**
> Hi! 

Yes, Jadzia dax from DS9, i always use this as my nick name hehe.

I did remove the driver earlier today, at least i think i did, and when i rebooted, i got only 1024x768, then i re-installed it and ended up with 1600 again.

I hate to be stucked with this resolution :(


Did you upgrade to 11.04? Or do a clean install?

---

### Post by Jadzia Dax on 2011-05-23
i made a clean install, as i was a few versions behind. 

Ah also, i forgot to say, when i took the drivers off, it did't boot on unity, it started up with the old gnome look, but i couldn't even see the whole screen :P

---

### Post by Hedgehog1 on 2011-05-23
> **Jadzia Dax said:**
> i made a clean install, as i was a few versions behind. 

Ah also, i forgot to say, when i took the drivers off, it did't boot on unity, it started up with the old gnome look, but i couldn't even see the whole screen :P

Well, that means my theory is wrong. Darn. So Please ignore that idea.

***Cisco Out...***

---

### Post by Jadzia Dax on 2011-05-23
I really hope this has a solution, it did work before, and now i cannot get it to work again, i don't want to end up re-installing, haha.

And nice to find another trekkie!! :)  I was in another community before (online game) and i was getting questions about my name being polish, and i had to explain it was from ST all the time haha.:D

---

### Post by Hedgehog1 on 2011-05-23
OK - I am back.

Here is a thread on where the resolutions are stored: [http://ubuntuforums.org/showthread.php?t=1449274]("http://ubuntuforums.org/showthread.php?t=1449274")

**Here is the text of that thread:**

*Just make a file with* ```
gksudo gedit /etc/X11/xorg.conf
``` *and then put what you need into i*t.

*This system may not work with all graphics cards, but it's worth a try.  If it does not help, just delete the xorg.conf file, and restart x.*
```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
EndSection 

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

**So I am thinking that you can change your maximum mode to 1920x1080 following this general idea.**

***The Hedge***

:KS

p.s. What is your opinion on Klingon Opera?

---

### Post by Hedgehog1 on 2011-05-23
It's weird seeing these vaules in this file.

I run all NVidia on my home systems, and my xorg.conf looks like this:

```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

```

**EDIT:** Found another short thread with a [SOLVED] on it: [http://ubuntuforums.org/showthread.php?t=1376927]("http://ubuntuforums.org/showthread.php?t=1376927")

---

### Post by hawthornso23 on 2011-05-23
Try running 
```
aticonfig --initial
```

---

### Post by Jadzia Dax on 2011-05-23
Report on progress, 

For the first solution, i checked when i got the resolution to be working fine, and that file was still empty, so i don't think changing that one will help much, as it worked without having that before (but still i'm a n00b :P) but that reminded me of this one and i googled it up again and followed all the instructions:
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

This one did work before, and now it is not working.

> 
jadzia@jadzia:~$ xrandr --output CRT2 --mode 1920x1080_60.00
xrandr: screen cannot be larger than 1600x1600 (desired size 1920x1080)


For the second one, i'm googling up the values of my screen, i tried though, and it gets stuck after i stop the service :S

About klingon Opera.... Scary!!! hahaha, still, having had a klingon husband,  i want a bathlet (however that is spelled )

Now for the aticonfig command, i did run it, is it pointing to a driver error?  I think its weird that what worked before isn't working now, and that the screen shows its CRT, when it isnt :S

> 
jadzia@jadzia:/etc/X11$ aticonfig --initial
Uninitialised file found, configuring.
Fail to link to fglrx-libglx.so, please check whether driver is installed correctly
Using xorg.conf
Saving back-up to xorg.conf.original-0
aticonfig: Writing to 'xorg.conf' failed. Permission denied.
jadzia@jadzia:/etc/X11$ sudo aticonfig --initial
[sudo] password for jadzia: 
Uninitialised file found, configuring.
Fail to link to fglrx-libglx.so, please check whether driver is installed correctly
Using xorg.conf
Saving back-up to xorg.conf.original-0
jadzia@jadzia:/etc/X11$ 

---

### Post by hawthornso23 on 2011-05-23
Something that often works for me is to open synaptic package manager and search for fglrx.  Mark all the already installed stuff for reinstallation and click apply.

---

### Post by Grenage on 2011-05-23
> **Jadzia Dax said:**
> Report on progress...

Hello there,

What monitor make and model are you using on the computer?

---

### Post by Jadzia Dax on 2011-05-23
I just reinstalled all the fglrx packages, but it's still the same :(

I have a Samsung syncmaster P2370MS

---

### Post by Grenage on 2011-05-23
> **Jadzia Dax said:**
> I have a Samsung syncmaster P2370MS

Try this as an xorg.conf.  First make a backup of the original if it exists:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Now create a new one, and add the config below:

```
gksu gedit /etc/X11/xorg.conf
```

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Samsung"
	ModelName "P2370MS"
	HorizSync 30 - 81
	VertRefresh 56 - 75
EndSection

Section "Device"
	Identifier "Device0"
	Driver "fglrx"
	VendorName "Radeon HD4670"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1920x1080"
	EndSubSection
EndSection
```

I've only listed one resolution, but we can add more if you wish. If that does not work, we can try adding a modeline to the config; if your computer doesn't display a GUI when it boots up, you can just delete the config and restart:

```
sudo rm /etc/X11/xorg.conf
```

---

### Post by Jadzia Dax on 2011-05-23
Hi Grenage, thanks a lot for the advice. It was really easy to follow :)

I just made the changes on the xorg file , and it booted up ok. But i still don't have the resolution showing on the resolution options to choose: 

[IMG]http://s1191.photobucket.com/albums/z466/danikz82/?action=view&current=Screenshot-4.png[/IMG] [http://s1191.photobucket.com/albums/z466/danikz82/?action=view&current=Screenshot-4.png](http://s1191.photobucket.com/albums/z466/danikz82/?action=view&current=Screenshot-4.png)

Just took a screenshot to show you.

---

### Post by Grenage on 2011-05-23
> **Jadzia Dax said:**
> Hi Grenage, thanks a lot for the advice. It was really easy to follow :)

I just made the changes on the xorg file , and it booted up ok. But i still don't have the resolution showing on the resolution options to choose: 

[IMG]http://s1191.photobucket.com/albums/z466/danikz82/?action=view&current=Screenshot-4.png[/IMG] [http://s1191.photobucket.com/albums/z466/danikz82/?action=view&current=Screenshot-4.png](http://s1191.photobucket.com/albums/z466/danikz82/?action=view&current=Screenshot-4.png)

Just took a screenshot to show you.

Nice wallpaper! Try this (I added a modeline):

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Samsung"
	ModelName "P2370MS"
	HorizSync 30 - 81
	VertRefresh 56 - 75
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "fglrx"
	VendorName "Radeon HD4670"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1920x1080"
	EndSubSection
EndSection
```

---

### Post by Jadzia Dax on 2011-05-23
I added the modeline, still the same :( it doesn't show me the option to change it, even though changes were successfully saved.

I was checking on xrandr, and i don't see it there either: 
> 
jadzia@jadzia:/etc/X11$ xrandr
Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 1600 x 1600
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0*+
   1400x1050      60.0  
   1280x1024      60.0     47.0     43.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       60.0  
   1152x864       60.0     47.0     43.0  
   1280x768       59.9     56.0  
   1280x720       60.0     50.0  
   1024x768       60.0     43.5  
   800x600        60.3     56.2     47.0  
   720x480        60.0  
   640x480        60.0  
jadzia@jadzia:/etc/X11$ 


And yeah, i love this wallpaper ^^

---

### Post by Grenage on 2011-05-23
> **Jadzia Dax said:**
> I added the modeline, still the same :( it doesn't show me the option to change it, even though changes were successfully saved.

I was checking on xrandr, and i don't see it there either: 


And yeah, i love this wallpaper ^^

We can try a BusID, you'll need to post the output of:

```
lspci | grep VGA
```

You could also try the open driver, rather than fglrx; is that an option?

---

### Post by Jadzia Dax on 2011-05-23
> 
jadzia@jadzia:/etc/X11$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]


Looks like i can try that one :)

How do i install it? and i need to get rid of the one i have now right? if i just disable it is it enough or do i need to take it off completely?  (i know how to disable, but i'm not sure about which packages should i uninstall)

---

### Post by Grenage on 2011-05-23
```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Samsung"
	ModelName "P2370MS"
	HorizSync 30 - 81
	VertRefresh 56 - 75
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "fglrx"
	VendorName "Radeon HD4670"
        BusID "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1920x1080"
	EndSubSection
EndSection
```

Try that.  If you want to try the open driver, you can just replace:

```
driver "fglrx"
```
with
```
driver "radeon"
```

You'll want to purge the proprietary driver, and there's some great info [here]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch").

---

### Post by Jadzia Dax on 2011-05-23
Well, first option didn't work, i just tried and rebooted.  I checked to make sure that changes were still there, and tried to change resolution but 1920 still doesn't show.  I shouldn't be doing anything else appart from that right?

If not, then i'll go ahead and remove all drivers with that info you just sent :)

I really hope i find the way to sort this out, i'd hate to reinstall again, and the worst part is that i know it will brake again, and i can't figure out why it breaks...

---

### Post by Grenage on 2011-05-23
> **Jadzia Dax said:**
> Well, first option didn't work, i just tried and rebooted.  I checked to make sure that changes were still there, and tried to change resolution but 1920 still doesn't show.  I shouldn't be doing anything else appart from that right?

If not, then i'll go ahead and remove all drivers with that info you just sent :)

I really hope i find the way to sort this out, i'd hate to reinstall again, and the worst part is that i know it will brake again, and i can't figure out why it breaks...

No, that should be it.  I've seen a few cases since the 11.04 release, where the rather specific xorg setting are ignored; I am assuming that something is rather different now.

Give the open driver a go, and let us know how it works out!

---

### Post by Jadzia Dax on 2011-05-23
Well, i just followed all this :
> 
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)

 sudo apt-get remove --purge fglrx*

 sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati

 sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core 
  sudo dpkg-reconfigure xserver-xorg
And changed the xorg.conf to "radeon".

Will reboot now and if i get video back again i will let you know haha :D  This is fun.

---

### Post by Jadzia Dax on 2011-05-23
Well, i'm glad to say i'm back!! yeai haha.

Almost there now Grenage.  When i rebooted after uninstalling the driver, it came up really ugly, in 1024x780 but when i went into monitor to check if i could change the resolution, it did show 1920x1080 this time, so i chose that one, and everything got frozen and started dying so i rebooted.  It came up in a good resolution, and it says it is 1920 x 1080, but it doesn't stretch enough to cover up the screen (i'm missing about 7 cms of screen on the left hand side), it's kind of weird now haha, but better than before :P

i took a picture of the LCD to show you:

[http://i1191.photobucket.com/albums/z466/danikz82/photo.jpg](http://i1191.photobucket.com/albums/z466/danikz82/photo.jpg)

---

### Post by Grenage on 2011-05-23
Welcome back. :)

Per chance, did the open driver create an xorg.conf, and if so could you post it here?  I had a similar problem at work to the one you're having now.

---

### Post by Jadzia Dax on 2011-05-23
Umm it seems like it is the same one i had .

> 
jadzia@jadzia:/etc/X11$ cat xorg.conf
Section "Monitor"
    Identifier "Monitor0"
    VendorName "Samsung"
    ModelName "P2370MS"
    HorizSync 30 - 81
    VertRefresh 56 - 75
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
EndSection

Section "Device"
    Identifier "Device0"
    Driver "radeon"
    VendorName "Radeon HD4670"
        BusID "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1920x1080"
    EndSubSection
EndSection
jadzia@jadzia:/etc/X11$ 


---

### Post by Jadzia Dax on 2011-05-23
I just decided to reboot again, to see what happened, and now i have real 1920x1080.

Grenage you did it  =D> It's solved now. (3 reboots did it after re installing the new driver)

I hope it stays this way, and if not i'll follow all these steps again.

Thank you all for your help!! , i am really glad i got my resolution back.  This forum rocks!!!:guitar:

Who marks it as resolved? do i have to let a mod know or something?  This may help other people also, i found many people with this issue, and not much of those with solutions hehe.

---

### Post by Hansholz on 2011-05-23
I've been following this problem closely...I have a similar problem but I don't understand think I can apply the same solution. I have an EeePC 1005HA with Intel 945G chipset and graphics. I got a 21" no-name touchscreen to link to the laptop with the intention of hiding the laptop away behind it and simply using the tactile widescreen with virtual keyboard. 

My problem is that I have mirrored the screens but the bigger one will only display in 800x600 (as does the netbook even though it's a wide screen) I want to be able to run the large screen in something like 1024x600 or better, as long as its 16:9.

Cant seem to work it out. The Monitor Config doesn't give me any higher options than 800x600. This is the output of xrandr. If it's any help. Also my xorg.conf file is practically empty. Can anyone please help?

xrandr

```
Screen 0: minimum 320 x 200, current 800 x 600, maximum 4096 x 4096
LVDS1 connected 800x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0 +   65.0  
   800x600        60.3*    56.2  
   640x480        59.9  
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3*    56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1
```
xorg.conf ... not sure if this is actually being used??

```
# Minimal xorg.conf for the Nouveau driver
Section "Device"
	Identifier	"Default screen"
      	Driver		"nouveau"
EndSection
```
Thanks in advance

---

### Post by Grenage on 2011-05-24
> **Jadzia Dax said:**
> I just decided to reboot again, to see what happened, and now i have real 1920x1080.

Grenage you did it  =D> It's solved now. (3 reboots did it after re installing the new driver)

I hope it stays this way, and if not i'll follow all these steps again.

Thank you all for your help!! , i am really glad i got my resolution back.  This forum rocks!!!:guitar:

Who marks it as resolved? do i have to let a mod know or something?  This may help other people also, i found many people with this issue, and not much of those with solutions hehe.

That's great news; sorry for the slow reply, I'm not usually at a PC in the evenings.  You can set the thread as solved using the *thread tools* at the top right.

> **Hansholz said:**
> I've been following this problem closely...I have a similar problem but I don't understand think I can apply the same solution. I have an EeePC 1005HA with Intel 945G chipset and graphics. I got a 21" no-name touchscreen to link to the laptop with the intention of hiding the laptop away behind it and simply using the tactile widescreen with virtual keyboard. 

My problem is that I have mirrored the screens but the bigger one will only display in 800x600 (as does the netbook even though it's a wide screen) I want to be able to run the large screen in something like 1024x600 or better, as long as its 16:9.

Cant seem to work it out. The Monitor Config doesn't give me any higher options than 800x600. This is the output of xrandr. If it's any help. Also my xorg.conf file is practically empty. Can anyone please help?

xrandr

```
Screen 0: minimum 320 x 200, current 800 x 600, maximum 4096 x 4096
LVDS1 connected 800x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0 +   65.0  
   800x600        60.3*    56.2  
   640x480        59.9  
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3*    56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1
```
xorg.conf ... not sure if this is actually being used??

```
# Minimal xorg.conf for the Nouveau driver
Section "Device"
	Identifier	"Default screen"
      	Driver		"nouveau"
EndSection
```
Thanks in advance

Howdy, Hansholz.  It's worth creating a new thread for your problem; I've not had any real experience with what you're doing, but I can try and help (and keep the thread active).

---

### Post by Hansholz on 2011-05-24
Thank you Sir!...I'll do that!:):arrow:

---

### Post by Jadzia Dax on 2011-05-24
> **Grenage said:**
> That's great news; sorry for the slow reply, I'm not usually at a PC in the evenings.  You can set the thread as solved using the *thread tools* at the top right.


What you said solved it, i just rebooted, as i'm a reboot fan!! haha.

Seriously, thanks a lot!!! I live in 1920x1080 again and i'm happy !!:D

Marked as solved!!

---

### Post by Jadzia Dax on 2011-05-30
> **Jadzia Dax said:**
> Well, i'm glad to say i'm back!! yeai haha.

Almost there now Grenage.  When i rebooted after uninstalling the driver, it came up really ugly, in 1024x780 but when i went into monitor to check if i could change the resolution, it did show 1920x1080 this time, so i chose that one, and everything got frozen and started dying so i rebooted.  It came up in a good resolution, and it says it is 1920 x 1080, but it doesn't stretch enough to cover up the screen (i'm missing about 7 cms of screen on the left hand side), it's kind of weird now haha, but better than before :P

i took a picture of the LCD to show you:

[http://i1191.photobucket.com/albums/z466/danikz82/photo.jpg](http://i1191.photobucket.com/albums/z466/danikz82/photo.jpg)


:( sad to be here again haha.

I rebooted the pc today and found that my monitor is back to not displaying full screen image (as shown on pic above).

I rebooted, it came back ok, and now i'm stucked with about 1/7th of my monitor in black :(

---

### Post by hawthornso23 on 2011-05-30
I sometimes have a similar problem after reboot on one of my machines where the display area is initially the wrong size and extends off the screen. The way to fix it is to trigger the monitor to refresh its settings which is most easily achieved by turning the monitor off and then on again.

---

### Post by Jadzia Dax on 2011-05-30
That didn't work :(

---

### Post by Grenage on 2011-05-31
Howdy again.

If we work on the assumption that it's underscan, can you try:

```
aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0
```

You may need to use sudo, I'm not sure - I don't have an ATI card.  If there is an under/overscan adjustment option in the catalyst control panel, use that instead.

---

### Post by Jadzia Dax on 2011-05-31
> 
sudjadzia@jadzia:~$ sudo aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUndersca[sudo] password for jadzia: 
sudo: aticonfig: command not found
jadzia@jadzia:~$ aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0aticonfig: command not found
jadzia@jadzia:~$ 
It doesn't find the command and i don't see ati catalyst stuff installed anymore either. 

It's really weird, if i left the pc off for about a day, it comes up ok again.  I guess i don't have to reboot anymore and if i do , turn it off for a day. 

Doesn't sound very logical though haha.  But this never happened on ubuntu 10.00 , if not, i would think there's something wrong with my video card.

---

### Post by Grenage on 2011-05-31
Urgh, of course it wouldn't be, we're using the open driver and not catalyst.  Try this:

```
xrandr --output CRT2 --set underscan off
```

I think xrandr reported CRT2 as your monitor?

---

### Post by Jadzia Dax on 2011-05-31
This is the xrandr i have now.  Since you fixed the resolution issue, it appears as VGA-0 now.

> 
jadzia@jadzia:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080      60.0*+
   1920x1080_60.00   60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1280x800       59.8  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)


I run it with VGA-0, and it came up with this:
> 
jadzia@jadzia:~$ xrandr --output VGA-0 --set underscan off
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  29
  Current serial number in output stream:  29
jadzia@jadzia:~$ 



---

### Post by Grenage on 2011-05-31
I am unfortunately at a loss as to why it's not accepting that option.  The only other suggestion I have is that we try to get the proprietary driver working again.

---

### Post by Jadzia Dax on 2011-05-31
My ubuntu hates me haha :(

Well, i'll leave it like this, I'd rather have 1920x1080 after many reboots, than not having it at all, so i will stay with the settings as i have them now .

And i'll see if maybe it gets fixed on an update or something , hopefully.

Thanks for your help Grenage, you are the best :popcorn:

---

### Post by Grenage on 2011-05-31
Under/overscan is one of those really irksome things that should have been cast unto the wind long ago.  It's just a shame we couldn't get it working perfectly.

---

