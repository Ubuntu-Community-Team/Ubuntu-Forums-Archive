---
title: "Still can't get waltop/medion graphics tablet to work, can't build drivers in karmic"
date: 2009-11-14
forum: General Help
---

### Post by user333 on 2009-11-14
[SIZE=1][COLOR=Black]I have a medion (waltop) graphics tablet that worked fine in 9.04 (with no drivers at all), but when I upgraded, I can't use the buttons to click, or use the pressure-sensitive tip. I have tried the wacom and wizzard pen drivers, but I can't seem to compile them. There is always some error when I try to "make". I get a bunch of lines, and then two that say, "ERROR 1" and "ERROR 2" I have tried countless how-tos, but nothing works. :( One problem is that my tablet isn't a really common one. It is small, 12.1" ,  and you can't even buy it on the waltop site. I think only Aldi sells it around Christmas. Will this problem disappear when I upgrade to 10.4? Do I have a problem with the make command? I have done many karmic-designed how-tos on this, but I always get stuck on "make" or "make install" or "./configure". I am running these commands as root, under sudo bash. 

I have tried the waltop linux drivers, but the same problem.[/COLOR][/SIZE]

---

### Post by user333 on 2009-11-14
What can I do????

---

### Post by emaydubya on 2009-11-17
I cant either and I give up on it now. 
[edit] Try again. (Missing data restored)

 Rather than start another thread. This one has Waltop in the title already.
 
 My unit is from Aldi and branded Medion, on the back sticker it says:
 6012
 MD 85637
 I've had it working in the past, in Kubuntu Intrepid it worked out of the box.
 But not the pen buttons correctly or the surrounding 29 buttons (around the pad) ever at all.
 The surrounding buttons are the least of our worries but would be grand to able to ues them so....
 
 We are gonna have to get this sorted. It's such a freakin pain to have hardware that can't be used. Windows users have all the fun... or do they.. anyway...
 
 I'll start.
 
 We got the driver file from:
 [http://www.waltop.com.tw/download.asp?lv=0&id=2](http://www.waltop.com.tw/download.asp?lv=0&id=2)
 near the bottom of that page.
 
 This is the complete README inside the unzipped package. (Below, is a Ubuntu summary.)
 
 > 0 USB HID
 ------------
 
 0.1 Fedora
 
 0.1.1 Copy hid-xxxx.c to kernel source code directory
 For kernel 2.6.21:
 #cp drv/2.6.21/hid-core.c /usr/src/kernels/'uname -r'/drivers/usb/input
 
 For kernel 2.6.23:
 #cp drv/2.6.23/hid-quirks.c /usr/src/kernels/'uname -r'/drivers/hid/usbhid
 
 0.1.2 Rebuild Linux Kernel
 
 0.1.3 Reboot Linux
 
 0.2 Ubuntu
 
 0.2.1 Copy hid-xxx.c to kernel source code directory
 Consult 0.1.1
 
 0.2.2 Rebuild (usb)hid.ko
 #make
 
 0.2.3 Install (usb)hid.ko
 #make install
 #make modules_install
 
 Or Copy (usb)hid.ko to kernel module directory
 
 0.2.4 Reboot Linux
 
 1 Compile
 ------------
 
 #make
 
 2 Install Waltop Linux Driver (waltoptablet.ko)
 ------------
 
 Linux Kernel version 2.6.21:
 #cp .\waltoptablet.ko /lib/modules/$(shell uname -r)/kernel/drivers/input
 
 Linux Kernel version 2.6.23 and above:
 #cp .\waltoptablet.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/tablet
 
 3 Register Linux kernel driver
 ------------
 
 #cd /lib/modules/'uname -r'/drivers/input
 #/sbin/insmod ./waltoptablet.ko
 #/sbin/depmod -e
 
 4 List the registered module
 ------------
 
 #/sbin/lsmod | grep waltop
 
 5 Plug-in the tablet device
 ------------
 
 6 Test tablet controller detection (waltoptablet.ko)
 ------------
 
 #more /proc/bus/usb/devices
 
 ...
 ... Driver=waltoptablet.ko
 ...
 
 6.1 If Driver=usbhid, add the waltop vendor id to the linux kernel
 6.2 If Driver=(none), install the waltop driver
 
 Or
 #more /proc/bus/input/devices
 
 I: Bus=xxxx Vendor=172f Product=0034 Version=1105
 N: Name="Slim Tablet"
 P:
 S: Sysfs=/class/input/input6
 H: Handlers=mouse2 event5
 B:
 B:
 
 /*****************************************************************************
 ** The Tablet of X11 Driver
 ****************************************************************************/
 
 
 1 Compile
 ------------
 
 #./configure
 #make
 
 
 
 2 Install Waltop X11 driver (waltoptablet_drv.so)
 ------------
 
 #cp .libs/waltoptablet_drv.so /usr/lib/xorg/modules/input
 
 
 
 3 Edit the Configuration file (xorg.conf)
 ------------
 
 3.0 Check Tablet device event number
 
 The event number will be used to xorg.conf "Device" option
 
 #more /proc/bus/input/devices
 
 I: Bus=xxxx Vendor=172f Product=0034 Version=1105
 N: Name="Slim Tablet"
 P:
 S: Sysfs=/class/input/input6
 H: Handlers=mouse2 event5
 B:
 B:
 
 
 3.1 Edit the xorg.conf
 
 
 3.1.0 Edit the xorg.conf
 
 #vi /etc/X11/xorg.conf
 
 
 3.1.1 Add InputDevice section
 
 Section "InputDevice"
 Identifier "WaltopStylus"
 Driver "waltoptablet"
 Option "Device" "/dev/input/eventX"
 Option "Type" "stylus"
 Option "Mode" "absolute"
 Option "USB" "on"
 Option "KeepShape" "off"
 Option "Pressure" "Soft"
 Option "debuglevel" "0"
 EndSection
 
 
 /*
 **Attention:
 ** 1 Option "Device" "/dev/input/eventX"
 ** X is the event number, consult 3.0
 **
 ** 2 Option "Pressure" "string"
 ** string value { "Soft" | "Hard" | "Linear" } .
 **
 ** 3 Option "debuglevel" "number"
 ** number "0 -12", 0 is Off.
 **
 */
 
 
 3.1.2 Edit ServerLayout
 
 Add below to ServerLayout:
 
 InputDevice "WaltopStylus" "SendCoreEvents"
 
 
 Example:
 
 Section "ServerLayout"
 Identifier "single head configuration"
 Screen 0 "Screen0" 0 0
 InputDevice "Keyboard0" "CoreKeyboard"
 ...
 InputDevice "WaltopStylus" "SendCoreEvents"
 EndSection
 
 
 
 4 Restart X Window
 ------------
 
 $init 3
 
 $startx
 
 
 
 5 GIMP and Tablet
 ------------
 
 Configure Gimp for the new devices.
 
 Start Gimp.
 Edit -> Preferences
 
 Select "Input Devices"
 Select "Configure Extended Input Devices"
 
 pad -> Mode: Screen
 stylus -> Mode: Screen
 eraser -> Mode: Screen
 cursor -> Mode: Screen
 Linux input: Wacom Graphire3 6x8 -> Mode: Screen
 Wacom Graphire3 6x8 -> Mode: Screen
 
 Make sure to save. Exit and restart Gimp.
 Your Graphire tablet should be working with the Gimp.
 
 
 Config file in the path:
 [http://www.gimp.org/man/gimp.html](http://www.gimp.org/man/gimp.html)So to summarise just for me Ubuntu Karmic Koala, kernel
 ```
uname -r 
```2.6.31-15-generic
 
 
 These are the questions that I/we need answers to please.
 
 0.2 Ubuntu
 Are we supposed to install something?
 Where is this supposed to go?
 0.2.1 Copy hid-xxx.c to kernel source code directory
 
 
 (Consult 0.1.1)
 4 x's here, again, where?
 0.1.1 Copy hid-xxxx.c to kernel source code directory
 
 Obviously change kernel version to suit yours!
 For kernel 2.6.21:
 #cp drv/2.6.21/hid-core.c /usr/src/kernels/'uname -r'/drivers/usb/input
 
 
 Where is this to be run from? And how?
 0.2.2 Rebuild (usb)hid.ko
 #make
 
 Same place as above?
 0.2.3 Install (usb)hid.ko
 #make install
 #make modules_install
 
 Which directory?
 Or Copy (usb)hid.ko to kernel module directory
 
 Ahha! I know this one.
 0.2.4 Reboot Linux[/quote]
 
 If some kind soul could answer the above questions I can at least make a start.
 The Waltop site is completely useless for help. And there is none that I can find searching the tubes.
 Thank you.

---

### Post by Favux on 2009-11-17
Hi emaydubya,

Actually this may not be too bad.  It seems more cryptic than it really is I think.
> Linux Kernel version 2.6.23 and above:
#cp .\waltoptablet.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/tablet
I think they're saying thats where to copy to module waltoptablet.ko once it's compiled for that kernel (and up) including the Karmic one.

**HOW TO Compile the Waltop Linux Driver for Hardy and Intrepid**
Enter (copy and paste) each line in a terminal and hit enter.  First change directory to the Desktop:
```
cd ./Desktop
```
Then download the Waltop Linux Driver onto your Desktop:
```
wget http://www.waltop.com.tw/file/News4/News420090811001_b.zip
```
Then make sure the build dependencies are installed:
```
sudo apt-get update

sudo apt-get install build-essential automake xserver-xorg-dev x11proto-input-dev

sudo apt-get upgrade
```
Now unzip the source code and change directories into it:
```
unzip News420090811001_b.zip

cd WaltopTablet_090325/WaltopTablet/Xdrv
```
The "configure" file turns out not to be executable so make it so:
```
chmod +x configure
```
And then probably:
```
./configure
```
[Aside:  it may want something like:  ./configure --prefix=/usr  just depending.  You can see it's available options by doing:  ./configure --help | less  To be honest I'm not sure how many of those are available.]
Once configure is done the makefile should be ready so:
```
make
```
Then install the make with:
```
sudo make install
```
Now on to compiling the waltoptablet.ko.  Change directory to util:
```
cd ..

cd util
```
Again the configure isn't executable:
```
chmod +x configure
```
Then:
```
./configure --enable-waltoptablet

make
```
[Aside:  We may not need to do:  sudo make install  We may only need the compiled waltoptablet.ko.]
Then copy the waltoptablet.ko (the usb kernel driver/module) into place:
```
sudo cp ./waltoptablet.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/waltoptablet.ko
```
Then rebuild all the module dependencies:
```
sudo depmod -a
```
Reboot.

To check if it's in the correct location:
```
modinfo -n waltoptablet
```
And to see if the kernel driver has loaded:
```
lsmod | grep waltoptablet
```

Notes from README file:
* There's a typo in the readme file, it should be like above not ".\waltoptablet.ko" and I'm pretty sure it needs a sudo in front.
*Then they're telling you how to get the kernel module "active" with:
```
cd /lib/modules/'uname -r'/drivers/input

/sbin/insmod ./waltoptablet.ko

/sbin/depmod -e
```
hard to tell if that works.  Maybe rebooting (up to a few times) may get the module to auto-load too.


**HOW TO Compile the Waltop Linux Driver for Jaunty and Karmic**

cd ./Desktop
```
wget http://www.waltop.com.tw/file/News4/News420090811001_b.zip
```
sudo apt-get update

sudo apt-get install build-essential automake xserver-xorg-dev x11proto-input-dev

sudo apt-get upgrade

unzip News420090811001_b.zip

Apply patches (really edits) in post #11

cd WaltopTablet_090325/WaltopTablet/Xdrv

chmod +x configure

./configure

make

sudo make install

cd ..

cd util

chmod +x configure

./configure --enable-waltoptablet

make

sudo make install(?)

sudo cp ./waltoptablet.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/waltoptablet.ko

sudo depmod -a

reboot

---

### Post by emaydubya on 2009-11-27
Yeah, sorry about that. Truly.  I get real flabbergasterated when I waste so much time working on these issues time and time again.
But I can't really give up. I ALWAYS keep coming back for more, to try again, to see if I just CAN get things to work.

So anyhow.... Lucky I saved a copy of that original post in Knotes. I replace it into Post#3 above to keep the sequence.  And post my unsuccessful result below.
I appreciate all the help I can get.

---

### Post by emaydubya on 2009-11-27
I changed directory to ./WaltopTablet/Xdrv
Ran ./configure and said I had no permission
After making it executable it completed without error.
Then ran make and it did error...

[php]
make  all-am
make[1]: Entering directory `/home/maxie/MyDownloads/WaltopTablet_090325/WaltopTablet/Xdrv'
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.    -DLINUX_INPUT -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1    -I./src -MT xf86Waltop.lo -MD -MP -MF .deps/xf86Waltop.Tpo -c -o xf86Waltop.lo xf86Waltop.c
 gcc -DHAVE_CONFIG_H -I. -DLINUX_INPUT -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1 -I./src -MT xf86Waltop.lo -MD -MP -MF .deps/xf86Waltop.Tpo -c xf86Waltop.c  -fPIC -DPIC -o .libs/xf86Waltop.o
In file included from xf86Waltop.c:16:
xf86Waltop.h:43:25: error: xf86Version.h: No such file or directory
xf86Waltop.c: In function 'WaltopDeviceControl':
xf86Waltop.c:1468: warning: passing argument 3 of 'InitValuatorClassDeviceStruct' makes integer from pointer without a cast
/usr/include/xorg/input.h:281: note: expected 'int' but argument is of type 'int (*)(struct _DeviceIntRec *, struct xTimecoord **, long unsigned int,  long unsigned int,  struct _Screen *, BOOL)'
xf86Waltop.c:1468: error: too many arguments to function 'InitValuatorClassDeviceStruct'
make[1]: *** [xf86Waltop.lo] Error 1
make[1]: Leaving directory `/home/maxie/MyDownloads/WaltopTablet_090325/WaltopTablet/Xdrv'
make: *** [all] Error 2
[/php]So again, I'm stuck.
Just sent an email to Waltop makers with this. Only my garden snail knows if it will help.

---

### Post by emaydubya on 2009-11-27
Oh well. From their "Contact Us" pages' email address. The email bounced. So much for help from there.


All right. I left a message through their contact enquiery form.

---

### Post by emaydubya on 2009-11-30
I got a reply: Said to refer to this: lol
**[SOLVED] Tablet Buttons don't work (Genius GPEN F610)  **
[http://ubuntuforums.org/showthread.php?t=1326789](http://ubuntuforums.org/showthread.php?t=1326789)

---

### Post by Favux on 2009-12-01
Hi emaydubya,

Now that is funny!  Self referential or what?   :p  Sort of a linux catch-22.


Before I took off for the holiday I loaded the Waltop stuff on my Karmic partition in my Desktop.  So I can try to compile it too.  If we get lucky maybe we'll figure something out.

---

### Post by emaydubya on 2009-12-01
Thanks Favux.
When it comes to errors compiling it's a real black zone for me.

---

### Post by Favux on 2009-12-03
Hi emaydubya,

I got the X driver to compile.  But it is such a horrendous kludge that I am ashamed to post it.  Hopefully I haven't broken anything too important.

I think we have all the depenencies, see my "HOW TO Compile the Waltop Driver" scratch sheet at the bottom of post #4.  So that leaves us with the following three errors in the code:

In file included from xf86Waltop.c:16:
1) xf86Waltop.h:43:25: error: xf86Version.h: No such file or directory
2) xf86Waltop.c: In function 'WaltopDeviceControl':
xf86Waltop.c:1468: warning: passing argument 3 of 'InitValuatorClassDeviceStruct' makes integer from pointer without a cast
/usr/include/xorg/input.h:281: note: expected 'int' but argument is of type 'int (*)(struct _DeviceIntRec *, struct xTimecoord **, long unsigned int,  long unsigned int,  struct _Screen *, BOOL)'
3) xf86Waltop.c:1468: error: too many arguments to function 'InitValuatorClassDeviceStruct'

The first one is easy.  Just comment out line 43 in xf86Waltop.h
```
//#include <xf86Version.h>
```
I don't think (hope) it's doing anything anyway.

The next two are much trickier.  I'll start with the third one.  It turns out that the function xf86GetMotionEvents was broken in 5/08 according to Peter Hutterer.  From his perspective nobody noticed so he dropped the function on 8/23/09.  In fact the "nobody noticed" was an illusion I guess due to the lag from upstream to the distributions.  Because starting with Jaunty/Xserver 1.6 people started noticing.  Along with the Waltop driver loss of the function also broke the WizardPen driver, probably along with others.  Unfortunately for us simply commenting it out doesn't work like it did with the WizardPen driver.

Now the second one is some kind of problem with mixing types.  I guess the pointer is pWaltop and the integer is numAxes.  Input.h is expecting an integer and not getting it.  There apparently is a way to do this, something about only for system calls, I haven't a clue.

So I messed around with the function for a while trying this and that.  I could get it to too few arguments and/or syntax errors, but nothing useful.  So I gave up and commented out the whole function.  And lo and behold it compiled.  One way to deal with errors two and three, nicht wahr?  I have no idea how important the function is and if (how badly) this will break things.  At least it moves us forward, I hope.  I'll keep plugging away but we will probably need a C coder to fix the function for us.

So in xf86Waltop.c starting with line 1458 comment out the entire function down to and including line 1480, like so:
```
//            if (InitValuatorClassDeviceStruct(pWaltop,
//                   numAxes,
//#if GET_ABI_MAJOR(ABI_XINPUT_VERSION) == 0                   
//                   xf86GetMotionEvents,
//                   local->history_size,
//#else
//		   GetMotionHistory,
//		   GetMotionHistorySize(),                   
//#endif
//                   ((device->flags & ABSOLUTE_FLAG) 
//                        ? Absolute : Relative) | OutOfProximity ) == FALSE)
//            {
//                ErrorF("Unable to allocate Valuator Class Device\n");
//                return !Success;
//            }
//			
//#if GET_ABI_MAJOR(ABI_XINPUT_VERSION) == 0
//            /* Allocate the motion history buffer if needed */
//            xf86MotionHistoryAllocate(local);
//#endif
//
//            /* Open the device to gather information */
//            WaltopOpenDevice(pWaltop);

```
Naturally it turns out there's more.  The waltoptablet.ko apparently has to be compiled separately in the util directory???  That doesn't make sense, but OK.  So I go there and with make get a bunch of new errors, of course:
```
waltop-calib.c: In function &#8216;cross&#8217;:
waltop-calib.c:208: error: &#8216;stdscr&#8217; undeclared (first use in this function)
waltop-calib.c:208: error: (Each undeclared identifier is reported only once
waltop-calib.c:208: error: for each function it appears in.)
waltop-calib.c: In function &#8216;Tablet&#8217;:
waltop-calib.c:347: error: &#8216;stdscr&#8217; undeclared (first use in this function)
```
Ouch.  I'm gathering that the newer(?) gcc compiler in Karmic is objecting to syntax errors the older compilers let slide.  I guess I can have a go at these errors too.  Appreciate any help needless to say.

Stepping back a moment, am I doing something really dumb?  Shouldn't there only need to be one compile?  From in the WaltopTablet folder say.  Maybe I'm mis-reading the README's?  It looked like part of what they were asking for was already done.  Part of the problem is the directory structure they talk about doesn't exist.  There's no /src.

---

### Post by Favux on 2009-12-04
Hi Hi emaydubya,

An update.  
```
error: &#8216;stdscr&#8217; undeclared (first use in this function)

```
Turned out to be easy.  It just needed to be defined as an integer.
```
	int stdscr;
```
So I added it near the top of each function just below:
```
	int cx, cy, tx, ty;
```
at line #197 in waltop-calib.c and below:
```
	int screenx,screeny;
```
at about line #299.

Unfortunately although those errors are fixed running make then resulted in a gazillion new errors:
```
make  all-am
make[1]: Entering directory `/home/user/Desktop/WaltopTablet_090325/WaltopTablet/util'
gcc  -g -O2   -o calib waltop-calib.o waltop-tablet.o waltop-usb.o  
waltop-calib.o: In function `Tablet':
/home/user/Desktop/WaltopTablet_090325/WaltopTablet/util/waltop-calib.c:323: undefined reference to `initscr'
waltop-calib.o: In function `cross':
/home/user/Desktop/WaltopTablet_090325/WaltopTablet/util/waltop-calib.c:202: undefined reference to `clear'
/home/user/Desktop/WaltopTablet_090325/WaltopTablet/util/waltop-calib.c:230: undefined reference to `move'
/home/user/Desktop/WaltopTablet_090325/WaltopTablet/util/waltop-calib.c:231: undefined reference to `printw'

etc.

/home/user/Desktop/WaltopTablet_090325/WaltopTablet/util/waltop-calib.c:210: undefined reference to `getmaxy'
collect2: ld returned 1 exit status
make[1]: *** [calib] Error 1
make[1]: Leaving directory `/home/user/Desktop/WaltopTablet_090325/WaltopTablet/util'
make: *** [all] Error 2
```
These turn out to be linker errors, not compile errors, and I don't think they are related to the above fix.

Apparently there can be three causes.  Since it's case specific something in the term may need to be capitalized.  But I doubt that there could be so many typos.

So that leaves a problem with the headers (.h) or with the libraries.  If it's a header(s) that could be a problem.  But most likely we're missing a library or libraries or we're pointing to the wrong place and not to the library.

Despite this mess I think we almost have it, if we can get over this last hump.

---

### Post by emaydubya on 2009-12-09
Thanks Favux.Your efforts are appreciated!
I had a run with some of that above but didn't get anywhere.

---

### Post by Favux on 2009-12-09
Hi emaydubya,

Good.  I haven't given up either.  I hope to get back to banging away at it in a few days.  Between us and anyone who cares to join us we'll get this thing.

---

### Post by pwojnowski on 2009-12-11
Hi!
I also have the same problem, but it looks like we have different drivers.
I downloaded drivers from this site: [http://www.waltop.com.tw/download.asp?lv=0&id=2](http://www.waltop.com.tw/download.asp?lv=0&id=2)
but content is different and i had no problems compiling drivers from "drv/2.30.1"  and "util" directories.

Kernel driver is compiled and loaded into the kernel, but there is some problem with xorg-input-wacom driver. I haven't had time to look at it.
IMHO you should download this driver again and try to compile it.

---

### Post by emaydubya on 2009-12-11
Indeed! Thanks pwojnowski.
There's even some screen shots.

Copied from the readme.doc file.
```
   	 	 	 	 	 	  [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]How to Load Linux driver [/FONT] 
 
[LIST]
[*][COLOR=#ff0000][FONT=&#32048;&#26126;&#39636;, MingLiU, monospace][SIZE=4]Kernel 	Mode Driver [/SIZE][/FONT][/COLOR] 	
[*][COLOR=#ff0000][SIZE=4]Please 	Download Linux Kernel from 	[/SIZE][/COLOR][COLOR=#0000ff]_[[SIZE=4]**http://www.kernel.org/pub/linux/kernel/v2.6/**[/SIZE]]("http://www.kernel.org/pub/linux/kernel/v2.6/")_[/COLOR]
[/LIST]
 [COLOR=#ff0000][FONT=&#32048;&#26126;&#39636;, MingLiU, monospace][SIZE=4]Get 2.6.30.X[/SIZE][/FONT][/COLOR]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]Modified file in attached file folder : [/FONT] 
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]**[COLOR=#0000ff]1. 2.6.30.1/Linux-kernel/ Hid-ids.h hid-core.c [/COLOR]**[/FONT] 
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	Copy the two files to  /usr/src/linux-2.6.30.X/drivers/hid [/FONT] 
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	And [COLOR=#0000ff]re-Build Linux OS Kernel[/COLOR] ( Please remove original kernel in /lib/modules )[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]&#12288;&#12288;[/FONT][FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]# make mrproper[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	#make menuconfig  --> save .config[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	#make clean[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	#make bzImage[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	#make modules[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	#make modules_install[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	#make install[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	#make mkinitramfs -o /boot/initrd.img-2.6.30.x /lib/modules/2.6.30.30.x[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	#cd /boot/grub[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	#update-grub [/FONT] 
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	#reboot[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]2. 2.6.30.1/waltop-kernel/[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	# make [/FONT] 
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	#cp waltoptablet.ko /lib/module/'uname -r'/kernel/drivers/input/tablet[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	( Please be sure to copy the Module to the Folder)[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	#/sbin/insmod waltoptablet.ko[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	#/sbin/depmod –e[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]	#/sbin/lsmod  | grep waltop[/FONT]
 

 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]#more /proc/bus/usb/input [/FONT] 
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]P:  Vendor=172f ProdID=0052 Rev= 0.04[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]S:  Manufacturer=         WALTOP   [/FONT] 
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]S:  Product=         Tablet    [/FONT] 
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=waltoptablet -->[COLOR=#ff0000] Please be sure the waltop device is used the  “waltoptablet.ko”[/COLOR][/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=4ms[/FONT]
 

 

 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]3. Support HAL[/FONT]
 [FONT=&#32048;&#26126;&#39636;, MingLiU, monospace]Put the 10-Waltop.fdi into /etc/hal/fdi/policy[/FONT]
 
```
make failed for me in /linuxwaltop-0.8.4 also in /waltop-kernel

Maaannn... I need sign-posted directions. I'm sure I got all the build tools. I've built a lot of stuff, but only if it's easy and don't error.

---

### Post by pwojnowski on 2009-12-11
Here's what i did:
1. Compile and install kernel module from waltop/drv/2.6.30.1/waltop_kernel:
$> make clean
$> make all
root$> cp waltoptablet.ko /lib/modules/2.6.31-generic/kernel/drivers/input/tablet

2. root$> cp waltop/drv/2.6.30.1/10-waltop.fdi /etc/hal/fdi/policy

3. Install kernel module
root$> insmod waltoptablet
root$> depmod -e

I also compiled calibration util from waltop/util, but i guess it's not necessery yet.

$> lsmod | grep waltop

I'm not sure whether there's need to compile wacom driver from waltop/linuxwaltop-0.8.4/ directory, because by default there's wacom driver already in linux kernel and in xserver-xorg-input-wacom.

Anyway, after installing waltoptablet kernel module and connecting my tablet X Server crashes. I don't know why, but in logs i've seen some stack trace, so i'll try to investigate this and fix - but don't have much time at this moment.

---

### Post by emaydubya on 2009-12-11
Thanks for that rundown pwojnowski

After several attempts I got the waltoptablet.ko made and copied to:
/lib/modules/2.6.31-16-generic/kernel/drivers/input/tablet
The 10-waltop.fdi to:
/etc/hal/fdi/policy

I have the modified /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
I guess I should revert that?
Maybe putting the waltop.fdi there?

But  ```
sudo insmod waltoptablet
insmod: can't read 'waltoptablet': No such file or directory
```

```
sudo modprobe waltoptablet
FATAL: Module waltoptablet not found.
```

After reboot, the tablet crashes the desktop with USB errors from the tablet (I guess) but desktop returns and tablet light dies.

Should I be removing any wacom references or drivers? Like the wacom module or config?
What about a udev Rules file?

---

### Post by emaydubya on 2009-12-11
There's a whole bunch of these, one input4 and from input9 to input38 from #dmesg | grep Tablet

```
[ 1492.904310] input: WALTOP International Corp. Slim Tablet as /devices/pci0000:00/0000:00:03.1/usb3/3-1/3-1:1.0/input/input38
[ 1492.904503] generic-usb 0003:172F:0031.0022: input,hidraw0: USB HID v1.10 Mouse [WALTOP International Corp. Slim Tablet] on usb-0000:00:03.1-1/input0
```

There's 29 buttons around the pad. could these relate to those buttons?
Maybe lineakd could map them.. Ok.. just dreaming.


And yeah.. If I plug the pad in now the desktop will crash.

---

### Post by RowanC on 2010-01-08
Is anyone still looking at this, I quite liked it when my tablet worked previously!

Happy to try things / test, but I'm a complete noob when it comes to compiling, problem solving etc in ubuntu/linux.

---

### Post by RowanC on 2010-01-08
oh no!
I followed the information on a linked thread to update my fdi file, now X crashes whenever I plug in the tablet. Looks like it's been identified as a bug? [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/392825]("https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/392825")

---

### Post by user333 on 2010-01-30
I guess I heard about that problem, but I never got that far. I am stuck with a bunch of errors when I compile the Xdrv... oh well
I'm just hoping that ubuntu 10.04 will fix things up the way they used to work in 9.04

---

### Post by jianboli on 2010-02-09
With the new version of driver posted on waltop:
[http://www.waltop.com.tw/download.asp?lv=0&id=2](http://www.waltop.com.tw/download.asp?lv=0&id=2)
I successfully install the driver on Karmic:
Basic followed Favux's flow. I have learned a lot from Favux. thanks, man.

The problem I met during the complying:
"X11/Xlib.h: No such file or directory", solved after installing libx11-dev
"X11/extensions/XInput.h: No such file or directory ubuntu", solved after installing libxi-dev
"&#8216;O_RDONLY&#8217; undeclared (first use in this function)", solved after adding header file "fcntl.h" on the top of xf86Wacom.c
Here are the detailed steps:

```

sudo apt-get update

sudo apt-get install build-essential automake xserver-xorg-dev x11proto-input-dev libx11-dev libxi-dev

sudo apt-get upgrade

unzip News420090811001_b.zip

cd WaltopTablet_091202/WaltopTablet/linuxwaltop-0.8.4/src/xdrv

gedit xf86Wacom.c (add one line at line 92 after all the including: #include "fcntl.h")

cd ../../

chmod +x configure

./configure

make

sudo make install

sudo cp ../drv/2.6.30.1/10-waltop.fdi /usr/share/hal/fdi/policy/20thirdparty/

sudo reboot

```And it worked smoothly after the reboot, even better than on 9.04.
I am not sure if every step is necessary and I may missed some steps that I think totally useless. 
I hope it work for you. Cheers.

---

### Post by Favux on 2010-02-10
Hi jianboli,

Outstanding!!!

Thank you.

---

### Post by emaydubya on 2010-02-13
SUCCESS!!!!!
Thanks ***ENORMOUSLY*** jianboli for your efforts into getting this beast working.

Previously I had built and installed the wacom 8.5 driver and could not bring up a screen unless I uninstalled xorg-xserver-input-wacom. Again I was left with no pad.

So I followed your post but came up with errors.
I also had to install tcl dev 8.4 and tk dev 8.4
That was after I installed xorg dev, kernel sources and some other stuff.

After reboot, no worky so...
I had a udev rule in /etc/udev/rules.d I removed that and rebooted again

BAM! Moving
Next I installed the tablet tools ( a gnome app) to test and it worked with pressure. 
Here:  [http://www.alexmac.cc/tablet-apps/](http://www.alexmac.cc/tablet-apps/)
In a terminal:  >tablet-capplet.py
Excellent!

Gimp also works with pressure and I'm once again a happy camper.

So thanks to everyone and especially jianboli. Oh, and Favux for all the work you do.

I, myself can call this one solved. :) Till next time anyway.
Well, the buttons don't really work but at least the pen does.

---

### Post by jianboli on 2010-02-14
While, in my case, my two buttons on the pen worked but they are indistinguishable with this driver. what is more, they all worked as button 2, which is kind of useless. So I changed them to button3(the right click) by editing the fdi file. Are you sure you are not the same case? You can try to test it by 
```
xinput set-button-map <device name> 1 3 2 4 5 6 7
```
and you can get the <device name> through 
```
xinput list
```
After setting it, click the buttons to see if they work as the right click.

If they work, you can edit your fdi file so that the buttons are set to button 3 by default.
Simply add the following line 
```
<append key="input.x11_options.Button2" type="string">3</append>
```
after
```
<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
```
in your 10-waltop.fid file and then restart your hal serverice by
```
sudo restart hal
```

While if they don't, I don't know what to do then. My tablet buttons never worked in 9.04. 

Hope this can help and good luck.

---

### Post by JaoJKJX on 2010-03-06
Can someone help me please? I am on 64bit system and I'm getting stuck at sudo make install:

[http://pastebin.ca/1825620](http://pastebin.ca/1825620)

after that
```
/sbin/lsmod | grep waltop
```
returns nothing

Does this driver support 64bit? Is it open source and if yes, then why is it not included in xorg? Aren't developers aware of it?

*edit*
I forgot to say that I am running Kubuntu 10.04 64bit from memory stick right now

---

### Post by Zayfox on 2010-03-14
> **JaoJKJX said:**
> Can someone help me please? I am on 64bit system and I'm getting stuck at sudo make install:

[http://pastebin.ca/1825620](http://pastebin.ca/1825620)

after that
```
/sbin/lsmod | grep waltop
```returns nothing

Does this driver support 64bit? Is it open source and if yes, then why is it not included in xorg? Aren't developers aware of it?

*edit*
I forgot to say that I am running Kubuntu 10.04 64bit from memory stick right now
This too, except I'm on Ubuntu Lucid 32bit

---

### Post by user333 on 2010-03-20
> **jianboli said:**
> with the new version of driver posted on waltop:
[http://www.waltop.com.tw/download.asp?lv=0&id=2](http://www.waltop.com.tw/download.asp?lv=0&id=2)
i successfully install the driver on karmic:
Basic followed favux's flow. I have learned a lot from favux. Thanks, man.

The problem i met during the complying:
"x11/xlib.h: No such file or directory", solved after installing libx11-dev
"x11/extensions/xinput.h: No such file or directory ubuntu", solved after installing libxi-dev
"&#8216;o_rdonly&#8217; undeclared (first use in this function)", solved after adding header file "fcntl.h" on the top of xf86wacom.c
here are the detailed steps:

```

sudo apt-get update

sudo apt-get install build-essential automake xserver-xorg-dev x11proto-input-dev libx11-dev libxi-dev

sudo apt-get upgrade

unzip news420090811001_b.zip

cd waltoptablet_091202/waltoptablet/linuxwaltop-0.8.4/src/xdrv

gedit xf86wacom.c (add one line at line 92 after all the including: #include "fcntl.h")

cd ../../

chmod +x configure

./configure

make

sudo make install

sudo cp ../drv/2.6.30.1/10-waltop.fdi /usr/share/hal/fdi/policy/20thirdparty/

sudo reboot

```and it worked smoothly after the reboot, even better than on 9.04.
I am not sure if every step is necessary and i may missed some steps that i think totally useless. 
I hope it work for you. Cheers.
**thank you so much jianboli!!! I thought i would *never* see this thing working again!!!**

---

### Post by RowanC on 2010-03-30
It Works! Thanks to everyone for getting this working. Favux & jianboli both deserve big high fives \\:D/

---

### Post by notsamoth on 2010-04-05
Hi, I had followed your steps and compiling went well. But if I plug in my tablet kde (or x-server) crashes to texdtmode with irregular switching to a black display. I own an ASUS-Notebook and uses Kubuntu 9.10 (x64) with kde 4.4.2

Any idea what's going wrong here ?


> **jianboli said:**
> With the new version of driver posted on waltop:
[http://www.waltop.com.tw/download.asp?lv=0&id=2](http://www.waltop.com.tw/download.asp?lv=0&id=2)
I successfully install the driver on Karmic:
Basic followed Favux's flow. I have learned a lot from Favux. thanks, man.

The problem I met during the complying:
"X11/Xlib.h: No such file or directory", solved after installing libx11-dev
"X11/extensions/XInput.h: No such file or directory ubuntu", solved after installing libxi-dev
"&#8216;O_RDONLY&#8217; undeclared (first use in this function)", solved after adding header file "fcntl.h" on the top of xf86Wacom.c
Here are the detailed steps:

```

sudo apt-get update

sudo apt-get install build-essential automake xserver-xorg-dev x11proto-input-dev libx11-dev libxi-dev

sudo apt-get upgrade

unzip News420090811001_b.zip

cd WaltopTablet_091202/WaltopTablet/linuxwaltop-0.8.4/src/xdrv

gedit xf86Wacom.c (add one line at line 92 after all the including: #include "fcntl.h")

cd ../../

chmod +x configure

./configure

make

sudo make install

sudo cp ../drv/2.6.30.1/10-waltop.fdi /usr/share/hal/fdi/policy/20thirdparty/

sudo reboot

```And it worked smoothly after the reboot, even better than on 9.04.
I am not sure if every step is necessary and I may missed some steps that I think totally useless. 
I hope it work for you. Cheers.

---

### Post by jianboli on 2010-04-17
I am not sure, it is exactly what happened when I used the wrong driver. Have you removed the default wacom driver?

---

### Post by notsamoth on 2010-04-30
At last this works for me on 9.10:

- uninstalling all driver
- install the waltop-driver
- delete all fdi files concerning the tablet

And all is fine - until I've updated to 10.04 and I've got this freezed mousepointer when pushing the pen onto the tablet. The cursor moves only if first I move the pen 3 cm up in the air and down again.

---

### Post by zdubun on 2010-05-07
Dear All Above,

I have been trying to get my Adesso Cyberpad to work on Ubuntu. This looks exactly like Waltop Digital Note T01S pad. Ubuntu 10.04 seems to recognise the tablet however somethings need addressing:-
1. Every time the pen is used to click with pressure there is a delay of 5 secs before the pointer moves again.
2. I used Wine to use My Ink before. However Free Notes cannot be used. These are he bundled software that come with the cyberpad. Free note allows the user to directly write and store these notes.

Any solutions please.

And dear high ups  of the Forums, I appreciate that these problems faced by us Ubuntu newbies seem trivial to you, but these are the things that make us go back to Windows, So please Solutions required. :-)

---

### Post by Zayfox on 2010-05-22
> **notsamoth said:**
> At last this works for me on 9.10:

- uninstalling all driver
- install the waltop-driver
- delete all fdi files concerning the tablet

And all is fine - until I've updated to 10.04 and I've got this freezed mousepointer when pushing the pen onto the tablet. The cursor moves only if first I move the pen 3 cm up in the air and down again.
Bumping this topic because I have the same problem with 10.04, it's hindering work and school now.

---

### Post by Zayfox on 2010-05-23
Rebumping, I seriously need this fixed. If **anyone** has this working in 10.04, please give me the steps you took. This is seriously messing with my capabilities for work and school. :(

---

### Post by sweena on 2010-06-10
hi, 
i've same problem. It seems like is a general trouble with tablets in last ubuntu, this issue happens also with wacom. But there is another problem with gimp: when i set the tablet device in preferences, gimp crashes with this message: 

(gimp:6893): Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_TOOLBAR (container) || widget->parent == GTK_WIDGET (container)' failed

(gimp:6893): Gtk-WARNING **: Attempting to add a widget with type GtkHBox to a GtkFrame, but as a GtkBin subclass a GtkFrame can only contain one widget at a time; it already contains a widget of type GtkHBox

(gimp:6893): Gtk-CRITICAL **: gtk_box_pack: assertion `child->parent == NULL' failed

(script-fu:6896): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault (`core' generate)

so, it looks like a bug, doesn't it?

---

### Post by Favux on 2010-06-10
Hi sweena,

[QUOTE=notsamoth]I've got this freezed mousepointer when pushing the pen onto the tablet. The cursor moves only if first I move the pen 3 cm up in the air and down again. [/QUOTE]
[QUOTE=Zayfox]Bumping this topic because I have the same problem with 10.04, it's hindering work and school now.[/QUOTE]
[QUOTE=sweena]i've same problem. It seems like is a general trouble with tablets in last ubuntu, this issue happens also with wacom. But there is another problem with gimp: when i set the tablet device in preferences, gimp crashes with this message:[/QUOTE]
Actually I'm kind of amazed that the Waltop driver is compiling in Lucid (10.4)/Xserver 1.7 because I don't believe it was updated for that.  I wish you folks would describe what you are doing to get it to compile.

Anyway that is likely the source of your problems/errors.  The LWP (Linux Wacom Project) developers have actually added support for the Waltop tablets back in to the Wacom X driver about 10 days ago with the merging of the Waltop branch with the xf86-input-wacom (the X driver) git master.  Since it turns out the "Waltop" drivers are basically the linuxwacom drivers this is good.  However the usb hid kernel part for Waltop tablets doesn't quite work yet, so the xf86-input-wacom doesn't quite get enough raw usb data to work.  Apparently support patches fixing this have been submitted to the kernel.

In the meantime you can set up with the WizardPen drivers.  See "Attention Waltop tablet in Lucid users" near the top in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") for links.

---

### Post by sweena on 2010-06-10
> **Favux said:**
> Hi sweena,

In the meantime you can set up with the WizardPen drivers.  See "Attention Waltop tablet in Lucid users" near the top in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") for links.

It works perfectly!
thanks

---

### Post by zax1 on 2012-07-13
worked perfectly for me - first time

---

### Post by nothingspecial on 2012-07-13
[IMG]http://img696.imageshack.us/img696/7058/necrov.png[/IMG]

---

