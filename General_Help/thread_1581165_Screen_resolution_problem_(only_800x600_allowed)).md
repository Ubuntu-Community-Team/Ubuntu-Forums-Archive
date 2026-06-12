---
title: "Screen resolution problem (only 800x600 allowed))"
date: 2010-09-24
forum: General Help
---

### Post by manfredrasta on 2010-09-24
Hi to everyone,

I am an absolute beginner and have installed LUbuntu from a desktop cd-rom in my Toshiba Satellite Pro 4600. There is a Pentium III inside.

I have searched in the forum and found that it is a common problem, but the solutions explained either did not work in my computer or I did not understand them. Maybe together we can fix the problem.

The maximun resolution I can select from the menu in preferences/monitor settings/ is 800x600 so there is a black band around my screen.

I do not have a file etc/X11/xorg.config and:
```

lspci | grep VGA

```
gives me:
```

01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)

```

Thank you very much.

EDIT: **[COLOR="Red"]if you have this same problem with this same card, and want the quick solution, just go to #7[/COLOR]**

---

### Post by Mark Phelps on 2010-09-24
This is a very OLD video chip.  Support for old chips is very limited in Linux.  It could very well be that 800x600 is the best you can get.

If it's any consolation, I have an old HP laptop and it too, can only get 800x600 using Ubuntu.

However, I was able to get 1024x768 using both OpenSUSE and PC Linux OS.

So, you can go to distrowatch.com, download and burn CDs of those distros, and try them out.  One of them might give you better resolution options.

---

### Post by IcewindDale on 2010-09-24
Hello.
It may very well be wrong EDID values detected although I have no idea if the issue even exists on laptops.
I used to have a somewhat old Samsung monitor that reported the wrong possible resolution values and ended up presenting a display with lower resolution than what I wanted.
At the time the solution involved editing xorg.conf and disabling EDID detection though I can't quite remember the details and disabling it entirely might even not be exactly healthy to your monitor.

The following articles might be a good place to start

