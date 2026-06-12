---
title: "Trouble with monitor"
date: 2010-07-02
forum: General Help
---

### Post by jeidern on 2010-07-02
Good day sirs and ma'ams,

This thread is somewhat a resurrection of my old thread with monitor over frequency because it has been dumped on and not solved. I have a few new observations to add too. I do hope someone helps :frown:

Here's the problem: Using the live CD, running quite fine too, i tried the "press the spacebar" when the screen shows 2 icons in the lower part of the monitor (one is a cut-out of a human being). After picking the "try ubuntu without any changes..." my monitor blacks out then displays an error message saying:
"Over Frequency H:60.1 khz V:75.2Hz"
This also happens with 9.04-9.10 versions of ubuntu, and the 10.04 of xubuntu and zorin also.

I also tried the ubuntu desktop minimal install i found in a guide , here. [http://www.cs.uml.edu/~aveilleu/projects/ubuntu-minimal/]("http://www.cs.uml.edu/%7Eaveilleu/projects/ubuntu-minimal/")
thinking maybe it might help because of it's minimal hardware usage approach. It didn't work either. The said error message still appears.

When I try a different monitor all seems to work fine. But when I tried Ubuntu 8.04 on the monitor that displayed an error with ubuntu 10.04 all seems fine. It works fine, I checked the list of resolutions available and its respective refresh rates, here's what i found:
monitor resolutions:
640x350 85hz
640x400 85hz
720x400 85hz,70hz
640x480 60hz,73hz,75hz,85hz
800x600 56hz,60hz,72hz,75hz,85hz
832x624 75hz
1024x768 60hz,70hz,75hz
1152x768 55hz
1280x768 60hz
1280x800 60hz
1440x900 60hz

Then, I went back again to the Ubuntu 10.04 with the working monitor and checked the resolutions and the only ones I found were 800x600 and 1024x768. 

Does the monitor resolution observation have anything to do with my problem? It seems that the only version of Ubuntu that the over-frequencied-monitor can run is 8.04. Someone help please.

---

### Post by Chame_Wizard on 2010-07-02
```
sudo xrandr -S 1440x900
```

---

### Post by stderr on 2010-07-02
Seen as you don't have the mode listed, to use xrandr you'd most probably have to add it first. You need to use cvt to generate a modeline with your desired resolution (and refresh rate if you desire - just add it after the resolution, e.g. 1440 900 60), add the mode to xrandr, associate it with your monitor, and finally switch to it.

I would emphasise most strongly that the code below is only intended for SINGLE MONITOR setups. For more than one monitor, you'll need to adjust it so that you choose the correct output - not hard, but more fiddly. As it stands, it just grabs the first output (monitor) name that it finds connected and tries to set the mode of that.

```
MODELINE=$(cvt 1440 900 | grep Modeline | cut -d\  -f 2- -)
MODENAME=$(echo $MLINE | awk '{ print $1 }')
OUTPUT=$(xrandr | grep ' connected' | awk '{ print $1 }')
xrandr --newmode $MODELINE
xrandr --addmode $OUTPUT $MODENAME
xrandr --output $OUTPUT --mode $MODENAME
```

FYI, the manpage of xrandr gives a decent enough overview of what's required:

```
       Forces to use a 1024x768 mode on an output called VGA:
              xrandr --newmode "1024x768" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
              xrandr --addmode VGA 1024x768
              xrandr --output VGA --mode 1024x768
```

However, Ubuntu should be detecting the resolution, refresh etc. correctly. Have you installed the proprietary graphics drivers (nvidia/ati)?

---

### Post by jeidern on 2010-07-03
@stderr
It's an onboard graphics card. Im currently re-installing ubuntu 10.04 and going to try out your solutions. Thank you for the help. I also checked this site [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)[FONT=monospace] because of what you mentioned about the randr's main page. I googled it and found the said site. It was similar to your solution ^_^ thanks.

After my re-installation and randr-ing (^_^) I will let you know what happens. Thanks again.
[/FONT]

---

### Post by jeidern on 2010-07-03
Well I've just finished installing and went directly to the terminal and typed "xrandr" to view the available outputs, I am using the monitor that works (I've set the monitor that displays the over frequency error aside for now. I'm going to connect it after I've set up the needed things with xrandr). Here's my result:

```
Screen 0: minimum 320 x 200, current 800 x 600, maximum 4096 x 4096
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 270mm x 200mm
     800x600          85.1*+
     1024x768        60.0
     640x480          85.0       60.0
     720x400          70.1
```

I've tried what you posted replacing the 1024x768 with 1440x900:
 
```
Forces to use a 1024x768 mode on an output called VGA:
              xrandr --newmode "1024x768" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
              xrandr --addmode VGA 1024x768
              xrandr --output VGA --mode 1024x768
```

It worked for one session only, whenever i restart I'd have to re-input the code again, hence I can't use it with the over-frequencied-monitor. Because I'd have to shut down and disconnect/connect the proper cables. So the second solution didn't quite solve my problem. I didn't or haven't tried your first solution for, forgive me for my newbness, I do not know where to start with what you've given me:

