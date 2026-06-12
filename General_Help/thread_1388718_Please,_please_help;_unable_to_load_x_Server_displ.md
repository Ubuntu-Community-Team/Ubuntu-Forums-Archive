---
title: "Please, please help; unable to load x Server display configuration page"
date: 2010-01-23
forum: General Help
---

### Post by homer1234 on 2010-01-23
Hey guys, I really need some help here;
I am using Nvidia Geforce Fx 5200 with Karmic and nvidia driver 173.14.20

Whenever I load it up, and select the option in the side menu labelled "X Server Display Configuration" which allows me to detect displays and configure them, it only shows a message 

"Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0."

This worked yesterday just fine and my setup yesterday was an AOC monitor hooked up as the primary display via VGA and a TV hooked up as the secondary display using S-video.

Today, I decided to get a DVI-d cable for my monitor and was trying to hook it up to the computer. At first, when the AOC was connected via just DVI-D, there was no display at all.
When I attempted to connect via VGA AND DVI, there was display just like before,  only nvidia saw THREE monitors connected to my computer instead of two (the tv, the AOC connected via VGA, and the same AOC monitor connected via DVI) 

I did some searching online and found a page about the "new nvidia settings released" and followed the instructions to attempt to upgrade to 190.42 and did this;

sudo add-apt-repository ppa:nvidia-vdpau/ppa
[INDENT]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767
[/INDENT]Update source list[INDENT]sudo apt-get update
[/INDENT]Install beta drivers[INDENT]sudo apt-get install nvidia-190-modaliases nvidia-glx-190  nvidia-settings-190
[/INDENT](here is the page) [http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html#more-2454](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html#more-2454)

When that did seemingly nothing, I got a little brave and opened the synaptics package manager and went through the packages that pulled up when I did a search for "nv"

Here is the history for what I did there;

Removed the following packages:
nvidia-173-kernel-source
nvidia-glx-173

Installed the following packages:
nvidia-195-kernel-source (195.30-0ubuntu1~karmic~nvidiavdpauppa5)
nvidia-glx-195 (195.30-0ubuntu1~karmic~nvidiavdpauppa5)


Many scary reboots later, I finally managed to get Nvidia 173.14.20 back and my AOC monitor is working (connected via VGA) and I can see my desktop just fine.
The problem is my tv is no longer getting any picture and I can't open up the display configuration panel to change any settings.


Please help me guys, I know I did this to myself, but is it soo bad to want to use my monitor as HD?!?

Thanks,
Homer

EDIT: just noticed this but under X server Information, It says 1 infront of Screens.
under GPU0-(geForce FX 5200) it shows three things connected (powermizer, CRT-0 (my AOC monitor) and TV-0
-the values under TV-0 aren't even there
-the values under CRT-0 are there (eg: to change digital vibrance and image sharpening) but attempting to change them forces the window to crash
-running using sudo in terminal prints the following error when I try 

The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 228 error_code 2 request_code 139 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by homer1234 on 2010-01-23
bump

---

### Post by homer1234 on 2010-01-23
bump

---

