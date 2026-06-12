---
title: "Desperately need help - monitor"
date: 2006-06-10
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-06-10
I just got the samsung syncmaster 173p plus silver and i have to install the driver. In the instructions, it says: 

To execute X-Window, you need to make the X86Config file, which is a type of system setting file.
 1. Press Enter at the first and the second screen after executing the X86Config file.
 2. The third screen is for setting your mouse.
 3. Set a mouse for your computer.
 4. The next screen is for selecting a keyboard.
 5. Set a keyboard for your computer.
 6. The next screen is for setting your monitor.
 7. First of all, set a horizontal frequency for your monitor. (You can enter the frequency
    directly.)
 8. Set a vertical frequency for your monitor. (You can enter the frequency directly.)
 9. Enter the model name of your monitor. This information will not affect the actual execution
    of X-Window.
10. You have finished setting up your monitor.
    Execute X-Window after setting other requested hardware.


But I don't know what ''To execute X-Window, you need to make the X86Config file, which is a type of system setting file''  means.

Where is this X86Config file? I don't understand. I'm desperate! Plz help!

---

### Post by IYY on 2006-06-10
XFree86 is an old X server. Ubuntu uses Xorg instead, and to configure it in a similar manner to the one described above, just run:

```
dpkg-reconfigure xserver-xorg
```

But if you ask me, I wouldn't even bother with that configuration. Just make the changes to your /etc/X11/xorg.conf file (with sudo and a text editor).  Look for the monitor section, and type in your rates:

```

Section "Monitor"
        Identifier      "COMPAQ V500"
        Option          "DPMS"
        HorizSync       30-60
        VertRefresh     50-85
EndSection

```

(of course, replace the rates with your own)

---

### Post by Scunizi on 2006-06-10
I looked up your monitor for the specs.  It looks like you have a standard VGA connector and a DVI connector.  You probably don't really need a driver since linux uses xorg.conf to configure the monitor.  Do your self a favor and from the consol "gedit /etc/X11/xorg.conf" and look at the file.  The text lines with a "#" in front of them are just notes.  In the top of the file it will often mention the command to have Ubuntu refresh or rebuild the xorg file in case of changes.  Write the command down.  I'd give it to you but I'm on a XP box right now.  Next, shutdown, plug in your new monitor to your video card.  If you have a choice of port types choose the DVI port (digital).  Reboot, you should get the system showing on the monitor with the Ubuntu main desktop.  Now back to the consol and enter the command line you wrote down preceeding it with sudo.. as in "sudo (command line)", enter, enter password, done.  Now you can "gedit /etc/X11/xorg.conf" and see the changes.  If your monitor is working great!

Here's the actual specs on your monitor you'll need if you're going to try to tweek it.

```
Specifications

Specifications
	

Model
	

173P

 
	

Part Number
	

173P - Silver

Panel
	

Type
	

a-si TFT /PVA

 
	

Size
	

17"

 
	

Pixel Pitch (mm)
	

0.264

 
	

Brightness
	

270cd/m2

 
	

Contrast Ratio
	

700:1

 
	

Viewing Angle
	

178o / 178o

 
	

Aspect Ratio
	

5:4

 
	

Response Time (ms)
	

25

 
	

Interface
	

Analog / Digital

Frequency
	

Horizontal Rate - (Analog)
	

30-81

 
	

Horizontal Rate - (Digital)
	

30-63

 
	

Vertical Rate
	

56-76

 
	

Bandwidth
	

140

Resolution
	

Maximum
	

1280 x 1024

Color
	

Maximum
	

16.7M

Signal Input
	

Input Video Signal
	

Analog RGB, DVI Digital link

 
	

Video Level: Analog
	

Analog:0.7VP-P

 
	

Video Level: Digital
	

TMDSTM

 
	

Sync Type
	

Separate H/V, Composite H/V, SOG

 
	

Input Connectors
	

15pin D-sub, DVI-D

Plug & Play
	

DDC
	

DDC 2B

Power
	

On / Working
	

40 Watts (Max)

Wall Mount
	

VESA®
	

VESA 75mm

 
	

Emission Standard
	

TCO '03

Cabinet Color
	

Bezel Color
	

Silver

Dimensions
	

Physical (WxHxD)
	

15.0" x 15.6" x 9.3"

 
	

Packaging (WxHxD)
	

18.7" x 16.1" x 6.9"

Weight
	

Net (physical)
	

13.2 lbs.

 
	

Gross (packaging)
	

17.6 lbs.

Special Features
	

Special Features
	

Ultra narrow bezel and slim design; Dual hinge stand; Pivot technology; Button less design; MagicTuneTM; MagicBrightTM; Color gamut 70.8%

Pivot
	

Pivot Technology
	

Yes
```

Now if you haven't already done so, install the correct driver for your video card.  Nvidia's latest is in Synaptic.  ATI I'm not sure about.  If you install the nvidia driver you'll have to go back into the xorg.conf file and replace the "nv" driver wording with "nvidia" and restart GDM.

Edit: Looks like someone beat me to it!

---

### Post by s_h_a_d_o_w_s on 2006-06-10
I'm sorry, I wasn't very clear. This new monitor has some weird function that if you rotate it, the desktop will rotatet with it. I want to activate it, but the instructions want some sort of driver. Is there a way to enable this function?

---

### Post by IYY on 2006-06-10
Do you have the full instructions? That part only talks about the refresh rates.

---

### Post by Scunizi on 2006-06-11
The manuel is available on Samsung's website.  Most monitors these days have the ability of automatically tellling the computer what their specs are.  It's possible that when you tilt the monitor into the verticle position it may automatically inform Ubuntu what's up.  However that may be a long shot.  There may be referances in the forums someplace to make this happen however I believe you'll be dealing with a couple of thing.  First, getting Ubuntu to automacilly recognize what position the monitor is in and make the appropriate changes on the fly.... and Second, for that to happen you will probably need some modifications to the xorg.conf file.  Thinking out loud now... It could actually be a function of the video driver itself.  If you are using Nvidia you should check out their page.  There is a whole section dedicated to Linux and various options to include for different situations.  xorg.conf is where you tell the video driver to do what you want.  Sorry I can't be more help.  It's an interesting problem.

---

### Post by mlind on 2006-06-11
I've got 970p, which is similar model
```

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       30-81
        VertRefresh     56-76
EndSection

```

I don't know if there's MagicRotate equivalent for linux, I thought
I saw a mention about such app on one 970p's reviews, but I couldn't find it anymore.

---

### Post by petex on 2007-11-22
did any of you manage to get linux drivers for this samsung 173p plus - I need them to set screen brigthness and other parameters - as you might know this monitor has no OSD other than software

---

