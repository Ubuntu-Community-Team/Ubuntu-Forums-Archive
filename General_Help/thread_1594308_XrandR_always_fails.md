---
title: "XrandR always fails"
date: 2010-10-12
forum: General Help
---

### Post by mabarian on 2010-10-12
Hi people,

I was trying to add a new resolution mode to my monitor, but XrandR always fails. These are the steps I follow:

> $ gtf 1280 768 60

then I copy the result and type

> xrandr --newmode "1280x768_60.00"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync


but always says:

> [COLOR="Red"]xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19[/COLOR]

Finally I just can't create another resolution. And yes, my monitor should run in 1280x768.

Anyone cuold help me please? Thank you very much!

---

### Post by Riccardix on 2010-10-15
I've the same problem here...
someone can help us solve ?

this is my hdw:

**lspci -nn | grep **
VGA01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)

**xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync**
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19

**xrandr --addmode default 1280x1024_60.00**
xrandr: Failed to get size of gamma for output default

I get blank screens if:
[I]1) erasing the xorg.conf
2) putting in the device section of the xorg anything other than "vesa"[/I]

putting "vesa" I get  a slow, not hdw accelerated screen, not good for nothing else than putting this text here ... ;(

In windows (other partition) everything is running well.

I remain at your disposal for any test.

Thanks
RiccardiX

---

### Post by Riccardix on 2010-10-16
Something that (i hope) can help solving this problem:

This error has begun when I decided to install the ATI fglrx drivers.

Now, if I want to uninstall them, I get an error message that broke the uninstall process leaving the fglrx driver on my computer.

Thanks again for help.

---

### Post by vs8 on 2010-11-14
I have the same problem. I followed the Wiki's instructions but they seem to fail every time.

---

### Post by Riccardix on 2010-11-14
Reinstalled ubuntu 10.04, upgraded to 10.10 without install anything else for managing the 3d, now everything work fine ;)

---

### Post by jameslyons on 2010-11-14
> **Riccardix said:**
> Reinstalled ubuntu 10.04, upgraded to 10.10 without install anything else for managing the 3d, now everything work fine ;)

I installed a fresh 10.10 and I have spent all day trying to resolve the resolution issue but get the following still:

root@jim-T8200:/home/jim# xrandr --output VGA1 --mode 1024×768_60.00
xrandr: Failed to get size of gamma for output default
warning: output VGA1 not found; ignoring

Please can anybody tell me what to do?
Thanks in advance, James.

---

### Post by realzippy on 2010-11-14
> **jameslyons said:**
> I installed a fresh 10.10 and I have spent all day trying to resolve the resolution issue but get the following still:

root@jim-T8200:/home/jim# xrandr --output VGA1 --mode 1024×768_60.00
xrandr: Failed to get size of gamma for output default
warning: output VGA1 not found; ignoring

Please can anybody tell me what to do?
Thanks in advance, James.

Welcome to UF!

Please post the output of

```
xrandr
```

please run it as normal user,not as "root";no need for root.

---

### Post by jameslyons on 2010-11-14
> **realzippy said:**
> Welcome to UF!

Please post the output of

```
xrandr
```please run it as normal user,not as "root";no need for root.

Here it is..... James.

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
  “1024×768&#8243; (0x10f)   70.0MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   52.7KHz
        v: height  768 start  771 end  775 total  798           clock   66.1Hz

---

### Post by realzippy on 2010-11-14
As you can see from the output,
there is whether a VGA1 display nor a 1024x768 resolution,so your command cannot work.
Is it an old trident cyberblade graphics device?
To see this paste into terminal:

```
lspci |grep VGA
```

---

### Post by realzippy on 2010-11-14
Sorry,just see this:
**“1024×768&#8243; (0x10f) 70.0MHz**

Have you run a *xrandr --addmode "1024x768 bla...* command formerly?


**EDIT**:
*If* so,try:

```
xrandr --output default --mode 1024×768
```

---

### Post by jameslyons on 2010-11-14
> **realzippy said:**
> As you can see from the output,
there is whether a VGA1 display nor a 1024x768 resolution,so your command cannot work.
Is it an old trident cyberblade graphics device?
To see this paste into terminal:

```
lspci |grep VGA
```

This is it ...... James.
jim@jim-T8200:~$ lspci |grep VGA
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)

---

### Post by realzippy on 2010-11-14
..sorry,crossposting.I edited post #10.Resume:

Have you run sort of xrandr command formerly like:

xrandr  --addmode "1024x768 modelinebla...

??
(just saw the "1024x768" output from your xrandrcommand)

If so,you can try:

```
xrandr --output default --mode 1024x768
```

---

### Post by jameslyons on 2010-11-14
> **realzippy said:**
> ..sorry,crossposting.I edited post #10.Resume:

Have you run sort of xrandr command formerly like:

xrandr  --addmode "1024x768 modelinebla...

??
(just saw the "1024x768" output from your xrandrcommand)

If so,you can try:

```
xrandr --output default --mode 1024x768
```


I didn't try addmode properly. If I try the command you suggest I get:

jim@jim-T8200:~$ xrandr --output default --mode 1024x768
xrandr: cannot find mode 1024x768

I guess I have to try addmode then... What's the format please? (meantime I'll try).
James.

---

### Post by realzippy on 2010-11-14
commands would be:

```
xrandr --newmode &#8220;1024x768_60.00&#8243;   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode default 1024x768_60.00
xrandr --output default --mode 1024x768_60.00
```

---

### Post by jameslyons on 2010-11-14
> **realzippy said:**
> commands would be:

```
xrandr --newmode “1024x768_60.00&#8243;   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode default 1024x768_60.00
xrandr --output default --mode 1024x768_60.00
```

I tried--newmode but we're back to the beginning again because xrandr gives an error:

jim@jim-T8200:~$ xrandr --newmode “1024x768_60.00&#8243;   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr: Failed to get size of gamma for output default

Any ideas? Thanks, James.

---

### Post by realzippy on 2010-11-14
Forget it for the moment...anyway,if xrandr had work,you had to make it permanent,means,put the xrandr command in autostart or create a script that runs it.
The correct solution would be to set up an xorg.conf file with your resolution;could be done by Xorg -configure (little pain,because it includes the whole bunch of possible configuration options);so it might be worth to try an existing xorg.conf file from the web.
Found this xorg.conf e.g. :

```
Section "Monitor"
    Identifier    "Configured Monitor"
      Option      "DPMS"  "true"
      HorizSync    30.0-60.0
      VertRefresh  50.0-70.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
      DefaultDepth      24
      SubSection "Display"
                  Depth         24
                  Modes         "1024x768" "800x600"
      EndSubSection
      
EndSection
```


First,check out if there is a existing xorg.conf,guess not.Type
```
gksudo gedit /etc/X11/xorg.conf
```

If an existing file opens,post it's content.If an empty file opens,paste the content from the example given into it and save the file closing.
Restart X or reboot.If you get a black screen,unable to start X,you had to boot in recovery mode,drop to root shell, (make sure you know how to do) and delete the created file with (write this down):

```
rm /etc/X11/xorg.conf
reboot
```

---

### Post by jameslyons on 2010-11-14
> **realzippy said:**
> Forget it for the moment...anyway,if xrandr had work,you had to make it permanent,means,put the xrandr command in autostart or create a script that runs it.
The correct solution would be to set up an xorg.conf file with your resolution;could be done by Xorg -configure (little pain,because it includes the whole bunch of possible configuration options);so it might be worth to try an existing xorg.conf file from the web.
Found this xorg.conf e.g. :

```
Section "Monitor"
    Identifier    "Configured Monitor"
      Option      "DPMS"  "true"
      HorizSync    30.0-60.0
      VertRefresh  50.0-70.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
      DefaultDepth      24
      SubSection "Display"
                  Depth         24
                  Modes         "1024x768" "800x600"
      EndSubSection
      
EndSection
```
First,check out if there is a existing xorg.conf,guess not.Type
```
gksudo gedit /etc/X11/xorg.conf
```If an existing file opens,post it's content.If an empty file opens,paste the content from the example given into it and save the file closing.
Restart X or reboot.If you get a black screen,unable to start X,you had to boot in recovery mode,drop to root shell, (make sure you know how to do) and delete the created file with (write this down):

```
rm /etc/X11/xorg.conf
reboot
```

Yes, I found that xorg.conf and tried it and also tried 4 others but they are either ignored or cause errors and I had to edit or rename the xorg.conf file from the b-shell. I even found a xorg.conf for my controller "Trident Microsystems CyberBlade/XP (rev 63)" but it didn't make any difference either. 
That's why I need help :( James.

---

### Post by realzippy on 2010-11-14
...if xorg.conf really is ignored (No typos?Capital X? aso ?),
google for KMS (kernelmodesetting) stuff concerning your trident graphics device;maybe that is similar to ATI where you have to disable KMS for using xorg.confs (afaik).
Sorry...I am out.(for the moment)



Edit:
**xserver-xorg-video-trident** 
is installed ?

---

### Post by jameslyons on 2010-11-14
> **realzippy said:**
> ...if xorg.conf really is ignored (No typos?Capital X? aso ?),
google for KMS (kernelmodesetting) stuff concerning your trident graphics device;maybe that is similar to ATI where you have to disable KMS for using xorg.confs (afaik).
Sorry...I am out.(for the moment)



Edit:
**xserver-xorg-video-trident** 
is installed ?

