---
title: "Nvidia card/driver and 2560x1440 Monitor"
date: 2012-08-07
forum: General Help
---

### Post by NertSkull on 2012-08-07
So I purchased a new monitor that lots of people have been talking about from Ebay.  The Yamakasi Catleap 270

I plugged it into my Nvidia gtx 460 and first tried to boot up windows (I dual boot).  Everything worked just perfect.

I then tried to boot up Kubuntu (12.04) and it went to a black screen, couldn't see anything.  If I did ctrl+alt+F1 to get to a terminal, it worked and I could issue commands.  So my computer wasn't frozen.

So I uninstalled all the nvidia drivers (I had the most current ones updated before adding the monitor) and when they were turned off, it works.  Using the built in video drivers for kubuntu it works just fine.

But I'd really like to use the nivida drivers instead.  So does anyone have any idea how I can do that?  Clearly my video card works, since the monitor works in windows and with the default kubuntu drivers.  So what do I do?  I'm totally lost.

I have two monitors, and when I install the nvidia drivers again, and go to the nvidia-settings and have it "detect" the monitors.  The new large one comes up with no identify information and a max resolution of like 320x460 (or something close to that).

Any ideas where I should go next?  Thanks everyone.

---

### Post by NertSkull on 2012-08-08
So I made things a bit easier to work with.

I switched my two monitors around.  So the new one is not in the primary DVI slot on the video card.  So now my 2ndary monitor (an old one) will boot and show me a desktop using the nvidia drivers.

But the new monitor still remains black.  But now, I can open nvidia settings and have it detect displays.  It obviously picks up the old one just fine.

But for the new, high resolution, one it just says this.

DFP-2 (DFP-2 on GPU-0)

I can tell it to do twin view, but when I do it doesn't work, it just reverts back to the old setting.  Also it tells me the max resolution is 640x480.  

So it feels as though nvidia isn't recognizing the monitor at all.  But I know it works, since it works in kubuntu when I turn off the nvidia driver and it works in windows.

Does this help any in getting closer to what to do?

---

### Post by rookworm on 2012-08-09
I have the exact same problem.

"X screen information" in the Nvidia control panel reports that the screen is 640x480 pixels, measuring 217x163mm at 24bpp. Name: DFP-2.

My card is GTX 560Ti, driver is 295.40 x86_64

Any help would be appreciated

I should add that the monitor works perfectly under windows, detected as a "generic 2560x1440 display"

---

### Post by NertSkull on 2012-08-09
Allright, I have this solved on my system.  So I'm going to document what I did here, in hopes that it may guide someone else to a possible solution.  My situation may be unlike anyone elses, but this is what I did.

**My Setup**

Video Card = Nvidia GTX 460
Nvidia drivers = 295.49
OS = Kubuntu 12.04
Monitors = Asus VE247H (1920x1080) and Yamakasi Catleap Q270

**The Problem**

From what I can tell, the problem is that the monitor is not correctly reporting the EDID.  Which is the information it sends to say what type of monitor it is, and everything about it.  So the nvidia drivers can't figure it out.

Because of that, I decided to see if I could manually set it up by directly editing xorg.conf.  I've never done that before, but I've got it working.

**Resource I used to Fix**

After searching for ages, I found this thread that directly confirmed my suspicion, and the basics of how to fix it.

