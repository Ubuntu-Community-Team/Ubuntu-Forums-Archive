---
title: "Forcing resolution using xrandr"
date: 2010-04-12
forum: General Help
---

### Post by stiggy1605 on 2010-04-12
I installed Ubuntu 9.10 on this laptop about a week ago, and after failing to find any graphic drivers (got a SiS Mirage 3 chipset) I tried upgrading to the 10.04 beta to see if it would work any better.

Unfortunately it didn't, and I can't change the resolution to anything other than 640x480 or 800x600. This monitor is capable of 1368x768, so I've been trying to use the xrandr command to force it to that.

I've been following the instructions on [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) but they aren't working.

Here's some copy and paste from the terminal of the different steps in the tutorial:
```
ben@ben-laptop:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0
```

```
ben@ben-laptop:~$ cvt 1368 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync

```


Adding 1368x768 using --newmode
```
ben@ben-laptop:~$ xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  18
  Current serial number in output stream:  18

```

Adding 1280x768 using --newmode
```
ben@ben-laptop:~$ cvt 1280 768
# 1280x768 59.87 Hz (CVT) hsync: 47.78 kHz; pclk: 79.50 MHz
Modeline "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
ben@ben-laptop:~$ xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
ben@ben-laptop:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
  1280x768_60.00 (0x72)   79.0MHz
        h: width  1280 start 1344 end 1472 total 1664 skew    0 clock   47.5KHz
        v: height  768 start  771 end  781 total  798           clock   59.5Hz

```
Then I add the mode, and try to set the resolution as 1280x768 using the new mode
```
ben@ben-laptop:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 1280 x 720
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
   1280x720_60.00   59.5
ben@ben-laptop:~$ xrandr --output default --mode 1280x720_60.00
xrandr: Configure crtc 0 failed


```

Can anyone see where I'm going wrong? I've been trying to figure this out for a couple of days now, I'm nearing the point of tearing my hair out in frustration so any help would be great.

---

### Post by in2smithereens on 2010-04-29
I have the exact same problem -- same intended resolution, same steps carried out on [http://wiki.ubuntu.com/X/Config/Resolution](http://wiki.ubuntu.com/X/Config/Resolution) and tried many many other solutions from threads on this and other sites -- and same results.  However, I have Ubuntu 9.04 and a nVidia GeForce GT 330M graphics processing unit.  Aside from your steps, I also tried installing a different version of the driver.  Are you still having this problem?  If not, do you remember how you fixed it??

in2smithereens - definitely a green user still :)
---Sony VAIO VPCCW22FX, Intel Core i3 CPU @2.13GHz, 4GB DDR3, 500GB HDD, 64-bit, nVidia GeForce GT 330M, 14", Resolution 1366x768 ---

---

### Post by mhgsys on 2010-05-13
You need to install the correct driver for sis 771/671

Since you are using 10.04 

follow;[http://ubuntuforums.org/showthread.php?t=958967&page=38](http://ubuntuforums.org/showthread.php?t=958967&page=38)

---