Hi, yes it is - version 1:1.3.4-0Ububtu1
I just found this thread which expanded the image of the screen so I don't have a black inch around it any more. however the resolution is 800x600 which is almost unreadable.
See ([http://ubuntuforums.org/showthread.php?t=1308193](http://ubuntuforums.org/showthread.php?t=1308193)) and you can also see the xorg.conf file here.

xrandr gives:

root@jim-T8200:/etc/X11# xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 800 x 600, maximum 1024 x 768
default connected 800x600+0+0 0mm x 0mm
   1024x768       60.0  
   800x600        60.0*    56.0  
   640x480        60.0  
   680x384        60.0  
   512x384        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
  &#8220;1024×768&#8243; (0xf3)   70.0MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   52.7KHz
        v: height  768 start  771 end  775 total  798           clock   66.1Hz

So it knows about 1280x800 now - but it just isn't using it yet. James.

---

### Post by realzippy on 2010-11-14
Is it available now also in the gnome display settings?

or try :


```
xrandr --output default --mode 1024x768
```

---

### Post by jameslyons on 2010-11-14
> **realzippy said:**
> Is it available now also in the gnome display settings?
It gives errors but starts:

[I]    jim@jim-T8200:/usr$ gnome-display-properties
    (gnome-display-properties:3712): Gtk-WARNING **: Ignoring the separator setting
    (gnome-display-properties:3712): Gtk-WARNING **: No object called: 
[/I]
Then the monitor icon says "unknown".
The res. is 800x600. I reset it to 1024x800, set as default and clicked apply. Then I logged out and back in but the res. is the same.
Progress but I'm not quite there yet. 
James.

---

### Post by jameslyons on 2010-11-14
Yea!!! I tried again to set gnome display resolution, this time as non-root, and gnome asked me for the password then reset the res. properly also as default. After a reboot it still works. Yipeeeeee! So I'm happy but knackered. Time to chill out in front of a film.:popcorn: I'm extremely grateful for your help and hope this thread might be useful to someone else in the future too. Bye, James. :P:KS:P

---

### Post by del_diablo on 2010-12-02
Sorry for the necroposting, but I have more or less the same issue, with the same output problem: *"xrandr: Failed to get size of gamma for output default"*
I get this when I attempt to forcefeed xrandr with the correct resolution.
I tried to run gnome-display-properties or whatever it is called, as root and as normal user, the results was abysmal.
The display is listed as "uknown", the resolution is quite a few pixels to small(1152x864 instead of 1280x1024), and the listed refresh rate is 0 Hz(xrandr tells me the screen is refreshing at 75Hz, like it is suppose to.

---

### Post by realzippy on 2010-12-02
**necroposting**  - nice word,thanks.  :D

Please post your "xrandr" terminal output.

Which graphics device/driver  ?

---

### Post by del_diablo on 2010-12-02
> xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1152 x 864, maximum 1152 x 864
default connected 1152x864+0+0 0mm x 0mm
   1152x864        0.0* 
   1024x768       61.0  
   800x600        61.0  
  1280x1024_75.00 (0x120)  138.8MHz
        h: width  1280 start 1368 end 1504 total 1728 skew    0 clock   80.3KHz
        v: height 1024 start 1027 end 1034 total 1072           clock   74.9Hz
Hmmm, tht modline seems to have been added, but it won't actually go to that resolution.

Lshw:
```
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Mobility Radeon HD 3400 Series
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:c0000000-dfffffff(prefetchable) ioport:a000(size=256) memory:9fbf0000-9fbfffff memory:9fb00000-9fb1ffff(prefetchable)

```
Driver would be radeon, using 36 kernel on the top of quite new dri libs.

---

### Post by realzippy on 2010-12-02
EDIT:
The "newmode" command seems to have worked,but what about
the "addmode" command? If  it ran successfully,the resolution would have appeared in the top resolution listing of "xrandr".....

---

### Post by del_diablo on 2010-12-02
I have a 1280x1024 LCD panel which support 75Hz refresh.
I ran "cvt 1280 1024 75", and then pasted the modline
```
 xrandr  --newmode "1280x1024_75.00"  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync 
```

---

### Post by realzippy on 2010-12-02
Please run those commands,ignore the "gamma error" you will get after every command...

```
xrandr --newmode test 138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync
```

```
xrandr --addmode default test
```

```
xrandr --output default --mode test
```


...should normally work.


**EDIT:**

..maybe there is a problem with that **75** Hz modeline...here it does not work.
Anyway,there is no much sense in running more than 60 since on a LCD,will only increase the panel lagging.So try *cvt 1280 1024* without any Hz specification,which would be:

```
xrandr --newmode rest 109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```

```
xrandr --addmode default rest
```

```
xrandr --output default --mode rest
```

...works here.

**EDIT2:**
If still no luck,or something like "*configure CRT 0 failed*",then your panel cannot run even 60 Hz on that large resolution,so lower it to 59 or 58 (by cvt),means :   ;-)

```
xrandr --newmode best 104.25  1280 1360 1488 1696  1024 1027 1034 1061 -hsync +vsync
```

```
xrandr --addmode default best
```

```
xrandr --output default --mode best
```

...works here too.

---

### Post by del_diablo on 2010-12-02
There is no sense to actually run below 75 Hz when the screen supports it I say, since the refresh lag is below neglishable. You might have one of those hardcoded monitors which can not go above 60Hz, even thou in theory it should support well beyond 120Hz.
```
04 1728  1024 1027 1034 1072 -hsync +vsyncde test 138.75  1280 1368 15 
xrandr: Failed to get size of gamma for output default
09:44 delly@delly-laptop /$ xrandr --addmode default test
xrandr: Failed to get size of gamma for output default
09:44 delly@delly-laptop /$ xrandr --output default --mode test
xrandr: Failed to get size of gamma for output default
xrandr: screen cannot be larger than 1152x864 (desired size 1280x1024)
```

Also tried the second thing you pasted up:
```
09:50 delly@delly-laptop /$ xrandr --output default --mode rest
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
```
That is... odd, I think it works under Windows, and I think it worked under fgrlx? Hmmm, any idea on where I should do further investigation before attempting to fire up a bugreport to the radeon tracker?

---

### Post by realzippy on 2010-12-02
...ah,you got a "Configure crtc 0 failed",so see my edit2 (which was made before you posted...)of post#28...

---

### Post by QLee on 2010-12-03
[QUOTE=del_diablo]There is no sense to actually run below 75 Hz when the screen supports it I say, since the refresh lag is below neglishable. You might have one of those hardcoded monitors which can not go above 60Hz, even thou in theory it should support well beyond 120Hz..[/QUOTE]

I want to respectfully agree with realzippy. The higher refresh rates (to avoid "flicker") were useful on CRTs because of the technology involved. The phosphors on the CRT would decay(lose brightness) if they weren't refreshed quickly enough and that could cause eyestrain. An LCD monitor doesn't work that way, basically it remains in state until changed.

---

### Post by del_diablo on 2010-12-03
Yeah, yeah...
But back to the issue:
```
88 1696  1024 1027 1034 1061 -hsync +vsyncde best 104.25  1280 1360 14 
xrandr: Failed to get size of gamma for output default
05:01 delly@delly-laptop /$ xrandr --addmode default best
xrandr: Failed to get size of gamma for output default
05:01 delly@delly-laptop /$ xrandr --output default --mode best
xrandr: Failed to get size of gamma for output default
xrandr: screen cannot be larger than 1152x864 (desired size 1280x1024)
05:01 delly@delly-laptop /$ 
```
1280x1024 finally shows up in gnome-display-properties, but i can't actually change to it. Attempted both with and without root powers :P

---

### Post by realzippy on 2010-12-03
Do you have a xorg.conf file?
If so,please post it.

---

### Post by del_diablo on 2010-12-03
Xorg.conf is empthy.
```
 cat /etc/X11/xorg.conf


06:13 delly@delly-laptop /$ 

```

---

### Post by realzippy on 2010-12-03
Empty?
There should be *none*;*if* there is one,it should not be empty.
Did you create it?
A relict from former attempts to fix your issue?
Delete it and restart X.

...please post your /var/log/**Xorg.0.log** file...

---

### Post by del_diablo on 2010-12-04
cat /var/log/Xorg.0.log:
```
X.Org X Server 1.7.7
Release Date: 2010-05-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.32-5-amd64 x86_64 Debian
Current Operating System: Linux delly-laptop 2.6.32-5-amd64 #1 SMP Thu Nov 25 18:02:11 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-5-amd64 root=UUID=97d9ab35-36a8-4192-87e5-2bc025d8d247 ro quiet
Build Date: 11 November 2010  11:44:20PM
xorg-server 2:1.7.7-9 (Julien Cristau <jcristau@debian.org>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec  4 13:58:09 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7c8a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI: (0:1:5:0) 1002:9612:1734:113b ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] rev 0, Mem @ 0xa0000000/268435456, 0x9fdf0000/65536, 0x9fe00000/1048576, I/O @ 0x00009000/256
(--) PCI:*(0:2:0:0) 1002:95c4:1734:113b ATI Technologies Inc Mobility Radeon HD 3400 Series rev 0, Mem @ 0xc0000000/536870912, 0x9fbf0000/65536, I/O @ 0x0000a000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension SELinux
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched ati as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(WW) Warning, couldn't open module ati
(II) UnloadModule: "ati"
(EE) Failed to load module "ati" (module does not exist, 0)
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(WW) Warning, couldn't open module fbdev
(II) UnloadModule: "fbdev"
(EE) Failed to load module "fbdev" (module does not exist, 0)
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
(II) VESA(0): VESA VBE OEM Software Rev: 10.88
(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) VESA(0): VESA VBE OEM Product: M82
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: CPT  Model: 1401  Serial#: 0
(II) VESA(0): Year: 2008  Week: 15
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) VESA(0): Gamma: 2.20
(II) VESA(0): No DPMS capabilities specified
(II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.595 redY: 0.343   greenX: 0.317 greenY: 0.559
(II) VESA(0): blueX: 0.156 blueY: 0.132   whiteX: 0.315 whiteY: 0.329
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported detailed timing:
(II) VESA(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) VESA(0): h_active: 1280  h_sync: 1312  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) VESA(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(II) VESA(0): Unknown vendor-specific block f
(II) VESA(0):  CPT
(II) VESA(0):  CLAA154WB03A
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff000e14011400000000
(II) VESA(0): 	0f120103802115780a743d9857518f28
(II) VESA(0): 	21505400000001010101010101010101
(II) VESA(0): 	010101010101ea1a0080502010302020
(II) VESA(0): 	13004bcf100000190000000f00202020
(II) VESA(0): 	2020202020206e050f00000000fe0043
(II) VESA(0): 	50540a202020202020202020000000fe
(II) VESA(0): 	00434c41413135345742303341200065
(II) VESA(0): EDID vendor "CPT", prod id 5121
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1280x800"x0.0   68.90  1280 1312 1344 1408  800 801 804 816 -hsync -vsync (48.9 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 101 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 50
	LinNumberOfImagePages: 50
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 103 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 832
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 832
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 105 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 18
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 18
	LinNumberOfImagePages: 18
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 107 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 111 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 24
	LinNumberOfImagePages: 24
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 114 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 117 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 11a (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 10e (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 127
	LinNumberOfImagePages: 127
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 120 (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 193 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 127
	LinNumberOfImagePages: 127
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 195 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 84
	LinNumberOfImagePages: 84
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 196 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 50
	LinNumberOfImagePages: 50
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1b3 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 512
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 512
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1b5 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1024
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 35
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 35
	LinNumberOfImagePages: 35
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 1b6 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 2048
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 18
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 18
	LinNumberOfImagePages: 18
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1c3 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1c5 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 35
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 35
	LinNumberOfImagePages: 35
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 1c6 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 17
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 17
	LinNumberOfImagePages: 17
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 133 (720x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 768
	XResolution: 720
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 768
	BnkNumberOfImagePages: 50
	LinNumberOfImagePages: 50
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 135 (720x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1472
	XResolution: 720
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 27
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1472
	BnkNumberOfImagePages: 27
	LinNumberOfImagePages: 27
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 136 (720x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 2944
	XResolution: 720
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 13
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2944
	BnkNumberOfImagePages: 13
	LinNumberOfImagePages: 13
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 153 (1152x864)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1152
	XResolution: 1152
	YResolution: 864
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1152
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 155 (1152x864)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 2304
	XResolution: 1152
	YResolution: 864
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2304
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 156 (1152x864)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 4608
	XResolution: 1152
	YResolution: 864
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 4608
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 163 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 165 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 166 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 121 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 12
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 12
	LinNumberOfImagePages: 12
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 122 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 123 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 124 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 143 (1400x1050)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1408
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1408
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 145 (1400x1050)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 2816
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2816
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 146 (1400x1050)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 5632
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 5632
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 173 (1600x1200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 175 (1600x1200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 176 (1600x1200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 183 (1792x1344)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1792
	XResolution: 1792
	YResolution: 1344
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1792
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 185 (1792x1344)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 3584
	XResolution: 1792
	YResolution: 1344
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3584
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 186 (1792x1344)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 7168
	XResolution: 1792
	YResolution: 1344
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 7168
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1d3 (1856x1392)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1856
	XResolution: 1856
	YResolution: 1392
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1856
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1d5 (1856x1392)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 3712
	XResolution: 1856
	YResolution: 1392
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3712
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 1d6 (1856x1392)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 7424
	XResolution: 1856
	YResolution: 1392
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 7424
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1e3 (1920x1440)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 1920
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1920
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1e5 (1920x1440)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 3840
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3840
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 1e6 (1920x1440)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00051eb
	BytesPerScanline: 7680
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 7680
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000

(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): <default monitor>: Using hsync value of 48.93 kHz
(II) VESA(0): <default monitor>: Using vrefresh value of 59.97 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1920x1440" (no mode of this name)
(II) VESA(0): Not using built-in mode "1856x1392" (no mode of this name)
(II) VESA(0): Not using built-in mode "1792x1344" (no mode of this name)
(II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
(II) VESA(0): Not using built-in mode "1400x1050" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(II) VESA(0): Not using built-in mode "1152x864" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "720x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
(II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): <default monitor>: Using hsync value of 48.93 kHz
(II) VESA(0): <default monitor>: Using vrefresh value of 59.97 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1920x1440" (hsync out of range)
(II) VESA(0): Not using built-in mode "1856x1392" (hsync out of range)
(II) VESA(0): Not using built-in mode "1792x1344" (hsync out of range)
(II) VESA(0): Not using built-in mode "1600x1200" (hsync out of range)
(II) VESA(0): Not using built-in mode "1400x1050" (hsync out of range)
(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
(II) VESA(0): Not using built-in mode "1152x864" (hsync out of range)
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
(II) VESA(0): Not using built-in mode "720x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x350" (hsync out of range)
(II) VESA(0): Not using built-in mode "512x384" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(WW) VESA(0): No valid modes left. Trying aggressive sync range...
(II) VESA(0): <default monitor>: Using hsync range of 31.50-48.93 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 50.00-59.97 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1920x1440" (hsync out of range)
(II) VESA(0): Not using built-in mode "1856x1392" (hsync out of range)
(II) VESA(0): Not using built-in mode "1792x1344" (hsync out of range)
(II) VESA(0): Not using built-in mode "1600x1200" (hsync out of range)
(II) VESA(0): Not using built-in mode "1400x1050" (hsync out of range)
(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
(II) VESA(0): Not using built-in mode "720x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x350" (hsync out of range)
(II) VESA(0): Not using built-in mode "512x384" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(--) VESA(0): Virtual size is 1152x864 (pitch 1152)
(**) VESA(0): *Built-in mode "1152x864"
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): Display dimensions: (330, 210) mm
(**) VESA(0): DPI set to (88, 104)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (123)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (122)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
(II) VESA(0): VESA VBE OEM Software Rev: 10.88
(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) VESA(0): VESA VBE OEM Product: M82
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(II) VESA(0): virtual address = 0x7f063f3be000,
	physical address = 0xc0000000, size = 16777216
(II) VESA(0): Setting up VESA Mode 0x156 (1152x864)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(==) VESA(0): DPMS enabled
(==) RandR enabled
(II) Found 2 VGA devices: arbiter wrapping enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
SELinux: Disabled on system, not enabling in X server
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/udev: Adding input device Power Button (/dev/input/event9)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6.901, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event9"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "no"
(II) config/udev: Adding input device Video Bus (/dev/input/event11)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event11"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "no"
(II) config/udev: Adding input device Video Bus (/dev/input/event12)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event12"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "no"
(II) config/udev: Adding input device Power Button (/dev/input/event6)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event6"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "no"
(II) config/udev: Adding input device Lid Switch (/dev/input/event7)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event8)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event8"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "no"
(II) config/udev: Adding input device Logitech Logitech RumblePad 2 USB (/dev/input/event2)
(**) Logitech Logitech RumblePad 2 USB: Applying InputClass "joystick catchall"
(II) LoadModule: "joystick"
(II) Loading /usr/lib/xorg/modules/input/joystick_drv.so
(II) Module joystick: vendor="X.Org Foundation"
	compiled for 1.7.6.901, module version = 1.5.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event2"
(**) Logitech Logitech RumblePad 2 USB: always reports core events
(**) Logitech Logitech RumblePad 2 USB (keys): always reports core events
(II) XINPUT: Adding extended input device "Logitech Logitech RumblePad 2 USB" (type: JOYSTICK)
(II) Joystick: Logitech Logitech RumblePad 2 USB. bus 0x3 vendor 0x46d product 0xc218 version 0x110
(II) Joystick: found 6 axes, 12 buttons
(II) XINPUT: Adding extended input device "Logitech Logitech RumblePad 2 USB (keys)" (type: JOYSTICK)
JOYSTICK: DebugLevel set to 0
(II) config/udev: Adding input device Logitech Logitech RumblePad 2 USB (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Trust GM-4200 Gamer Optical Mouse (/dev/input/event3)
(**) Trust GM-4200 Gamer Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Trust GM-4200 Gamer Optical Mouse: always reports core events
(**) Trust GM-4200 Gamer Optical Mouse: Device: "/dev/input/event3"
(II) Trust GM-4200 Gamer Optical Mouse: Found 10 mouse buttons
(II) Trust GM-4200 Gamer Optical Mouse: Found scroll wheel(s)
(II) Trust GM-4200 Gamer Optical Mouse: Found relative axes
(II) Trust GM-4200 Gamer Optical Mouse: Found x and y relative axes
(II) Trust GM-4200 Gamer Optical Mouse: Configuring as mouse
(**) Trust GM-4200 Gamer Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Trust GM-4200 Gamer Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Trust GM-4200 Gamer Optical Mouse" (type: MOUSE)
(II) Trust GM-4200 Gamer Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Trust GM-4200 Gamer Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech Logitech USB Keyboard (/dev/input/event4)
(**) Logitech Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Logitech Logitech USB Keyboard: always reports core events
(**) Logitech Logitech USB Keyboard: Device: "/dev/input/event4"
(II) Logitech Logitech USB Keyboard: Found keys
(II) Logitech Logitech USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech Logitech USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "no"
(II) config/udev: Adding input device Logitech Logitech USB Keyboard (/dev/input/event5)
(**) Logitech Logitech USB Keyboard: Applying InputClass "evdev pointer catchall"
(**) Logitech Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Logitech Logitech USB Keyboard: always reports core events
(**) Logitech Logitech USB Keyboard: Device: "/dev/input/event5"
(II) Logitech Logitech USB Keyboard: Found 20 mouse buttons
(II) Logitech Logitech USB Keyboard: Found scroll wheel(s)
(II) Logitech Logitech USB Keyboard: Found relative axes
(II) Logitech Logitech USB Keyboard: Found x and y relative axes
(II) Logitech Logitech USB Keyboard: Found keys
(II) Logitech Logitech USB Keyboard: Configuring as mouse
(II) Logitech Logitech USB Keyboard: Configuring as keyboard
(**) Logitech Logitech USB Keyboard: YAxisMapping: buttons 4 and 5
(**) Logitech Logitech USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Logitech USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "no"
(II) Logitech Logitech USB Keyboard: initialized for relative axes.
(II) config/udev: Adding input device Logitech Logitech USB Keyboard (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event13)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event1)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "no"
(II) config/udev: Adding input device PC Speaker (/dev/input/event10)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event0)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ACPI Virtual Keyboard Device (/dev/input/event14)
(**) ACPI Virtual Keyboard Device: Applying InputClass "evdev keyboard catchall"
(**) ACPI Virtual Keyboard Device: always reports core events
(**) ACPI Virtual Keyboard Device: Device: "/dev/input/event14"
(II) ACPI Virtual Keyboard Device: Found keys
(II) ACPI Virtual Keyboard Device: Configuring as keyboard
(II) XINPUT: Adding extended input device "ACPI Virtual Keyboard Device" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "no"
```

Xorg.conf is a relic from the time I used fglrx, I think I just deleted all lines in it instead of running rm on the file.

---

### Post by realzippy on 2010-12-04
*Asked you to delete* your empty xorg.conf....please do this.As you can read in your xorg log file,your empty file is used;failed of course:

[B](==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.

aso.[/B]

Normally the ATI driver is loaded as module by KMS (kernelmodesetting) during boot,this is not the case:

[B](II) LoadModule: "ati"
(WW) Warning, couldn't open module ati
(II) UnloadModule: "ati"
(EE) Failed to load module "ati" (module does not exist, 0)
[/B]

...maybe because formerly installed fglrx blacklisted the ati module.
Suggest to search the web for uninstalling the fglrx driver *correctly* and reinstall the ati driver.
E.G.: (Do not know if this is correct,but think it cannot do harm)
```
dpkg-divert --list | grep fglrx | cut -d' ' -f3
sudo dpkg-divert --remove /usr/lib/libGL.so.1.2 
```
if it is a 64bit system run also:
```
sudo dpkg-divert --remove /usr/lib32/libGL.so.1.2 
```
reboot.then:
```
sudo apt-get purge fglrx fglrx-modaliases fglrx-amdcccle
sudo rm -r /etc/ati /etc/X11/xorg.conf 
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core xserver-xorg-video-ati
```
Reboot..

You could also start an Ubuntu liveCD,I guess your resolution will be correct there,just to prove that it is the missing ati kernel module.

---

### Post by del_diablo on 2010-12-04
Ok, thanks for the help, that fixed it.
Fglrx left behind 1 blacklist, that removed. /etc/ati was also removed.
Now it worked properly, it was just to set up the monitors, and it worked <3

---

### Post by sky5564 on 2010-12-10
im having the same problem with a memorex lcd tv/monitor combo mine will only do 800x600 but i need 1024x768. windows 7 runs at 1024x768 on this same monitor so i know it can do it.

```
skilo@skilo-OptiPlex-GX240:~$ cvt 1024x768 60.00
# 1024x60 51.40 Hz (CVT) hsync: 3.91 kHz; pclk: 5.00 MHz
Modeline "1024x60_60.00"    5.00  1024 1056 1152 1280  60 63 73 76 -hsync +vsync
skilo@skilo-OptiPlex-GX240:~$ xrandr  --newmode "1024x768_60.00" 5.00 1024 1056 1152 1280 60 63 73 76 -hsync +vsync
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19
skilo@skilo-OptiPlex-GX240:~$ 

```

---

### Post by sky5564 on 2010-12-10
```
skilo@skilo-OptiPlex-GX240:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
  1024x768_60.00 (0x83)  138.8MHz
        h: width  1280 start 1368 end 1504 total 1728 skew    0 clock   80.3KHz
        v: height 1024 start 1027 end 1034 total 1072           clock   74.9Hz
  1024x768 (0x84)  138.8MHz
        h: width  1280 start 1368 end 1504 total 1728 skew    0 clock   80.3KHz
        v: height 1024 start 1027 end 1034 total 1072           clock   74.9Hz
skilo@skilo-OptiPlex-GX240:~$ 


```

---

### Post by realzippy on 2010-12-10
..run no "addmode" ?

---

### Post by sky5564 on 2010-12-10
> **realzippy said:**
> ..run no "addmode" ?

im confused what would the addmode command be? like this - xrandr --addmode "1024x60_60.00"    5.00  1024 1056 1152 1280  60 63 73 76 -hsync +vsync ????

---

### Post by sky5564 on 2010-12-10
never mind what i posted before i had to reinstall so everything is fresh now. 

so what do i need to do from here???????????

```
skilo@desktop:~$ lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
skilo@desktop:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
skilo@desktop:~$ xrandr -s 1024x768
Size 1024x768 not found in available modes
skilo@desktop:~$ 

```

---

### Post by realzippy on 2010-12-10
try:
```
xrandr --newmode test 62.25  1024 1072 1176 1328  768 771 775 797 -hsync +vsync
```

```
xrandr --addmode default test
```

```
xrandr --output default --mode test
```
-------------------------------------------------------------------------------------------------

BTW,folks,this cannot turn to an one-size-fits-all graphics HowTo.

So read e.g.this for general xrandr usage:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

---

### Post by sky5564 on 2010-12-10
> **realzippy said:**
> try:
```
xrandr --newmode test 62.25  1024 1072 1176 1328  768 771 775 797 -hsync +vsync
```

```
xrandr --addmode default test
```

```
xrandr --output default --mode test
```
-------------------------------------------------------------------------------------------------

BTW,folks,this cannot turn to an one-size-fits-all graphics HowTo.

So read e.g.this for general xrandr usage:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)


```
skilo@desktop:~$ xrandr --newmode test 62.25  1024 1072 1176 1328  768 771 775 797 -hsync +vsync
xrandr: Failed to get size of gamma for output default
skilo@desktop:~$ xrandr --addmode default test
xrandr: Failed to get size of gamma for output default
skilo@desktop:~$ xrandr --output default --mode test
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
skilo@desktop:~$ 

```

---

### Post by realzippy on 2010-12-10
Sorry,no idea.

---

### Post by sky5564 on 2010-12-10
LOL !!!!!!!

im about to break down and buy a new monitor..... i have posted this same question on numerous forums and NO ONE CAN FIGURE IT OUT !!!!!!!! :shock: [-o< :cry:

---

### Post by sky5564 on 2010-12-10
just found some new info so i tried a few things.

first i followed these steps to create a new xorg.conf file

```
ctrl +alt+f1

sudo service gdm stop

sudo Xorg -configure

sudo mv /somedir/user/xorg.conf.new /etc/X11/xorg.conf

sudo service gdm start
```

that created a new xorg.conf but 1024x768 still is not available anywhere urrrrghhh the file it created below 

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "record"
	Load  "extmod"
	Load  "glx"
	Load  "dbe"
	Load  "dri2"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "ForcePCIMode"       	# [<bool>]
        #Option     "CCEPIOMode"         	# [<bool>]
        #Option     "CCENoSecurity"      	# [<bool>]
        #Option     "CCEusecTimeout"     	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPSize"            	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "Display"            	# <str>
        #Option     "PanelWidth"         	# <i>
        #Option     "PanelHeight"        	# <i>
        #Option     "ProgramFPRegs"      	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "ShowCache"          	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
	Identifier  "Card0"
	Driver      "r128"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by sky5564 on 2010-12-10
i think im starting to see whats wrong here.

here the var xorg log

```
[   305.762] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   305.763] X Protocol Version 11, Revision 0
[   305.763] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   305.763] Current Operating System: Linux desktop 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686
[   305.763] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=6ebf1970-d1b3-4fa9-8267-3bdb0b60c951 ro quiet splash
[   305.764] Build Date: 16 September 2010  05:39:22PM
[   305.764] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[   305.764] Current version of pixman: 0.18.4
[   305.764] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   305.765] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   305.766] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 10 20:05:23 2010
[   305.766] (==) Using config file: "/etc/X11/xorg.conf"
[   305.767] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   305.768] (==) ServerLayout "X.org Configured"
[   305.768] (**) |-->Screen "Screen0" (0)
[   305.768] (**) |   |-->Monitor "Monitor0"
[   305.769] (**) |   |-->Device "Card0"
[   305.769] (**) |-->Input Device "Mouse0"
[   305.769] (**) |-->Input Device "Keyboard0"
[   305.769] (==) Automatically adding devices
[   305.769] (==) Automatically enabling devices
[   305.769] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   305.769] 	Entry deleted from font path.
[   305.770] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   305.770] 	Entry deleted from font path.
[   305.770] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   305.770] (**) ModulePath set to "/usr/lib/xorg/modules"
[   305.770] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   305.770] (WW) Disabling Mouse0
[   305.770] (WW) Disabling Keyboard0
[   305.770] (II) Loader magic: 0x81f8e00
[   305.770] (II) Module ABI versions:
[   305.770] 	X.Org ANSI C Emulation: 0.4
[   305.770] 	X.Org Video Driver: 8.0
[   305.770] 	X.Org XInput driver : 11.0
[   305.770] 	X.Org Server Extension : 4.0
[   305.772] (--) PCI:*(0:1:0:0) 1002:5446:1002:0408 rev 0, Mem @ 0xf8000000/67108864, 0xff8fc000/16384, I/O @ 0x0000ec00/256, BIOS @ 0x????????/131072
[   305.773] (II) Open ACPI successful (/var/run/acpid.socket)
[   305.773] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[   305.773] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[   305.773] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[   305.773] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[   305.773] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[   305.773] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[   305.773] (II) LoadModule: "record"
[   305.790] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   305.791] (II) Module record: vendor="X.Org Foundation"
[   305.791] 	compiled for 1.9.0, module version = 1.13.0
[   305.791] 	Module class: X.Org Server Extension
[   305.791] 	ABI class: X.Org Server Extension, version 4.0
[   305.791] (II) Loading extension RECORD
[   305.791] (II) LoadModule: "extmod"
[   305.792] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   305.792] (II) Module extmod: vendor="X.Org Foundation"
[   305.792] 	compiled for 1.9.0, module version = 1.0.0
[   305.792] 	Module class: X.Org Server Extension
[   305.792] 	ABI class: X.Org Server Extension, version 4.0
[   305.792] (II) Loading extension MIT-SCREEN-SAVER
[   305.792] (II) Loading extension XFree86-VidModeExtension
[   305.792] (II) Loading extension XFree86-DGA
[   305.792] (II) Loading extension DPMS
[   305.793] (II) Loading extension XVideo
[   305.793] (II) Loading extension XVideo-MotionCompensation
[   305.793] (II) Loading extension X-Resource
[   305.793] (II) LoadModule: "glx"
[   305.793] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   305.794] (II) Module glx: vendor="X.Org Foundation"
[   305.794] 	compiled for 1.9.0, module version = 1.0.0
[   305.794] 	ABI class: X.Org Server Extension, version 4.0
[   305.794] (==) AIGLX enabled
[   305.794] (II) Loading extension GLX
[   305.794] (II) LoadModule: "dbe"
[   305.795] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   305.795] (II) Module dbe: vendor="X.Org Foundation"
[   305.795] 	compiled for 1.9.0, module version = 1.0.0
[   305.795] 	Module class: X.Org Server Extension
[   305.795] 	ABI class: X.Org Server Extension, version 4.0
[   305.795] (II) Loading extension DOUBLE-BUFFER
[   305.795] (II) LoadModule: "dri2"
[   305.796] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   305.797] (II) Module dri2: vendor="X.Org Foundation"
[   305.797] 	compiled for 1.9.0, module version = 1.2.0
[   305.797] 	ABI class: X.Org Server Extension, version 4.0
[   305.797] (II) Loading extension DRI2
[   305.797] (II) LoadModule: "dri"
[   305.798] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   305.799] (II) Module dri: vendor="X.Org Foundation"
[   305.799] 	compiled for 1.9.0, module version = 1.0.0
[   305.799] 	ABI class: X.Org Server Extension, version 4.0
[   305.799] (II) Loading extension XFree86-DRI
[   305.799] (II) LoadModule: "r128"
[   305.799] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[   305.800] (II) Module r128: vendor="X.Org Foundation"
[   305.800] 	compiled for 1.8.99.905, module version = 6.8.1
[   305.800] 	Module class: X.Org Video Driver
[   305.800] 	ABI class: X.Org Video Driver, version 8.0
[   305.800] (II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
[   305.801] (--) using VT number 8

[   305.815] (II) R128(0): PCI bus 1 card 0 func 0
[   305.816] (==) R128(0): Depth 24, (--) framebuffer bpp 32
[   305.816] (II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   305.816] (==) R128(0): Default visual is TrueColor
[   305.816] (II) Loading sub module "vgahw"
[   305.816] (II) LoadModule: "vgahw"
[   305.817] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[   305.817] (II) Module vgahw: vendor="X.Org Foundation"
[   305.817] 	compiled for 1.9.0, module version = 0.1.0
[   305.817] 	ABI class: X.Org Video Driver, version 8.0
[   305.817] (II) R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[   305.817] (==) R128(0): RGB weight 888
[   305.817] (II) R128(0): Using 8 bits per RGB (8 bit DAC)
[   305.817] (II) Loading sub module "int10"
[   305.817] (II) LoadModule: "int10"
[   305.818] (II) Loading /usr/lib/xorg/modules/libint10.so
[   305.819] (II) Module int10: vendor="X.Org Foundation"
[   305.819] 	compiled for 1.9.0, module version = 1.0.0
[   305.819] 	ABI class: X.Org Video Driver, version 8.0
[   305.819] (II) R128(0): initializing int10
[   305.826] (II) R128(0): Primary V_BIOS segment is: 0xc000
[   305.827] (--) R128(0): Chipset: "ATI Rage 128 Pro ULTRA TF (AGP)" (ChipID = 0x5446)
[   305.827] (--) R128(0): Linear framebuffer at 0xf8000000
[   305.827] (--) R128(0): MMIO registers at 0xff8fc000
[   305.827] (--) R128(0): VideoRAM: 16384 kByte (128-bit SDR SGRAM 1:1)
[   305.827] (**) R128(0): Using external CRT for display
[   305.828] (II) R128(0): Primary Display == Type 3
[   305.828] (WW) R128(0): Can't determine panel dimensions, and none specified.
	Disabling programming of FP registers.
[   305.828] (II) R128(0): PLL parameters: rf=2950 rd=65 min=12500 max=35000; xclk=13000
[   305.828] (II) Loading sub module "ddc"
[   305.828] (II) LoadModule: "ddc"
[   305.828] (II) Module "ddc" already built-in
[   305.828] (II) Loading sub module "vbe"
[   305.828] (II) LoadModule: "vbe"
[   305.828] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   305.829] (II) Module vbe: vendor="X.Org Foundation"
[   305.829] 	compiled for 1.9.0, module version = 1.1.0
[   305.829] 	ABI class: X.Org Video Driver, version 8.0
[   305.829] (II) R128(0): VESA BIOS detected
[   305.830] (II) R128(0): VESA VBE Version 2.0
[   305.830] (II) R128(0): VESA VBE Total Mem: 16384 kB
[   305.830] (II) R128(0): VESA VBE OEM: ATI RAGE128
[   305.830] (II) R128(0): VESA VBE OEM Software Rev: 1.0
[   305.830] (II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
[   305.830] (II) R128(0): VESA VBE OEM Product: R128
[   305.830] (II) R128(0): VESA VBE OEM Product Rev: 01.00
[   305.830] (II) Loading sub module "ddc"
[   305.830] (II) LoadModule: "ddc"
[   305.830] (II) Module "ddc" already built-in
[   305.932] (II) R128(0): VESA VBE DDC supported
[   305.932] (II) R128(0): VESA VBE DDC Level none
[   305.932] (II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
[   306.027] (II) R128(0): VESA VBE DDC read failed
[   306.027] (==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
[   306.033] (II) Loading sub module "i2c"
[   306.033] (II) LoadModule: "i2c"
[   306.033] (II) Module "i2c" already built-in
[   306.033] (II) R128(0): I2C bus "DDC" initialized.
[   306.033] (II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
[   306.038] (EE) R128(0): No DFP detected
[   306.044] (II) R128(0): Monitor0: Using default hsync range of 31.50-37.90 kHz
[   306.044] (II) R128(0): Monitor0: Using default vrefresh range of 50.00-70.00 Hz
[   306.044] (WW) R128(0): Unable to estimate virtual size
[   306.044] (II) R128(0): Clock range:  12.50 to 350.00 MHz
[   306.044] (II) R128(0): Not using default mode "640x350" (vrefresh out of range)
[   306.044] (II) R128(0): Not using default mode "320x175" (vrefresh out of range)
[   306.044] (II) R128(0): Not using default mode "640x400" (vrefresh out of range)
[   306.044] (II) R128(0): Not using default mode "320x200" (vrefresh out of range)
[   306.044] (II) R128(0): Not using default mode "720x400" (vrefresh out of range)
[   306.044] (II) R128(0): Not using default mode "360x200" (vrefresh out of range)
[   306.044] (II) R128(0): Not using default mode "640x480" (vrefresh out of range)
[   306.044] (II) R128(0): Not using default mode "320x240" (vrefresh out of range)
[   306.044] (II) R128(0): Not using default mode "640x480" (vrefresh out of range)
[   306.044] (II) R128(0): Not using default mode "320x240" (vrefresh out of range)
[   306.044] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[   306.044] (II) R128(0): Not using default mode "320x240" (hsync out of range)
[   306.044] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[   306.044] (II) R128(0): Not using default mode "400x300" (hsync out of range)
[   306.044] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[   306.044] (II) R128(0): Not using default mode "400x300" (hsync out of range)
[   306.044] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[   306.044] (II) R128(0): Not using default mode "400x300" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1024x768i" (vrefresh out of range)
[   306.045] (II) R128(0): Not using default mode "512x384i" (vrefresh out of range)
[   306.045] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "512x384" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "512x384" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "512x384" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "512x384" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1280x960" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1280x960" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "640x512" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "640x512" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "640x512" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1792x1344" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "896x672" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1792x1344" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "896x672" (hsync out of range)
[   306.045] (II) R128(0): Not using default mode "1856x1392" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "928x696" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1856x1392" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "928x696" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1920x1440" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "960x720" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1920x1440" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "960x720" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "832x624" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "416x312" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1360x768" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "680x384" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1360x768" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "680x384" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1440x900" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "720x450" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "1600x1024" (hsync out of range)
[   306.046] (II) R128(0): Not using default mode "800x512" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "1920x1080" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "960x540" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "1920x1200" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "960x600" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "1920x1440" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "960x720" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "2048x1536" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "2048x1536" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[   306.047] (II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[   306.047] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[   306.047] (--) R128(0): Virtual size is 800x600 (pitch 800)
[   306.047] (**) R128(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[   306.047] (II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   306.047] (**) R128(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[   306.047] (II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   306.047] (**) R128(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[   306.047] (II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   306.047] (**) R128(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
[   306.047] (II) R128(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
[   306.048] (**) R128(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
[   306.048] (II) R128(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
[   306.048] (**) R128(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
[   306.048] (II) R128(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
[   306.048] (==) R128(0): DPI set to (96, 96)
[   306.048] (II) Loading sub module "fb"
[   306.048] (II) LoadModule: "fb"
[   306.049] (II) Loading /usr/lib/xorg/modules/libfb.so
[   306.050] (II) Module fb: vendor="X.Org Foundation"
[   306.050] 	compiled for 1.9.0, module version = 1.0.0
[   306.050] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   306.050] (II) Loading sub module "ramdac"
[   306.050] (II) LoadModule: "ramdac"
[   306.050] (II) Module "ramdac" already built-in
[   306.050] (II) Loading sub module "xaa"
[   306.050] (II) LoadModule: "xaa"
[   306.051] (II) Loading /usr/lib/xorg/modules/libxaa.so
[   306.051] (II) Module xaa: vendor="X.Org Foundation"
[   306.051] 	compiled for 1.9.0, module version = 1.2.1
[   306.051] 	ABI class: X.Org Video Driver, version 8.0
[   306.051] (II) Loading sub module "shadowfb"
[   306.051] (II) LoadModule: "shadowfb"
[   306.052] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[   306.052] (II) Module shadowfb: vendor="X.Org Foundation"
[   306.052] 	compiled for 1.9.0, module version = 1.0.0
[   306.052] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   306.052] (II) R128(0): Page flipping disabled
[   306.053] (!!) R128(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
[   306.053] (--) Depth 24 pixmap format is 32 bpp
[   306.165] drmOpenDevice: node name is /dev/dri/card0
[   306.169] drmOpenDevice: node name is /dev/dri/card0
[   306.269] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   306.269] drmOpenDevice: node name is /dev/dri/card0
[   306.269] drmOpenDevice: open result is 11, (OK)
[   306.269] drmOpenByBusid: drmOpenMinor returns 11
[   306.269] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   306.269] (II) [drm] loaded kernel module for "r128" driver.
[   306.269] (II) [drm] DRM interface version 1.3
[   306.270] (II) [drm] DRM open master succeeded.
[   306.270] (II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
[   306.270] (II) R128(0): [drm] framebuffer handle = 0xf8000000
[   306.270] (II) R128(0): [drm] added 1 reserved context for kernel
[   306.270] (II) R128(0): X context handle = 0x1
[   306.270] (II) R128(0): [drm] installed DRM signal handler
[   306.271] (II) R128(0): [agp] Mode 0x1f000211 [AGP 0x8086/0x1a30; Card 0x1002/0x5446]
[   306.302] (II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
[   306.303] (II) R128(0): [agp] ring handle = 0xf0000000
[   306.304] (II) R128(0): [agp] Ring mapped at 0xb773a000
[   306.304] (II) R128(0): [agp] ring read ptr handle = 0xf0101000
[   306.304] (II) R128(0): [agp] Ring read ptr mapped at 0xb784f000
[   306.304] (II) R128(0): [agp] vertex/indirect buffers handle = 0xf0102000
[   306.305] (II) R128(0): [agp] Vertex/indirect buffers mapped at 0xb64ee000
[   306.305] (II) R128(0): [agp] AGP texture map handle = 0xf0302000
[   306.307] (II) R128(0): [agp] AGP Texture map mapped at 0xb600e000
[   306.307] (II) R128(0): [drm] register handle = 0xff8fc000
[   306.307] (II) R128(0): [dri] Visual configs initialized
[   306.307] (II) R128(0): CCE in BM mode
[   306.307] (II) R128(0): Using 8 MB AGP aperture
[   306.307] (II) R128(0): Using 1 MB for the ring buffer
[   306.307] (II) R128(0): Using 2 MB for vertex/indirect buffers
[   306.307] (II) R128(0): Using 5 MB for AGP textures
[   306.307] (II) R128(0): Memory manager initialized to (0,0) (800,2457)
[   306.307] (II) R128(0): Reserved area from (0,600) to (800,602)
[   306.308] (II) R128(0): Largest offscreen area available: 800 x 1855
[   306.308] (II) R128(0): Reserved back buffer from (0,602) to (800,1202)
[   306.308] (II) R128(0): Reserved depth buffer from (0,1202) to (800,1803)
[   306.308] (II) R128(0): Reserved depth span from (0,1802) offset 0x57fd00
[   306.308] (II) R128(0): Reserved 8704 kb for textures at offset 0x77f880
[   306.308] (II) R128(0): Using XFree86 Acceleration Architecture (XAA)
[   306.308] 	Screen to screen bit blits
[   306.308] 	Solid filled rectangles
[   306.308] 	8x8 mono pattern filled rectangles
[   306.308] 	Indirect CPU to Screen color expansion
[   306.308] 	Solid Lines
[   306.308] 	Dashed Lines
[   306.308] 	Setting up tile and stipple cache:
[   306.308] 		30 128x128 slots
[   306.308] (II) R128(0): Acceleration enabled
[   306.308] (==) R128(0): Backing store disabled
[   306.309] (==) R128(0): Silken mouse enabled
[   306.309] (II) R128(0): Using hardware cursor (scanline 7212)
[   306.309] (II) R128(0): Largest offscreen area available: 800 x 651
[   306.309] (==) R128(0): DPMS enabled
[   306.309] (II) R128(0): [DRI] installation complete
[   306.323] (II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
[   306.324] (II) R128(0): [drm] Mapped 128 vertex/indirect buffers
[   306.324] (II) R128(0): [drm] dma control initialized, using IRQ 16
[   306.324] (II) R128(0): Direct rendering enabled
[   306.324] (==) RandR enabled
[   306.324] (II) Initializing built-in extension Generic Event Extension
[   306.324] (II) Initializing built-in extension SHAPE
[   306.324] (II) Initializing built-in extension MIT-SHM
[   306.324] (II) Initializing built-in extension XInputExtension
[   306.324] (II) Initializing built-in extension XTEST
[   306.324] (II) Initializing built-in extension BIG-REQUESTS
[   306.324] (II) Initializing built-in extension SYNC
[   306.324] (II) Initializing built-in extension XKEYBOARD
[   306.324] (II) Initializing built-in extension XC-MISC
[   306.324] (II) Initializing built-in extension SECURITY
[   306.324] (II) Initializing built-in extension XINERAMA
[   306.324] (II) Initializing built-in extension XFIXES
[   306.324] (II) Initializing built-in extension RENDER
[   306.324] (II) Initializing built-in extension RANDR
[   306.324] (II) Initializing built-in extension COMPOSITE
[   306.325] (II) Initializing built-in extension DAMAGE
[   306.325] (II) Initializing built-in extension GESTURE
[   306.355] (II) AIGLX: Screen 0 is not DRI2 capable
[   306.355] drmOpenDevice: node name is /dev/dri/card0
[   306.355] drmOpenDevice: open result is 12, (OK)
[   306.355] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   306.355] drmOpenDevice: node name is /dev/dri/card0
[   306.355] drmOpenDevice: open result is 12, (OK)
[   306.355] drmOpenByBusid: drmOpenMinor returns 12
[   306.355] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   306.372] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   306.372] (II) AIGLX: Loaded and initialized /usr/lib/dri/r128_dri.so
[   306.373] (II) GLX: Initialized DRI GL provider for screen 0
[   306.465] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   306.576] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   306.576] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   306.576] (II) LoadModule: "evdev"
[   306.576] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   306.577] (II) Module evdev: vendor="X.Org Foundation"
[   306.578] 	compiled for 1.9.0, module version = 2.3.2
[   306.578] 	Module class: X.Org XInput Driver
[   306.578] 	ABI class: X.Org XInput driver, version 11.0
[   306.578] (**) Power Button: always reports core events
[   306.578] (**) Power Button: Device: "/dev/input/event1"
[   306.578] (II) Power Button: Found keys
[   306.578] (II) Power Button: Configuring as keyboard
[   306.578] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   306.578] (**) Option "xkb_rules" "evdev"
[   306.578] (**) Option "xkb_model" "pc105"
[   306.578] (**) Option "xkb_layout" "us"
[   306.581] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   306.581] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   306.581] (**) Power Button: always reports core events
[   306.581] (**) Power Button: Device: "/dev/input/event0"
[   306.581] (II) Power Button: Found keys
[   306.581] (II) Power Button: Configuring as keyboard
[   306.581] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   306.581] (**) Option "xkb_rules" "evdev"
[   306.581] (**) Option "xkb_model" "pc105"
[   306.581] (**) Option "xkb_layout" "us"
[   306.589] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[   306.589] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[   306.589] (**) Logitech USB Receiver: always reports core events
[   306.589] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[   306.590] (II) Logitech USB Receiver: Found keys
[   306.590] (II) Logitech USB Receiver: Configuring as keyboard
[   306.590] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[   306.590] (**) Option "xkb_rules" "evdev"
[   306.590] (**) Option "xkb_model" "pc105"
[   306.590] (**) Option "xkb_layout" "us"
[   306.592] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[   306.592] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[   306.592] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[   306.592] (**) Logitech USB Receiver: always reports core events
[   306.592] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[   306.592] (II) Logitech USB Receiver: Found 12 mouse buttons
[   306.592] (II) Logitech USB Receiver: Found scroll wheel(s)
[   306.592] (II) Logitech USB Receiver: Found relative axes
[   306.592] (II) Logitech USB Receiver: Found x and y relative axes
[   306.592] (II) Logitech USB Receiver: Found absolute axes
[   306.593] (II) evdev-grail: failed to open grail, no gesture support
[   306.593] (II) Logitech USB Receiver: Found keys
[   306.593] (II) Logitech USB Receiver: Configuring as mouse
[   306.593] (II) Logitech USB Receiver: Configuring as keyboard
[   306.593] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[   306.593] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   306.593] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[   306.593] (**) Option "xkb_rules" "evdev"
[   306.593] (**) Option "xkb_model" "pc105"
[   306.593] (**) Option "xkb_layout" "us"
[   306.594] (II) Logitech USB Receiver: initialized for relative axes.
[   306.594] (WW) Logitech USB Receiver: ignoring absolute axes.
[   306.595] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[   306.595] (II) No input driver/identifier specified (ignoring)
```

so basically it is saying the 1024x768 hsync and vertrefresh are "out of range" and also it says "cannot determine monitor demensions, none specified using default"

so if only i knew what to do to that xorg file to make it recognize the demensions at boot i think everything would work.

just need a little help with xorg.conf files please.... anyone??

---

### Post by realzippy on 2010-12-11
306.045] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[   306.044] (II) R128(0): Monitor0: Using default hsync range of 31.50-37.90 kHz


You have to edit a hsync value in xorg.conf....

Try this xorg.conf:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "record"
	Load  "extmod"
	Load  "glx"
	Load  "dbe"
	Load  "dri2"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        [COLOR="Lime"]HorizSync       28.0 - 83.0[/COLOR]
        VertRefresh     56.0 - 75.0
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "r128"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

---

### Post by realzippy on 2010-12-11
> **sky5564 said:**
> LOL !!!!!!!

im about to break down and buy a new monitor..... i have posted this same question on numerous forums and NO ONE CAN FIGURE IT OUT !!!!!!!! :shock: [-o< :cry:


Common,this graphics card really reached EOL.....not the monitor's fault.See post #50.

---

### Post by sky5564 on 2010-12-11
> **realzippy said:**
> Common,this graphics card really reached EOL.....not the monitor's fault.See post #50.

i just figured it out.

had to manuall add hsync and vsnc lines under monitor in xorg



```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "record"
	Load  "extmod"
	Load  "glx"
	Load  "dbe"
	Load  "dri2"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        Horizsync 30.0-60.0
        VertRefresh 50.0-70.0
        Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
        
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "ForcePCIMode"       	# [<bool>]
        #Option     "CCEPIOMode"         	# [<bool>]
        #Option     "CCENoSecurity"      	# [<bool>]
        #Option     "CCEusecTimeout"     	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPSize"            	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "Display"            	# <str>
        #Option     "PanelWidth"         	# <i>
        #Option     "PanelHeight"        	# <i>
        #Option     "ProgramFPRegs"      	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "ShowCache"          	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
	Identifier  "Card0"
	Driver      "r128"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
        
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

now i have alot of resolutions to chose from and 1024x768 is working now but when i reboot it still hangs and dosent show the login screen so i have to ctrl alt f1 to go to the command line then enter ```
sudo gdm service stop
``` then ```
startx
``` to start the xserver wich then brings up my desktop lol for somereason i cant just type ```
startx
``` because it gives and error that the xserver is already running?????

o well i dont mind doing it that way just so long as its working.

---

### Post by realzippy on 2010-12-11
..Xorg.log file again?

---

### Post by sky5564 on 2010-12-11
> **realzippy said:**
> ..Xorg.log file again?

```
[    82.885] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    82.886] X Protocol Version 11, Revision 0
[    82.886] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    82.886] Current Operating System: Linux desktop 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686
[    82.886] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=6ebf1970-d1b3-4fa9-8267-3bdb0b60c951 ro quiet splash
[    82.887] Build Date: 16 September 2010  05:39:22PM
[    82.887] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    82.887] Current version of pixman: 0.18.4
[    82.887] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    82.887] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    82.889] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 11 11:28:30 2010
[    82.889] (==) Using config file: "/etc/X11/xorg.conf"
[    82.890] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    82.891] (==) ServerLayout "X.org Configured"
[    82.891] (**) |-->Screen "Screen0" (0)
[    82.891] (**) |   |-->Monitor "Monitor0"
[    82.892] (**) |   |-->Device "Card0"
[    82.892] (**) |-->Input Device "Mouse0"
[    82.892] (**) |-->Input Device "Keyboard0"
[    82.892] (==) Automatically adding devices
[    82.892] (==) Automatically enabling devices
[    82.892] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    82.892] 	Entry deleted from font path.
[    82.892] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    82.892] 	Entry deleted from font path.
[    82.893] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    82.893] (**) ModulePath set to "/usr/lib/xorg/modules"
[    82.893] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    82.893] (WW) Disabling Mouse0
[    82.893] (WW) Disabling Keyboard0
[    82.893] (II) Loader magic: 0x81f8e00
[    82.893] (II) Module ABI versions:
[    82.893] 	X.Org ANSI C Emulation: 0.4
[    82.893] 	X.Org Video Driver: 8.0
[    82.893] 	X.Org XInput driver : 11.0
[    82.893] 	X.Org Server Extension : 4.0
[    82.894] (--) PCI:*(0:1:0:0) 1002:5446:1002:0408 rev 0, Mem @ 0xf8000000/67108864, 0xff8fc000/16384, I/O @ 0x0000ec00/256, BIOS @ 0x????????/131072
[    82.896] (II) Open ACPI successful (/var/run/acpid.socket)
[    82.896] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    82.896] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    82.896] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    82.896] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    82.896] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    82.896] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    82.896] (II) LoadModule: "record"
[    82.897] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    82.898] (II) Module record: vendor="X.Org Foundation"
[    82.898] 	compiled for 1.9.0, module version = 1.13.0
[    82.898] 	Module class: X.Org Server Extension
[    82.898] 	ABI class: X.Org Server Extension, version 4.0
[    82.898] (II) Loading extension RECORD
[    82.898] (II) LoadModule: "extmod"
[    82.899] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    82.899] (II) Module extmod: vendor="X.Org Foundation"
[    82.899] 	compiled for 1.9.0, module version = 1.0.0
[    82.899] 	Module class: X.Org Server Extension
[    82.899] 	ABI class: X.Org Server Extension, version 4.0
[    82.899] (II) Loading extension MIT-SCREEN-SAVER
[    82.899] (II) Loading extension XFree86-VidModeExtension
[    82.899] (II) Loading extension XFree86-DGA
[    82.899] (II) Loading extension DPMS
[    82.900] (II) Loading extension XVideo
[    82.900] (II) Loading extension XVideo-MotionCompensation
[    82.900] (II) Loading extension X-Resource
[    82.900] (II) LoadModule: "glx"
[    82.900] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    82.901] (II) Module glx: vendor="X.Org Foundation"
[    82.901] 	compiled for 1.9.0, module version = 1.0.0
[    82.901] 	ABI class: X.Org Server Extension, version 4.0
[    82.901] (==) AIGLX enabled
[    82.901] (II) Loading extension GLX
[    82.901] (II) LoadModule: "dbe"
[    82.902] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    82.902] (II) Module dbe: vendor="X.Org Foundation"
[    82.902] 	compiled for 1.9.0, module version = 1.0.0
[    82.902] 	Module class: X.Org Server Extension
[    82.902] 	ABI class: X.Org Server Extension, version 4.0
[    82.902] (II) Loading extension DOUBLE-BUFFER
[    82.902] (II) LoadModule: "dri2"
[    82.903] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    82.904] (II) Module dri2: vendor="X.Org Foundation"
[    82.904] 	compiled for 1.9.0, module version = 1.2.0
[    82.904] 	ABI class: X.Org Server Extension, version 4.0
[    82.904] (II) Loading extension DRI2
[    82.904] (II) LoadModule: "dri"
[    82.905] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    82.906] (II) Module dri: vendor="X.Org Foundation"
[    82.906] 	compiled for 1.9.0, module version = 1.0.0
[    82.906] 	ABI class: X.Org Server Extension, version 4.0
[    82.906] (II) Loading extension XFree86-DRI
[    82.906] (II) LoadModule: "r128"
[    82.906] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    82.907] (II) Module r128: vendor="X.Org Foundation"
[    82.907] 	compiled for 1.8.99.905, module version = 6.8.1
[    82.907] 	Module class: X.Org Video Driver
[    82.907] 	ABI class: X.Org Video Driver, version 8.0
[    82.907] (II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
[    82.908] (--) using VT number 8

[    82.934] (II) R128(0): PCI bus 1 card 0 func 0
[    82.934] (==) R128(0): Depth 24, (--) framebuffer bpp 32
[    82.934] (II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    82.934] (==) R128(0): Default visual is TrueColor
[    82.934] (II) Loading sub module "vgahw"
[    82.934] (II) LoadModule: "vgahw"
[    82.935] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    82.936] (II) Module vgahw: vendor="X.Org Foundation"
[    82.936] 	compiled for 1.9.0, module version = 0.1.0
[    82.936] 	ABI class: X.Org Video Driver, version 8.0
[    82.936] (II) R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    82.936] (==) R128(0): RGB weight 888
[    82.936] (II) R128(0): Using 8 bits per RGB (8 bit DAC)
[    82.936] (II) Loading sub module "int10"
[    82.936] (II) LoadModule: "int10"
[    82.937] (II) Loading /usr/lib/xorg/modules/libint10.so
[    82.937] (II) Module int10: vendor="X.Org Foundation"
[    82.937] 	compiled for 1.9.0, module version = 1.0.0
[    82.937] 	ABI class: X.Org Video Driver, version 8.0
[    82.937] (II) R128(0): initializing int10
[    82.939] (II) R128(0): Primary V_BIOS segment is: 0xc000
[    82.939] (--) R128(0): Chipset: "ATI Rage 128 Pro ULTRA TF (AGP)" (ChipID = 0x5446)
[    82.939] (--) R128(0): Linear framebuffer at 0xf8000000
[    82.939] (--) R128(0): MMIO registers at 0xff8fc000
[    82.939] (--) R128(0): VideoRAM: 16384 kByte (128-bit SDR SGRAM 1:1)
[    82.939] (**) R128(0): Using external CRT for display
[    82.944] (II) R128(0): Primary Display == Type 3
[    82.944] (WW) R128(0): Can't determine panel dimensions, and none specified.
	Disabling programming of FP registers.
[    82.944] (II) R128(0): PLL parameters: rf=2950 rd=65 min=12500 max=35000; xclk=13000
[    82.944] (II) Loading sub module "ddc"
[    82.944] (II) LoadModule: "ddc"
[    82.944] (II) Module "ddc" already built-in
[    82.944] (II) Loading sub module "vbe"
[    82.944] (II) LoadModule: "vbe"
[    82.945] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    82.945] (II) Module vbe: vendor="X.Org Foundation"
[    82.945] 	compiled for 1.9.0, module version = 1.1.0
[    82.945] 	ABI class: X.Org Video Driver, version 8.0
[    82.946] (II) R128(0): VESA BIOS detected
[    82.946] (II) R128(0): VESA VBE Version 2.0
[    82.946] (II) R128(0): VESA VBE Total Mem: 16384 kB
[    82.946] (II) R128(0): VESA VBE OEM: ATI RAGE128
[    82.946] (II) R128(0): VESA VBE OEM Software Rev: 1.0
[    82.946] (II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
[    82.946] (II) R128(0): VESA VBE OEM Product: R128
[    82.946] (II) R128(0): VESA VBE OEM Product Rev: 01.00
[    82.946] (II) Loading sub module "ddc"
[    82.946] (II) LoadModule: "ddc"
[    82.946] (II) Module "ddc" already built-in
[    83.045] (II) R128(0): VESA VBE DDC supported
[    83.046] (II) R128(0): VESA VBE DDC Level none
[    83.046] (II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
[    83.139] (II) R128(0): VESA VBE DDC read failed
[    83.139] (==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
[    83.146] (II) Loading sub module "i2c"
[    83.146] (II) LoadModule: "i2c"
[    83.146] (II) Module "i2c" already built-in
[    83.146] (II) R128(0): I2C bus "DDC" initialized.
[    83.146] (II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
[    83.151] (EE) R128(0): No DFP detected
[    83.157] (II) R128(0): Monitor0: Using hsync range of 30.00-60.00 kHz
[    83.157] (II) R128(0): Monitor0: Using vrefresh range of 50.00-70.00 Hz
[    83.157] (WW) R128(0): Unable to estimate virtual size
[    83.157] (II) R128(0): Clock range:  12.50 to 350.00 MHz
[    83.157] (II) R128(0): Not using default mode "640x350" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "320x175" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "640x400" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "320x200" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "720x400" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "360x200" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "640x480" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "320x240" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "640x480" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "320x240" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "640x480" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "320x240" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "800x600" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "400x300" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "800x600" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "400x300" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "800x600" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "400x300" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "1024x768i" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "512x384i" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "1024x768" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "512x384" (vrefresh out of range)
[    83.157] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    83.157] (II) R128(0): Not using default mode "512x384" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1280x960" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "640x512" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "640x512" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "640x512" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1792x1344" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "896x672" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1792x1344" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "896x672" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1856x1392" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "928x696" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1856x1392" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "928x696" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1920x1440" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "960x720" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "1920x1440" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "960x720" (hsync out of range)
[    83.158] (II) R128(0): Not using default mode "832x624" (vrefresh out of range)
[    83.158] (II) R128(0): Not using default mode "416x312" (vrefresh out of range)
[    83.158] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    83.159] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1600x1024" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "800x512" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1920x1080" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "960x540" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1920x1200" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "960x600" (hsync out of range)
[    83.159] (II) R128(0): Not using default mode "1920x1440" (hsync out of range)
[    83.160] (II) R128(0): Not using default mode "960x720" (hsync out of range)
[    83.160] (II) R128(0): Not using default mode "2048x1536" (hsync out of range)
[    83.160] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    83.160] (II) R128(0): Not using default mode "2048x1536" (hsync out of range)
[    83.160] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    83.160] (II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    83.160] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    83.160] (--) R128(0): Virtual size is 1440x960 (pitch 1440)
[    83.160] (**) R128(0): *Default mode "1440x900": 106.5 MHz, 55.9 kHz, 59.9 Hz
[    83.160] (II) R128(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    83.160] (**) R128(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
[    83.160] (II) R128(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    83.161] (**) R128(0): *Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz
[    83.161] (II) R128(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    83.161] (**) R128(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
[    83.161] (II) R128(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    83.161] (**) R128(0): *Mode "1024x768_60.00": 64.1 MHz, 47.7 kHz, 60.0 Hz
[    83.161] (II) R128(0): Modeline "1024x768_60.00"x60.0   64.11  1024 1080 1184 1344  768 769 772 795 -hsync +vsync (47.7 kHz)
[    83.161] (**) R128(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[    83.161] (II) R128(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    83.161] (**) R128(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    83.161] (II) R128(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    83.161] (**) R128(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    83.161] (II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    83.161] (**) R128(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[    83.161] (II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    83.161] (**) R128(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
[    83.161] (II) R128(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
[    83.161] (**) R128(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
[    83.161] (II) R128(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
[    83.161] (**) R128(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    83.161] (II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    83.161] (**) R128(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
[    83.161] (II) R128(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
[    83.161] (**) R128(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
[    83.161] (II) R128(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
[    83.161] (**) R128(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
[    83.162] (II) R128(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
[    83.162] (**) R128(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
[    83.162] (II) R128(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
[    83.162] (**) R128(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
[    83.162] (II) R128(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
[    83.162] (**) R128(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
[    83.162] (II) R128(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
[    83.162] (**) R128(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
[    83.162] (II) R128(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
[    83.162] (**) R128(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
[    83.162] (II) R128(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
[    83.162] (==) R128(0): DPI set to (96, 96)
[    83.162] (II) Loading sub module "fb"
[    83.162] (II) LoadModule: "fb"
[    83.163] (II) Loading /usr/lib/xorg/modules/libfb.so
[    83.163] (II) Module fb: vendor="X.Org Foundation"
[    83.163] 	compiled for 1.9.0, module version = 1.0.0
[    83.163] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    83.164] (II) Loading sub module "ramdac"
[    83.164] (II) LoadModule: "ramdac"
[    83.164] (II) Module "ramdac" already built-in
[    83.164] (II) Loading sub module "xaa"
[    83.164] (II) LoadModule: "xaa"
[    83.164] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    83.165] (II) Module xaa: vendor="X.Org Foundation"
[    83.165] 	compiled for 1.9.0, module version = 1.2.1
[    83.165] 	ABI class: X.Org Video Driver, version 8.0
[    83.165] (II) Loading sub module "shadowfb"
[    83.165] (II) LoadModule: "shadowfb"
[    83.166] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    83.166] (II) Module shadowfb: vendor="X.Org Foundation"
[    83.166] 	compiled for 1.9.0, module version = 1.0.0
[    83.166] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    83.166] (II) R128(0): Page flipping disabled
[    83.166] (!!) R128(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
[    83.167] (--) Depth 24 pixmap format is 32 bpp
[    83.278] drmOpenDevice: node name is /dev/dri/card0
[    83.279] drmOpenDevice: open result is 11, (OK)
[    83.279] drmOpenDevice: node name is /dev/dri/card0
[    83.279] drmOpenDevice: open result is 11, (OK)
[    83.279] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    83.279] drmOpenDevice: node name is /dev/dri/card0
[    83.279] drmOpenDevice: open result is 11, (OK)
[    83.279] drmOpenByBusid: drmOpenMinor returns 11
[    83.279] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    83.279] (II) [drm] DRM interface version 1.3
[    83.279] (II) [drm] DRM open master succeeded.
[    83.279] (II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
[    83.280] (II) R128(0): [drm] framebuffer handle = 0xf8000000
[    83.280] (II) R128(0): [drm] added 1 reserved context for kernel
[    83.280] (II) R128(0): X context handle = 0x1
[    83.280] (II) R128(0): [drm] installed DRM signal handler
[    83.280] (II) R128(0): [agp] Mode 0x1f000211 [AGP 0x8086/0x1a30; Card 0x1002/0x5446]
[    83.306] (II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
[    83.307] (II) R128(0): [agp] ring handle = 0xf0000000
[    83.307] (II) R128(0): [agp] Ring mapped at 0xb75ed000
[    83.308] (II) R128(0): [agp] ring read ptr handle = 0xf0101000
[    83.308] (II) R128(0): [agp] Ring read ptr mapped at 0xb7702000
[    83.308] (II) R128(0): [agp] vertex/indirect buffers handle = 0xf0102000
[    83.308] (II) R128(0): [agp] Vertex/indirect buffers mapped at 0xb63a1000
[    83.308] (II) R128(0): [agp] AGP texture map handle = 0xf0302000
[    83.310] (II) R128(0): [agp] AGP Texture map mapped at 0xb5ec1000
[    83.310] (II) R128(0): [drm] register handle = 0xff8fc000
[    83.310] (II) R128(0): [dri] Visual configs initialized
[    83.311] (II) R128(0): CCE in BM mode
[    83.311] (II) R128(0): Using 8 MB AGP aperture
[    83.311] (II) R128(0): Using 1 MB for the ring buffer
[    83.311] (II) R128(0): Using 2 MB for vertex/indirect buffers
[    83.311] (II) R128(0): Using 5 MB for AGP textures
[    83.311] (II) R128(0): Memory manager initialized to (0,0) (1440,2912)
[    83.311] (II) R128(0): Reserved area from (0,960) to (1440,962)
[    83.311] (II) R128(0): Largest offscreen area available: 1440 x 1950
[    83.311] (II) R128(0): Reserved back buffer from (0,962) to (1440,1922)
[    83.311] (II) R128(0): Reserved depth buffer from (0,1922) to (1440,2883)
[    83.311] (II) R128(0): Reserved depth span from (0,2882) offset 0xfd4d00
[    83.311] (II) R128(0): Reserved 0 kb for textures at offset 0xfff000
[    83.311] (II) R128(0): Using XFree86 Acceleration Architecture (XAA)
[    83.311] 	Screen to screen bit blits
[    83.311] 	Solid filled rectangles
[    83.311] 	8x8 mono pattern filled rectangles
[    83.311] 	Indirect CPU to Screen color expansion
[    83.312] 	Solid Lines
[    83.312] 	Dashed Lines
[    83.312] 	Setting up tile and stipple cache:
[    83.312] 		12 32x29 slots
[    83.312] (II) R128(0): Acceleration enabled
[    83.312] (==) R128(0): Backing store disabled
[    83.312] (==) R128(0): Silken mouse enabled
[    83.312] (II) R128(0): Using hardware cursor (scanline 11532)
[    83.312] (II) R128(0): Largest offscreen area available: 1440 x 27
[    83.313] (==) R128(0): DPMS enabled
[    83.313] (II) R128(0): [DRI] installation complete
[    83.326] (II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
[    83.327] (II) R128(0): [drm] Mapped 128 vertex/indirect buffers
[    83.327] (II) R128(0): [drm] dma control initialized, using IRQ 16
[    83.327] (II) R128(0): Direct rendering enabled
[    83.327] (==) RandR enabled
[    83.327] (II) Initializing built-in extension Generic Event Extension
[    83.327] (II) Initializing built-in extension SHAPE
[    83.330] (II) Initializing built-in extension MIT-SHM
[    83.330] (II) Initializing built-in extension XInputExtension
[    83.330] (II) Initializing built-in extension XTEST
[    83.330] (II) Initializing built-in extension BIG-REQUESTS
[    83.330] (II) Initializing built-in extension SYNC
[    83.330] (II) Initializing built-in extension XKEYBOARD
[    83.330] (II) Initializing built-in extension XC-MISC
[    83.330] (II) Initializing built-in extension SECURITY
[    83.330] (II) Initializing built-in extension XINERAMA
[    83.330] (II) Initializing built-in extension XFIXES
[    83.330] (II) Initializing built-in extension RENDER
[    83.330] (II) Initializing built-in extension RANDR
[    83.330] (II) Initializing built-in extension COMPOSITE
[    83.330] (II) Initializing built-in extension DAMAGE
[    83.330] (II) Initializing built-in extension GESTURE
[    83.358] (II) AIGLX: Screen 0 is not DRI2 capable
[    83.358] drmOpenDevice: node name is /dev/dri/card0
[    83.358] drmOpenDevice: open result is 12, (OK)
[    83.358] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    83.358] drmOpenDevice: node name is /dev/dri/card0
[    83.358] drmOpenDevice: open result is 12, (OK)
[    83.359] drmOpenByBusid: drmOpenMinor returns 12
[    83.359] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    83.375] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    83.375] (II) AIGLX: Loaded and initialized /usr/lib/dri/r128_dri.so
[    83.375] (II) GLX: Initialized DRI GL provider for screen 0
[    83.474] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    83.583] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    83.583] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    83.583] (II) LoadModule: "evdev"
[    83.584] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    83.585] (II) Module evdev: vendor="X.Org Foundation"
[    83.585] 	compiled for 1.9.0, module version = 2.3.2
[    83.585] 	Module class: X.Org XInput Driver
[    83.585] 	ABI class: X.Org XInput driver, version 11.0
[    83.585] (**) Power Button: always reports core events
[    83.585] (**) Power Button: Device: "/dev/input/event1"
[    83.585] (II) Power Button: Found keys
[    83.585] (II) Power Button: Configuring as keyboard
[    83.585] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    83.585] (**) Option "xkb_rules" "evdev"
[    83.585] (**) Option "xkb_model" "pc105"
[    83.585] (**) Option "xkb_layout" "us"
[    83.588] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    83.588] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    83.588] (**) Power Button: always reports core events
[    83.588] (**) Power Button: Device: "/dev/input/event0"
[    83.588] (II) Power Button: Found keys
[    83.588] (II) Power Button: Configuring as keyboard
[    83.588] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    83.588] (**) Option "xkb_rules" "evdev"
[    83.589] (**) Option "xkb_model" "pc105"
[    83.589] (**) Option "xkb_layout" "us"
[    83.596] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    83.596] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    83.596] (**) Logitech USB Receiver: always reports core events
[    83.596] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    83.597] (II) Logitech USB Receiver: Found keys
[    83.597] (II) Logitech USB Receiver: Configuring as keyboard
[    83.597] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    83.597] (**) Option "xkb_rules" "evdev"
[    83.597] (**) Option "xkb_model" "pc105"
[    83.597] (**) Option "xkb_layout" "us"
[    83.599] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    83.599] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    83.599] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    83.599] (**) Logitech USB Receiver: always reports core events
[    83.599] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    83.599] (II) Logitech USB Receiver: Found 12 mouse buttons
[    83.599] (II) Logitech USB Receiver: Found scroll wheel(s)
[    83.599] (II) Logitech USB Receiver: Found relative axes
[    83.599] (II) Logitech USB Receiver: Found x and y relative axes
[    83.599] (II) Logitech USB Receiver: Found absolute axes
[    83.600] (II) evdev-grail: failed to open grail, no gesture support
[    83.600] (II) Logitech USB Receiver: Found keys
[    83.600] (II) Logitech USB Receiver: Configuring as mouse
[    83.600] (II) Logitech USB Receiver: Configuring as keyboard
[    83.600] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    83.600] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    83.600] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    83.600] (**) Option "xkb_rules" "evdev"
[    83.600] (**) Option "xkb_model" "pc105"
[    83.600] (**) Option "xkb_layout" "us"
[    83.601] (II) Logitech USB Receiver: initialized for relative axes.
[    83.601] (WW) Logitech USB Receiver: ignoring absolute axes.
[    83.602] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    83.602] (II) No input driver/identifier specified (ignoring)
```

it still says not using this and that blah blah but 1024x768 is working so thats all i care about.

---

### Post by jcinmd on 2010-12-24
Thanks, my screen is no longer 800 x 600! It's 1280 x 768.

I use a Matrox MGA G100 but I don't have the MB or revision # handy. I had the same probs & results as others on here. I don't care about super graphics so an older card is what I use. 

This is what eventually worked for me: I tried many suggestions found here over several late night sittings but the Horizsync and VertRefresh seemed to finally do it. I kept checking the desktop's GUI monitor settings and more options became ava as I tried more steps. I ran this instead of rebooting after each try:

	sudo /etc/init.d/gdm restart

Having no xorg.conf did nothing (except for my other old card that is an ATI R128P 73100 and it was intermittent...and that's another story still in process). This is the xorg.conf that worked:

# xorg.conf (X.Org X Window System server configuration file)
#
Section "Device"
	# for BusID I ran this U used #s at left of results: lspci | grep VGA
	Identifier "Card0"
	Driver "vesa" #card0driver
	VendorName "Matrox Graphics, Inc."
	BoardName "MGA G100 [Productiva] AGP"
	BusID "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier "Monitor0"
	VendorName "Monitor Vendor"
	ModelName "Monitor Model"
	# this didn't work, but when I tried the 2 under it that I got on this forum thread it worked
	#Horizsync 30.0-64.0
	#VertRefresh 50.0-100.0
	Horizsync 30.0-60.0
	VertRefresh 50.0-70.0
	# ran this to get the line below: gtf 1280 768 60
	Modeline "1280x768_60.00"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync
	# I also tried these and a command w/o the hz but dont know which worked
	# xrandr --newmode "1280x768_60.00"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync

	# xrandr --addmode default 1280x768_60.00

	# xrandr --output default --mode 1280x768_60.00
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Monitor0"
	Device		"Card0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by klimm01 on 2010-12-29
Hi Guys,

I do have also the prob with the low  resolution(max 800x600),the LCD panel should be able to manage 1024x768.  Tried to follow some threads concerning the xorg.conf (which is missing) but I just broke the system and due to missing experience in linux, needed reinstall 
I use an old HP 455 with triden Cyberblade/xp; here the infos  I could gather. No xorg.conf in X11 I didn't create one , because earlier following this way was not the right one. I'm actually coming from windows, try to learn but with this small screen is a real burden
Could someone help with a xorg.conf file that should work on my system?

lspci
00:00.0 Host bridge: ALi Corporation M1647 Northbridge [MAGiK 1 / MobileMAGiK 1] (rev 04)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:04.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
00:08.1 Communication controller: ESS Technology ESS Modem (rev 12)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:10.0 Ethernet controller: Accton Technology Corporation EN-1216 Ethernet Adapter (rev 11)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)
06:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)


 
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
Current Operating System: Linux xubi-laptop 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-27-generic root=UUID=9b3f9f1e-f3da-4e8e-8bb5-d879d838e254 ro quiet splash
Build Date: 10 November 2010  11:25:26AM
xorg-server 2:1.7.6-2ubuntu7.4  
Current version of pixman: 0.16.4
    Before reporting problems, check 
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 29 08:18:47 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f1b20
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1023:9910:103c:0018 Trident Microsystems CyberBlade/XP rev 99, Mem @ 0xee000000/33554432, 0xea400000/4194304, 0xec000000/33554432, 0xea100000/32768, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched trident as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "trident"
(II) Loading /usr/lib/xorg/modules/drivers/trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
    compiled for 1.7.2, module version = 1.3.3
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) TRIDENT: driver for Trident chipsets: tvga9000, tvga9000i, tvga8900c,
    tvga8900d, tvga9200cxr, tgui9400cxi, cyber9320, cyber9388, cyber9397,
    cyber9397dvd, cyber9520, cyber9525dvd, cyberblade/e4, tgui9420dgi,
    tgui9440agi, tgui9660, tgui9680, providia9682, providia9685,
    cyber9382, cyber9385, 3dimage975, 3dimage985, blade3d, cyberbladei7,
    cyberbladei7d, cyberbladei1, cyberbladei1d, cyberbladeAi1,
    cyberbladeAi1d, bladeXP, cyberbladeXPAi1, cyberbladeXP4, XP5
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for trident
(--) Assigning device section with no busID to primary device
(--) Chipset bladeXP found
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) TRIDENT(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) TRIDENT(0): Depth 24, (--) framebuffer bpp 32
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) TRIDENT(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) TRIDENT(0): RGB weight 888
(==) TRIDENT(0): Default visual is TrueColor
(==) TRIDENT(0): Using gamma correction (1.0, 1.0, 1.0)
(==) TRIDENT(0): Using XAA for acceleration
(==) TRIDENT(0): Linear framebuffer at 0xEE000000
(--) TRIDENT(0): IO registers at 0xEA400000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) TRIDENT(0): initializing int10
(II) TRIDENT(0): Primary V_BIOS segment is: 0xc000
(II) TRIDENT(0): VESA BIOS detected
(II) TRIDENT(0): VESA VBE Version 2.0
(II) TRIDENT(0): VESA VBE Total Mem: 8192 kB
(II) TRIDENT(0): VESA VBE OEM: Trident CYBER 9910
(II) TRIDENT(0): VESA VBE OEM Software Rev: 2.0
(II) TRIDENT(0): VESA VBE OEM Vendor: TRIDENT MICROSYSTEMS INC.
(II) TRIDENT(0): VESA VBE OEM Product: CYBER 9910
(II) TRIDENT(0): VESA VBE OEM Product Rev: NTC 7.0 (25.25)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) TRIDENT(0): VESA VBE DDC read failed
(--) TRIDENT(0): Revision is 99
(--) TRIDENT(0): Found CyberBladeXP chip
(--) TRIDENT(0): RAM type is SGRAM
(--) TRIDENT(0): Using HW cursor
(--) TRIDENT(0): VideoRAM: 8192 kByte
(--) TRIDENT(0): TFT Panel 1024x768 found
(--) TRIDENT(0): Memory Clock is 120.00 MHz
(==) TRIDENT(0): Min pixel clock is 12 MHz
(--) TRIDENT(0): Max pixel clock is 115 MHz
(II) TRIDENT(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
(II) TRIDENT(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
(WW) TRIDENT(0): Unable to estimate virtual size
(II) TRIDENT(0): Clock range:  12.00 to 115.00 MHz
(II) TRIDENT(0): Not using default mode "640x350" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x175" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x400" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x200" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "720x400" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "360x200" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x480" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x240" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x480" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x240" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x480" (hsync out of range)
(II) TRIDENT(0): Not using default mode "320x240" (hsync out of range)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "400x300" (hsync out of range)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "400x300" (hsync out of range)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "400x300" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1024x768" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "512x384" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "1024x768" (hsync out of range)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1024x768" (hsync out of range)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1024x768" (hsync out of range)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1024x768" (hsync out of range)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (1024x768 )
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Removing mode (1280x960) larger than the LCD panel (1024x768 )
(II) TRIDENT(0): Not using default mode "1280x960" (unknown reason)
(II) TRIDENT(0): Not using default mode "640x480" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x480" (hsync out of range)
(II) TRIDENT(0): Removing mode (1280x1024) larger than the LCD panel (1024x768 )
(II) TRIDENT(0): Not using default mode "1280x1024" (unknown reason)
(II) TRIDENT(0): Not using default mode "640x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "896x672" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "928x696" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "832x624" (hsync out of range)
(II) TRIDENT(0): Not using default mode "416x312" (hsync out of range)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (1024x768 )
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (1024x768 )
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (1024x768 )
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Removing mode (1360x768 )  larger than the LCD panel (1024x768 )
(II) TRIDENT(0): Not using default mode "1360x768" (unknown reason)
(II) TRIDENT(0): Not using default mode "680x384" (hsync out of range)
(II) TRIDENT(0): Removing mode (1360x768 ) larger than the LCD panel (1024x768 )
(II) TRIDENT(0): Not using default mode "1360x768" (unknown reason)
(II) TRIDENT(0): Not using default mode "680x384" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Removing mode (1440x900) larger than the LCD panel (1024x768 )
(II) TRIDENT(0): Not using default mode "1440x900" (unknown reason)
(II) TRIDENT(0): Not using default mode "720x450" (hsync out of range)
(II) TRIDENT(0): Removing mode (1600x1024) larger than the LCD panel (1024x768 )
(II) TRIDENT(0): Not using default mode "1600x1024" (unknown reason)
(II) TRIDENT(0): Not using default mode "800x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "840x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "840x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "840x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "840x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "840x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1920x1080" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "960x540" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "960x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) TRIDENT(0): Virtual size is 800x600 (pitch 800)
(**) TRIDENT(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) TRIDENT(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) TRIDENT(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) TRIDENT(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) TRIDENT(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) TRIDENT(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) TRIDENT(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) TRIDENT(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) TRIDENT(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) TRIDENT(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) TRIDENT(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) TRIDENT(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) TRIDENT(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.1
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) TRIDENT(0): Initializing int10
(II) TRIDENT(0): Primary V_BIOS segment is: 0xc000
(II) TRIDENT(0): Overriding Horizontal timings.
(II) TRIDENT(0): Shadow on
(II) TRIDENT(0): H-timing shadow registers: 0xa3           0x00 0x84 0x94
(II) TRIDENT(0): H-timing registers:        0x7f 0x63 0x63 0x82 0x69 0x19
(II) TRIDENT(0): V-timing shadow registers: 0x24 0xf5 0x03 0x09           0x24 (0x0)

(II) TRIDENT(0): V-timing registers:        0x72 0xf0 0x59 0x2d 0x57 0x00 0x00
(II) TRIDENT(0): Setting BIOS Mode Regs: 13 62 for: 800x600
(II) TRIDENT(0): Found Clock  65.00 n=219 m=23 k=1
(II) TRIDENT(0): Using 1447 scanlines of offscreen memory for area's 
(II) TRIDENT(0): Using 1838208 bytes of offscreen memory for linear (offset=0x63f380)
(II) TRIDENT(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Solid Horizontal and Vertical Lines
    Setting up tile and stipple cache:
        32 128x128 slots
        8 256x256 slots
(==) TRIDENT(0): Backing store disabled
(==) TRIDENT(0): Silken mouse enabled
(==) TRIDENT(0): DPMS enabled
(II) TRIDENT(0): Trident Video Flags: VID_ZOOM_INV  VID_OFF_SHIFT_4 
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event1)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event5"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

```

Thanks

---

### Post by klimm01 on 2011-01-09
Ok, thanks for not helping was maybe better so.I needed to work on the command line; good exercise.
As averyone I generated my own xorg.conf.new tried to bring it working no result. Tried another thread about the issue,  with a bit different settings didn't work
At least I found a thread about the fact that the .xinitrc may be missing from the home directory and should be copied into it the content from  /etc/X11/xinit/xinitrc.
after doing so, the test worked and copying the xorg.conf.new to the etc/X11/xorg.conf, works by boot

As one of the guys in the forums said, :D I success!

hope this will also help someone

---

### Post by trovador on 2011-01-29
> **realzippy said:**
> Forget it for the moment...anyway,if xrandr had work,you had to make it permanent,means,put the xrandr command in autostart or create a script that runs it.
The correct solution would be to set up an xorg.conf file with your resolution;could be done by Xorg -configure (little pain,because it includes the whole bunch of possible configuration options);so it might be worth to try an existing xorg.conf file from the web.
Found this xorg.conf e.g. :

```
Section "Monitor"
    Identifier    "Configured Monitor"
      Option      "DPMS"  "true"
      HorizSync    30.0-60.0
      VertRefresh  50.0-70.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
      DefaultDepth      24
      SubSection "Display"
                  Depth         24
                  Modes         "1024x768" "800x600"
      EndSubSection
      
EndSection
```


First,check out if there is a existing xorg.conf,guess not.Type
```
gksudo gedit /etc/X11/xorg.conf
```

If an existing file opens,post it's content.If an empty file opens,paste the content from the example given into it and save the file closing.
Restart X or reboot.If you get a black screen,unable to start X,you had to boot in recovery mode,drop to root shell, (make sure you know how to do) and delete the created file with (write this down):

```
rm /etc/X11/xorg.conf
reboot
```

Hi,
I,ve a similar problem and I want to solve it
at first I've xubuntu 10.10 and the old graphic dev
> trovador@trovador-S1800-314:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)
trovador@trovador-S1800-314:~$ 
I've already tried different ways I list in order the steps that I've done
**1-**> trovador@trovador-S1800-314:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 800 x 600, **maximum 800 x 600**
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
  1024x768_60.00 (0x10f)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz
trovador@trovador-S1800-314:~$ 

**2-**> trovador@trovador-S1800-314:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
trovador@trovador-S1800-314:~$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr: Failed to get size of gamma for output default
trovador@trovador-S1800-314:~$ xrandr --addmode default 1024x768_60.00
xrandr: Failed to get size of gamma for output default
trovador@trovador-S1800-314:~$ xrandr --output default --mode 1024x768
xrandr: cannot find mode 1024x768
trovador@trovador-S1800-314:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 800 x 600,** maximum 1024 x 768**
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
   1024x768_60.00   59.9  
trovador@trovador-S1800-314:~$ 

As you can see after "CVT" the Screen maximum could be 1024x768
Does it mean something ?
I'd like to set up an xorg.conf file ,but I'm worried about it, as you say above.
I've this file
> trovador@trovador-S1800-314:~$ cat /usr/share/doc/xserver-xorg-video-nouveau/examples/xorg.conf
# Minimal xorg.conf for the Nouveau driver

Section "Device"
	Identifier	"Default screen"
      	Driver		"nouveau"
EndSection
trovador@trovador-S1800-314:~$ 

What do think if I delete this and paste yours in it ?
I looking forward to have news
Many thanks
ps I'm not English speakers sorry for the language.

---

### Post by nishdo on 2011-01-31
Hi, for those who see or are getting this error from xrandr:
xrandr: Failed to get size of gamma for output default

One more check, which was annoyingly obvious afterwards, but still spent an hour until I remembered. I solved this in my system by remembering one change I'd made before reinstalling Ubuntu 10.10. Having got a second computer in the meantime, I'd added a KVM switch to manage both machines with one monitor. 

So, when reinstalling Ubuntu, whatever this KVM switch was doing, it was blocking Ubuntu in detecting my monitor. All I got was minimum resolution all the time. Doh! 

By removing the KVM for the purposes of the installation, connecting the monitor directly, that error went away easy, detect monitor worked fine. Now back to nVidia drivers and 3D.

---

### Post by perspectoff on 2011-01-31
I know I'm late to the party. The last version of (K)Ubuntu in which I used xRandR was Karmic. I stopped using XRandR as of Lucid.

My nVidia card drivers now have their own settings module (for screen size and resolution, etc.), and I change it directly using that. Do the ATI graphics drivers (perhaps the proprietary ones) not have a similar type of settings module?

---

### Post by wweeks on 2011-03-01
Bump. I have the same problem. Did anyone find a solution?

---

### Post by santa_klaus on 2011-03-04
Hi there, I got a different bot somehow related problem. I´m setting up Ubuntu 10.10 on a Fujitsu AMILO Pro V2030 laptop.
The screen resolution i get is far to high (1600x1200) for the screen, so the lower and right part of the screen are not visible. From what I understand the resolution should be 1024x768.

I already tried some things. Setting up new modes with Xrandr always gives me errormessages like "failed to get size of gamma for output default" and "configure crtc 0 failed".
Then I created a xorg.conf (which previously not existed) with some minimal information which at least added an extra resolution option in the GNOME display manager. tried it out and looked like the frequency was bad.

The graphic-chip is VIA VN800 Chipsatz, UniChrome Pro 3D/2D. It should be running with the openchrome driver...

Here is my xorg.0.log file:

```


[LIST=1]
[*][    18.657] 
[*]X.Org X Server 1.9.0
[*]Release Date: 2010-08-20
[*][    18.657] X Protocol Version 11, Revision 0
[*][    18.657] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[*][    18.657] Current Operating System: Linux Johanna 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[*][    18.657] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic  root=UUID=bf9bf0ab-1419-4992-bf74-8d83626d98b7 ro quiet splash
[*][    18.657] Build Date: 16 September 2010  05:39:22PM
[*][    18.657] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[*][    18.657] Current version of pixman: 0.18.4
[*][    18.657]    Before reporting problems, check http://wiki.x.org
[*]        to make sure that you have the latest version.
[*][    18.657] Markers: (--) probed, (**) from config file, (==) default setting,
[*]        (++) from command line, (!!) notice, (II) informational,
[*]        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[*][    18.657] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  4 08:08:23 2011
[*][    18.671] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[*][    18.672] (==) No Layout section.  Using the first Screen section.
[*][    18.672] (==) No screen section available. Using defaults.
[*][    18.672] (**) |-->Screen "Default Screen Section" (0)
[*][    18.672] (**) |   |-->Monitor "<default monitor>"
[*][    18.672] (==) No monitor specified for screen "Default Screen Section".
[*]        Using a default monitor configuration.
[*][    18.672] (==) Automatically adding devices
[*][    18.672] (==) Automatically enabling devices
[*][    18.672] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[*][    18.672]    Entry deleted from font path.
[*][    18.672] (==) FontPath set to:
[*]        /usr/share/fonts/X11/misc,
[*]        /usr/share/fonts/X11/100dpi/:unscaled,
[*]        /usr/share/fonts/X11/75dpi/:unscaled,
[*]        /usr/share/fonts/X11/Type1,
[*]        /usr/share/fonts/X11/100dpi,
[*]        /usr/share/fonts/X11/75dpi,
[*]        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
[*]        built-ins
[*][    18.672] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[*][    18.672] (II) The server relies on udev to provide the list of input devices.
[*]        If no devices become available, reconfigure udev or disable AutoAddDevices.
[*][    18.672] (II) Loader magic: 0x81f8e00
[*][    18.672] (II) Module ABI versions:
[*][    18.672]    X.Org ANSI C Emulation: 0.4
[*][    18.672]    X.Org Video Driver: 8.0
[*][    18.672]    X.Org XInput driver : 11.0
[*][    18.672]    X.Org Server Extension : 4.0
[*][    18.674] (--) PCI:*(0:1:0:0) 1106:3344:1734:109b rev 1, Mem @ 0xf0000000/67108864, 0xd1000000/16777216
[*][    18.674] (II) Open ACPI successful (/var/run/acpid.socket)
[*][    18.674] (II) LoadModule: "extmod"
[*][    18.687] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[*][    18.687] (II) Module extmod: vendor="X.Org Foundation"
[*][    18.687]    compiled for 1.9.0, module version = 1.0.0
[*][    18.687]    Module class: X.Org Server Extension
[*][    18.687]    ABI class: X.Org Server Extension, version 4.0
[*][    18.687] (II) Loading extension MIT-SCREEN-SAVER
[*][    18.687] (II) Loading extension XFree86-VidModeExtension
[*][    18.687] (II) Loading extension XFree86-DGA
[*][    18.687] (II) Loading extension DPMS
[*][    18.687] (II) Loading extension XVideo
[*][    18.687] (II) Loading extension XVideo-MotionCompensation
[*][    18.687] (II) Loading extension X-Resource
[*][    18.687] (II) LoadModule: "dbe"
[*][    18.688] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[*][    18.688] (II) Module dbe: vendor="X.Org Foundation"
[*][    18.688]    compiled for 1.9.0, module version = 1.0.0
[*][    18.688]    Module class: X.Org Server Extension
[*][    18.688]    ABI class: X.Org Server Extension, version 4.0
[*][    18.688] (II) Loading extension DOUBLE-BUFFER
[*][    18.688] (II) LoadModule: "glx"
[*][    18.688] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[*][    18.688] (II) Module glx: vendor="X.Org Foundation"
[*][    18.688]    compiled for 1.9.0, module version = 1.0.0
[*][    18.688]    ABI class: X.Org Server Extension, version 4.0
[*][    18.688] (==) AIGLX enabled
[*][    18.688] (II) Loading extension GLX
[*][    18.688] (II) LoadModule: "record"
[*][    18.689] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[*][    18.689] (II) Module record: vendor="X.Org Foundation"
[*][    18.689]    compiled for 1.9.0, module version = 1.13.0
[*][    18.689]    Module class: X.Org Server Extension
[*][    18.689]    ABI class: X.Org Server Extension, version 4.0
[*][    18.689] (II) Loading extension RECORD
[*][    18.689] (II) LoadModule: "dri"
[*][    18.689] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[*][    18.689] (II) Module dri: vendor="X.Org Foundation"
[*][    18.689]    compiled for 1.9.0, module version = 1.0.0
[*][    18.689]    ABI class: X.Org Server Extension, version 4.0
[*][    18.690] (II) Loading extension XFree86-DRI
[*][    18.690] (II) LoadModule: "dri2"
[*][    18.690] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[*][    18.690] (II) Module dri2: vendor="X.Org Foundation"
[*][    18.690]    compiled for 1.9.0, module version = 1.2.0
[*][    18.690]    ABI class: X.Org Server Extension, version 4.0
[*][    18.690] (II) Loading extension DRI2
[*][    18.690] (==) Matched openchrome as autoconfigured driver 0
[*][    18.690] (==) Matched vesa as autoconfigured driver 1
[*][    18.690] (==) Matched fbdev as autoconfigured driver 2
[*][    18.690] (==) Assigned the driver to the xf86ConfigLayout
[*][    18.690] (II) LoadModule: "openchrome"
[*][    18.690] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[*][    18.691] (II) Module openchrome: vendor="http://openchrome.org/"
[*][    18.691]    compiled for 1.8.99.905, module version = 0.2.904
[*][    18.691]    Module class: X.Org Video Driver
[*][    18.691]    ABI class: X.Org Video Driver, version 8.0
[*][    18.691] (II) LoadModule: "vesa"
[*][    18.691] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[*][    18.691] (II) Module vesa: vendor="X.Org Foundation"
[*][    18.691]    compiled for 1.8.99.905, module version = 2.3.0
[*][    18.691]    Module class: X.Org Video Driver
[*][    18.691]    ABI class: X.Org Video Driver, version 8.0
[*][    18.691] (II) LoadModule: "fbdev"
[*][    18.691] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[*][    18.691] (II) Module fbdev: vendor="X.Org Foundation"
[*][    18.691]    compiled for 1.8.99.905, module version = 0.4.2
[*][    18.692]    ABI class: X.Org Video Driver, version 8.0
[*][    18.692] (II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
[*]        K8M800/K8N800, PM800/PM880/CN400, VM800/P4M800Pro/VN800/CN700,
[*]        K8M890/K8N890, P4M900/VN896/CN896, CX700/VX700, P4M890, VX800/VX820,
[*]        VX855/VX875
[*][    18.692] (II) VESA: driver for VESA chipsets: vesa
[*][    18.692] (II) FBDEV: driver for framebuffer: fbdev
[*][    18.692] (++) using VT number 7
[*] 
[*][    18.693] (!!) VIA Technologies does not support this driver in any way.
[*][    18.693] (!!) For support, please refer to http://www.openchrome.org/.
[*][    18.693] (!!) (development build, compiled on Tue 10 Aug 2010 10:07:16 EST)
[*][    18.693] (WW) Falling back to old probe method for vesa
[*][    18.693] (WW) Falling back to old probe method for fbdev
[*][    18.693] (II) Loading sub module "fbdevhw"
[*][    18.693] (II) LoadModule: "fbdevhw"
[*][    18.712] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[*][    18.712] (II) Module fbdevhw: vendor="X.Org Foundation"
[*][    18.712]    compiled for 1.9.0, module version = 0.0.2
[*][    18.712]    ABI class: X.Org Video Driver, version 8.0
[*][    18.712] (EE) open /dev/fb0: No such file or directory
[*][    18.713] (II) CHROME(0): VIAPreInit
[*][    18.713] (II) Loading sub module "vgahw"
[*][    18.713] (II) LoadModule: "vgahw"
[*][    18.713] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[*][    18.713] (II) Module vgahw: vendor="X.Org Foundation"
[*][    18.713]    compiled for 1.9.0, module version = 0.1.0
[*][    18.713]    ABI class: X.Org Video Driver, version 8.0
[*][    18.713] (II) CHROME(0): VIAGetRec
[*][    18.713] (II) CHROME(0): Creating default Display subsection in Screen section
[*]        "Default Screen Section" for depth/fbbpp 24/32
[*][    18.713] (==) CHROME(0): Depth 24, (--) framebuffer bpp 32
[*][    18.713] (==) CHROME(0): RGB weight 888
[*][    18.713] (==) CHROME(0): Default visual is TrueColor
[*][    18.713] (--) CHROME(0): Chipset: VM800/P4M800Pro/VN800/CN700
[*][    18.713] (--) CHROME(0): Chipset revision: 0
[*][    18.713] (--) CHROME(0): Probed amount of VideoRAM = 65536 kB
[*][    18.713] (II) CHROME(0): VIASetupDefaultOptions - Setting up default chipset options.
[*][    18.713] (==) CHROME(0): Shadow framebuffer is disabled.
[*][    18.713] (==) CHROME(0): Hardware acceleration is enabled.
[*][    18.713] (==) CHROME(0): Using XAA acceleration architecture.
[*][    18.713] (==) CHROME(0): Using hardware two-color cursors and software full-color cursors.
[*][    18.713] (==) CHROME(0): GPU virtual command queue will be enabled.
[*][    18.713] (==) CHROME(0): DRI IRQ will be enabled if DRI is enabled.
[*][    18.713] (==) CHROME(0): AGP DMA will be enabled if DRI is enabled.
[*][    18.713] (==) CHROME(0): AGP DMA will be used for 2D acceleration.
[*][    18.713] (==) CHROME(0): PCI DMA will be used for XV image transfer if DRI is enabled.
[*][    18.713] (==) CHROME(0): Will not enable VBE modes.
[*][    18.713] (==) CHROME(0): VBE VGA register save & restore will not be used
[*]        if VBE modes are enabled.
[*][    18.713] (==) CHROME(0): Xv Bandwidth check is enabled.
[*][    18.713] (==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
[*][    18.713] (==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
[*][    18.713] (==) CHROME(0): Digital output bus width is 12 bits.
[*][    18.713] (==) CHROME(0): DVI Center is disabled.
[*][    18.713] (==) CHROME(0): Panel size is not selected from config file.
[*][    18.713] (==) CHROME(0): Panel will not be forced.
[*][    18.713] (==) CHROME(0): TV dotCrawl is disabled.
[*][    18.714] (==) CHROME(0): TV deflicker is set to 0.
[*][    18.714] (==) CHROME(0): No default TV type is set.
[*][    18.714] (==) CHROME(0): No default TV output signal type is set.
[*][    18.714] (==) CHROME(0): No default TV output port is set.
[*][    18.714] (II) CHROME(0): VIAMapMMIO
[*][    18.714] (--) CHROME(0): mapping MMIO @ 0xd1000000 with size 0x9000
[*][    18.714] (--) CHROME(0): mapping BitBlt MMIO @ 0xd1200000 with size 0x200000
[*][    18.714] (II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[*][    18.714] (==) CHROME(0): Will not print VGA registers.
[*][    18.714] (==) CHROME(0): Will not scan I2C buses.
[*][    18.714] (II) CHROME(0): ...Finished parsing config file options.
[*][    18.714] (--) CHROME(0): Detected Fujitsu/Siemens Amilo Pro V2030. Card-Ids (1734|109B)
[*][    18.714] (II) CHROME(0): Detected MemClk 3
[*][    18.714] (II) CHROME(0): ViaGetMemoryBandwidth. Memory type: 3
[*][    18.714] (II) CHROME(0): Detected TV standard: PAL.
[*][    18.714] (==) CHROME(0): Using gamma correction (1.0, 1.0, 1.0)
[*][    18.714] (II) Loading sub module "i2c"
[*][    18.714] (II) LoadModule: "i2c"
[*][    18.714] (II) Module "i2c" already built-in
[*][    18.714] (II) CHROME(0): ViaI2CInit
[*][    18.714] (II) CHROME(0): ViaI2CBus1Init
[*][    18.714] (II) CHROME(0): I2C bus "I2C bus 1" initialized.
[*][    18.714] (II) CHROME(0): ViaI2cBus2Init
[*][    18.714] (II) CHROME(0): I2C bus "I2C bus 2" initialized.
[*][    18.714] (II) CHROME(0): ViaI2CBus3Init
[*][    18.714] (II) CHROME(0): I2C bus "I2C bus 3" initialized.
[*][    18.714] (II) Loading sub module "ddc"
[*][    18.714] (II) LoadModule: "ddc"
[*][    18.714] (II) Module "ddc" already built-in
[*][    18.714] (II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
[*][    18.719] (II) CHROME(0): ViaOutputsDetect
[*][    18.719] (II) CHROME(0): Enabling panel from PCI-subsystem ID information.
[*][    18.719] (II) CHROME(0): VIATVDetect
[*][    18.720] (II) CHROME(0): ViaOutputsSelect
[*][    18.720] (II) CHROME(0): ViaOutputsSelect: X Configuration: 0x00
[*][    18.720] (II) CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x07
[*][    18.720] (II) CHROME(0): ViaOutputsSelect: Panel.
[*][    18.720] (II) CHROME(0): ViaPanelPreInit
[*][    18.720] (II) CHROME(0): VIAGetPanelSizeFromDDCv1
[*][    18.721] (II) CHROME(0): I2C device "I2C bus 2:ddc2" registered at address 0xA0.
[*][    18.775] (II) CHROME(0): Manufacturer: SEC  Model: 4944  Serial#: 0
[*][    18.775] (II) CHROME(0): Year: 2005  Week: 0
[*][    18.775] (II) CHROME(0): EDID Version: 1.3
[*][    18.775] (II) CHROME(0): Digital Display Input
[*][    18.775] (II) CHROME(0): Max Image Size [cm]: horiz.: 31  vert.: 23
[*][    18.775] (II) CHROME(0): Gamma: 2.20
[*][    18.775] (II) CHROME(0): No DPMS capabilities specified
[*][    18.775] (II) CHROME(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[*][    18.775] (II) CHROME(0): First detailed timing is preferred mode
[*][    18.775] (II) CHROME(0): redX: 0.589 redY: 0.337   greenX: 0.322 greenY: 0.524
[*][    18.775] (II) CHROME(0): blueX: 0.152 blueY: 0.137   whiteX: 0.315 whiteY: 0.330
[*][    18.775] (II) CHROME(0): Manufacturer's mask: 0
[*][    18.775] (II) CHROME(0): Supported detailed timing:
[*][    18.775] (II) CHROME(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
[*][    18.775] (II) CHROME(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[*][    18.775] (II) CHROME(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[*][    18.775] (II) CHROME(0): Unknown vendor-specific block f
[*][    18.775] (II) CHROME(0):  SAMSUNG
[*][    18.775] (II) CHROME(0):  LTN150XG-L05
[*][    18.775] (II) CHROME(0): EDID (in hex):
[*][    18.775] (II) CHROME(0):    00ffffffffffff004ca3444900000000
[*][    18.775] (II) CHROME(0):    000f0103801f17780ad90e9656528627
[*][    18.775] (II) CHROME(0):    23505400000001010101010101010101
[*][    18.775] (II) CHROME(0):    01010101010164190040410026301888
[*][    18.775] (II) CHROME(0):    360030e4100000190000000f00047e18
[*][    18.775] (II) CHROME(0):    ff0105026f18ff027400000000fe0053
[*][    18.775] (II) CHROME(0):    414d53554e470a2020202020000000fe
[*][    18.775] (II) CHROME(0):    004c544e31353058472d4c30350a00b4
[*][    18.775] (II) CHROME(0): EDID vendor "SEC", prod id 18756
[*][    18.775] (II) CHROME(0): Printing DDC gathered Modelines:
[*][    18.775] (II) CHROME(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[*][    18.775] (II) CHROME(0): VIAGetPanelSizeFromEDID
[*][    18.775] (II) CHROME(0): VIAGetPanelSizeFromDDCv1: (1024x768)
[*][    18.775] (II) CHROME(0): ViaPanelLookUpModeIndex, Width 1024, Height 768, NativeModeIndex2
[*][    18.775] (II) CHROME(0): ViaPanelGetNativeDisplayMode
[*][    18.775] (II) CHROME(0): NativeModeIndex: 2
[*][    18.775] (WW) CHROME(0): Panel on K8M800 and VM800 is currently not supported.
[*][    18.775] (WW) CHROME(0): Using VBE to set modes to work around this.
[*][    18.775] (II) Loading sub module "int10"
[*][    18.775] (II) LoadModule: "int10"
[*][    18.776] (II) Loading /usr/lib/xorg/modules/libint10.so
[*][    18.776] (II) Module int10: vendor="X.Org Foundation"
[*][    18.776]    compiled for 1.9.0, module version = 1.0.0
[*][    18.776]    ABI class: X.Org Video Driver, version 8.0
[*][    18.776] (II) Loading sub module "vbe"
[*][    18.776] (II) LoadModule: "vbe"
[*][    18.776] (II) Loading /usr/lib/xorg/modules/libvbe.so
[*][    18.777] (II) Module vbe: vendor="X.Org Foundation"
[*][    18.777]    compiled for 1.9.0, module version = 1.1.0
[*][    18.777]    ABI class: X.Org Video Driver, version 8.0
[*][    18.777] (II) Loading sub module "int10"
[*][    18.777] (II) LoadModule: "int10"
[*][    18.777] (II) Reloading /usr/lib/xorg/modules/libint10.so
[*][    18.777] (II) CHROME(0): initializing int10
[*][    18.783] (II) CHROME(0): Primary V_BIOS segment is: 0xc000
[*][    18.784] (II) CHROME(0): VESA BIOS detected
[*][    18.784] (II) CHROME(0): VESA VBE Version 3.0
[*][    18.784] (II) CHROME(0): VESA VBE Total Mem: 65536 kB
[*][    18.784] (II) CHROME(0): VESA VBE OEM: VIA P4N800 PRO
[*] 
[*] 
[*][    18.784] (II) CHROME(0): VESA VBE OEM Software Rev: 1.0
[*][    18.784] (II) CHROME(0): VESA VBE OEM Vendor: 
[*][    18.784] (II) CHROME(0): VESA VBE OEM Product: 
[*][    18.784] (II) CHROME(0): VESA VBE OEM Product Rev: 
[*][    18.784] (II) CHROME(0): Searching for matching VESA mode(s):
[*][    18.785] Mode: 101 (640x480)
[*][    18.786]    ModeAttributes: 0x9f
[*][    18.786]    WinAAttributes: 0x7
[*][    18.786]    WinBAttributes: 0x0
[*][    18.786]    WinGranularity: 64
[*][    18.786]    WinSize: 64
[*][    18.786]    WinASegment: 0xa000
[*][    18.786]    WinBSegment: 0xa000
[*][    18.786]    WinFuncPtr: 0xc000a833
[*][    18.786]    BytesPerScanline: 640
[*][    18.786]    XResolution: 640
[*][    18.786]    YResolution: 480
[*][    18.786]    XCharSize: 8
[*][    18.786]    YCharSize: 16
[*][    18.786]    NumberOfPlanes: 1
[*][    18.786]    BitsPerPixel: 8
[*][    18.786]    NumberOfBanks: 1
[*][    18.786]    MemoryModel: 4
[*][    18.786]    BankSize: 0
[*][    18.786]    NumberOfImages: 203
[*][    18.786]    RedMaskSize: 0
[*][    18.786]    RedFieldPosition: 0
[*][    18.786]    GreenMaskSize: 0
[*][    18.786]    GreenFieldPosition: 0
[*][    18.786]    BlueMaskSize: 0
[*][    18.786]    BlueFieldPosition: 0
[*][    18.786]    RsvdMaskSize: 0
[*][    18.786]    RsvdFieldPosition: 0
[*][    18.786]    DirectColorModeInfo: 2
[*][    18.786]    PhysBasePtr: 0xf0000000
[*][    18.786]    LinBytesPerScanLine: 640
[*][    18.786]    BnkNumberOfImagePages: 203
[*][    18.786]    LinNumberOfImagePages: 203
[*][    18.786]    LinRedMaskSize: 0
[*][    18.786]    LinRedFieldPosition: 0
[*][    18.786]    LinGreenMaskSize: 0
[*][    18.786]    LinGreenFieldPosition: 0
[*][    18.786]    LinBlueMaskSize: 0
[*][    18.786]    LinBlueFieldPosition: 0
[*][    18.786]    LinRsvdMaskSize: 0
[*][    18.786]    LinRsvdFieldPosition: 0
[*][    18.786]    MaxPixelClock: 0
[*][    18.787] Mode: 111 (640x480)
[*][    18.787]    ModeAttributes: 0x9b
[*][    18.787]    WinAAttributes: 0x7
[*][    18.787]    WinBAttributes: 0x0
[*][    18.787]    WinGranularity: 64
[*][    18.787]    WinSize: 64
[*][    18.787]    WinASegment: 0xa000
[*][    18.787]    WinBSegment: 0xa000
[*][    18.787]    WinFuncPtr: 0xc000a833
[*][    18.787]    BytesPerScanline: 1280
[*][    18.787]    XResolution: 640
[*][    18.787]    YResolution: 480
[*][    18.787]    XCharSize: 8
[*][    18.787]    YCharSize: 16
[*][    18.787]    NumberOfPlanes: 1
[*][    18.787]    BitsPerPixel: 16
[*][    18.787]    NumberOfBanks: 1
[*][    18.787]    MemoryModel: 6
[*][    18.787]    BankSize: 0
[*][    18.787]    NumberOfImages: 101
[*][    18.787]    RedMaskSize: 5
[*][    18.787]    RedFieldPosition: 11
[*][    18.787]    GreenMaskSize: 6
[*][    18.787]    GreenFieldPosition: 5
[*][    18.787]    BlueMaskSize: 5
[*][    18.787]    BlueFieldPosition: 0
[*][    18.787]    RsvdMaskSize: 0
[*][    18.787]    RsvdFieldPosition: 0
[*][    18.787]    DirectColorModeInfo: 2
[*][    18.787]    PhysBasePtr: 0xf0000000
[*][    18.787]    LinBytesPerScanLine: 1280
[*][    18.787]    BnkNumberOfImagePages: 101
[*][    18.787]    LinNumberOfImagePages: 101
[*][    18.787]    LinRedMaskSize: 5
[*][    18.787]    LinRedFieldPosition: 11
[*][    18.787]    LinGreenMaskSize: 6
[*][    18.787]    LinGreenFieldPosition: 5
[*][    18.787]    LinBlueMaskSize: 5
[*][    18.787]    LinBlueFieldPosition: 0
[*][    18.787]    LinRsvdMaskSize: 0
[*][    18.787]    LinRsvdFieldPosition: 0
[*][    18.787]    MaxPixelClock: 0
[*][    18.788] *Mode: 112 (640x480)
[*][    18.788]    ModeAttributes: 0x9b
[*][    18.788]    WinAAttributes: 0x7
[*][    18.788]    WinBAttributes: 0x0
[*][    18.789]    WinGranularity: 64
[*][    18.789]    WinSize: 64
[*][    18.789]    WinASegment: 0xa000
[*][    18.789]    WinBSegment: 0xa000
[*][    18.789]    WinFuncPtr: 0xc000a833
[*][    18.789]    BytesPerScanline: 2560
[*][    18.789]    XResolution: 640
[*][    18.789]    YResolution: 480
[*][    18.789]    XCharSize: 8
[*][    18.789]    YCharSize: 16
[*][    18.789]    NumberOfPlanes: 1
[*][    18.789]    BitsPerPixel: 32
[*][    18.789]    NumberOfBanks: 1
[*][    18.789]    MemoryModel: 6
[*][    18.789]    BankSize: 0
[*][    18.789]    NumberOfImages: 50
[*][    18.789]    RedMaskSize: 8
[*][    18.789]    RedFieldPosition: 16
[*][    18.789]    GreenMaskSize: 8
[*][    18.789]    GreenFieldPosition: 8
[*][    18.789]    BlueMaskSize: 8
[*][    18.789]    BlueFieldPosition: 0
[*][    18.789]    RsvdMaskSize: 0
[*][    18.789]    RsvdFieldPosition: 0
[*][    18.789]    DirectColorModeInfo: 2
[*][    18.789]    PhysBasePtr: 0xf0000000
[*][    18.789]    LinBytesPerScanLine: 2560
[*][    18.789]    BnkNumberOfImagePages: 50
[*][    18.789]    LinNumberOfImagePages: 50
[*][    18.789]    LinRedMaskSize: 8
[*][    18.789]    LinRedFieldPosition: 16
[*][    18.789]    LinGreenMaskSize: 8
[*][    18.789]    LinGreenFieldPosition: 8
[*][    18.789]    LinBlueMaskSize: 8
[*][    18.789]    LinBlueFieldPosition: 0
[*][    18.789]    LinRsvdMaskSize: 0
[*][    18.789]    LinRsvdFieldPosition: 0
[*][    18.789]    MaxPixelClock: 0
[*][    18.790] Mode: 171 (720x480)
[*][    18.790]    ModeAttributes: 0x9f
[*][    18.790]    WinAAttributes: 0x7
[*][    18.790]    WinBAttributes: 0x0
[*][    18.790]    WinGranularity: 64
[*][    18.790]    WinSize: 64
[*][    18.790]    WinASegment: 0xa000
[*][    18.790]    WinBSegment: 0xa000
[*][    18.790]    WinFuncPtr: 0xc000a833
[*][    18.790]    BytesPerScanline: 720
[*][    18.790]    XResolution: 720
[*][    18.790]    YResolution: 480
[*][    18.790]    XCharSize: 8
[*][    18.790]    YCharSize: 16
[*][    18.790]    NumberOfPlanes: 1
[*][    18.790]    BitsPerPixel: 8
[*][    18.790]    NumberOfBanks: 1
[*][    18.790]    MemoryModel: 4
[*][    18.790]    BankSize: 0
[*][    18.790]    NumberOfImages: 169
[*][    18.790]    RedMaskSize: 0
[*][    18.790]    RedFieldPosition: 0
[*][    18.790]    GreenMaskSize: 0
[*][    18.790]    GreenFieldPosition: 0
[*][    18.790]    BlueMaskSize: 0
[*][    18.790]    BlueFieldPosition: 0
[*][    18.790]    RsvdMaskSize: 0
[*][    18.790]    RsvdFieldPosition: 0
[*][    18.790]    DirectColorModeInfo: 2
[*][    18.790]    PhysBasePtr: 0xf0000000
[*][    18.790]    LinBytesPerScanLine: 720
[*][    18.791]    BnkNumberOfImagePages: 169
[*][    18.791]    LinNumberOfImagePages: 169
[*][    18.791]    LinRedMaskSize: 0
[*][    18.791]    LinRedFieldPosition: 0
[*][    18.791]    LinGreenMaskSize: 0
[*][    18.791]    LinGreenFieldPosition: 0
[*][    18.791]    LinBlueMaskSize: 0
[*][    18.791]    LinBlueFieldPosition: 0
[*][    18.791]    LinRsvdMaskSize: 0
[*][    18.791]    LinRsvdFieldPosition: 0
[*][    18.791]    MaxPixelClock: 0
[*][    18.792] Mode: 173 (720x480)
[*][    18.792]    ModeAttributes: 0x9b
[*][    18.792]    WinAAttributes: 0x7
[*][    18.792]    WinBAttributes: 0x0
[*][    18.792]    WinGranularity: 64
[*][    18.792]    WinSize: 64
[*][    18.792]    WinASegment: 0xa000
[*][    18.792]    WinBSegment: 0xa000
[*][    18.792]    WinFuncPtr: 0xc000a833
[*][    18.792]    BytesPerScanline: 1440
[*][    18.792]    XResolution: 720
[*][    18.792]    YResolution: 480
[*][    18.792]    XCharSize: 8
[*][    18.792]    YCharSize: 16
[*][    18.792]    NumberOfPlanes: 1
[*][    18.792]    BitsPerPixel: 16
[*][    18.792]    NumberOfBanks: 1
[*][    18.792]    MemoryModel: 6
[*][    18.792]    BankSize: 0
[*][    18.792]    NumberOfImages: 84
[*][    18.792]    RedMaskSize: 5
[*][    18.792]    RedFieldPosition: 11
[*][    18.792]    GreenMaskSize: 6
[*][    18.792]    GreenFieldPosition: 5
[*][    18.792]    BlueMaskSize: 5
[*][    18.792]    BlueFieldPosition: 0
[*][    18.792]    RsvdMaskSize: 0
[*][    18.792]    RsvdFieldPosition: 0
[*][    18.792]    DirectColorModeInfo: 2
[*][    18.792]    PhysBasePtr: 0xf0000000
[*][    18.792]    LinBytesPerScanLine: 1440
[*][    18.792]    BnkNumberOfImagePages: 84
[*][    18.792]    LinNumberOfImagePages: 84
[*][    18.792]    LinRedMaskSize: 5
[*][    18.792]    LinRedFieldPosition: 11
[*][    18.792]    LinGreenMaskSize: 6
[*][    18.792]    LinGreenFieldPosition: 5
[*][    18.792]    LinBlueMaskSize: 5
[*][    18.792]    LinBlueFieldPosition: 0
[*][    18.792]    LinRsvdMaskSize: 0
[*][    18.792]    LinRsvdFieldPosition: 0
[*][    18.792]    MaxPixelClock: 0
[*][    18.793] *Mode: 175 (720x480)
[*][    18.793]    ModeAttributes: 0x9b
[*][    18.793]    WinAAttributes: 0x7
[*][    18.793]    WinBAttributes: 0x0
[*][    18.793]    WinGranularity: 64
[*][    18.793]    WinSize: 64
[*][    18.793]    WinASegment: 0xa000
[*][    18.794]    WinBSegment: 0xa000
[*][    18.794]    WinFuncPtr: 0xc000a833
[*][    18.794]    BytesPerScanline: 2880
[*][    18.794]    XResolution: 720
[*][    18.794]    YResolution: 480
[*][    18.794]    XCharSize: 8
[*][    18.794]    YCharSize: 16
[*][    18.794]    NumberOfPlanes: 1
[*][    18.794]    BitsPerPixel: 32
[*][    18.794]    NumberOfBanks: 1
[*][    18.794]    MemoryModel: 6
[*][    18.794]    BankSize: 0
[*][    18.794]    NumberOfImages: 41
[*][    18.794]    RedMaskSize: 8
[*][    18.794]    RedFieldPosition: 16
[*][    18.794]    GreenMaskSize: 8
[*][    18.794]    GreenFieldPosition: 8
[*][    18.794]    BlueMaskSize: 8
[*][    18.794]    BlueFieldPosition: 0
[*][    18.794]    RsvdMaskSize: 0
[*][    18.794]    RsvdFieldPosition: 0
[*][    18.794]    DirectColorModeInfo: 2
[*][    18.794]    PhysBasePtr: 0xf0000000
[*][    18.794]    LinBytesPerScanLine: 2880
[*][    18.794]    BnkNumberOfImagePages: 41
[*][    18.794]    LinNumberOfImagePages: 41
[*][    18.794]    LinRedMaskSize: 8
[*][    18.794]    LinRedFieldPosition: 16
[*][    18.794]    LinGreenMaskSize: 8
[*][    18.794]    LinGreenFieldPosition: 8
[*][    18.794]    LinBlueMaskSize: 8
[*][    18.794]    LinBlueFieldPosition: 0
[*][    18.794]    LinRsvdMaskSize: 0
[*][    18.794]    LinRsvdFieldPosition: 0
[*][    18.794]    MaxPixelClock: 0
[*][    18.795] Mode: 1b9 (720x540)
[*][    18.795]    ModeAttributes: 0x9f
[*][    18.795]    WinAAttributes: 0x7
[*][    18.795]    WinBAttributes: 0x0
[*][    18.795]    WinGranularity: 64
[*][    18.795]    WinSize: 64
[*][    18.795]    WinASegment: 0xa000
[*][    18.795]    WinBSegment: 0xa000
[*][    18.795]    WinFuncPtr: 0xc000a833
[*][    18.795]    BytesPerScanline: 720
[*][    18.795]    XResolution: 720
[*][    18.795]    YResolution: 540
[*][    18.795]    XCharSize: 8
[*][    18.795]    YCharSize: 16
[*][    18.795]    NumberOfPlanes: 1
[*][    18.795]    BitsPerPixel: 8
[*][    18.795]    NumberOfBanks: 1
[*][    18.795]    MemoryModel: 4
[*][    18.795]    BankSize: 0
[*][    18.795]    NumberOfImages: 145
[*][    18.795]    RedMaskSize: 0
[*][    18.795]    RedFieldPosition: 0
[*][    18.795]    GreenMaskSize: 0
[*][    18.795]    GreenFieldPosition: 0
[*][    18.795]    BlueMaskSize: 0
[*][    18.795]    BlueFieldPosition: 0
[*][    18.795]    RsvdMaskSize: 0
[*][    18.795]    RsvdFieldPosition: 0
[*][    18.795]    DirectColorModeInfo: 2
[*][    18.795]    PhysBasePtr: 0xf0000000
[*][    18.795]    LinBytesPerScanLine: 720
[*][    18.795]    BnkNumberOfImagePages: 145
[*][    18.795]    LinNumberOfImagePages: 145
[*][    18.795]    LinRedMaskSize: 0
[*][    18.795]    LinRedFieldPosition: 0
[*][    18.795]    LinGreenMaskSize: 0
[*][    18.795]    LinGreenFieldPosition: 0
[*][    18.795]    LinBlueMaskSize: 0
[*][    18.795]    LinBlueFieldPosition: 0
[*][    18.795]    LinRsvdMaskSize: 0
[*][    18.795]    LinRsvdFieldPosition: 0
[*][    18.795]    MaxPixelClock: 0
[*][    18.796] Mode: 1ba (720x540)
[*][    18.797]    ModeAttributes: 0x9b
[*][    18.797]    WinAAttributes: 0x7
[*][    18.797]    WinBAttributes: 0x0
[*][    18.797]    WinGranularity: 64
[*][    18.797]    WinSize: 64
[*][    18.797]    WinASegment: 0xa000
[*][    18.797]    WinBSegment: 0xa000
[*][    18.797]    WinFuncPtr: 0xc000a833
[*][    18.797]    BytesPerScanline: 1440
[*][    18.797]    XResolution: 720
[*][    18.797]    YResolution: 540
[*][    18.797]    XCharSize: 8
[*][    18.797]    YCharSize: 16
[*][    18.797]    NumberOfPlanes: 1
[*][    18.797]    BitsPerPixel: 16
[*][    18.797]    NumberOfBanks: 1
[*][    18.797]    MemoryModel: 6
[*][    18.797]    BankSize: 0
[*][    18.797]    NumberOfImages: 72
[*][    18.797]    RedMaskSize: 5
[*][    18.797]    RedFieldPosition: 11
[*][    18.797]    GreenMaskSize: 6
[*][    18.797]    GreenFieldPosition: 5
[*][    18.797]    BlueMaskSize: 5
[*][    18.797]    BlueFieldPosition: 0
[*][    18.797]    RsvdMaskSize: 0
[*][    18.797]    RsvdFieldPosition: 0
[*][    18.797]    DirectColorModeInfo: 2
[*][    18.797]    PhysBasePtr: 0xf0000000
[*][    18.797]    LinBytesPerScanLine: 1440
[*][    18.797]    BnkNumberOfImagePages: 72
[*][    18.797]    LinNumberOfImagePages: 72
[*][    18.797]    LinRedMaskSize: 5
[*][    18.797]    LinRedFieldPosition: 11
[*][    18.797]    LinGreenMaskSize: 6
[*][    18.797]    LinGreenFieldPosition: 5
[*][    18.797]    LinBlueMaskSize: 5
[*][    18.797]    LinBlueFieldPosition: 0
[*][    18.797]    LinRsvdMaskSize: 0
[*][    18.797]    LinRsvdFieldPosition: 0
[*][    18.797]    MaxPixelClock: 0
[*][    18.798] *Mode: 1bb (720x540)
[*][    18.798]    ModeAttributes: 0x9b
[*][    18.798]    WinAAttributes: 0x7
[*][    18.798]    WinBAttributes: 0x0
[*][    18.798]    WinGranularity: 64
[*][    18.798]    WinSize: 64
[*][    18.798]    WinASegment: 0xa000
[*][    18.798]    WinBSegment: 0xa000
[*][    18.798]    WinFuncPtr: 0xc000a833
[*][    18.798]    BytesPerScanline: 2880
[*][    18.798]    XResolution: 720
[*][    18.798]    YResolution: 540
[*][    18.798]    XCharSize: 8
[*][    18.798]    YCharSize: 16
[*][    18.798]    NumberOfPlanes: 1
[*][    18.798]    BitsPerPixel: 32
[*][    18.798]    NumberOfBanks: 1
[*][    18.798]    MemoryModel: 6
[*][    18.798]    BankSize: 0
[*][    18.798]    NumberOfImages: 35
[*][    18.798]    RedMaskSize: 8
[*][    18.798]    RedFieldPosition: 16
[*][    18.798]    GreenMaskSize: 8
[*][    18.798]    GreenFieldPosition: 8
[*][    18.798]    BlueMaskSize: 8
[*][    18.798]    BlueFieldPosition: 0
[*][    18.798]    RsvdMaskSize: 0
[*][    18.798]    RsvdFieldPosition: 0
[*][    18.798]    DirectColorModeInfo: 2
[*][    18.798]    PhysBasePtr: 0xf0000000
[*][    18.798]    LinBytesPerScanLine: 2880
[*][    18.798]    BnkNumberOfImagePages: 35
[*][    18.798]    LinNumberOfImagePages: 35
[*][    18.798]    LinRedMaskSize: 8
[*][    18.798]    LinRedFieldPosition: 16
[*][    18.798]    LinGreenMaskSize: 8
[*][    18.798]    LinGreenFieldPosition: 8
[*][    18.798]    LinBlueMaskSize: 8
[*][    18.798]    LinBlueFieldPosition: 0
[*][    18.798]    LinRsvdMaskSize: 0
[*][    18.798]    LinRsvdFieldPosition: 0
[*][    18.798]    MaxPixelClock: 0
[*][    18.800] Mode: 17c (720x576)
[*][    18.800]    ModeAttributes: 0x9f
[*][    18.800]    WinAAttributes: 0x7
[*][    18.800]    WinBAttributes: 0x0
[*][    18.800]    WinGranularity: 64
[*][    18.800]    WinSize: 64
[*][    18.800]    WinASegment: 0xa000
[*][    18.800]    WinBSegment: 0xa000
[*][    18.800]    WinFuncPtr: 0xc000a833
[*][    18.800]    BytesPerScanline: 720
[*][    18.800]    XResolution: 720
[*][    18.800]    YResolution: 576
[*][    18.800]    XCharSize: 8
[*][    18.800]    YCharSize: 16
[*][    18.800]    NumberOfPlanes: 1
[*][    18.800]    BitsPerPixel: 8
[*][    18.800]    NumberOfBanks: 1
[*][    18.800]    MemoryModel: 4
[*][    18.800]    BankSize: 0
[*][    18.800]    NumberOfImages: 145
[*][    18.800]    RedMaskSize: 0
[*][    18.800]    RedFieldPosition: 0
[*][    18.800]    GreenMaskSize: 0
[*][    18.800]    GreenFieldPosition: 0
[*][    18.800]    BlueMaskSize: 0
[*][    18.800]    BlueFieldPosition: 0
[*][    18.800]    RsvdMaskSize: 0
[*][    18.800]    RsvdFieldPosition: 0
[*][    18.800]    DirectColorModeInfo: 2
[*][    18.800]    PhysBasePtr: 0xf0000000
[*][    18.800]    LinBytesPerScanLine: 720
[*][    18.800]    BnkNumberOfImagePages: 145
[*][    18.800]    LinNumberOfImagePages: 145
[*][    18.800]    LinRedMaskSize: 0
[*][    18.800]    LinRedFieldPosition: 0
[*][    18.800]    LinGreenMaskSize: 0
[*][    18.800]    LinGreenFieldPosition: 0
[*][    18.800]    LinBlueMaskSize: 0
[*][    18.800]    LinBlueFieldPosition: 0
[*][    18.800]    LinRsvdMaskSize: 0
[*][    18.800]    LinRsvdFieldPosition: 0
[*][    18.800]    MaxPixelClock: 0
[*][    18.801] Mode: 17e (720x576)
[*][    18.801]    ModeAttributes: 0x9b
[*][    18.801]    WinAAttributes: 0x7
[*][    18.801]    WinBAttributes: 0x0
[*][    18.801]    WinGranularity: 64
[*][    18.801]    WinSize: 64
[*][    18.801]    WinASegment: 0xa000
[*][    18.801]    WinBSegment: 0xa000
[*][    18.801]    WinFuncPtr: 0xc000a833
[*][    18.801]    BytesPerScanline: 1440
[*][    18.801]    XResolution: 720
[*][    18.801]    YResolution: 576
[*][    18.801]    XCharSize: 8
[*][    18.801]    YCharSize: 16
[*][    18.801]    NumberOfPlanes: 1
[*][    18.801]    BitsPerPixel: 16
[*][    18.801]    NumberOfBanks: 1
[*][    18.801]    MemoryModel: 6
[*][    18.801]    BankSize: 0
[*][    18.801]    NumberOfImages: 72
[*][    18.801]    RedMaskSize: 5
[*][    18.801]    RedFieldPosition: 11
[*][    18.801]    GreenMaskSize: 6
[*][    18.801]    GreenFieldPosition: 5
[*][    18.801]    BlueMaskSize: 5
[*][    18.801]    BlueFieldPosition: 0
[*][    18.801]    RsvdMaskSize: 0
[*][    18.801]    RsvdFieldPosition: 0
[*][    18.801]    DirectColorModeInfo: 2
[*][    18.802]    PhysBasePtr: 0xf0000000
[*][    18.802]    LinBytesPerScanLine: 1440
[*][    18.802]    BnkNumberOfImagePages: 72
[*][    18.802]    LinNumberOfImagePages: 72
[*][    18.802]    LinRedMaskSize: 5
[*][    18.802]    LinRedFieldPosition: 11
[*][    18.802]    LinGreenMaskSize: 6
[*][    18.802]    LinGreenFieldPosition: 5
[*][    18.802]    LinBlueMaskSize: 5
[*][    18.802]    LinBlueFieldPosition: 0
[*][    18.802]    LinRsvdMaskSize: 0
[*][    18.802]    LinRsvdFieldPosition: 0
[*][    18.802]    MaxPixelClock: 0
[*][    18.803] *Mode: 17f (720x576)
[*][    18.803]    ModeAttributes: 0x9b
[*][    18.803]    WinAAttributes: 0x7
[*][    18.803]    WinBAttributes: 0x0
[*][    18.803]    WinGranularity: 64
[*][    18.803]    WinSize: 64
[*][    18.803]    WinASegment: 0xa000
[*][    18.803]    WinBSegment: 0xa000
[*][    18.803]    WinFuncPtr: 0xc000a833
[*][    18.803]    BytesPerScanline: 2880
[*][    18.803]    XResolution: 720
[*][    18.803]    YResolution: 576
[*][    18.803]    XCharSize: 8
[*][    18.803]    YCharSize: 16
[*][    18.803]    NumberOfPlanes: 1
[*][    18.803]    BitsPerPixel: 32
[*][    18.803]    NumberOfBanks: 1
[*][    18.803]    MemoryModel: 6
[*][    18.803]    BankSize: 0
[*][    18.803]    NumberOfImages: 35
[*][    18.803]    RedMaskSize: 8
[*][    18.803]    RedFieldPosition: 16
[*][    18.803]    GreenMaskSize: 8
[*][    18.803]    GreenFieldPosition: 8
[*][    18.803]    BlueMaskSize: 8
[*][    18.803]    BlueFieldPosition: 0
[*][    18.803]    RsvdMaskSize: 0
[*][    18.803]    RsvdFieldPosition: 0
[*][    18.803]    DirectColorModeInfo: 2
[*][    18.803]    PhysBasePtr: 0xf0000000
[*][    18.803]    LinBytesPerScanLine: 2880
[*][    18.803]    BnkNumberOfImagePages: 35
[*][    18.803]    LinNumberOfImagePages: 35
[*][    18.803]    LinRedMaskSize: 8
[*][    18.803]    LinRedFieldPosition: 16
[*][    18.803]    LinGreenMaskSize: 8
[*][    18.803]    LinGreenFieldPosition: 8
[*][    18.803]    LinBlueMaskSize: 8
[*][    18.803]    LinBlueFieldPosition: 0
[*][    18.803]    LinRsvdMaskSize: 0
[*][    18.803]    LinRsvdFieldPosition: 0
[*][    18.803]    MaxPixelClock: 0
[*][    18.804] Mode: 103 (800x600)
[*][    18.804]    ModeAttributes: 0x9f
[*][    18.804]    WinAAttributes: 0x7
[*][    18.804]    WinBAttributes: 0x0
[*][    18.804]    WinGranularity: 64
[*][    18.804]    WinSize: 64
[*][    18.804]    WinASegment: 0xa000
[*][    18.804]    WinBSegment: 0xa000
[*][    18.804]    WinFuncPtr: 0xc000a833
[*][    18.804]    BytesPerScanline: 800
[*][    18.804]    XResolution: 800
[*][    18.804]    YResolution: 600
[*][    18.804]    XCharSize: 8
[*][    18.804]    YCharSize: 8
[*][    18.804]    NumberOfPlanes: 1
[*][    18.804]    BitsPerPixel: 8
[*][    18.805]    NumberOfBanks: 1
[*][    18.805]    MemoryModel: 4
[*][    18.805]    BankSize: 0
[*][    18.805]    NumberOfImages: 127
[*][    18.805]    RedMaskSize: 0
[*][    18.805]    RedFieldPosition: 0
[*][    18.805]    GreenMaskSize: 0
[*][    18.805]    GreenFieldPosition: 0
[*][    18.805]    BlueMaskSize: 0
[*][    18.805]    BlueFieldPosition: 0
[*][    18.805]    RsvdMaskSize: 0
[*][    18.805]    RsvdFieldPosition: 0
[*][    18.805]    DirectColorModeInfo: 2
[*][    18.805]    PhysBasePtr: 0xf0000000
[*][    18.805]    LinBytesPerScanLine: 800
[*][    18.805]    BnkNumberOfImagePages: 127
[*][    18.805]    LinNumberOfImagePages: 127
[*][    18.805]    LinRedMaskSize: 0
[*][    18.805]    LinRedFieldPosition: 0
[*][    18.805]    LinGreenMaskSize: 0
[*][    18.805]    LinGreenFieldPosition: 0
[*][    18.805]    LinBlueMaskSize: 0
[*][    18.805]    LinBlueFieldPosition: 0
[*][    18.805]    LinRsvdMaskSize: 0
[*][    18.805]    LinRsvdFieldPosition: 0
[*][    18.805]    MaxPixelClock: 0
[*][    18.806] Mode: 114 (800x600)
[*][    18.806]    ModeAttributes: 0x9b
[*][    18.806]    WinAAttributes: 0x7
[*][    18.806]    WinBAttributes: 0x0
[*][    18.806]    WinGranularity: 64
[*][    18.806]    WinSize: 64
[*][    18.806]    WinASegment: 0xa000
[*][    18.806]    WinBSegment: 0xa000
[*][    18.806]    WinFuncPtr: 0xc000a833
[*][    18.806]    BytesPerScanline: 1600
[*][    18.806]    XResolution: 800
[*][    18.806]    YResolution: 600
[*][    18.806]    XCharSize: 8
[*][    18.806]    YCharSize: 8
[*][    18.806]    NumberOfPlanes: 1
[*][    18.806]    BitsPerPixel: 16
[*][    18.806]    NumberOfBanks: 1
[*][    18.806]    MemoryModel: 6
[*][    18.806]    BankSize: 0
[*][    18.806]    NumberOfImages: 63
[*][    18.806]    RedMaskSize: 5
[*][    18.806]    RedFieldPosition: 11
[*][    18.806]    GreenMaskSize: 6
[*][    18.806]    GreenFieldPosition: 5
[*][    18.806]    BlueMaskSize: 5
[*][    18.806]    BlueFieldPosition: 0
[*][    18.806]    RsvdMaskSize: 0
[*][    18.806]    RsvdFieldPosition: 0
[*][    18.806]    DirectColorModeInfo: 2
[*][    18.806]    PhysBasePtr: 0xf0000000
[*][    18.806]    LinBytesPerScanLine: 1600
[*][    18.806]    BnkNumberOfImagePages: 63
[*][    18.806]    LinNumberOfImagePages: 63
[*][    18.806]    LinRedMaskSize: 5
[*][    18.806]    LinRedFieldPosition: 11
[*][    18.806]    LinGreenMaskSize: 6
[*][    18.806]    LinGreenFieldPosition: 5
[*][    18.806]    LinBlueMaskSize: 5
[*][    18.806]    LinBlueFieldPosition: 0
[*][    18.806]    LinRsvdMaskSize: 0
[*][    18.806]    LinRsvdFieldPosition: 0
[*][    18.806]    MaxPixelClock: 0
[*][    18.807] *Mode: 115 (800x600)
[*][    18.807]    ModeAttributes: 0x9b
[*][    18.807]    WinAAttributes: 0x7
[*][    18.807]    WinBAttributes: 0x0
[*][    18.807]    WinGranularity: 64
[*][    18.807]    WinSize: 64
[*][    18.807]    WinASegment: 0xa000
[*][    18.807]    WinBSegment: 0xa000
[*][    18.807]    WinFuncPtr: 0xc000a833
[*][    18.807]    BytesPerScanline: 3200
[*][    18.807]    XResolution: 800
[*][    18.807]    YResolution: 600
[*][    18.807]    XCharSize: 8
[*][    18.807]    YCharSize: 8
[*][    18.807]    NumberOfPlanes: 1
[*][    18.807]    BitsPerPixel: 32
[*][    18.807]    NumberOfBanks: 1
[*][    18.807]    MemoryModel: 6
[*][    18.807]    BankSize: 0
[*][    18.808]    NumberOfImages: 31
[*][    18.808]    RedMaskSize: 8
[*][    18.808]    RedFieldPosition: 16
[*][    18.808]    GreenMaskSize: 8
[*][    18.808]    GreenFieldPosition: 8
[*][    18.808]    BlueMaskSize: 8
[*][    18.808]    BlueFieldPosition: 0
[*][    18.808]    RsvdMaskSize: 0
[*][    18.808]    RsvdFieldPosition: 0
[*][    18.808]    DirectColorModeInfo: 2
[*][    18.808]    PhysBasePtr: 0xf0000000
[*][    18.808]    LinBytesPerScanLine: 3200
[*][    18.808]    BnkNumberOfImagePages: 31
[*][    18.808]    LinNumberOfImagePages: 31
[*][    18.808]    LinRedMaskSize: 8
[*][    18.808]    LinRedFieldPosition: 16
[*][    18.808]    LinGreenMaskSize: 8
[*][    18.808]    LinGreenFieldPosition: 8
[*][    18.808]    LinBlueMaskSize: 8
[*][    18.808]    LinBlueFieldPosition: 0
[*][    18.808]    LinRsvdMaskSize: 0
[*][    18.808]    LinRsvdFieldPosition: 0
[*][    18.808]    MaxPixelClock: 0
[*][    18.809] Mode: 105 (1024x768)
[*][    18.809]    ModeAttributes: 0x9f
[*][    18.809]    WinAAttributes: 0x7
[*][    18.809]    WinBAttributes: 0x0
[*][    18.809]    WinGranularity: 64
[*][    18.809]    WinSize: 64
[*][    18.809]    WinASegment: 0xa000
[*][    18.809]    WinBSegment: 0xa000
[*][    18.809]    WinFuncPtr: 0xc000a833
[*][    18.809]    BytesPerScanline: 1024
[*][    18.809]    XResolution: 1024
[*][    18.809]    YResolution: 768
[*][    18.809]    XCharSize: 8
[*][    18.809]    YCharSize: 16
[*][    18.809]    NumberOfPlanes: 1
[*][    18.809]    BitsPerPixel: 8
[*][    18.809]    NumberOfBanks: 1
[*][    18.809]    MemoryModel: 4
[*][    18.809]    BankSize: 0
[*][    18.809]    NumberOfImages: 84
[*][    18.809]    RedMaskSize: 0
[*][    18.809]    RedFieldPosition: 0
[*][    18.809]    GreenMaskSize: 0
[*][    18.809]    GreenFieldPosition: 0
[*][    18.809]    BlueMaskSize: 0
[*][    18.809]    BlueFieldPosition: 0
[*][    18.809]    RsvdMaskSize: 0
[*][    18.809]    RsvdFieldPosition: 0
[*][    18.809]    DirectColorModeInfo: 2
[*][    18.809]    PhysBasePtr: 0xf0000000
[*][    18.809]    LinBytesPerScanLine: 1024
[*][    18.809]    BnkNumberOfImagePages: 84
[*][    18.809]    LinNumberOfImagePages: 84
[*][    18.809]    LinRedMaskSize: 0
[*][    18.809]    LinRedFieldPosition: 0
[*][    18.809]    LinGreenMaskSize: 0
[*][    18.809]    LinGreenFieldPosition: 0
[*][    18.809]    LinBlueMaskSize: 0
[*][    18.809]    LinBlueFieldPosition: 0
[*][    18.809]    LinRsvdMaskSize: 0
[*][    18.809]    LinRsvdFieldPosition: 0
[*][    18.809]    MaxPixelClock: 0
[*][    18.810] Mode: 117 (1024x768)
[*][    18.810]    ModeAttributes: 0x9b
[*][    18.810]    WinAAttributes: 0x7
[*][    18.810]    WinBAttributes: 0x0
[*][    18.810]    WinGranularity: 64
[*][    18.810]    WinSize: 64
[*][    18.810]    WinASegment: 0xa000
[*][    18.810]    WinBSegment: 0xa000
[*][    18.810]    WinFuncPtr: 0xc000a833
[*][    18.810]    BytesPerScanline: 2048
[*][    18.810]    XResolution: 1024
[*][    18.810]    YResolution: 768
[*][    18.810]    XCharSize: 8
[*][    18.810]    YCharSize: 16
[*][    18.810]    NumberOfPlanes: 1
[*][    18.810]    BitsPerPixel: 16
[*][    18.810]    NumberOfBanks: 1
[*][    18.810]    MemoryModel: 6
[*][    18.810]    BankSize: 0
[*][    18.811]    NumberOfImages: 41
[*][    18.811]    RedMaskSize: 5
[*][    18.811]    RedFieldPosition: 11
[*][    18.811]    GreenMaskSize: 6
[*][    18.811]    GreenFieldPosition: 5
[*][    18.811]    BlueMaskSize: 5
[*][    18.811]    BlueFieldPosition: 0
[*][    18.811]    RsvdMaskSize: 0
[*][    18.811]    RsvdFieldPosition: 0
[*][    18.811]    DirectColorModeInfo: 2
[*][    18.811]    PhysBasePtr: 0xf0000000
[*][    18.811]    LinBytesPerScanLine: 2048
[*][    18.811]    BnkNumberOfImagePages: 41
[*][    18.811]    LinNumberOfImagePages: 41
[*][    18.811]    LinRedMaskSize: 5
[*][    18.811]    LinRedFieldPosition: 11
[*][    18.811]    LinGreenMaskSize: 6
[*][    18.811]    LinGreenFieldPosition: 5
[*][    18.811]    LinBlueMaskSize: 5
[*][    18.811]    LinBlueFieldPosition: 0
[*][    18.811]    LinRsvdMaskSize: 0
[*][    18.811]    LinRsvdFieldPosition: 0
[*][    18.811]    MaxPixelClock: 0
[*][    18.812] *Mode: 118 (1024x768)
[*][    18.812]    ModeAttributes: 0x9b
[*][    18.812]    WinAAttributes: 0x7
[*][    18.812]    WinBAttributes: 0x0
[*][    18.812]    WinGranularity: 64
[*][    18.812]    WinSize: 64
[*][    18.812]    WinASegment: 0xa000
[*][    18.812]    WinBSegment: 0xa000
[*][    18.812]    WinFuncPtr: 0xc000a833
[*][    18.812]    BytesPerScanline: 4096
[*][    18.812]    XResolution: 1024
[*][    18.812]    YResolution: 768
[*][    18.812]    XCharSize: 8
[*][    18.812]    YCharSize: 16
[*][    18.812]    NumberOfPlanes: 1
[*][    18.812]    BitsPerPixel: 32
[*][    18.812]    NumberOfBanks: 1
[*][    18.812]    MemoryModel: 6
[*][    18.812]    BankSize: 0
[*][    18.812]    NumberOfImages: 20
[*][    18.812]    RedMaskSize: 8
[*][    18.812]    RedFieldPosition: 16
[*][    18.812]    GreenMaskSize: 8
[*][    18.812]    GreenFieldPosition: 8
[*][    18.812]    BlueMaskSize: 8
[*][    18.812]    BlueFieldPosition: 0
[*][    18.812]    RsvdMaskSize: 0
[*][    18.812]    RsvdFieldPosition: 0
[*][    18.812]    DirectColorModeInfo: 2
[*][    18.812]    PhysBasePtr: 0xf0000000
[*][    18.812]    LinBytesPerScanLine: 4096
[*][    18.812]    BnkNumberOfImagePages: 20
[*][    18.812]    LinNumberOfImagePages: 20
[*][    18.812]    LinRedMaskSize: 8
[*][    18.812]    LinRedFieldPosition: 16
[*][    18.812]    LinGreenMaskSize: 8
[*][    18.812]    LinGreenFieldPosition: 8
[*][    18.812]    LinBlueMaskSize: 8
[*][    18.812]    LinBlueFieldPosition: 0
[*][    18.812]    LinRsvdMaskSize: 0
[*][    18.812]    LinRsvdFieldPosition: 0
[*][    18.812]    MaxPixelClock: 0
[*][    18.813] Mode: 179 (1280x768)
[*][    18.813]    ModeAttributes: 0x9f
[*][    18.813]    WinAAttributes: 0x7
[*][    18.813]    WinBAttributes: 0x0
[*][    18.813]    WinGranularity: 64
[*][    18.813]    WinSize: 64
[*][    18.813]    WinASegment: 0xa000
[*][    18.813]    WinBSegment: 0xa000
[*][    18.813]    WinFuncPtr: 0xc000a833
[*][    18.813]    BytesPerScanline: 1280
[*][    18.813]    XResolution: 1280
[*][    18.813]    YResolution: 768
[*][    18.814]    XCharSize: 8
[*][    18.814]    YCharSize: 16
[*][    18.814]    NumberOfPlanes: 1
[*][    18.814]    BitsPerPixel: 8
[*][    18.814]    NumberOfBanks: 1
[*][    18.814]    MemoryModel: 4
[*][    18.814]    BankSize: 0
[*][    18.814]    NumberOfImages: 67
[*][    18.814]    RedMaskSize: 0
[*][    18.814]    RedFieldPosition: 0
[*][    18.814]    GreenMaskSize: 0
[*][    18.814]    GreenFieldPosition: 0
[*][    18.814]    BlueMaskSize: 0
[*][    18.814]    BlueFieldPosition: 0
[*][    18.814]    RsvdMaskSize: 0
[*][    18.814]    RsvdFieldPosition: 0
[*][    18.814]    DirectColorModeInfo: 2
[*][    18.814]    PhysBasePtr: 0xf0000000
[*][    18.814]    LinBytesPerScanLine: 1280
[*][    18.814]    BnkNumberOfImagePages: 67
[*][    18.814]    LinNumberOfImagePages: 67
[*][    18.814]    LinRedMaskSize: 0
[*][    18.814]    LinRedFieldPosition: 0
[*][    18.814]    LinGreenMaskSize: 0
[*][    18.814]    LinGreenFieldPosition: 0
[*][    18.814]    LinBlueMaskSize: 0
[*][    18.814]    LinBlueFieldPosition: 0
[*][    18.814]    LinRsvdMaskSize: 0
[*][    18.814]    LinRsvdFieldPosition: 0
[*][    18.814]    MaxPixelClock: 0
[*][    18.815] Mode: 17a (1280x768)
[*][    18.815]    ModeAttributes: 0x9b
[*][    18.815]    WinAAttributes: 0x7
[*][    18.815]    WinBAttributes: 0x0
[*][    18.815]    WinGranularity: 64
[*][    18.815]    WinSize: 64
[*][    18.815]    WinASegment: 0xa000
[*][    18.815]    WinBSegment: 0xa000
[*][    18.815]    WinFuncPtr: 0xc000a833
[*][    18.815]    BytesPerScanline: 2560
[*][    18.815]    XResolution: 1280
[*][    18.815]    YResolution: 768
[*][    18.815]    XCharSize: 8
[*][    18.815]    YCharSize: 16
[*][    18.815]    NumberOfPlanes: 1
[*][    18.815]    BitsPerPixel: 16
[*][    18.815]    NumberOfBanks: 1
[*][    18.815]    MemoryModel: 6
[*][    18.815]    BankSize: 0
[*][    18.815]    NumberOfImages: 33
[*][    18.815]    RedMaskSize: 5
[*][    18.815]    RedFieldPosition: 11
[*][    18.815]    GreenMaskSize: 6
[*][    18.815]    GreenFieldPosition: 5
[*][    18.815]    BlueMaskSize: 5
[*][    18.815]    BlueFieldPosition: 0
[*][    18.815]    RsvdMaskSize: 0
[*][    18.815]    RsvdFieldPosition: 0
[*][    18.815]    DirectColorModeInfo: 2
[*][    18.815]    PhysBasePtr: 0xf0000000
[*][    18.815]    LinBytesPerScanLine: 2560
[*][    18.815]    BnkNumberOfImagePages: 33
[*][    18.815]    LinNumberOfImagePages: 33
[*][    18.815]    LinRedMaskSize: 5
[*][    18.815]    LinRedFieldPosition: 11
[*][    18.815]    LinGreenMaskSize: 6
[*][    18.815]    LinGreenFieldPosition: 5
[*][    18.815]    LinBlueMaskSize: 5
[*][    18.815]    LinBlueFieldPosition: 0
[*][    18.815]    LinRsvdMaskSize: 0
[*][    18.815]    LinRsvdFieldPosition: 0
[*][    18.815]    MaxPixelClock: 0
[*][    18.817] *Mode: 17b (1280x768)
[*][    18.817]    ModeAttributes: 0x9b
[*][    18.817]    WinAAttributes: 0x7
[*][    18.817]    WinBAttributes: 0x0
[*][    18.817]    WinGranularity: 64
[*][    18.817]    WinSize: 64
[*][    18.817]    WinASegment: 0xa000
[*][    18.817]    WinBSegment: 0xa000
[*][    18.817]    WinFuncPtr: 0xc000a833
[*][    18.817]    BytesPerScanline: 5120
[*][    18.817]    XResolution: 1280
[*][    18.817]    YResolution: 768
[*][    18.817]    XCharSize: 8
[*][    18.817]    YCharSize: 16
[*][    18.817]    NumberOfPlanes: 1
[*][    18.817]    BitsPerPixel: 32
[*][    18.817]    NumberOfBanks: 1
[*][    18.817]    MemoryModel: 6
[*][    18.817]    BankSize: 0
[*][    18.817]    NumberOfImages: 16
[*][    18.817]    RedMaskSize: 8
[*][    18.817]    RedFieldPosition: 16
[*][    18.817]    GreenMaskSize: 8
[*][    18.817]    GreenFieldPosition: 8
[*][    18.817]    BlueMaskSize: 8
[*][    18.817]    BlueFieldPosition: 0
[*][    18.817]    RsvdMaskSize: 0
[*][    18.817]    RsvdFieldPosition: 0
[*][    18.817]    DirectColorModeInfo: 2
[*][    18.817]    PhysBasePtr: 0xf0000000
[*][    18.817]    LinBytesPerScanLine: 5120
[*][    18.817]    BnkNumberOfImagePages: 16
[*][    18.817]    LinNumberOfImagePages: 16
[*][    18.817]    LinRedMaskSize: 8
[*][    18.817]    LinRedFieldPosition: 16
[*][    18.817]    LinGreenMaskSize: 8
[*][    18.817]    LinGreenFieldPosition: 8
[*][    18.817]    LinBlueMaskSize: 8
[*][    18.817]    LinBlueFieldPosition: 0
[*][    18.817]    LinRsvdMaskSize: 0
[*][    18.817]    LinRsvdFieldPosition: 0
[*][    18.817]    MaxPixelClock: 0
[*][    18.818] Mode: 107 (1280x1024)
[*][    18.818]    ModeAttributes: 0x9f
[*][    18.818]    WinAAttributes: 0x7
[*][    18.818]    WinBAttributes: 0x0
[*][    18.818]    WinGranularity: 64
[*][    18.818]    WinSize: 64
[*][    18.818]    WinASegment: 0xa000
[*][    18.818]    WinBSegment: 0xa000
[*][    18.818]    WinFuncPtr: 0xc000a833
[*][    18.818]    BytesPerScanline: 1280
[*][    18.818]    XResolution: 1280
[*][    18.818]    YResolution: 1024
[*][    18.818]    XCharSize: 8
[*][    18.818]    YCharSize: 16
[*][    18.818]    NumberOfPlanes: 1
[*][    18.818]    BitsPerPixel: 8
[*][    18.818]    NumberOfBanks: 1
[*][    18.818]    MemoryModel: 4
[*][    18.818]    BankSize: 0
[*][    18.818]    NumberOfImages: 50
[*][    18.818]    RedMaskSize: 0
[*][    18.818]    RedFieldPosition: 0
[*][    18.818]    GreenMaskSize: 0
[*][    18.818]    GreenFieldPosition: 0
[*][    18.818]    BlueMaskSize: 0
[*][    18.818]    BlueFieldPosition: 0
[*][    18.818]    RsvdMaskSize: 0
[*][    18.818]    RsvdFieldPosition: 0
[*][    18.818]    DirectColorModeInfo: 2
[*][    18.818]    PhysBasePtr: 0xf0000000
[*][    18.818]    LinBytesPerScanLine: 1280
[*][    18.818]    BnkNumberOfImagePages: 50
[*][    18.818]    LinNumberOfImagePages: 50
[*][    18.818]    LinRedMaskSize: 0
[*][    18.818]    LinRedFieldPosition: 0
[*][    18.818]    LinGreenMaskSize: 0
[*][    18.818]    LinGreenFieldPosition: 0
[*][    18.818]    LinBlueMaskSize: 0
[*][    18.818]    LinBlueFieldPosition: 0
[*][    18.818]    LinRsvdMaskSize: 0
[*][    18.818]    LinRsvdFieldPosition: 0
[*][    18.818]    MaxPixelClock: 0
[*][    18.820] Mode: 11a (1280x1024)
[*][    18.820]    ModeAttributes: 0x9b
[*][    18.820]    WinAAttributes: 0x7
[*][    18.820]    WinBAttributes: 0x0
[*][    18.820]    WinGranularity: 64
[*][    18.820]    WinSize: 64
[*][    18.820]    WinASegment: 0xa000
[*][    18.820]    WinBSegment: 0xa000
[*][    18.820]    WinFuncPtr: 0xc000a833
[*][    18.820]    BytesPerScanline: 2560
[*][    18.820]    XResolution: 1280
[*][    18.820]    YResolution: 1024
[*][    18.820]    XCharSize: 8
[*][    18.820]    YCharSize: 16
[*][    18.820]    NumberOfPlanes: 1
[*][    18.820]    BitsPerPixel: 16
[*][    18.820]    NumberOfBanks: 1
[*][    18.820]    MemoryModel: 6
[*][    18.820]    BankSize: 0
[*][    18.820]    NumberOfImages: 24
[*][    18.820]    RedMaskSize: 5
[*][    18.820]    RedFieldPosition: 11
[*][    18.820]    GreenMaskSize: 6
[*][    18.820]    GreenFieldPosition: 5
[*][    18.820]    BlueMaskSize: 5
[*][    18.820]    BlueFieldPosition: 0
[*][    18.820]    RsvdMaskSize: 0
[*][    18.820]    RsvdFieldPosition: 0
[*][    18.820]    DirectColorModeInfo: 2
[*][    18.820]    PhysBasePtr: 0xf0000000
[*][    18.820]    LinBytesPerScanLine: 2560
[*][    18.820]    BnkNumberOfImagePages: 24
[*][    18.820]    LinNumberOfImagePages: 24
[*][    18.820]    LinRedMaskSize: 5
[*][    18.820]    LinRedFieldPosition: 11
[*][    18.820]    LinGreenMaskSize: 6
[*][    18.820]    LinGreenFieldPosition: 5
[*][    18.820]    LinBlueMaskSize: 5
[*][    18.820]    LinBlueFieldPosition: 0
[*][    18.820]    LinRsvdMaskSize: 0
[*][    18.820]    LinRsvdFieldPosition: 0
[*][    18.820]    MaxPixelClock: 0
[*][    18.821] *Mode: 11b (1280x1024)
[*][    18.821]    ModeAttributes: 0x9b
[*][    18.821]    WinAAttributes: 0x7
[*][    18.821]    WinBAttributes: 0x0
[*][    18.821]    WinGranularity: 64
[*][    18.821]    WinSize: 64
[*][    18.821]    WinASegment: 0xa000
[*][    18.821]    WinBSegment: 0xa000
[*][    18.821]    WinFuncPtr: 0xc000a833
[*][    18.821]    BytesPerScanline: 5120
[*][    18.821]    XResolution: 1280
[*][    18.821]    YResolution: 1024
[*][    18.821]    XCharSize: 8
[*][    18.821]    YCharSize: 16
[*][    18.821]    NumberOfPlanes: 1
[*][    18.821]    BitsPerPixel: 32
[*][    18.821]    NumberOfBanks: 1
[*][    18.821]    MemoryModel: 6
[*][    18.821]    BankSize: 0
[*][    18.821]    NumberOfImages: 11
[*][    18.821]    RedMaskSize: 8
[*][    18.821]    RedFieldPosition: 16
[*][    18.821]    GreenMaskSize: 8
[*][    18.821]    GreenFieldPosition: 8
[*][    18.821]    BlueMaskSize: 8
[*][    18.821]    BlueFieldPosition: 0
[*][    18.821]    RsvdMaskSize: 0
[*][    18.821]    RsvdFieldPosition: 0
[*][    18.821]    DirectColorModeInfo: 2
[*][    18.821]    PhysBasePtr: 0xf0000000
[*][    18.822]    LinBytesPerScanLine: 5120
[*][    18.822]    BnkNumberOfImagePages: 11
[*][    18.822]    LinNumberOfImagePages: 11
[*][    18.822]    LinRedMaskSize: 8
[*][    18.822]    LinRedFieldPosition: 16
[*][    18.822]    LinGreenMaskSize: 8
[*][    18.822]    LinGreenFieldPosition: 8
[*][    18.822]    LinBlueMaskSize: 8
[*][    18.822]    LinBlueFieldPosition: 0
[*][    18.822]    LinRsvdMaskSize: 0
[*][    18.822]    LinRsvdFieldPosition: 0
[*][    18.822]    MaxPixelClock: 0
[*][    18.823] Mode: 120 (1600x1200)
[*][    18.823]    ModeAttributes: 0x9f
[*][    18.823]    WinAAttributes: 0x7
[*][    18.823]    WinBAttributes: 0x0
[*][    18.823]    WinGranularity: 64
[*][    18.823]    WinSize: 64
[*][    18.823]    WinASegment: 0xa000
[*][    18.823]    WinBSegment: 0xa000
[*][    18.823]    WinFuncPtr: 0xc000a833
[*][    18.823]    BytesPerScanline: 1600
[*][    18.823]    XResolution: 1600
[*][    18.823]    YResolution: 1200
[*][    18.823]    XCharSize: 8
[*][    18.823]    YCharSize: 16
[*][    18.823]    NumberOfPlanes: 1
[*][    18.823]    BitsPerPixel: 8
[*][    18.823]    NumberOfBanks: 1
[*][    18.823]    MemoryModel: 4
[*][    18.823]    BankSize: 0
[*][    18.823]    NumberOfImages: 33
[*][    18.823]    RedMaskSize: 0
[*][    18.823]    RedFieldPosition: 0
[*][    18.823]    GreenMaskSize: 0
[*][    18.823]    GreenFieldPosition: 0
[*][    18.823]    BlueMaskSize: 0
[*][    18.823]    BlueFieldPosition: 0
[*][    18.823]    RsvdMaskSize: 0
[*][    18.823]    RsvdFieldPosition: 0
[*][    18.823]    DirectColorModeInfo: 2
[*][    18.823]    PhysBasePtr: 0xf0000000
[*][    18.823]    LinBytesPerScanLine: 1600
[*][    18.823]    BnkNumberOfImagePages: 33
[*][    18.823]    LinNumberOfImagePages: 33
[*][    18.823]    LinRedMaskSize: 0
[*][    18.823]    LinRedFieldPosition: 0
[*][    18.823]    LinGreenMaskSize: 0
[*][    18.823]    LinGreenFieldPosition: 0
[*][    18.823]    LinBlueMaskSize: 0
[*][    18.823]    LinBlueFieldPosition: 0
[*][    18.823]    LinRsvdMaskSize: 0
[*][    18.823]    LinRsvdFieldPosition: 0
[*][    18.823]    MaxPixelClock: 0
[*][    18.824] Mode: 122 (1600x1200)
[*][    18.824]    ModeAttributes: 0x9b
[*][    18.824]    WinAAttributes: 0x7
[*][    18.824]    WinBAttributes: 0x0
[*][    18.824]    WinGranularity: 64
[*][    18.824]    WinSize: 64
[*][    18.824]    WinASegment: 0xa000
[*][    18.824]    WinBSegment: 0xa000
[*][    18.824]    WinFuncPtr: 0xc000a833
[*][    18.824]    BytesPerScanline: 3200
[*][    18.824]    XResolution: 1600
[*][    18.824]    YResolution: 1200
[*][    18.824]    XCharSize: 8
[*][    18.824]    YCharSize: 16
[*][    18.824]    NumberOfPlanes: 1
[*][    18.824]    BitsPerPixel: 16
[*][    18.825]    NumberOfBanks: 1
[*][    18.825]    MemoryModel: 6
[*][    18.825]    BankSize: 0
[*][    18.825]    NumberOfImages: 16
[*][    18.825]    RedMaskSize: 5
[*][    18.825]    RedFieldPosition: 11
[*][    18.825]    GreenMaskSize: 6
[*][    18.825]    GreenFieldPosition: 5
[*][    18.825]    BlueMaskSize: 5
[*][    18.825]    BlueFieldPosition: 0
[*][    18.825]    RsvdMaskSize: 0
[*][    18.825]    RsvdFieldPosition: 0
[*][    18.825]    DirectColorModeInfo: 2
[*][    18.825]    PhysBasePtr: 0xf0000000
[*][    18.825]    LinBytesPerScanLine: 3200
[*][    18.825]    BnkNumberOfImagePages: 16
[*][    18.825]    LinNumberOfImagePages: 16
[*][    18.825]    LinRedMaskSize: 5
[*][    18.825]    LinRedFieldPosition: 11
[*][    18.825]    LinGreenMaskSize: 6
[*][    18.825]    LinGreenFieldPosition: 5
[*][    18.825]    LinBlueMaskSize: 5
[*][    18.825]    LinBlueFieldPosition: 0
[*][    18.825]    LinRsvdMaskSize: 0
[*][    18.825]    LinRsvdFieldPosition: 0
[*][    18.825]    MaxPixelClock: 0
[*][    18.826] *Mode: 124 (1600x1200)
[*][    18.826]    ModeAttributes: 0x9b
[*][    18.826]    WinAAttributes: 0x7
[*][    18.826]    WinBAttributes: 0x0
[*][    18.826]    WinGranularity: 64
[*][    18.826]    WinSize: 64
[*][    18.826]    WinASegment: 0xa000
[*][    18.826]    WinBSegment: 0xa000
[*][    18.826]    WinFuncPtr: 0xc000a833
[*][    18.826]    BytesPerScanline: 6400
[*][    18.826]    XResolution: 1600
[*][    18.826]    YResolution: 1200
[*][    18.826]    XCharSize: 8
[*][    18.826]    YCharSize: 16
[*][    18.826]    NumberOfPlanes: 1
[*][    18.826]    BitsPerPixel: 32
[*][    18.826]    NumberOfBanks: 1
[*][    18.826]    MemoryModel: 6
[*][    18.826]    BankSize: 0
[*][    18.826]    NumberOfImages: 7
[*][    18.826]    RedMaskSize: 8
[*][    18.826]    RedFieldPosition: 16
[*][    18.826]    GreenMaskSize: 8
[*][    18.826]    GreenFieldPosition: 8
[*][    18.826]    BlueMaskSize: 8
[*][    18.826]    BlueFieldPosition: 0
[*][    18.826]    RsvdMaskSize: 0
[*][    18.826]    RsvdFieldPosition: 0
[*][    18.826]    DirectColorModeInfo: 2
[*][    18.826]    PhysBasePtr: 0xf0000000
[*][    18.826]    LinBytesPerScanLine: 6400
[*][    18.826]    BnkNumberOfImagePages: 7
[*][    18.826]    LinNumberOfImagePages: 7
[*][    18.826]    LinRedMaskSize: 8
[*][    18.826]    LinRedFieldPosition: 16
[*][    18.826]    LinGreenMaskSize: 8
[*][    18.826]    LinGreenFieldPosition: 8
[*][    18.826]    LinBlueMaskSize: 8
[*][    18.826]    LinBlueFieldPosition: 0
[*][    18.826]    LinRsvdMaskSize: 0
[*][    18.826]    LinRsvdFieldPosition: 0
[*][    18.826]    MaxPixelClock: 0
[*][    18.828] Mode: 22e (800x480)
[*][    18.828]    ModeAttributes: 0x9f
[*][    18.828]    WinAAttributes: 0x7
[*][    18.828]    WinBAttributes: 0x0
[*][    18.828]    WinGranularity: 64
[*][    18.828]    WinSize: 64
[*][    18.828]    WinASegment: 0xa000
[*][    18.828]    WinBSegment: 0xa000
[*][    18.828]    WinFuncPtr: 0xc000a833
[*][    18.828]    BytesPerScanline: 800
[*][    18.828]    XResolution: 800
[*][    18.828]    YResolution: 480
[*][    18.828]    XCharSize: 8
[*][    18.828]    YCharSize: 8
[*][    18.828]    NumberOfPlanes: 1
[*][    18.828]    BitsPerPixel: 8
[*][    18.828]    NumberOfBanks: 1
[*][    18.828]    MemoryModel: 4
[*][    18.828]    BankSize: 0
[*][    18.828]    NumberOfImages: 127
[*][    18.828]    RedMaskSize: 0
[*][    18.828]    RedFieldPosition: 0
[*][    18.828]    GreenMaskSize: 0
[*][    18.828]    GreenFieldPosition: 0
[*][    18.828]    BlueMaskSize: 0
[*][    18.828]    BlueFieldPosition: 0
[*][    18.828]    RsvdMaskSize: 0
[*][    18.828]    RsvdFieldPosition: 0
[*][    18.828]    DirectColorModeInfo: 2
[*][    18.828]    PhysBasePtr: 0xf0000000
[*][    18.828]    LinBytesPerScanLine: 800
[*][    18.828]    BnkNumberOfImagePages: 127
[*][    18.828]    LinNumberOfImagePages: 127
[*][    18.828]    LinRedMaskSize: 0
[*][    18.828]    LinRedFieldPosition: 0
[*][    18.828]    LinGreenMaskSize: 0
[*][    18.828]    LinGreenFieldPosition: 0
[*][    18.828]    LinBlueMaskSize: 0
[*][    18.828]    LinBlueFieldPosition: 0
[*][    18.828]    LinRsvdMaskSize: 0
[*][    18.828]    LinRsvdFieldPosition: 0
[*][    18.828]    MaxPixelClock: 0
[*][    18.829] Mode: 22f (800x480)
[*][    18.829]    ModeAttributes: 0x9b
[*][    18.829]    WinAAttributes: 0x7
[*][    18.829]    WinBAttributes: 0x0
[*][    18.829]    WinGranularity: 64
[*][    18.829]    WinSize: 64
[*][    18.829]    WinASegment: 0xa000
[*][    18.829]    WinBSegment: 0xa000
[*][    18.829]    WinFuncPtr: 0xc000a833
[*][    18.829]    BytesPerScanline: 1600
[*][    18.829]    XResolution: 800
[*][    18.829]    YResolution: 480
[*][    18.829]    XCharSize: 8
[*][    18.829]    YCharSize: 8
[*][    18.829]    NumberOfPlanes: 1
[*][    18.829]    BitsPerPixel: 16
[*][    18.829]    NumberOfBanks: 1
[*][    18.830]    MemoryModel: 6
[*][    18.830]    BankSize: 0
[*][    18.830]    NumberOfImages: 63
[*][    18.830]    RedMaskSize: 5
[*][    18.830]    RedFieldPosition: 11
[*][    18.830]    GreenMaskSize: 6
[*][    18.830]    GreenFieldPosition: 5
[*][    18.830]    BlueMaskSize: 5
[*][    18.830]    BlueFieldPosition: 0
[*][    18.830]    RsvdMaskSize: 0
[*][    18.830]    RsvdFieldPosition: 0
[*][    18.830]    DirectColorModeInfo: 2
[*][    18.830]    PhysBasePtr: 0xf0000000
[*][    18.830]    LinBytesPerScanLine: 1600
[*][    18.830]    BnkNumberOfImagePages: 63
[*][    18.830]    LinNumberOfImagePages: 63
[*][    18.830]    LinRedMaskSize: 5
[*][    18.830]    LinRedFieldPosition: 11
[*][    18.830]    LinGreenMaskSize: 6
[*][    18.830]    LinGreenFieldPosition: 5
[*][    18.830]    LinBlueMaskSize: 5
[*][    18.830]    LinBlueFieldPosition: 0
[*][    18.830]    LinRsvdMaskSize: 0
[*][    18.830]    LinRsvdFieldPosition: 0
[*][    18.830]    MaxPixelClock: 0
[*][    18.831] *Mode: 230 (800x480)
[*][    18.831]    ModeAttributes: 0x9b
[*][    18.831]    WinAAttributes: 0x7
[*][    18.831]    WinBAttributes: 0x0
[*][    18.831]    WinGranularity: 64
[*][    18.831]    WinSize: 64
[*][    18.831]    WinASegment: 0xa000
[*][    18.831]    WinBSegment: 0xa000
[*][    18.831]    WinFuncPtr: 0xc000a833
[*][    18.831]    BytesPerScanline: 3200
[*][    18.831]    XResolution: 800
[*][    18.831]    YResolution: 480
[*][    18.831]    XCharSize: 8
[*][    18.831]    YCharSize: 8
[*][    18.831]    NumberOfPlanes: 1
[*][    18.831]    BitsPerPixel: 32
[*][    18.831]    NumberOfBanks: 1
[*][    18.831]    MemoryModel: 6
[*][    18.831]    BankSize: 0
[*][    18.831]    NumberOfImages: 31
[*][    18.831]    RedMaskSize: 8
[*][    18.831]    RedFieldPosition: 16
[*][    18.831]    GreenMaskSize: 8
[*][    18.831]    GreenFieldPosition: 8
[*][    18.831]    BlueMaskSize: 8
[*][    18.831]    BlueFieldPosition: 0
[*][    18.831]    RsvdMaskSize: 0
[*][    18.831]    RsvdFieldPosition: 0
[*][    18.831]    DirectColorModeInfo: 2
[*][    18.831]    PhysBasePtr: 0xf0000000
[*][    18.831]    LinBytesPerScanLine: 3200
[*][    18.831]    BnkNumberOfImagePages: 31
[*][    18.831]    LinNumberOfImagePages: 31
[*][    18.831]    LinRedMaskSize: 8
[*][    18.831]    LinRedFieldPosition: 16
[*][    18.831]    LinGreenMaskSize: 8
[*][    18.831]    LinGreenFieldPosition: 8
[*][    18.831]    LinBlueMaskSize: 8
[*][    18.831]    LinBlueFieldPosition: 0
[*][    18.831]    LinRsvdMaskSize: 0
[*][    18.831]    LinRsvdFieldPosition: 0
[*][    18.831]    MaxPixelClock: 0
[*][    18.833] Mode: 108 (80x60)
[*][    18.833]    ModeAttributes: 0xf
[*][    18.833]    WinAAttributes: 0x7
[*][    18.833]    WinBAttributes: 0x0
[*][    18.833]    WinGranularity: 64
[*][    18.833]    WinSize: 64
[*][    18.833]    WinASegment: 0xa000
[*][    18.833]    WinBSegment: 0xa000
[*][    18.833]    WinFuncPtr: 0xc000a833
[*][    18.833]    BytesPerScanline: 160
[*][    18.833]    XResolution: 80
[*][    18.833]    YResolution: 60
[*][    18.833]    XCharSize: 8
[*][    18.833]    YCharSize: 8
[*][    18.833]    NumberOfPlanes: 1
[*][    18.833]    BitsPerPixel: 4
[*][    18.833]    NumberOfBanks: 1
[*][    18.833]    MemoryModel: 0
[*][    18.833]    BankSize: 0
[*][    18.833]    NumberOfImages: 254
[*][    18.833]    RedMaskSize: 0
[*][    18.833]    RedFieldPosition: 0
[*][    18.833]    GreenMaskSize: 0
[*][    18.833]    GreenFieldPosition: 0
[*][    18.833]    BlueMaskSize: 0
[*][    18.833]    BlueFieldPosition: 0
[*][    18.833]    RsvdMaskSize: 0
[*][    18.833]    RsvdFieldPosition: 0
[*][    18.833]    DirectColorModeInfo: 2
[*][    18.833]    PhysBasePtr: 0x0
[*][    18.833]    LinBytesPerScanLine: 160
[*][    18.833]    BnkNumberOfImagePages: 254
[*][    18.833]    LinNumberOfImagePages: 254
[*][    18.833]    LinRedMaskSize: 0
[*][    18.833]    LinRedFieldPosition: 0
[*][    18.833]    LinGreenMaskSize: 0
[*][    18.833]    LinGreenFieldPosition: 0
[*][    18.833]    LinBlueMaskSize: 0
[*][    18.833]    LinBlueFieldPosition: 0
[*][    18.833]    LinRsvdMaskSize: 0
[*][    18.833]    LinRsvdFieldPosition: 0
[*][    18.833]    MaxPixelClock: 0
[*][    18.834] Mode: 102 (800x600)
[*][    18.834]    ModeAttributes: 0x1f
[*][    18.834]    WinAAttributes: 0x7
[*][    18.834]    WinBAttributes: 0x0
[*][    18.834]    WinGranularity: 64
[*][    18.834]    WinSize: 64
[*][    18.834]    WinASegment: 0xa000
[*][    18.834]    WinBSegment: 0xa000
[*][    18.834]    WinFuncPtr: 0xc000a833
[*][    18.834]    BytesPerScanline: 100
[*][    18.834]    XResolution: 800
[*][    18.834]    YResolution: 600
[*][    18.834]    XCharSize: 8
[*][    18.834]    YCharSize: 8
[*][    18.834]    NumberOfPlanes: 4
[*][    18.834]    BitsPerPixel: 4
[*][    18.834]    NumberOfBanks: 1
[*][    18.834]    MemoryModel: 3
[*][    18.834]    BankSize: 0
[*][    18.834]    NumberOfImages: 31
[*][    18.834]    RedMaskSize: 0
[*][    18.834]    RedFieldPosition: 0
[*][    18.834]    GreenMaskSize: 0
[*][    18.834]    GreenFieldPosition: 0
[*][    18.834]    BlueMaskSize: 0
[*][    18.834]    BlueFieldPosition: 0
[*][    18.834]    RsvdMaskSize: 0
[*][    18.834]    RsvdFieldPosition: 0
[*][    18.834]    DirectColorModeInfo: 2
[*][    18.834]    PhysBasePtr: 0x0
[*][    18.834]    LinBytesPerScanLine: 100
[*][    18.834]    BnkNumberOfImagePages: 31
[*][    18.835]    LinNumberOfImagePages: 31
[*][    18.835]    LinRedMaskSize: 0
[*][    18.835]    LinRedFieldPosition: 0
[*][    18.835]    LinGreenMaskSize: 0
[*][    18.835]    LinGreenFieldPosition: 0
[*][    18.835]    LinBlueMaskSize: 0
[*][    18.835]    LinBlueFieldPosition: 0
[*][    18.835]    LinRsvdMaskSize: 0
[*][    18.835]    LinRsvdFieldPosition: 0
[*][    18.835]    MaxPixelClock: 0
[*][    18.835] (II) CHROME(0): <default monitor>: Using hsync value of 48.36 kHz
[*][    18.835] (II) CHROME(0): <default monitor>: Using vrefresh value of 60.00 Hz
[*][    18.835] (WW) CHROME(0): Unable to estimate virtual size
[*][    18.835] (II) CHROME(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
[*][    18.835] (--) CHROME(0): Virtual size is 1600x1200 (pitch 1600)
[*][    18.835] (**) CHROME(0): *Built-in mode "1600x1200"
[*][    18.835] (**) CHROME(0): *Built-in mode "1280x1024"
[*][    18.835] (**) CHROME(0): *Built-in mode "1280x768"
[*][    18.835] (**) CHROME(0): *Built-in mode "1024x768": 0.0 MHz, 48363.6 kHz, 60.5 Hz
[*][    18.835] (II) CHROME(0): Modeline "1024x768"x60.5    0.00  1024 0 0 0  768 0 0 0 (48363.6 kHz)
[*][    18.835] (**) CHROME(0): *Built-in mode "800x600"
[*][    18.835] (**) CHROME(0): *Built-in mode "720x576"
[*][    18.835] (**) CHROME(0): *Built-in mode "720x540"
[*][    18.835] (**) CHROME(0): *Built-in mode "800x480"
[*][    18.835] (**) CHROME(0): *Built-in mode "720x480"
[*][    18.835] (**) CHROME(0): *Built-in mode "640x480"
[*][    18.835] (**) CHROME(0): Display dimensions: (310, 230) mm
[*][    18.835] (**) CHROME(0): DPI set to (131, 132)
[*][    18.835] (II) Loading sub module "fb"
[*][    18.835] (II) LoadModule: "fb"
[*][    18.836] (II) Loading /usr/lib/xorg/modules/libfb.so
[*][    18.836] (II) Module fb: vendor="X.Org Foundation"
[*][    18.836]    compiled for 1.9.0, module version = 1.0.0
[*][    18.836]    ABI class: X.Org ANSI C Emulation, version 0.4
[*][    18.836] (II) Loading sub module "xaa"
[*][    18.836] (II) LoadModule: "xaa"
[*][    18.837] (II) Loading /usr/lib/xorg/modules/libxaa.so
[*][    18.837] (II) Module xaa: vendor="X.Org Foundation"
[*][    18.837]    compiled for 1.9.0, module version = 1.2.1
[*][    18.837]    ABI class: X.Org Video Driver, version 8.0
[*][    18.837] (II) Loading sub module "ramdac"
[*][    18.837] (II) LoadModule: "ramdac"
[*][    18.837] (II) Module "ramdac" already built-in
[*][    18.837] (II) CHROME(0): VIAUnmapMem
[*][    18.837] (II) UnloadModule: "vesa"
[*][    18.837] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[*][    18.837] (II) UnloadModule: "fbdev"
[*][    18.837] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[*][    18.837] (II) UnloadModule: "fbdevhw"
[*][    18.837] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[*][    18.837] (--) Depth 24 pixmap format is 32 bpp
[*][    18.837] (II) CHROME(0): VIAScreenInit
[*][    18.837] (II) CHROME(0): VIAMapFB
[*][    18.837] (--) CHROME(0): mapping framebuffer @ 0xf0000000 with size 0x4000000
[*][    18.845] (--) CHROME(0): Frame buffer start: 0xaf566000, free start: 0x753000 end: 0x4000000
[*][    18.846] (II) CHROME(0): VIAMapMMIO
[*][    18.846] (--) CHROME(0): mapping MMIO @ 0xd1000000 with size 0x9000
[*][    18.846] (--) CHROME(0): mapping BitBlt MMIO @ 0xd1200000 with size 0x200000
[*][    18.846] (II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[*][    18.846] (II) CHROME(0): VIASave
[*][    18.846] (II) CHROME(0): Primary
[*][    18.948] (II) CHROME(0): Primary Adapter! saving VGA_SR_ALL !!
[*][    18.948] (II) CHROME(0): Crtc...
[*][    18.948] (II) CHROME(0): TVSave...
[*][    18.948] (WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
[*][    18.948] (II) CHROME(0): Trying VBE Mode 1600x1200 (0xc124) Refresh 60.00:
[*][    18.948] (II) CHROME(0): ViaVbeSetRefresh
[*][    18.948] (II) CHROME(0): Active Device: 2
[*][    18.948] (II) CHROME(0): Refresh Rate Index: 0
[*][    19.292] (II) CHROME(0): VIAAdjustFrame 0x0
[*][    19.305] (II) CHROME(0): - Blanked
[*][    19.305] drmOpenDevice: node name is /dev/dri/card0
[*][    19.309] drmOpenDevice: node name is /dev/dri/card0
[*][    19.374] drmOpenByBusid: Searching for BusID PCI:1:0:0
[*][    19.375] drmOpenDevice: node name is /dev/dri/card0
[*][    19.375] drmOpenDevice: open result is 11, (OK)
[*][    19.375] drmOpenByBusid: drmOpenMinor returns 11
[*][    19.375] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[*][    19.375] (II) [drm] loaded kernel module for "via" driver.
[*][    19.375] (II) [drm] DRM interface version 1.3
[*][    19.375] (II) [drm] DRM open master succeeded.
[*][    19.375] (II) CHROME(0): [drm] Using the DRM lock SAREA also for drawables.
[*][    19.375] (II) CHROME(0): [drm] framebuffer handle = 0xf0000000
[*][    19.375] (II) CHROME(0): [drm] added 1 reserved context for kernel
[*][    19.375] (II) CHROME(0): X context handle = 0x1
[*][    19.375] (II) CHROME(0): [drm] installed DRM signal handler
[*][    19.375] (II) CHROME(0): [dri] visual configs initialized.
[*][    19.375] (II) CHROME(0): [drm] register handle = 0xd1000000
[*][    19.375] (II) CHROME(0): [drm] framebuffer handle = 0xf0000000
[*][    19.375] (II) CHROME(0): [drm] mmio Registers = 0xd1000000
[*][    19.375] (II) CHROME(0): [dri] mmio mapped.
[*][    19.375] (II) CHROME(0): - Visuals set up
[*][    19.375] (II) CHROME(0): VIAInternalScreenInit
[*][    19.375] (II) CHROME(0): - B & W
[*][    19.375] (II) CHROME(0): CursorStart: 0x3fc0000
[*][    19.375] (II) CHROME(0): Frame Buffer From (0,0) To (1600,4800)
[*][    19.375] (II) CHROME(0): Using 3600 lines for offscreen memory.
[*][    19.376] (II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)
[*][    19.376]    Screen to screen bit blits
[*][    19.376]    Solid filled rectangles
[*][    19.376]    8x8 mono pattern filled rectangles
[*][    19.376]    8x8 color pattern filled rectangles
[*][    19.376]    Solid Lines
[*][    19.376]    Dashed Lines
[*][    19.376]    Image Writes
[*][    19.377]    Setting up tile and stipple cache:
[*][    19.377]            32 128x128 slots
[*][    19.377]            24 256x256 slots
[*][    19.377]            13 512x512 slots
[*][    19.377]            32 8x8 color pattern slots
[*][    19.377] (==) CHROME(0): Backing store disabled
[*][    19.377] (II) CHROME(0): - Backing store set up
[*][    19.377] (II) CHROME(0): - SW cursor set up
[*][    19.377] (II) CHROME(0): VIAHWCursorInit
[*][    19.377] (II) CHROME(0): HWCursor ARGB enabled
[*][    19.377] (II) CHROME(0): - Def Color map set up
[*][    19.377] (II) CHROME(0): VIALoadPalette: numColors: 256
[*][    19.377] (II) CHROME(0): VIALoadRgbLut
[*][    19.377] (II) CHROME(0): - Palette loaded
[*][    19.377] (==) CHROME(0): DPMS enabled
[*][    19.377] (II) CHROME(0): - DPMS set up
[*][    19.377] (II) CHROME(0): - Color maps etc. set up
[*][    19.377] (II) CHROME(0): [drm] Detected AGP vendor 0x1106, device 0x0314
[*][    19.377] (II) CHROME(0): [drm] Didn't find any AGP v3 compatible device. Trying AGP 4X mode.
[*][    19.377] (II) CHROME(0): [drm] Trying to enable AGP fast writes.
[*][    19.378] (II) CHROME(0): [drm] drmAgpEnabled succeeded
[*][    19.429] (II) CHROME(0): [drm] agpAddr = 0xe0000000
[*][    19.432] (II) CHROME(0): [drm] agpBase = (nil)
[*][    19.432] (II) CHROME(0): [drm] agpAddr = 0xe0000000
[*][    19.432] (II) CHROME(0): [drm] agpSize = 0x01e00000
[*][    19.432] (II) CHROME(0): [drm] agp physical addr = 0x00000000
[*][    19.432] (II) CHROME(0): [dri] Using AGP.
[*][    19.432] (II) CHROME(0): [drm] Using 36113888 bytes for DRM memory heap.
[*][    19.432] (II) CHROME(0): [dri] Frame buffer initialized.
[*][    19.432] (II) CHROME(0): [DRI] installation complete
[*][    19.432] (II) CHROME(0): [dri] Kernel data initialized.
[*][    19.432] (WW) CHROME(0): [drm] Failure adding IRQ handler. Falling back to IRQ-free operation.
[*][    19.432] (II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
[*][    19.432] (II) CHROME(0): direct rendering enabled
[*][    19.435] (II) CHROME(0): [Xv] Using PCI DMA for Xv image transfer.
[*][    19.435] Fulfilled via DRI at 30726400
[*][    19.439] (II) CHROME(0): Benchmarking video copy.  Less time is better.
[*][    19.446] (--) CHROME(0): Timed   libc YUV420 copy... 5911152. Throughput: 171.5 MiB/s.
[*][    19.453] (--) CHROME(0): Timed kernel YUV420 copy... 5816307. Throughput: 174.3 MiB/s.
[*][    19.461] (--) CHROME(0): Timed    SSE YUV420 copy... 5932351. Throughput: 170.9 MiB/s.
[*][    19.468] (--) CHROME(0): Timed    MMX YUV420 copy... 5866727. Throughput: 172.8 MiB/s.
[*][    19.468] (--) CHROME(0): Ditching 3DNow! YUV420 copy. Not supported by CPU.
[*][    19.475] (--) CHROME(0): Timed   MMX2 YUV420 copy... 5929031. Throughput: 171.0 MiB/s.
[*][    19.475] Freed 30726400 (pool 2)
[*][    19.475] (--) CHROME(0): Using kernel YUV42X copy for video.
[*][    19.475] (II) CHROME(0): [XvMC] Registering chromeXvMC.
[*][    19.475] (II) CHROME(0): [XvMC] Initialized XvMC extension.
[*][    19.475] (II) CHROME(0): - Done
[*][    19.475] (==) RandR enabled
[*][    19.475] (II) Initializing built-in extension Generic Event Extension
[*][    19.476] (II) Initializing built-in extension SHAPE
[*][    19.476] (II) Initializing built-in extension MIT-SHM
[*][    19.476] (II) Initializing built-in extension XInputExtension
[*][    19.476] (II) Initializing built-in extension XTEST
[*][    19.476] (II) Initializing built-in extension BIG-REQUESTS
[*][    19.476] (II) Initializing built-in extension SYNC
[*][    19.476] (II) Initializing built-in extension XKEYBOARD
[*][    19.476] (II) Initializing built-in extension XC-MISC
[*][    19.476] (II) Initializing built-in extension SECURITY
[*][    19.476] (II) Initializing built-in extension XINERAMA
[*][    19.476] (II) Initializing built-in extension XFIXES
[*][    19.476] (II) Initializing built-in extension RENDER
[*][    19.476] (II) Initializing built-in extension RANDR
[*][    19.476] (II) Initializing built-in extension COMPOSITE
[*][    19.476] (II) Initializing built-in extension DAMAGE
[*][    19.476] (II) Initializing built-in extension GESTURE
[*][    19.492] (II) AIGLX: Screen 0 is not DRI2 capable
[*][    19.492] drmOpenDevice: node name is /dev/dri/card0
[*][    19.492] drmOpenDevice: open result is 12, (OK)
[*][    19.492] drmOpenByBusid: Searching for BusID PCI:1:0:0
[*][    19.492] drmOpenDevice: node name is /dev/dri/card0
[*][    19.492] drmOpenDevice: open result is 12, (OK)
[*][    19.492] drmOpenByBusid: drmOpenMinor returns 12
[*][    19.492] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[*][    19.504] (II) AIGLX: enabled GLX_SGI_make_current_read
[*][    19.505] (II) AIGLX: Loaded and initialized /usr/lib/dri/unichrome_dri.so
[*][    19.505] (II) GLX: Initialized DRI GL provider for screen 0
[*][    19.534] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[*][    19.545] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[*][    19.546] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[*][    19.546] (II) LoadModule: "evdev"
[*][    19.546] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[*][    19.547] (II) Module evdev: vendor="X.Org Foundation"
[*][    19.547]    compiled for 1.9.0, module version = 2.3.2
[*][    19.547]    Module class: X.Org XInput Driver
[*][    19.547]    ABI class: X.Org XInput driver, version 11.0
[*][    19.547] (**) Power Button: always reports core events
[*][    19.547] (**) Power Button: Device: "/dev/input/event2"
[*][    19.547] (II) Power Button: Found keys
[*][    19.547] (II) Power Button: Configuring as keyboard
[*][    19.547] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[*][    19.547] (**) Option "xkb_rules" "evdev"
[*][    19.547] (**) Option "xkb_model" "pc105"
[*][    19.547] (**) Option "xkb_layout" "de"
[*][    19.547] (**) Option "xkb_variant" "nodeadkeys"
[*][    19.547] (**) Option "xkb_options" "lv3:ralt_switch"
[*][    19.551] (II) XKB: reuse xkmfile /var/lib/xkb/server-32CF54508D1127B0F32CA64F4D9024E09F623E78.xkm
[*][    19.553] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[*][    19.554] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[*][    19.554] (**) Video Bus: always reports core events
[*][    19.554] (**) Video Bus: Device: "/dev/input/event4"
[*][    19.554] (II) Video Bus: Found keys
[*][    19.554] (II) Video Bus: Configuring as keyboard
[*][    19.554] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[*][    19.554] (**) Option "xkb_rules" "evdev"
[*][    19.554] (**) Option "xkb_model" "pc105"
[*][    19.554] (**) Option "xkb_layout" "de"
[*][    19.554] (**) Option "xkb_variant" "nodeadkeys"
[*][    19.554] (**) Option "xkb_options" "lv3:ralt_switch"
[*][    19.554] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[*][    19.555] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[*][    19.555] (**) Power Button: always reports core events
[*][    19.555] (**) Power Button: Device: "/dev/input/event0"
[*][    19.555] (II) Power Button: Found keys
[*][    19.555] (II) Power Button: Configuring as keyboard
[*][    19.555] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[*][    19.555] (**) Option "xkb_rules" "evdev"
[*][    19.555] (**) Option "xkb_model" "pc105"
[*][    19.555] (**) Option "xkb_layout" "de"
[*][    19.555] (**) Option "xkb_variant" "nodeadkeys"
[*][    19.555] (**) Option "xkb_options" "lv3:ralt_switch"
[*][    19.555] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[*][    19.555] (II) No input driver/identifier specified (ignoring)
[*][    19.561] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[*][    19.561] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[*][    19.561] (**) AT Translated Set 2 keyboard: always reports core events
[*][    19.561] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[*][    19.561] (II) AT Translated Set 2 keyboard: Found keys
[*][    19.561] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[*][    19.561] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[*][    19.561] (**) Option "xkb_rules" "evdev"
[*][    19.561] (**) Option "xkb_model" "pc105"
[*][    19.561] (**) Option "xkb_layout" "de"
[*][    19.561] (**) Option "xkb_variant" "nodeadkeys"
[*][    19.561] (**) Option "xkb_options" "lv3:ralt_switch"
[*][    19.562] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event5)
[*][    19.562] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[*][    19.562] (**) PS/2 Mouse: always reports core events
[*][    19.562] (**) PS/2 Mouse: Device: "/dev/input/event5"
[*][    19.562] (II) PS/2 Mouse: Found 3 mouse buttons
[*][    19.562] (II) PS/2 Mouse: Found relative axes
[*][    19.562] (II) PS/2 Mouse: Found x and y relative axes
[*][    19.562] (II) PS/2 Mouse: Configuring as mouse
[*][    19.562] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[*][    19.562] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[*][    19.562] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[*][    19.562] (II) PS/2 Mouse: initialized for relative axes.
[*][    19.563] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse0)
[*][    19.563] (II) No input driver/identifier specified (ignoring)
[*][    19.563] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event6)
[*][    19.563] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[*][    19.563] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[*][    19.563] (II) LoadModule: "synaptics"
[*][    19.564] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[*][    19.564] (II) Module synaptics: vendor="X.Org Foundation"
[*][    19.564]    compiled for 1.9.0, module version = 1.2.2
[*][    19.564]    Module class: X.Org XInput Driver
[*][    19.564]    ABI class: X.Org XInput driver, version 11.0
[*][    19.564] (II) Synaptics touchpad driver version 1.2.2
[*][    19.564] (**) Option "Device" "/dev/input/event6"
[*][    19.564] (II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[*][    19.564] (II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[*][    19.564] (II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[*][    19.564] (II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
[*][    19.564] (II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[*][    19.564] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[*][    19.564] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[*][    19.564] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[*][    19.564] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[*][    19.564] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 0
[*][    19.564] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[*][    19.564] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[*][    19.565] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[*][    19.565] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[*][    19.565] (II) No input driver/identifier specified (ignoring)
[/LIST]


```

Thanks for your help so far, the german forum and the #xorg channel didn´t have any solutions so far - i´ve been working on this for some weeks by now...

---

### Post by fluft on 2011-12-07
hello, I hope its o.k to ask for help also. as i am having trouble too

my LCD needs 1280 x720 ( 70hz)  i have tried the commands suggested, but i think i have messed my xrandr file up at the bottom.

these quotes below are supposed to be code quotes sorry. :

> xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1280 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0*    51.0  
   960x540        52.0  
   840x525        53.0     54.0  
   800x600        55.0     56.0     57.0  
   800x512        58.0  
   720x450        59.0  
   680x384        60.0     61.0  
   640x512        62.0  
   640x480        63.0     64.0  
   576x432        65.0     66.0  
   512x384        67.0     68.0  
   400x300        69.0     70.0     71.0  
   320x240        72.0  
   1280x720_70.00   59.9  
  1280x720_60.00 (0x1dd)   74.5MHz
        h: width  1280 start 1344 end 1472 total 1664 skew    0 clock   44.8KHz
        v: height  720 start  723 end  728 total  748           clock   59.9Hz


at the bottom of the xrandr list you can see my attempt to add 1280x720, i think i may have tried to add in the wrong format?

here is my xorg.conf file 

> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.29  (buildd@roseapple)  Fri Feb 25 14:43:24 UTC 2011

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Mon Apr 18 15:15:12 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 72.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 SE/7200 GS"
EndSection

Section "Screen"

# Removed Option "metamodes" "1152x864_70 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "modes" "1280x720_70"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Thank you for any help, i am using

Ubuntu 11.04 - the Natty Narwhal - released in April 2011
2.32.1 gnome 
peace: )

---

### Post by ajmc on 2012-05-01
I followed the steps stated on this thread and good to say that I have some added resolution options.  At first I only have an option 
1024x768.  After following the steps on this thread 800x600 was added.  Here are the specifications of my system:

Laptop: acer aspire 4736
VGA: VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

~xrandr output
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       71.0* 
   800x600        61.0  
   640x480        60.0  
  1368x768_60.00 (0x148)   85.9MHz
        h: width  1368 start 1440 end 1584 total 1800 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
  test (0x149)   62.2MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   46.9KHz
        v: height  768 start  771 end  775 total  797           clock   58.8Hz

OS: Ubuntu 12.04

Previous experience:  Yesterday I was using 10.04 and everything worked well.  The resolution was perfect not until I updated to 11.04.  By default 1024x768 is displayed which makes the screen a bit stretched. Here is how it looks like after the update.

[IMG]http://i50.tinypic.com/2iktq8w.png[/IMG]

---

### Post by Juankof on 2012-05-02
> **ajmc said:**
> I followed the steps stated on this thread and good to say that I have some added resolution options.  At first I only have an option 
1024x768.  After following the steps on this thread 800x600 was added.  Here are the specifications of my system:

Laptop: acer aspire 4736
VGA: VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

~xrandr output
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       71.0* 
   800x600        61.0  
   640x480        60.0  
  1368x768_60.00 (0x148)   85.9MHz
        h: width  1368 start 1440 end 1584 total 1800 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
  test (0x149)   62.2MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   46.9KHz
        v: height  768 start  771 end  775 total  797           clock   58.8Hz

OS: Ubuntu 12.04

Previous experience:  Yesterday I was using 10.04 and everything worked well.  The resolution was perfect not until I updated to 11.04.  By default 1024x768 is displayed which makes the screen a bit stretched. Here is how it looks like after the update.


I got the same problem. Any ideas?

---

### Post by ajmc on 2012-05-02
I haven't figure it out yet.  A friend suggested to install intel's propriety driver and gave me this link >[ http://intellinuxgraphics.org/]("http://intellinuxgraphics.org/").  I haven't tried installing it yet.

---

### Post by ajmc on 2012-05-02
> **Juankof said:**
> I got the same problem. Any ideas?

I finally found an answer: [http://www.icpep.org/mobile-series-4-display-problem-on-ubuntu-10-10-or-higher/](http://www.icpep.org/mobile-series-4-display-problem-on-ubuntu-10-10-or-higher/)

---

### Post by Poilaupat on 2012-09-14
> **nishdo said:**
> Hi, for those who see or are getting this error from xrandr:
xrandr: Failed to get size of gamma for output default

One more check, which was annoyingly obvious afterwards, but still spent an hour until I remembered. I solved this in my system by remembering one change I'd made before reinstalling Ubuntu 10.10. Having got a second computer in the meantime, I'd added a KVM switch to manage both machines with one monitor. 

So, when reinstalling Ubuntu, whatever this KVM switch was doing, it was blocking Ubuntu in detecting my monitor. All I got was minimum resolution all the time. Doh! 

By removing the KVM for the purposes of the installation, connecting the monitor directly, that error went away easy, detect monitor worked fine. Now back to nVidia drivers and 3D.

You saved my day. I had exactly the same problem with a KVM... I restarted after unplugging it and all went fine, I finally had my 1680*1060 resolution. Just to be completely sure, I restarted with the KVM (in case it would have worked once the configuration was wrote) but I was back with 1280*768 :sad:

What is sad is that the other station plugged on the KVM is under Windows Vista and no resolution problem with it ! :lolflag:

---

### Post by Peter2009 on 2012-10-15
> **realzippy said:**
> try:
```
xrandr --newmode test 62.25  1024 1072 1176 1328  768 771 775 797 -hsync +vsync
```

```
xrandr --addmode default test
```

```
xrandr --output default --mode test
```
-------------------------------------------------------------------------------------------------

BTW,folks,this cannot turn to an one-size-fits-all graphics HowTo.

So read e.g.this for general xrandr usage:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)


Hi James! Could you please help here!

I have two machine on which I cannot get the multi display going. I will start with one.

Its a:
GeForce 8200M, Ubuntu 12.04

Before I carry on I would like to play with the xorg.conf file but I am a bit worried if I would not be able to long in again, could you please give more details how to recovery if this happen???

here is my  xrandr -q reply

```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1360 x 768, maximum 1366 x 768
default connected 1360x768+0+0 0mm x 0mm
   1366x768       50.0  
   1360x768       51.0* 
   1024x768       52.0     53.0  
   960x540        54.0  
   840x525        55.0  
   832x624        56.0  
   800x600        57.0     58.0     59.0     60.0     61.0  
   800x512        62.0  
   720x450        63.0  
   720x400        64.0  
   700x525        65.0  
   680x384        66.0     67.0  
   640x512        68.0     69.0  
   640x480        70.0     71.0     72.0     73.0     74.0  
   640x400        75.0  
   640x350        76.0  
   576x432        77.0     78.0     79.0     80.0     81.0     82.0     83.0  
   512x384        84.0     85.0     86.0     87.0     88.0  
   416x312        89.0  
   400x300        90.0     91.0     92.0     93.0     94.0  
   360x200        95.0  
   320x240        96.0     97.0     98.0     99.0  
   320x200       100.0  
   320x175       101.0  


```

I tried all the Edit and all Configure crtc 0 failed

I got here because I want to get the other VGA output going but I want to sort out the
```

xrandr: Failed to get size of gamma for output default

```

also here is my /etc/X11/xorg.conf

```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS" 
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

I tried lot of things all on this threat but no working.

Also went ot that like and try to do the xorg.conf but had a fatal error

Please help!

---