```
MODELINE=$(cvt 1440 900 | grep Modeline | cut -d\  -f 2- -)
MODENAME=$(echo $MLINE | awk '{ print $1 }')
OUTPUT=$(xrandr | grep ' connected' | awk '{ print $1 }')
xrandr --newmode $MODELINE
xrandr --addmode $OUTPUT $MODENAME
xrandr --output $OUTPUT --mode $MODENAME
```

How do I start up in the terminal to do the things stated in the code above? Am I supposed to type the following "as-is" in the terminal or what?? I'm sorry again for I am very new to this. Thanks again.

---

### Post by jeidern on 2010-07-04
Bumping thread... Thanks again.

---

### Post by stderr on 2010-07-04
Hi

Right, firstly you're quite correct, the commands I gave you will only work for your current session. On a reboot, you need to execute the commands again. You can automate this however you like. Here's one example from [ubuntugeek]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html") (a big name on this forum!) Just look towards the bottom of the post, the bit about inserting the lines into /etc/gdm/Init/Default (obviously insert the code that works for you, not the exact code he gives).

Now, you could either follow ubuntugeek's example and just insert 3 lines, copying output from cvt etc, or you can use my 6 lines above, which automates the process a little more, but isn't really necessary :) Here's the 6 lines you'd insert in my example:

```
MODELINE=$(cvt 1440 900 | grep Modeline | cut -d\  -f 2- -)
MODENAME=$(echo $MLINE | awk '{ print $1 }')
OUTPUT=$(xrandr | grep ' connected' | awk '{ print $1 }')
xrandr --newmode $MODELINE
xrandr --addmode $OUTPUT $MODENAME
xrandr --output $OUTPUT --mode $MODENAME
```

Or you can follow ubuntugeek's example. Up to you! If you'd like me to explain any of the code I'd be more than happy to do so.

edit: In fact, sod it, might as well.

```
MODELINE=$(cvt 1440 900 | grep Modeline | cut -d\  -f 2- -)
```

This sets a variable called MODELINE to the Modeline generated by cvt. This is the same as in Ubuntugeek's post. E.g. here's the modeline I get from cvt with your resolution settings:

```
ace@ace1:~$ cvt 1440 900
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

```

Since you only want this bit of it (**"1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync**) I pipe the output through grep and cut to extract the necessary bits, and then it's stored in the variable MODELINE.

```
MODENAME=$(echo $MLINE | awk '{ print $1 }')
```

Here I set the variable MODENAME. We need to refer to the Mode with its name (the first bit of the modeline in quotes - in the example above, **"1440x900_60.00"**). This just extracts it from the modeline and stores it in MODENAME

```
OUTPUT=$(xrandr | grep ' connected' | awk '{ print $1 }')
```

This gets the name of the first connected monitor (this is why my code will only work for single monitor setups) from xrandr and stores it in the variable OUTPUT.

The other three lines are as in ubuntugeek's example. I simply plug in the 3 variables created to achieve the end result. I'm essentially replicating one of the examples given at the bottom of xrandr's manpage:

```
man xrandr
```

So, really, the **best advice** for permanently storing the resolution settings is to **follow ubuntugeek's example and just store the 3 lines he does**. My code is really just to make setting a resolution for a single login session easier (since copying bits from cvt output into more commands is a bit of a pain in the backside, if you have to do it regularly).


> How do I start up in the terminal to do the things stated in the code above? Am I supposed to type the following "as-is" in the terminal or what?? I'm sorry again for I am very new to this. Thanks again.
If I haven't completely confused you by trying to explain something quite simple with the same amount of text as you'd find in the encyclopedia Brittanica :), to run the 6 lines I gave you, there are many ways. You can quite literally select them with your mouse, and without selecting anything else, click in a terminal window to give it focus and click the middle mouse button to copy the commands. Alternatively, you can select the 6 lines and copy with Ctrl+C, and then paste into the terminal with Ctrl+Shift+V. You can select the lines individually and copy and paste, you can type each line individually and hit enter after each one, etc, etc etc.

---

### Post by jeidern on 2010-07-05
Thanks a bunch Stderr. I did the method of ubuntugeek. Was successful with it. The 1440x900 resolution became permanent in the resolution options. All worked fine in the monitor I am presently working with. However, the monitor stated in my first post, the one with the monitor over frequency error, the monitor which started all this ^_^ still diplays the error T_T. 

The error appears before the login screen,.I tried to disable the login screen to automatically login my account but still the problem remains. Is there still a solution for this problem other than buying a new monitor? Or do I have to downgrade to ubuntu 8.04, the only version of ubuntu that works on the said monitor.

---

### Post by jeidern on 2010-07-05
Scratch that! I made it work. Thanks to you Stderr and your link to ubuntugeek's xrandr method. The problem was the monitor that displayed the over frequency error was looking for a 1024x768 resolution with a 60 hz refresh rate. Thanks so much ^_^

---

