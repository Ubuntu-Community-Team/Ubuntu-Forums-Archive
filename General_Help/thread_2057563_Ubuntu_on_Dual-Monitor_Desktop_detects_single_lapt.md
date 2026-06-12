---
title: "Ubuntu on Dual-Monitor Desktop detects single laptop screen"
date: 2012-09-13
forum: General Help
---

### Post by wiseguy12851 on 2012-09-13
I have a custom built gaming computer with 2 monitors, after using Ubuntu on my laptop since 8.04 on up to 12.04 I decided to install the same 12.04 on my desktop which usually runs Windows.

The main problem I'm having now is it only detects 1 monitor and treats it like a laptop monitor. I read in other places this is usually dismissed by the community as a "silly" bug and should be fixed sometime soon as I guess most people have just one monitor anyways.

During installation it detected the 2nd monitor just fine and duplicated my screen onto it but after installation it remained unused. At one point I did use synaptic to export a list of all the installed packages on my laptop to my Desktop for download so I don't know if that fiddled with anything or not.

I use the 2nd monitor pretty often for a lot of different stuff. Is there anyway to fix this, if theres no way to fix it now and I have to wait until some unspecified time in the future for it to be fixed then I need to stop setting up Ubuntu and re-install Windows.

Also, is this Ubuntu specific, I have other Desktops installed so would Kubuntu or some other one be able to detect the 2nd monitor?

---

### Post by cortman on 2012-09-13
To see if we can fix it with a quick command, run

```
xrandr
```

with both screens connected, and post output.

---

### Post by wiseguy12851 on 2012-09-13
The output is below

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      50.0     51.0* 
   1680x1050      52.0     53.0  
   1600x1024      54.0  
   1440x900       55.0  
   1400x1050      56.0     57.0     58.0  
   1360x768       59.0     60.0  
   1280x1024      61.0     62.0     63.0  
   1280x960       64.0     65.0  
   1152x864       66.0     67.0     68.0     69.0     70.0     71.0     72.0  
   1024x768       73.0     74.0     75.0     76.0     77.0     78.0  
   960x720        79.0     80.0  
   960x600        81.0  
   960x540        82.0  
   928x696        83.0     84.0  
   896x672        85.0     86.0  
   840x525        87.0     88.0     89.0     90.0     91.0  
   832x624        92.0  
   800x600        93.0     94.0     95.0     96.0     97.0     98.0     99.0    100.0    101.0    102.0  
   800x512       103.0  
   720x450       104.0  
   720x400       105.0  
   700x525       106.0    107.0    108.0    109.0  
   680x384       110.0    111.0  
   640x512       112.0    113.0    114.0  
   640x480       115.0    116.0    117.0    118.0    119.0    120.0    121.0    122.0  
   640x400       123.0  
   640x350       124.0  
   576x432       125.0    126.0    127.0    128.0    129.0    130.0    131.0  
   512x384       132.0    133.0    134.0    135.0    136.0  
   416x312       137.0  
   400x300       138.0    139.0    140.0    141.0    142.0  
   360x200       143.0  
   320x240       144.0    145.0    146.0    147.0  
   320x200       148.0  
   320x175       149.0
```

---

### Post by cortman on 2012-09-13
Hm, what about

```
lspci | grep -i vga
lshw -C video
```

Please post output.

Oh, and I doubt Kubuntu would do a better job of detecting- sounds like drivers to me.

---

### Post by wiseguy12851 on 2012-09-13
Following output below

> lspci | grep -i vga```
01:00.0 VGA compatible controller: NVIDIA Corporation GT200 [GeForce GTX 260] (rev a1)
```> lshw -C video```
*-display               
       description: VGA compatible controller
       product: GT200 [GeForce GTX 260]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:cc000000-ccffffff memory:b0000000-bfffffff memory:ca000000-cbffffff ioport:8c00(size=128) memory:cd000000-cd07ffff
```

---

### Post by wiseguy12851 on 2012-09-14
In about 3 hours I'm going to switch to the NVIDIA post release update proprietary driver, perhaps that may reset whatever is convincing Ubuntu it's handling a laptop screen.

Would anything else come into factor for this problem, such as some of the packages that carried over from my laptop  or something to do with the linux kernel. Maye a configuration file. Or just *buntu. If it's *buntu then it's not fixable and I needn't configure ubuntu any further, but I don't want to come to that conclusion just right away mainly because I dislike Windows and the week-long setup process it puts me through rather than the few hours with Ubuntu.

---

### Post by cortman on 2012-09-14
I can't conceive the package transfer affecting this in any way.
I'm pretty sure the Nvidia driver will fix it for you. This is a very common issue.

---

### Post by wiseguy12851 on 2012-09-14
The driver update didnt work. Same issue.

---

### Post by cortman on 2012-09-14
You tried running

```

sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig

```

And a reboot?

---

### Post by wiseguy12851 on 2012-09-14
That worked,

In case anyone else has this problem and can't get it resolved, here is what worked for me.

run from the terminal or console,
```
sudo nvidia-settings
```

This launches the special app for controlling your nvidia card, apparently Ubuntu can't control it probably due to proprietary drivers and firmware so Ubuntu thinks it's a laptop screen. This happens even if the correct drivers are installed so all configuration must go through this tool.

I think you can select it from the launcher / other menu but I tend to mainly use the terminal. Either way the program won't pop-up automatically.

The tool is a bit complicated at first but you must click the button "Save to X File" before closing the app or all changes are temporary.

Thanks cortman

---

### Post by cortman on 2012-09-14
No problem; glad I was able to at least "aim you" in the right direction. :)
Mark the thread [SOLVED] if you would, so others can benefit.
Good luck!

---