[https://wiki.ubuntu.com/X/Troubleshooting/Resolution#Problem:%20%20Incorrect%20Resolution%20when%20no%20EDID%20available%20such%20as%20from%20old%20monitor%20or%20a%20KVM%20device](https://wiki.ubuntu.com/X/Troubleshooting/Resolution#Problem:%20%20Incorrect%20Resolution%20when%20no%20EDID%20available%20such%20as%20from%20old%20monitor%20or%20a%20KVM%20device)

[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)

---

### Post by Cpierce on 2010-09-24
I just fixed this with a trident card and Lubuntu install. Check this out:

[http://ubuntuforums.org/showthread.php?t=1579242](http://ubuntuforums.org/showthread.php?t=1579242)

Hope it help!

---

### Post by cavalier911 on 2010-09-24
Start here to determine if you can drive the screen to 1024x768

See #6 of this thread: 
[http://ubuntuforums.org/showthread.php?t=1536228](http://ubuntuforums.org/showthread.php?t=1536228)
Logon screen will be at 800x600 lxsession will autostart xrandr to force desktop to 1024x768

If you don't auto-logon and the logon screen has to be 1024x768.
This solution involves generating and configuring a xorg.conf to start xserver at 1024x768:
[http://ubuntuforums.org/showthread.php?t=1544285](http://ubuntuforums.org/showthread.php?t=1544285)

---

### Post by manfredrasta on 2010-09-25
Thank you all for the answer, it is a good feeling knowing that I am not alone in the dark .),
 
> **Cpierce said:**
> I just fixed this with a trident card and Lubuntu install. Check this out:
 
[http://ubuntuforums.org/showthread.php?t=1579242](http://ubuntuforums.org/showthread.php?t=1579242)
 
Hope it help!
 
mmmm, in the first post you say: 
'I checked the package manager and the trident 1.3.3-1 driver is installed'
 
How do I check that? If I go to Preferences/Hardware Drivers, it says that there are no private drivers used in this system, or something like that (I have it in italian).
 
 
 
> **IcewindDale said:**
> Hello.
It may very well be wrong EDID values detected although I have no idea if the issue even exists on laptops.
I used to have a somewhat old Samsung monitor that reported the wrong possible resolution values and ended up presenting a display with lower resolution than what I wanted.
At the time the solution involved editing xorg.conf and disabling EDID detection though I can't quite remember the details and disabling it entirely might even not be exactly healthy to your monitor.
 
The following articles might be a good place to start
 
[https://wiki.ubuntu.com/X/Troubleshooting/Resolution#Problem:%20%20Incorrect%20Resolution%20when%20no%20EDID%20available%20such%20as%20from%20old%20monitor%20or%20a%20KVM%20device]("https://wiki.ubuntu.com/X/Troubleshooting/Resolution#Problem:%20%20Incorrect%20Resolution%20when%20no%20EDID%20available%20such%20as%20from%20old%20monitor%20or%20a%20KVM%20device")
 
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)
 
Having a look at the first link my problem is one of these two: 
 
_Problem: Incorrect Resolution when no EDID available such as from old monitor or a KVM deviceProblem: Incorrect Resolution when no EDID available such as from old monitor or a KVM device_
In this case how can i know if I am using  KMS?
 
or
 
_Problem: Autodetection results in reduced resolutions available_
In this case, the problem is that i do not have a /etc/X11/xorg.conf file


At the second link I can see that I can create a new resolution:
The comand
```
xrandr
``` gives me,
```

Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  

```
so I have to add a new resolution. But:
```

marino@marino-laptop:~$ xrandr --addmode S-video 1024x768
# xrandr: cannot find output "S-video"

```
so I think that I have to create the mode first. I copy the terminal of what I have done. No changes after that:
```

marino@marino-laptop:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
marino@marino-laptop:~$ ^C
marino@marino-laptop:~$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
marino@marino-laptop:~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
  1024x768_60.00 (0x140)   63.0MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.4KHz
        v: height  768 start  771 end  775 total  798           clock   59.4Hz
marino@marino-laptop:~$ xrandr --admode S-video 1024x768
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>

```
Did I do anything wrong? Maybe the resolution for my screen is not 1024x768. It is an old Toshiba Satellite Pro 4600. How do I check my best resolution?



Thank you very much

---

### Post by Cpierce on 2010-09-26
Let me see if I can explain a little better what worked for me.

First, I would check to see if your computer can display 1024x768. You might need to check the manufacturer's specs or google it. 

To check if the Trident driver is installed, Go to "Synaptic Package manager" in sytem>admin and type in "trident". You will see if it is installed.

Then in terminal, type "sudo leafpad /etc/X11/xorg.conf"  This will open a xorg.conf even if you don't have one. then cut and paste this into the xorg.conf file, and save:

Section "Device"
  Identifier "Trident Microsystems CyberBlade XP"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  HorizSync 28-51
  VertRefresh 43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Trident Microsystems CyberBlade XP"
	SubSection "Display"
		   Depth 8
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 16
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 24
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 32
		   Modes "1024x768"
	EndSubSection
EndSection


Reboot and that's all I did ! Hope it works for you. If it does lock up or doesn't work, boot up on the live CD and in terminal run "sudo leafpad /media/<your_hard_drive_name>/etc/X11/xorg.conf" and delete the changes, save, and reboot and you should be back where you started.

---

### Post by manfredrasta on 2010-09-27
> **Cpierce said:**
> Let me see if I can explain a little better what worked for me.

First, I would check to see if your computer can display 1024x768. You might need to check the manufacturer's specs or google it. 

To check if the Trident driver is installed, Go to "Synaptic Package manager" in sytem>admin and type in "trident". You will see if it is installed.

Then in terminal, type "sudo leafpad /etc/X11/xorg.conf"  This will open a xorg.conf even if you don't have one. then cut and paste this into the xorg.conf file, and save:

Section "Device"
  Identifier "Trident Microsystems CyberBlade XP"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  HorizSync 28-51
  VertRefresh 43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Trident Microsystems CyberBlade XP"
	SubSection "Display"
		   Depth 8
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 16
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 24
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 32
		   Modes "1024x768"
	EndSubSection
EndSection


Reboot and that's all I did ! Hope it works for you. If it does lock up or doesn't work, boot up on the live CD and in terminal run "sudo leafpad /media/<your_hard_drive_name>/etc/X11/xorg.conf" and delete the changes, save, and reboot and you should be back where you started.

Ok, thank you again. In the Synaptic Pakage Manager there is not any package called trident or similar.

Should I try modifying the xorg.conf anyway?

---

### Post by manfredrasta on 2010-09-27
So,

i tried anyway, rebooted, and........ My screen is 1024x768!!!! Without the drivers.

Thank you Cpierce, and everyone who wrote here.

---

### Post by Cpierce on 2010-09-28
You are more than welcome. If you notice in the script, it tells it to use the Trident driver, Glad it worked for you too.

---

