---
title: "Only able to get 1024x768 and 800x600 resolution. Monitor not detected"
date: 2012-07-21
forum: General Help
---

### Post by MBCommander on 2012-07-21
xorg 0 log - [http://pastebin.com/ef9v3w5g](http://pastebin.com/ef9v3w5g)
xorg 1 log - [http://pastebin.com/VrJEzT3T](http://pastebin.com/VrJEzT3T)
xorg conf -  [http://pastebin.com/GWFwZFQs](http://pastebin.com/GWFwZFQs)

NVIDIA Driver Version: 295.40
Model : CRT-1 (CRT-1 on GPU-0)
Resolution: 1024x768

Monitor: [http://www.amazon.co.uk/HW191D-Widescreen-Monitor-1440x900-Speakers/dp/B000GYHS6Y](http://www.amazon.co.uk/HW191D-Widescreen-Monitor-1440x900-Speakers/dp/B000GYHS6Y)

Dual booting. HDD1 = Windows 7. HDD2 = Ubuntu

Also: Sorry if this thread has been asked a million times. 

Hi all,

I installed Ubuntu (the latest version) yesterday and I have been having problems with the resolution going higher than 1024x768. On Windows 7, my monitor is picked up without problems and can go to this resolution. However on Ubuntu I seem to be unable to detect the correct monitor - it still shows the screen output though.

Someone suggested that Ubuntu was not detecting my monitor but I have no clue how to make it do so. I have printed all the relevant information at the top of the thread. 

I have tried removing the Nvidia drivers but to no help.

Any suggestions would be very appreciated :)

Thanks!


Edit: Solved! Check below

---

### Post by cwsnyder on 2012-07-21
[https://wiki.ubuntu.com/X/Config/Resolution/](https://wiki.ubuntu.com/X/Config/Resolution/) is the official wiki on setting your screen resolution.

If you need more explanation or a clearer step-by-step method, check [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

---

### Post by MBCommander on 2012-07-21
xrandr is saying my maximum allowed resolution is 1024x768. I don't think it is properly detecting my monitor

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   640x480        51.0  
   800x600        52.0     53.0     54.0  
   680x384        55.0     56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0

---

### Post by cwsnyder on 2012-07-21
Try setting a new mode for xrandr, as in: ```
$ cvt 1440 900
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
$ xrandr --newmode "1440x900" 106.50 1440 1528 1672 1904 900 903 909 934 -hsync +vsync
$ xrandr --addmode "Screen 0" 1440x900
$ xrandr --output "Screen 0" --mode 1440x900
```

---

### Post by MBCommander on 2012-07-21
Hi there

That did not work. Output is below:(

dominic@dominic-pc:~$ cvt 1440 900
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
dominic@dominic-pc:~$ xrandr --newmode "1440x900" 106.50 1440 1528 1672 1904 900 903 909 934 -hsync +vsync
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19
dominic@dominic-pc:~$ xrandr --addmode "Screen 0" 1440x900
xrandr: Failed to get size of gamma for output default
xrandr: cannot find output "Screen 0"
dominic@dominic-pc:~$ 
dominic@dominic-pc:~$ xrandr --output "Screen 0" --mode 1440x900
xrandr: Failed to get size of gamma for output default
warning: output Screen 0 not found; ignoring

---

### Post by cwsnyder on 2012-07-22
I double-checked against your xrandr output and log files.  You may try CRT-1 as your device instead of "Screen 0" and see if that works better.  You don't need quotes around CRT-1 because there is no space in the name.

---

### Post by MBCommander on 2012-07-22
I solved my problem thanks to some folks at the #ubuntu channel

Note this solution was specific ( I believe) to my monitor - HaansG HW191D

[http://www.linuxformat.com/content/xorgconf-hacking](http://www.linuxformat.com/content/xorgconf-hacking)
I copied the two files from that link to the respective directories

After I went to [http://askubuntu.com/questions/83538/monitor-resolution-changes-after-login-lower-than-optimal](http://askubuntu.com/questions/83538/monitor-resolution-changes-after-login-lower-than-optimal)

and followed the top answer, changing my monitor.xml width and height

Now it works great.

cwsnyder thanks a lot for your time also!

---

