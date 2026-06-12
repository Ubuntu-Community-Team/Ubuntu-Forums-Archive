---
title: "Wacom bamboo pen on Lucid lynx works but..."
date: 2010-05-02
forum: General Help
---

### Post by aklo on 2010-05-02
OK i manage to get it working follow this thread:

[http://ubuntuforums.org/showthread.php?t=1458678&highlight=wacom+bamboo](http://ubuntuforums.org/showthread.php?t=1458678&highlight=wacom+bamboo)

So i tested out in gimp, i configured the inputdevice in gimp too.

I can draw but once i press it down on my tablet then pointer will stuck there. So moving around my stylus pen will not move the pointer. I have to lift my pen till the tablet could not detect it and go near to make the pointer move where i want it....so basically it seems to act like a mouse instead of a pen.

[LEFT] Any fix for this or is there any settings i can change to configure it.

Edit: I'm not sure if what i did messed up those settings.

After a reboot it doesn't work again.

Basically the first thing i tried was a method which works on karmic for me. I simply copy and paste the commandline code and download the wacom linux zip file and extract it. Afterwards i pasted yet another bunch of code something like making the install. Anyway i tried what works in kamic on lucid but unfortunately it doesn't work. So i looked around and found some "wacom for lucid lynx" so again i copy and pasted a bunch of commands...i honestly don't know what those commands did but at least in karmic blindly pasting works for me.

So i'm not sure if installing so many different solutions will mess up some config? 

I'm using wacom bamboo pen.
[/LEFT]

---

### Post by Favux on 2010-05-02
Hi aklo,

Let me try to explain what's happened.  In Karmic you were compiling and installing linuxwacom.  In Lucid the X driver part of linuxwacom has been replaced by xf86-input-wacom.  This is because the linuxwacom X driver won't run on the 1.7 Xserver in Lucid.  In other words Xorg is now in charge of the X part.  However linuxwacom still supplies the kernel driver/module wacom.ko.  That's what you should have compiled and installed on the link you gave.

So let's see the output of the following:
```
xinput --list
```
in a terminal.

---

### Post by aklo on 2010-05-02
Hello 

Thank you for replying, i got it to work by copying yet another chunk of code...

> 
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

wget [http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6-1.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6-1.tar.bz2)

tar -xf linuxwacom-0.8.6.tar.bz2
cd linuxwacom-0.8.6
./configure --enable-wacom
cd src/2.6.30/
make
sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/
sudo rmmod wacom
sudo modprobe wacom



---

### Post by Favux on 2010-05-02
Good!  :D

But these two lines need to change to:
```
tar -xf linuxwacom-0.8.6-1.tar.bz2
cd linuxwacom-0.8.6-1
```

---

### Post by dedhandi on 2010-05-03
Got my tablet to work once but had the problem with the pointer sticking in one place, then the whole thing not working after a reboot. The steps worked up to:

sudo rmmod wacom

at which point I got:

ERROR: Module wacom does not exist in /proc/modules

Not really sure what to do about that. I skipped past that step and tried:

sudo modprobe wacom

which worked temporarily, only for the above issue to occur. Here is the ouput from xinput --list:

alex@ubuntu:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Dell Dell USB Optical Mouse             	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen                    	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger                 	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; USB Multimedia Keyboard                 	id=8	[slave  keyboard (3)]
    &#8627; USB Multimedia Keyboard                 	id=9	[slave  keyboard (3)]
alex@ubuntu:~$

---

### Post by Favux on 2010-05-03
Hi dedhandi,

Not sure I understand the error message either.  The xinput list shows there's usb communication to the tablet because of the Bamboo lines.  So a wacom.ko is working, the question is is it the right one.  We can look at the output in a terminal
```
modinfo -n wacom
```

You might also want to try:
```
sudo depmod -a
```
That should rebuild the module dependencies, and then reboot.

If that doesn't work let's see if the wacom.ko is auto-loading:
```
lsmod | grep [Ww]acom
```

---

### Post by mve-lamb on 2010-05-25
Hi there, I had same issue, with compiling and running linuxwacom-0.8.7.tar.bz2 and [xf86-input-wacom-0.10.5.tar.bz2]("http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.10.5.tar.bz2/download")
 Bambo Pen as described above. 
Before I did compile wacom and xorg I removed xserver-xorg-input-wacom ver.1:0.10.5-0ubuntu4 package from Synaptic Package Manager as somewhere was suggested so for Lucid 10.04. 
But after getting in this first tap freezing trouble I installed back that package and that solve my problem.
Everything working now even after reboot :) Hope it will help to someone...

mve

---