[http://www.codesim.com/tips/index.php?t=3](http://www.codesim.com/tips/index.php?t=3)

By using that link, you should in theory be able to fix yours.  Thats all I used.  I just had to play around with the xorg.conf to make it actually work for my system.  You can see the link suggests this works with multiple monitors (Achieva Schimian, Catleap and Crossover)

**Specifically fixed for my system**

The problem I had with that, is I had never setup twinview manually.  I was able get the Catleap up working alone really quick, but figuring out twinview was more difficult.

(Their example has twinview in it, but it wasn't the same as what my system needed.  If you disable those two lines in their example, a single monitor should work just by pasting that into your xorg.conf)

I'll post my xorg.conf below twice.  The first one I'll go through and explain as much as I can what I changed.  And the 2nd time I'll just put it up straight as it is in my system.

Annotated with what I changed
```

[COLOR="Blue"]# This section defines the Catleap (HiRes) monitor.  
# I just left this section completely the same as in the example
#[/COLOR]

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Shimian"
    ModelName      "QHD270"
    HorizSync      88.8
    VertRefresh    59.5
    Option         "DPMS"
    Modeline       "2560x1440" 241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
    DisplaySize    597 336  
EndSection

[COLOR="blue"]#
# This section defines the video card, I didn't change anything here either
#[/COLOR]
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 460"
EndSection

[COLOR="blue"]# This is the section I changed
#
# The BIGGEST issue I had, was figuring out what was on DFP-0, DFP-1 and DFP-2 (which are the dvi/hdmi outputs)
# In MY system, DFP-0 is the "primary" DVI output
# and DFP-1 is the mini-HDMI output
# and DFP-2 is the 2ndary DVI output
# So I want my Catleap on DVI-0 and the Asus twinview monitor on the DFP-2 (so I had to change my cables)
#[/COLOR]
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "1"
[COLOR="blue"]# Leave this as DFP-0, which is where the Catleap(hires) monitor is plugged into.
# This (I believe) tells the system what the "primary" display is in the twin view[/COLOR]
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "UseEDID" "False"
    Option         "UseEDIDDPI" "False"
    Option         "UseEDIDFreqs" "False"
    Option         "ExactModeTimingsDVI" "True"
[COLOR="Blue"]# This is the only other line I had to change from the example
# DFP-0: 2560x1440_60 +0 +0   <--- This line is the "primary" display on DFP-0 (the Catleap HiRes)
# DFP-2: 1920x1080 +2560 +0   <--- This was for the 2nd monitor, resolution and offset.
# Don't forget the comma between the two monitors[/COLOR]
    Option         "metamodes" "DFP-0: 2560x1440_60 +0 +0, DFP-2: 1920x1080 +2560+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Option         "Xinerama" "0"
EndSection

```

As it is in my system
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Shimian"
    ModelName      "QHD270"
    HorizSync      88.8
    VertRefresh    59.5
    Option         "DPMS"
    Modeline       "2560x1440" 241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
    DisplaySize    597 336  
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 460"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "UseEDID" "False"
    Option         "UseEDIDDPI" "False"
    Option         "UseEDIDFreqs" "False"
    Option         "ExactModeTimingsDVI" "True"
    Option         "metamodes" "DFP-0: 2560x1440_60 +0 +0, DFP-2: 1920x1080 +2560+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Option         "Xinerama" "0"
EndSection

```

I hope that helps people.  Feel free to ask questions if what I did doesn't make sense.  But I'm by no means an expert.

I know have my two monitors working using the Nvidia Drivers.  Thanks for those who pointed me in the right direction.

**Sidenotes**
For those that may not know

xorg.conf is located in 

```
/etc/X11/xorg.conf
```

If it doesn't exist, create it.

Also, this command is useful to restart to x-server

```
sudo service kdm restart     (if you are kubuntu)
sudo service gdm restart     (if you are ubuntu)
```

Also, since you often don't have a working monitor.  

```
ctrl+alt+F1 and ctrl+alt+F7 
```

will switch you back between terminal and graphical modes.

Hope that helps.  Thanks

---

### Post by Mearis on 2012-08-10
That worked perfectly for me, thank you very much for the help!

---

### Post by rockets on 2012-08-11
Also worked for me. Catleap Q270 SE with NVIDIA GTX 560  on Kubuntu Lucid 10.04.

---

### Post by spundot on 2012-08-26
@NertSkull thanks for the instructions. They helped me get my Potalion 2710QW working in Ubuntu 12.04.

Both your instructions and the ones on codesim were for dual monitors and I only have one, so I had to modify the x.conf file to remove all the dual monitor stuff.

The lines I removed were:
```
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "Xinerama" "0"
```

The line I changed was from this:
```
Option         "metamodes" "2560x1440_60 +0 +0, 2560x1440_60 +2560+0"
```
to this:
```
Option         "metamodes" "2560x1440_60 +0 +0"
```

I also changed some of the device and monitor strings for my setup. Full x.conf follows:

```
Section "Monitor"
	Identifier	"Monitor0"
	VendorName	"Potalion"
	ModelName	"Magical Monitor"
	HorizSync	88.8
	VertRefresh	59.5
	Option		"DPMS"
	Modeline	"2560x1440" 241.50 2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
	DisplaySize	597 336
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Device0"
	Monitor		"Monitor0"
	DefaultDepth	24
	Option		"NoLogo" "True"
	Option		"UseEDID" "False"
	Option		"UseEDIDDPI" "False"
	Option		"UseEDIDFreqs" "False"
	Option		"ExactModeTimingsDVI" "True"
	Option		"metamodes" "2560x1440_60 +0 +0"
	SubSection "Display"
		Depth	24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Layout0"
	Screen	0	"Screen0" 0 0
EndSection

Section "Device"
	Identifier	"Device0"
	Driver		"nvidia"
	VendorName	"NVIDIA Corporation"
	BoardName	"GeForce GT 430"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by spundot on 2012-08-26
I just ran across an alternate method for this fix - basically it uses a prebuilt EDID file for the monitor instead of typing it all out in the x.conf file. I tried it and it seems to work - I do like that it keeps your x.conf nice and tidy. I did get an error after boot saying that colord crashed, but I don't know if it's related (Ubuntu 12.04).

[http://www.overclock.net/a/sound-quieter-in-linux-than-windows-2560x1440-27-korean-display-not-working-the-problems-i-encountered-and-their-solution]("http://www.overclock.net/a/sound-quieter-in-linux-than-windows-2560x1440-27-korean-display-not-working-the-problems-i-encountered-and-their-solution")

---

### Post by [Neurotic] on 2012-09-06
Hey - has anyone tried this with the Nvidia driver 304.43?

I can't seem to get it to work! (Although I had it working with the old driver).

Reason I want to upgrade is that this driver lets us do per physical screen colour correction, and I find the blue tint on my catleap is driving me a little crazy.

Anyone managed to get this working? I've tried both the custom EDID and also the modified xorg.conf file, and both either won't display or I get a really mangled screen.

Help?!

---

### Post by jemmy on 2012-10-14
Many Thanks for all the good help contained here.
For a couple of days, I thought I was up the creek without a paddle
my korean Crossover 27Q monitor now works well on 12.04 @ 2560 x 1440

I patched an xorg.conf file together from the posts on this thread
after i finally got some ATI drivers to load for a Radeon 7750 

Quote:
Section "Monitor"
	Identifier	"Monitor0"
	VendorName	"Crossover"
	ModelName	"27Q"
	HorizSync	88.8
	VertRefresh	59.5
	Option		"DPMS"
	Modeline	"2560x1440" 241.50 2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
	DisplaySize	597 336
EndSection
	
Section "Screen"
		Identifier	"Screen0"
	Device		"Device0"
	Monitor		"Monitor0"
	DefaultDepth	24
	Option		"NoLogo" "True"
	Option		"UseEDID" "False"
	Option		"UseEDIDDPI" "False"
	Option		"UseEDIDFreqs" "False"
	Option		"ExactModeTimingsDVI" "True"
	Option		"metamodes" "2560x1440_60 +0 +0"
	SubSection 	"Display"
			Depth	24
	EndSubSection
EndSection
	
Section "Module"
	Load		"glx"
EndSection

Section "ServerLayout"
	Identifier	"Layout0"
	Screen	0	"Screen0" 0 0
EndSection

Section "Device"
	Identifier   	"Device0"
	Driver      	"fglrx"
	BusID       	"PCI:1:0:0"
EndSection

---

### Post by Silvo on 2012-12-07
Help please!

I'm trying to follow these instructions to run my Catleap Q270 with twinview with my smaller LG monitor. I am able to get each one working individually, but the problem happens when I try to run them with twinview. 

If I connect only the LG, nvidia-settings will let me select from a variety of resolutions for it. However, if I use the xorg.conf file posted above, the LG stops working properly, and the only options are Auto (800x600) and 2560x1440, but the LG is only 1680x1050. I think this line might be the problem:

```
Modeline "2560x1440" 241.50 2560 2608 2640 2720 1440 1443 1448 1481 +hsync -vsync
```

because now the only resolution I can pick is 2560x1440 even for the LG. It seems to have stopped auto-detecting the valid resolutions. 

Is there some way to modify xorg.conf to add this resolution (1680x1050) back in?

Just so we're clear, I have this line that specifies both monitors' resolutions, but it just results in a black screen on the LG, or alternatively an 800x600 resolution:

```
Option         "metamodes" "2560x1440_60 +0 +0, 1680x1050 +2560+0"
```

Thanks!

---

### Post by sylar666 on 2013-02-06
> **Silvo said:**
> Help please!

I'm trying to follow these instructions to run my Catleap Q270 with twinview with my smaller LG monitor. I am able to get each one working individually, but the problem happens when I try to run them with twinview. 

If I connect only the LG, nvidia-settings will let me select from a variety of resolutions for it. However, if I use the xorg.conf file posted above, the LG stops working properly, and the only options are Auto (800x600) and 2560x1440, but the LG is only 1680x1050. I think this line might be the problem:

```
Modeline "2560x1440" 241.50 2560 2608 2640 2720 1440 1443 1448 1481 +hsync -vsync
```because now the only resolution I can pick is 2560x1440 even for the LG. It seems to have stopped auto-detecting the valid resolutions. 

Is there some way to modify xorg.conf to add this resolution (1680x1050) back in?

Just so we're clear, I have this line that specifies both monitors' resolutions, but it just results in a black screen on the LG, or alternatively an 800x600 resolution:

```
Option         "metamodes" "2560x1440_60 +0 +0, 1680x1050 +2560+0"
```Thanks!

Refloating the thread, I have the same issue as you, I have a Achieva Simyian, 2560*1440 monitor.
Thanks to prior posts I was able to configure it, but I cant make my other display, a SONY BRAVIA 1920x1080 to work above 800x600. 

¿Anyone knows how can we force it to work? My xorg.conf is almost tfe same as the previous ones.

Thank You in advance :D

---

### Post by dekoomer on 2013-02-06
I also have a problem doing this.

I have Four monitors, without the Xorg.conf file they all work just fine except for my main 2560x1440 monitor.

When i do create the Xorg.conf file, using OP method. The 2560x1440 monitor works, however the others will stop working. i can get them to Turn on with twinview but the res cannot go any higher then 800x600.

attempts to edit the EDID file for my setup have only led to all of my monitor to stop working.

---

### Post by sylar666 on 2013-02-07
> **dekoomer said:**
> I also have a problem doing this.

I have Four monitors, without the Xorg.conf file they all work just fine except for my main 2560x1440 monitor.

When i do create the Xorg.conf file, using OP method. The 2560x1440 monitor works, however the others will stop working. i can get them to Turn on with twinview but the res cannot go any higher then 800x600.

attempts to edit the EDID file for my setup have only led to all of my monitor to stop working.

I'm using nvidia-experimental-310 driver,  after many attemps without success I'm thinking to switch to previous versions to see if that fixes the problem. Which nvidia driver are you using?

EDIT: NO DRIVER change had solved anything... :(

---

### Post by Silvo on 2013-02-12
Hey guys,

I managed to get it to work, by generating a new EDID manually for my LG monitor, and using the EDID file for the Catleap from here: [http://learnitwithme.com/?p=342](http://learnitwithme.com/?p=342)

I've made a note of the steps I used to do this, which might help you solve it for your monitors. Note that I had to boot Windows to run Phoenix EDID Designer to get my LG's EDID file.

More info at:
[http://ubuntuforums.org/showthread.php?t=1946208](http://ubuntuforums.org/showthread.php?t=1946208)
[http://ubuntuforums.org/showthread.php?t=1857772&highlight=edid](http://ubuntuforums.org/showthread.php?t=1857772&highlight=edid)


Manual EDID for non-Catleap monitor:
* Boot Windows
* Install Phoenix EDID Designer
* Save all registry EDIDs to text files
* Boot Linux
* Compile C program to turn text files into binary files
* Manually edit the text files to remove columns and row headings
* Convert into .bin files:
        .EDIDprog < GSM.txt > GSM.bin
* Install read-edid (command is for Arch Linux, you'll need to find the Ubuntu equivalent, it's probably just an apt-get away though):
        yaourt -S read-edid
* Parse EDID files to look at contents:
        parse-edid < GSM.bin
* Keep the one for the LG monitor


Add line to xorg.conf:
    Option         "CustomEDID" "DFP-0:/path/to/EDIDs/edid-catleap.bin; DFP-1:/path/to/EDIDs/edid-LG.bin"



NOTE: this problem can definitely be solved another (simpler) way. I had it working before and definitely didn't need to generate any EDID files, I managed to solve it by playing with the xorg.conf file. But I didn't back it up and now it's gone so I don't know how I did it. But this method is working perfectly for me (for now, until I get a new monitor and it all goes to hell) so I'm not going to touch it anymore. 

Good luck!

---

### Post by sylar666 on 2013-02-12
> **Silvo said:**
> Hey guys,

I managed to get it to work, by generating a new EDID manually for my LG monitor, and using the EDID file for the Catleap from here: [http://learnitwithme.com/?p=342](http://learnitwithme.com/?p=342)

I've made a note of the steps I used to do this, which might help you solve it for your monitors. Note that I had to boot Windows to run Phoenix EDID Designer to get my LG's EDID file.

More info at:
[http://ubuntuforums.org/showthread.php?t=1946208](http://ubuntuforums.org/showthread.php?t=1946208)
[http://ubuntuforums.org/showthread.php?t=1857772&highlight=edid](http://ubuntuforums.org/showthread.php?t=1857772&highlight=edid)


Manual EDID for non-Catleap monitor:
* Boot Windows
* Install Phoenix EDID Designer
* Save all registry EDIDs to text files
* Boot Linux
* Compile C program to turn text files into binary files
* Manually edit the text files to remove columns and row headings
* Convert into .bin files:
        .EDIDprog < GSM.txt > GSM.bin
* Install read-edid (command is for Arch Linux, you'll need to find the Ubuntu equivalent, it's probably just an apt-get away though):
        yaourt -S read-edid
* Parse EDID files to look at contents:
        parse-edid < GSM.bin
* Keep the one for the LG monitor


Add line to xorg.conf:
    Option         "CustomEDID" "DFP-0:/path/to/EDIDs/edid-catleap.bin; DFP-1:/path/to/EDIDs/edid-LG.bin"



NOTE: this problem can definitely be solved another (simpler) way. I had it working before and definitely didn't need to generate any EDID files, I managed to solve it by playing with the xorg.conf file. But I didn't back it up and now it's gone so I don't know how I did it. But this method is working perfectly for me (for now, until I get a new monitor and it all goes to hell) so I'm not going to touch it anymore. 

Good luck!

Thanks for the help, unfortunately, my compiling skills are very low, Im very lost at this steps:

* Compile C program to turn text files into binary files
* Manually edit the text files to remove columns and row headings
* Convert into .bin files:
        .EDIDprog < GSM.txt > GSM.bin

As far as I know, this is my C program as I saw on the other thread

```
#include <stdio.h>

int main()
{
  while (!feof(stdin))
  {
    unsigned char i;
    scanf("%02X ", &i);
    printf("%c", i);
  }
  return 0;
```I'm using Anjuta to make the program, and I have my txt files ready to conversion
But thats all I have manage to do :(, Can you help me here, please?

If it's worth it, there are my .txt files

---

### Post by Silvo on 2013-02-13
> **sylar666 said:**
> Thanks for the help, unfortunately, my compiling skills are very low, Im very lost at this steps:

* Compile C program to turn text files into binary files
* Manually edit the text files to remove columns and row headings
* Convert into .bin files:
        .EDIDprog < GSM.txt > GSM.bin

As far as I know, this is my C program as I saw on the other thread

```
#include <stdio.h>

int main()
{
  while (!feof(stdin))
  {
    unsigned char i;
    scanf("%02X ", &i);
    printf("%c", i);
  }
  return 0;
```I'm using Anjuta to make the program, and I have my txt files ready to conversion
But thats all I have manage to do :(, Can you help me here, please?

If it's worth it, there are my .txt files


No worries! It is a little difficult to follow, I agree. That's the right C code (except there should be one more line at the end with just a right curly brace } after the return statement), save it as say main.c

Then compile it, naming the program as EDIDprog:
gcc main.c -o EDIDprog

Then run it with:
./EDIDprog < sony.txt > sony.bin

(I forgot the ./ in my original post). I got several files for my monitor, and just picked the best-looking one and used that. 

Good luck!

---

### Post by sylar666 on 2013-02-13
> **Silvo said:**
> No worries! It is a little difficult to follow, I agree. That's the right C code (except there should be one more line at the end with just a right curly brace } after the return statement), save it as say main.c

Then compile it, naming the program as EDIDprog:
gcc main.c -o EDIDprog

Then run it with:
./EDIDprog < sony.txt > sony.bin

(I forgot the ./ in my original post). I got several files for my monitor, and just picked the best-looking one and used that. 

Good luck!

All clear and perfect, I manage to make my .bin files and to learn in the process, thnaks a lot.

This is my xorg.conf now

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Shimian"
    ModelName      "QHD270"
    HorizSync      88.8
    VertRefresh    59.5
    Option         "DPMS"
    Modeline       "2560x1440" 241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
    DisplaySize    597 336  
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 670"  
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-3"
    Option         "CustomEDID" "DFP-3:/home/carlos/Documentos/BIN/monitor2.bin; DFP-1:/home/carlos/Documentos/BIN/sony.bin"
    Option         "UseEDID" "True"
    Option         "UseEDIDDPI" "False"
    Option         "UseEDIDFreqs" "False"
    Option         "ExactModeTimingsDVI" "True"
    Option         "metamodes" "DFP-3: 2560x1440_60 +0 +0, DFP-1: 1920x1080 +2560+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Option         "Xinerama" "0"
EndSection



```Still not working :/ , I added the line to other places, but no luck, where shoul it be added?  I also changed the option 

```
Option         "UseEDID" "False" 
```to true. Something I'm not doing here right....

---

### Post by Silvo on 2013-02-13
Hmm, not sure. I take it you've double checked your DFP-x numbers?

If it helps, my xorg.conf now looks like this:

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Shimian"
    ModelName      "QHD270"
    HorizSync      88.8
    VertRefresh    59.5
    Option         "DPMS"
    Modeline       "2560x1440" 241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
    DisplaySize    597 336  
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "LG Electronics W2252"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GTX+"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "ExactModeTimingsDVI" "True"
    Option         "metamodes" "DFP-0: 2560x1440_60 +1680+0, DFP-1: 1680x1050 +0+0"
    Option         "CustomEDID" "DFP-0:/etc/dotfiles/edid-catleap.bin; DFP-1:/etc/dotfiles/xorg/edid-LG.bin"
    Option         "ConnectedMonitor" "Monitor0, Monitor1"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Option         "Xinerama" "0"
EndSection

```

A lot of that is unnecessary, I'm sure. Maybe try removing those extra EDID lines you have? I really don't know, sorry!

---

### Post by sylar666 on 2013-02-13
> **Silvo said:**
> Hmm, not sure. I take it you've double checked your DFP-x numbers?

If it helps, my xorg.conf now looks like this:

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Shimian"
    ModelName      "QHD270"
    HorizSync      88.8
    VertRefresh    59.5
    Option         "DPMS"
    Modeline       "2560x1440" 241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
    DisplaySize    597 336  
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "LG Electronics W2252"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GTX+"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "ExactModeTimingsDVI" "True"
    Option         "metamodes" "DFP-0: 2560x1440_60 +1680+0, DFP-1: 1680x1050 +0+0"
    Option         "CustomEDID" "DFP-0:/etc/dotfiles/edid-catleap.bin; DFP-1:/etc/dotfiles/xorg/edid-LG.bin"
    Option         "ConnectedMonitor" "Monitor0, Monitor1"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Option         "Xinerama" "0"
EndSection

```A lot of that is unnecessary, I'm sure. Maybe try removing those extra EDID lines you have? I really don't know, sorry!

thanks for the quick answer, I'll check later at home and let you know.

EDIT: DONE¡¡¡ Thank you very much pal, now everything works fine. Just a tip, don't save options with nvidia-settings, will destroy everything.

---

### Post by sylar666 on 2013-02-15
Well, I think it's not necesary to start another thread, it seems the problem I'm going to explain maybe related to this Xorg.conf.

Ok, so I have finally the multy monitor set up nice and today I bought several linux games at steam.
I'm trying some games and everything seems to work, until I check killing floor,  (others like FTL and PENUMBRA failed too, so its not a specific game issue), the game starts and the X screen crashes. I see the blue light from the shimian monitor blinking and I have to restart the X server to come back to life.

Windowed mode in these games works.  First I'm trying to solve here is what the problem is
Scalating?  Xorg.conf? OpenGL?

Are you experiencing the same issues?

EDIT: Well, everything is a little messed up, first of all, I managed to make some games work by manually adding to the .ini and .cong files the monitor resolution. Unfortunately, It's not possible (or I can't) to use this solution with all games/software. I.e. opening XBMC directly kills the Shimian monitor and arrange the layout telling me there is only the 190x1080 monitor, and so on...
How can I make my xorg.conf to eork properly?

---

### Post by sinsterizme on 2013-04-05
THANK YOU OP - you are a life saver!
Just to help anyone who reads this this xorg.conf worked for 1 catleap monitor and a gtx 670: 
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Shimian"
    ModelName      "QHD270"
    HorizSync      88.8
    VertRefresh    59.5
    Option         "DPMS"
    Modeline       "2560x1440" 241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
    DisplaySize    597 336
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 670"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "UseEDID" "False"
    Option         "UseEDIDDPI" "False"
    Option         "UseEDIDFreqs" "False"
    Option         "ExactModeTimingsDVI" "True"
    Option         "metamodes" "2560x1440_60 +0 +0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Option         "Xinerama" "0"
EndSection

```

Just a tip, if you can't even get to a tty shell (for example my monitor turned off if I tried to) then just put the file on a usb, boot into grub > recover mode > fsck > root 
now you have a console and simply move the file to /etc/X11/xorg.conf 

Again, awesome work for figuring this out :)

---

### Post by ShamoIdol on 2013-05-06
My particular model is QNIX QX2710

When I got it was not working  but I've fixed with "modeline". There's a lot of info on this.

However when I upgrade to kubuntu 13.04 raring the 'kde plasma workspace' stopped working. I.e. lightkdm showed it's login screen but when I hit Enter after few secs the monitor starts flickering (red,blue,green then stripes etc).

After spending couple of hours (playing with edid etc) finally I've easy workaround:

Just when you enter login/pass and hit Enter switch termorary to terminal with Ctrl-Alt-F1, wait few secs till it boots and then switch back with Alt+7.

While this workaround is required for KDE GNOME (as in Ubuntu session) worked fine.

---

### Post by boast on 2013-05-07
Anyone got this running past 60Hz? I can't get it to work with anything but the 60hz modeline from cvt

---

### Post by ShamoIdol on 2013-05-20
> **boast said:**
> Anyone got this running past 60Hz? I can't get it to work with anything but the 60hz modeline from cvt


cvt tool didn't work for me either.

---

### Post by ShamoIdol on 2013-05-20
Here's my config for dual monitors in portrait mode:

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "QNIX"
    ModelName      "QX2710"
    HorizSync      88.8
    VertRefresh    59.5
    Option         "DPMS"
    # 60
    Modeline       "2560x1440" 241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
    
    #DisplaySize    597 336 # one monitor 
    DisplaySize    672 597 # two in portrait mode
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusId          "PCI:5:0:0" # eGPU
    Option          "Coolbits" "1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "UseEDID" "False"
    Option         "UseEDIDDPI" "False"
    Option         "UseEDIDFreqs" "False"
    Option         "ExactModeTimingsDVI" "True"
    Option         "metamodes" "DFP-0: 2560x1440_60 +0 +0 { Rotation=left }, DFP-1: 2560x1440 +1440 +0 { Rotation=right }"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Option         "Xinerama" "0"
EndSection



```

I run this using Thinkpad x220 and PH4E eGPU card with GF 8800 GTS attached. Everything is pretty smooth. No lags or hangouts. Now looking for a way to make it tripple head.
The only noticed problem is lag while scrolling extreamly heavy pages (mostily forums) in Firefox.

---

### Post by ShamoIdol on 2013-05-20
I've finally got it overclocked to 100Hz using modeline I've got from 
[http://www.overclock.net/t/1225919/yamakasi-catleap-monitor-club/2290](http://www.overclock.net/t/1225919/yamakasi-catleap-monitor-club/2290)
(as I said that forums slows down my whole desktop)

Here's my new xorg.conf: 
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "QNIX"
    ModelName      "QX2710"
    Option         "DPMS"

	# 100Hz
	VertRefresh 43 - 120
	HorizSync 28 - 200
	Modeline "2560x1440" 400.00 2560 2592 2612 2692 1440 1443 1448 1480 +Hsync +Vsync
	
    #DisplaySize    597 336 # one monitor 
    DisplaySize    672 597 # two in portrait mode
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
	BoardName	   "GeForce 8800 GTS"
	BusId          "PCI:5:0:0" # eGPU on ThinkPad x220
	Option			"Coolbits" "1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
	
	Option "UseEDID" "FALSE"
	Option "ExactModeTimingsDVI" "True"
	Option "ModeValidation" "NoVertRefreshCheck, NoHorizSyncCheck, NoDFPNativeResolutionCheck, NoMaxSizeCheck, NoMaxPClkCheck, NoEDIDModes"

	# one landscape
    #Option         "metamodes" "DFP-0: 2560x1440 +0 +0"

	# two portrait
    Option         "metamodes" "DFP-0: 2560x1440 +0 +0 { Rotation=left }, DFP-1: 2560x1440 +1440 +0 { Rotation=right }"

    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Option         "Xinerama" "0"
EndSection


```

---

### Post by jonkul2 on 2013-09-26
Running Ubuntu 13.04, with Nvidia's 325 drivers via xorg-edgers. After  finally getting the drivers to work without bricking the whole install,  it turned out I was still limited to 1024x768 because of my Catleap.  Fixing the xorg.conf like you've described in this thread actually  helped, but now I'm limited to 1600x1200 instead. =/ I've tried several  of xorg.conf posted here, but can't make any progress.
Does anyone know how to fix my problem?

---

### Post by xalu on 2014-01-06
Hi All,

I wanted to thank the op for this. I was having a killer time getting my Korean Crossover 27QW to work with ubuntu nvidia 331.20 drivers I installed( for anyone having issues installing the nvidia driver for ubuntu 13.10. Use this repo [http://www.ubuntuupdates.org/ppa/ubuntu-x-swat](http://www.ubuntuupdates.org/ppa/ubuntu-x-swat) with this guide [http://news.softpedia.com/news/How-to-Install-the-Latest-NVIDIA-331-20-Drivers-in-Ubuntu-13-10-399182.shtml](http://news.softpedia.com/news/How-to-Install-the-Latest-NVIDIA-331-20-Drivers-in-Ubuntu-13-10-399182.shtml), I tried a million ways and this was the only one that worked. The edgers ppa doesn't work. 

After I ran sudo nvidia-config. Then sudo nvidia settings. Used the assigned names to make changes in the xorg file. Here is my xorg. My major change  to get me smasung 27" monitor to work was to enable the "UseEDID" If I set it to false, then my samsung monitor wasn't detected. Maybe this will help someone else. So just delete all the EDID false options and your second monitor should be detected.

```

# James Set up based on http://ubuntuforums.org/showthread.php?t=2038997



Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Crossover"
    ModelName      "27QW"
    HorizSync      88.8
    VertRefresh    59.5
    Option         "DPMS"
    Modeline       "2560x1440" 241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
    DisplaySize    597 336  
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "ExactModeTimingsDVI" "True"
    Option         "metamodes" "DFP-0: 2560x1440_60 +0 +0, DFP-1: 1920x1080_60 +2560+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Option         "Xinerama" "0"
EndSection


```

---

### Post by Vr_Rm on 2014-06-29
Holy Crap!  It's things like this that make me wonder if I have any competance to even come near a computer, this after being a computer programer professionally, on Linux, for the last 20+ years.  Though before blaming the sorry state of Linux device configuration, don't forget about the sorrier state of Windows device configuration where I still haven't been able to get this to work.

So, there might be better ways to do this, but if you have an NVIDIA GTX5XX series video card, eg GTX 560M, and are connecting with an HDMI cable to a Samsung UD590, you'll get hit with a double whammy.  

First you'll need to make a change to your xorg.conf file to overcome the 30Ghz limitation of HDMI:  


```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LGD"
    HorizSync       44.4 - 66.6
    VertRefresh     39.9 - 59.9
    ModeLine       "2560x1440@30" 148.78 2560 2696 2968 3376 1440 1441 1444 1469 -hsync +vsync
    # Above params recalibrated for 30Ghz --^    -- ^  --^ ....
    Option         "DPMS"
EndSection



```


  But you'll also need to make the following change to overcome a bug in either the monitor firmware or Nvidia driver for checksums:

```


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ModeValidation" "AllowNon60hzmodesDFPModes, NoEDIDDFPMaxSizeCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoDFPNativeResolutionCheck, NoMaxSizeCheck, NoMaxPClkCheck, AllowNonEdidModes, NoEdidMaxPClkCheck"
    # Switch off a bunch of features, I have no idea what all (any really) of them mean  --^
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "LVDS-0: nvidia-auto-select +0+0, HDMI-0: 2560x1440@30 +1920+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Of course even after this, you'll still limited to 2560x1440 or whatever the capabilities are of your GTX 5xx card (it won't magically upgrade your 5xx series card to be magically 4K).  But you won't be stuck at 1920x1080.

---

### Post by mike204 on 2014-07-01
I created an account on the forums just to thank you for this!  I've been working on this problem for days, trying to get my dual Shimian monitors working with the nvidia driver.  Thank you!

---

### Post by NertSkull on 2014-07-24
I'm glad this thread has helped a few people, I'm loving my hi-res monitor.

---

