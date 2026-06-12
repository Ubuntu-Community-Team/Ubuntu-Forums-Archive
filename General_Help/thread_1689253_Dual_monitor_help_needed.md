---
title: "Dual monitor help needed"
date: 2011-02-16
forum: General Help
---

### Post by Mariane on 2011-02-16
Hi, 

My system functions fine with Kubuntu 10.10 until I boot with a second monitor. The second one lights up during boot but then it goes black and stays black. 

In "System Settings/Display and Monitors/Multiple Monitors" it says: 
"This system is just for configuring systems with a single desktop spread across multiple monitors. You do not appear to have this configuration"

What should I do please? 

Mariane

---

### Post by Mariane on 2011-02-20
bump

---

### Post by Mariane on 2011-02-28
bump

---

### Post by Mariane on 2011-03-02
bump

---

### Post by Dans564 on 2011-03-02
nvidia or ati???

---

### Post by COKEDUDE on 2011-03-03
Read this. 

[https://wiki.ubuntu.com/X/Config/Resolution/#How%20to%20setup%20a%20dual%20monitor](https://wiki.ubuntu.com/X/Config/Resolution/#How%20to%20setup%20a%20dual%20monitor)

---

### Post by COKEDUDE on 2011-06-01
Have you had any luck with fixing this?

---

### Post by Mariane on 2011-06-01
Not yet. I was doing other things. But as it is now you who are bumping me I'll have a go following your wiki page. Cheers for the reminder :D . 

Mariane

---

### Post by Mariane on 2011-06-02
Thank you for your wiki page, COKEDUDE, it got me a bit further. But now I'm stuck again. 

```

gnome-display-properties

```

is a nice one. At first it showed my second monitor as "unknown". Under "X Server Display Configuration" I have the "Detect Displays" button, which functioned. It got the details of the second monitor and it seems it got them right. Then I did "Save to X Configuration File" and rebooted. I did this command again and the second monitor showed up straight away. 

"Computer/System Settings/Display and Monitor/Multiple Monitors" still says "This module is only for configuring systems with a single desktop spread across multiple monitors. You do not appear to have this configuration". 

"Computer/System Settings/Display and Monitor/Size and Orientation" shows the laptop screen settings. It has a button called "Identify Outputs" but clicking on it only writes "default" in a very large font. 

```

xrandr

```

also only shows output for the laptop monitor. 

The second monitor still only shows its own screensaver. 

Now I have several questions: 

I am puzzled by: "If your watch a lot of movies it is important to set your Monitors to your lower resolution. For example, if they are both 1440 x 900 monitors, make sure it is set to that resolution. If the monitors are different resolutions, you will need it to the resolution of the smaller monitor." 

My laptop screen is:
1440 x 900 pixels
110 x 108 dots per inch
Display AUO (DFP_0)

The extra monitor is: 
1680 x 1050 pixels
90 x 88 dots per inch
DELL E228WFP (CRT-0)

Both have:
GPUs: GeForce 9300M GS

I do watch movies, does the sentence quoted above mean that I should set the second monitor to 1440 x 900 pixels or did I misunderstand? 

The last thing I want to do is to mess up my laptop so that it will no longer function on its own. I don't fancy having to carry a large, heavy and extremely fragile screen around :). So which method should I select among: 
- By session with .xprofile.
- Dynamically by using xrandr tool
- Statically by setting in xorg.conf? 

I am not the only user of this laptop but we all have the same profile. 

Mariane

---

### Post by COKEDUDE on 2011-06-02
> **Mariane said:**
> Thank you for your wiki page, COKEDUDE, it got me a bit further. But now I'm stuck again. 

```

gnome-display-properties

```

is a nice one. At first it showed my second monitor as "unknown". Under "X Server Display Configuration" I have the "Detect Displays" button, which functioned. It got the details of the second monitor and it seems it got them right. Then I did "Save to X Configuration File" and rebooted. I did this command again and the second monitor showed up straight away. 

"Computer/System Settings/Display and Monitor/Multiple Monitors" still says "This module is only for configuring systems with a single desktop spread across multiple monitors. You do not appear to have this configuration". 

"Computer/System Settings/Display and Monitor/Size and Orientation" shows the laptop screen settings. It has a button called "Identify Outputs" but clicking on it only writes "default" in a very large font. 

```

xrandr

```

also only shows output for the laptop monitor. 

The second monitor still only shows its own screensaver. 

Now I have several questions: 

I am puzzled by: "If your watch a lot of movies it is important to set your Monitors to your lower resolution. For example, if they are both 1440 x 900 monitors, make sure it is set to that resolution. If the monitors are different resolutions, you will need it to the resolution of the smaller monitor." 

My laptop screen is:
1440 x 900 pixels
110 x 108 dots per inch
Display AUO (DFP_0)

The extra monitor is: 
1680 x 1050 pixels
90 x 88 dots per inch
DELL E228WFP (CRT-0)

Both have:
GPUs: GeForce 9300M GS

**I do watch movies, does the sentence quoted above mean that I should set the second monitor to 1440 x 900 pixels or did I misunderstand? **

The last thing I want to do is to mess up my laptop so that it will no longer function on its own. I don't fancy having to carry a large, heavy and extremely fragile screen around :). So which method should I select among: 
**- By session with .xprofile.**
- Dynamically by using xrandr tool
- Statically by setting in xorg.conf? 

I am not the only user of this laptop but we all have the same profile. 

Mariane

Show me the output for both of these commands. 

```
xrandr --verbose
xrandr
```

Try it both ways. You have a newer video card than me. I could not see the video of the movie without lowering the resolution. 

I prefer to use the .xprofile. I know it works :). Thats the only method I have personally tested.

---

### Post by CunningGoose on 2011-06-03
What are you using to connect the second monitor? I had problems using VGA until I switched it to DVI, works fine now.

---

### Post by Mariane on 2011-06-03
Thank you.

xrandr:
```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0*    51.0  
   1360x768       52.0     53.0  
   1152x864       54.0     55.0     56.0     57.0  
   1024x768       58.0     59.0     60.0     61.0     62.0  
   960x600        63.0  
   960x540        64.0  
   896x672        65.0  
   840x525        66.0     67.0     68.0     69.0     70.0  
   832x624        71.0  
   800x600        72.0     73.0     74.0     75.0     76.0     77.0     78.0     79.0     80.0  
   800x512        81.0  
   720x450        82.0  
   720x400        83.0  
   700x525        84.0     85.0     86.0     87.0  
   680x384        88.0     89.0  
   640x512        90.0     91.0     92.0  
   640x480        93.0     94.0     95.0     96.0     97.0     98.0  
   640x400        99.0  
   640x350       100.0  
   576x432       101.0    102.0    103.0    104.0    105.0    106.0    107.0  
   512x384       108.0    109.0    110.0    111.0    112.0  
   416x312       113.0  
   400x300       114.0    115.0    116.0    117.0    118.0  
   360x200       119.0  
   320x240       120.0    121.0    122.0    123.0  
   320x200       124.0  
   320x175       125.0  

```

xrandr --verbose:
```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 (0x2b9) normal (normal) 0mm x 0mm
        Identifier: 0x2b8
        Timestamp:  18224
        Subpixel:   unknown
        Clones:    
        CRTC:       0
        CRTCs:      0
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
  1440x900 (0x2b9)   64.8MHz *current
        h: width  1440 start    0 end    0 total 1440 skew    0 clock   45.0KHz
        v: height  900 start    0 end    0 total  900           clock   50.0Hz
  1440x900 (0x2ba)   66.1MHz
        h: width  1440 start    0 end    0 total 1440 skew    0 clock   45.9KHz
        v: height  900 start    0 end    0 total  900           clock   51.0Hz
  1360x768 (0x2bb)   54.3MHz
        h: width  1360 start    0 end    0 total 1360 skew    0 clock   39.9KHz
        v: height  768 start    0 end    0 total  768           clock   52.0Hz
  1360x768 (0x2bc)   55.4MHz
        h: width  1360 start    0 end    0 total 1360 skew    0 clock   40.7KHz
        v: height  768 start    0 end    0 total  768           clock   53.0Hz
  1152x864 (0x2bd)   53.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   46.7KHz
        v: height  864 start    0 end    0 total  864           clock   54.0Hz
  1152x864 (0x2be)   54.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   47.5KHz
        v: height  864 start    0 end    0 total  864           clock   55.0Hz
  1152x864 (0x2bf)   55.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   48.4KHz
        v: height  864 start    0 end    0 total  864           clock   56.0Hz
  1152x864 (0x2c0)   56.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   49.2KHz
        v: height  864 start    0 end    0 total  864           clock   57.0Hz
  1024x768 (0x2c1)   45.6MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   44.5KHz
        v: height  768 start    0 end    0 total  768           clock   58.0Hz
  1024x768 (0x2c2)   46.4MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   45.3KHz
        v: height  768 start    0 end    0 total  768           clock   59.0Hz
  1024x768 (0x2c3)   47.2MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   46.1KHz
        v: height  768 start    0 end    0 total  768           clock   60.0Hz
  1024x768 (0x2c4)   48.0MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   46.8KHz
        v: height  768 start    0 end    0 total  768           clock   61.0Hz
  1024x768 (0x2c5)   48.8MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   47.6KHz
        v: height  768 start    0 end    0 total  768           clock   62.0Hz
  960x600 (0x2c6)   36.3MHz
        h: width   960 start    0 end    0 total  960 skew    0 clock   37.8KHz
        v: height  600 start    0 end    0 total  600           clock   63.0Hz
  960x540 (0x2c7)   33.2MHz
        h: width   960 start    0 end    0 total  960 skew    0 clock   34.6KHz
        v: height  540 start    0 end    0 total  540           clock   64.0Hz
  896x672 (0x2c8)   39.1MHz
        h: width   896 start    0 end    0 total  896 skew    0 clock   43.7KHz
        v: height  672 start    0 end    0 total  672           clock   65.0Hz
  840x525 (0x2c9)   29.1MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   34.6KHz
        v: height  525 start    0 end    0 total  525           clock   66.0Hz
  840x525 (0x2ca)   29.5MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   35.2KHz
        v: height  525 start    0 end    0 total  525           clock   67.0Hz
  840x525 (0x2cb)   30.0MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   35.7KHz
        v: height  525 start    0 end    0 total  525           clock   68.0Hz
  840x525 (0x2cc)   30.4MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   36.2KHz
        v: height  525 start    0 end    0 total  525           clock   69.0Hz
  840x525 (0x2cd)   30.9MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   36.8KHz
        v: height  525 start    0 end    0 total  525           clock   70.0Hz
  832x624 (0x2ce)   36.9MHz
        h: width   832 start    0 end    0 total  832 skew    0 clock   44.3KHz
        v: height  624 start    0 end    0 total  624           clock   71.0Hz
  800x600 (0x2cf)   34.6MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   43.2KHz
        v: height  600 start    0 end    0 total  600           clock   72.0Hz
  800x600 (0x2d0)   35.0MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   43.8KHz
        v: height  600 start    0 end    0 total  600           clock   73.0Hz
  800x600 (0x2d1)   35.5MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   44.4KHz
        v: height  600 start    0 end    0 total  600           clock   74.0Hz
  800x600 (0x2d2)   36.0MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   45.0KHz
        v: height  600 start    0 end    0 total  600           clock   75.0Hz
  800x600 (0x2d3)   36.5MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   45.6KHz
        v: height  600 start    0 end    0 total  600           clock   76.0Hz
  800x600 (0x2d4)   37.0MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   46.2KHz
        v: height  600 start    0 end    0 total  600           clock   77.0Hz
  800x600 (0x2d5)   37.4MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   46.8KHz
        v: height  600 start    0 end    0 total  600           clock   78.0Hz
  800x600 (0x2d6)   37.9MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   47.4KHz
        v: height  600 start    0 end    0 total  600           clock   79.0Hz
  800x600 (0x2d7)   38.4MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   48.0KHz
        v: height  600 start    0 end    0 total  600           clock   80.0Hz
  800x512 (0x2d8)   33.2MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   41.5KHz
        v: height  512 start    0 end    0 total  512           clock   81.0Hz
  720x450 (0x2d9)   26.6MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock   36.9KHz
        v: height  450 start    0 end    0 total  450           clock   82.0Hz
  720x400 (0x2da)   23.9MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock   33.2KHz
        v: height  400 start    0 end    0 total  400           clock   83.0Hz
  700x525 (0x2db)   30.9MHz
        h: width   700 start    0 end    0 total  700 skew    0 clock   44.1KHz
        v: height  525 start    0 end    0 total  525           clock   84.0Hz
  700x525 (0x2dc)   31.2MHz
        h: width   700 start    0 end    0 total  700 skew    0 clock   44.6KHz
        v: height  525 start    0 end    0 total  525           clock   85.0Hz
  700x525 (0x2dd)   31.6MHz
        h: width   700 start    0 end    0 total  700 skew    0 clock   45.1KHz
        v: height  525 start    0 end    0 total  525           clock   86.0Hz
  700x525 (0x2de)   32.0MHz
        h: width   700 start    0 end    0 total  700 skew    0 clock   45.7KHz
        v: height  525 start    0 end    0 total  525           clock   87.0Hz
  680x384 (0x2df)   23.0MHz
        h: width   680 start    0 end    0 total  680 skew    0 clock   33.8KHz
        v: height  384 start    0 end    0 total  384           clock   88.0Hz
  680x384 (0x2e0)   23.2MHz
        h: width   680 start    0 end    0 total  680 skew    0 clock   34.2KHz
        v: height  384 start    0 end    0 total  384           clock   89.0Hz
  640x512 (0x2e1)   29.5MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   46.1KHz
        v: height  512 start    0 end    0 total  512           clock   90.0Hz
  640x512 (0x2e2)   29.8MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   46.6KHz
        v: height  512 start    0 end    0 total  512           clock   91.0Hz
  640x512 (0x2e3)   30.1MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   47.1KHz
        v: height  512 start    0 end    0 total  512           clock   92.0Hz
  640x480 (0x2e4)   28.6MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   44.6KHz
        v: height  480 start    0 end    0 total  480           clock   93.0Hz
  640x480 (0x2e5)   28.9MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   45.1KHz
        v: height  480 start    0 end    0 total  480           clock   94.0Hz
  640x480 (0x2e6)   29.2MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   45.6KHz
        v: height  480 start    0 end    0 total  480           clock   95.0Hz
  640x480 (0x2e7)   29.5MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   46.1KHz
        v: height  480 start    0 end    0 total  480           clock   96.0Hz
  640x480 (0x2e8)   29.8MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   46.6KHz
        v: height  480 start    0 end    0 total  480           clock   97.0Hz
  640x480 (0x2e9)   30.1MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   47.0KHz
        v: height  480 start    0 end    0 total  480           clock   98.0Hz
  640x400 (0x2ea)   25.3MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   39.6KHz
        v: height  400 start    0 end    0 total  400           clock   99.0Hz
  640x350 (0x2eb)   22.4MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   35.0KHz
        v: height  350 start    0 end    0 total  350           clock  100.0Hz
  576x432 (0x2ec)   25.1MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   43.6KHz
        v: height  432 start    0 end    0 total  432           clock  101.0Hz
  576x432 (0x2ed)   25.4MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   44.1KHz
        v: height  432 start    0 end    0 total  432           clock  102.0Hz
  576x432 (0x2ee)   25.6MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   44.5KHz
        v: height  432 start    0 end    0 total  432           clock  103.0Hz
  576x432 (0x2ef)   25.9MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   44.9KHz
        v: height  432 start    0 end    0 total  432           clock  104.0Hz
  576x432 (0x2f0)   26.1MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   45.4KHz
        v: height  432 start    0 end    0 total  432           clock  105.0Hz
  576x432 (0x2f1)   26.4MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   45.8KHz
        v: height  432 start    0 end    0 total  432           clock  106.0Hz
  576x432 (0x2f2)   26.6MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   46.2KHz
        v: height  432 start    0 end    0 total  432           clock  107.0Hz
  512x384 (0x2f3)   21.2MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   41.5KHz
        v: height  384 start    0 end    0 total  384           clock  108.0Hz
  512x384 (0x2f4)   21.4MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   41.9KHz
        v: height  384 start    0 end    0 total  384           clock  109.0Hz
  512x384 (0x2f5)   21.6MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   42.2KHz
        v: height  384 start    0 end    0 total  384           clock  110.0Hz
  512x384 (0x2f6)   21.8MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   42.6KHz
        v: height  384 start    0 end    0 total  384           clock  111.0Hz
  512x384 (0x2f7)   22.0MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   43.0KHz
        v: height  384 start    0 end    0 total  384           clock  112.0Hz
  416x312 (0x2f8)   14.7MHz
        h: width   416 start    0 end    0 total  416 skew    0 clock   35.3KHz
        v: height  312 start    0 end    0 total  312           clock  113.0Hz
  400x300 (0x2f9)   13.7MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   34.2KHz
        v: height  300 start    0 end    0 total  300           clock  114.0Hz
  400x300 (0x2fa)   13.8MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   34.5KHz
        v: height  300 start    0 end    0 total  300           clock  115.0Hz
  400x300 (0x2fb)   13.9MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   34.8KHz
        v: height  300 start    0 end    0 total  300           clock  116.0Hz
  400x300 (0x2fc)   14.0MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   35.1KHz
        v: height  300 start    0 end    0 total  300           clock  117.0Hz
  400x300 (0x2fd)   14.2MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   35.4KHz
        v: height  300 start    0 end    0 total  300           clock  118.0Hz
  360x200 (0x2fe)    8.6MHz
        h: width   360 start    0 end    0 total  360 skew    0 clock   23.8KHz
        v: height  200 start    0 end    0 total  200           clock  119.0Hz
  320x240 (0x2ff)    9.2MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   28.8KHz
        v: height  240 start    0 end    0 total  240           clock  120.0Hz
  320x240 (0x300)    9.3MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   29.0KHz
        v: height  240 start    0 end    0 total  240           clock  121.0Hz
  320x240 (0x301)    9.4MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   29.3KHz
        v: height  240 start    0 end    0 total  240           clock  122.0Hz
  320x240 (0x302)    9.4MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   29.5KHz
        v: height  240 start    0 end    0 total  240           clock  123.0Hz
  320x200 (0x303)    7.9MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   24.8KHz
        v: height  200 start    0 end    0 total  200           clock  124.0Hz
  320x175 (0x304)    7.0MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   21.9KHz
        v: height  175 start    0 end    0 total  175           clock  125.0Hz

```

I'll try .xprofile too then.

> **CunningGoose said:**
> 
What are you using to connect the second monitor? I had problems using VGA until I switched it to DVI, works fine now.


My laptop only has a VGA port. The external monitor has both. I'm currently connected with a DVI cable via an adapter for the VGA laptop port. I'll look around, I should have an old VGA cable somewhere.

Mariane

---

### Post by COKEDUDE on 2011-06-04
Show me the output for both of these commands with your second monitor plugged in. 

```
xrandr --verbose
xrandr
```

Show me the output of this command

```
xrandr -v

```

What your showing me is a bit different than what I see. I am also using a laptop with vga for my second monitor. This is what I see on mine. 

```
~ $ xrandr
Screen 0: minimum 320 x 200, current 2048 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+1024+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0* 
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768       60.0*+
   800x600        60.3  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)
```

```
~ $ xrandr --verbose
Screen 0: minimum 320 x 200, current 2048 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+1024+0 (0x45) normal (normal left inverted right x axis y axis) 338mm x 270mm
	Identifier: 0x41
	Timestamp:  75210611
	Subpixel:   unknown
	Clones:    
	CRTC:       0
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID:
		00ffffffffffff0010ac234053524830
		281101036a221b78ee8d45a5564b9b26
		135054a54b008180714f010101010101
		010101010101302a009851002a403070
		1300520e1100001e000000ff00504d33
		3732374135304852530a000000fc0044
		454c4c203137303846500a20000000fd
		00384c1e510e000a20202020202000a3
  1280x1024 (0x147)  108.0MHz +HSync +VSync +preferred
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1280x1024 (0x148)  135.0MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1152x864 (0x149)  108.0MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock   67.5KHz
        v: height  864 start  865 end  868 total  900           clock   75.0Hz
  1024x768 (0x14a)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.1KHz
        v: height  768 start  769 end  772 total  800           clock   75.1Hz
  1024x768 (0x45)   65.0MHz -HSync -VSync *current
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x14b)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x46)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x14c)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x14d)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   60.0Hz
  720x400 (0x14e)   28.3MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock   31.5KHz
        v: height  400 start  412 end  414 total  449           clock   70.1Hz
LVDS1 connected 1024x768+0+0 (0x45) normal (normal left inverted right x axis y axis) 304mm x 228mm
	Identifier: 0x42
	Timestamp:  75210611
	Subpixel:   horizontal rgb
	Clones:    
	CRTC:       1
	CRTCs:      1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID:
		00ffffffffffff0006af512300000000
		010e0103801e17780a87f594574f8c27
		27505400000001010101010101010101
		01010101010164190040410026301888
		360030e4100000180000000000000000
		00000000000000000000000000fe004a
		463338330042313530584732000000fe
		00e7d4c4bc98704c0001010a2020003b
	BACKLIGHT: 7 (0x00000007)	range:  (0,7)
	Backlight: 7 (0x00000007)	range:  (0,7)
	scaling mode:	Full
		supported: None         Full         Center       Full aspect 
  1024x768 (0x45)   65.0MHz -HSync -VSync *current +preferred
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x46)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x47)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
DVI1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x43
	Timestamp:  75210611
	Subpixel:   horizontal rgb
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
TV1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x44
	Timestamp:  75210611
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	bottom margin: 37 (0x00000025)	range:  (0,100)
	right margin: 46 (0x0000002e)	range:  (0,100)
	top margin: 36 (0x00000024)	range:  (0,100)
	left margin: 54 (0x00000036)	range:  (0,100)
	mode:	NTSC-M
		supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
		           PAL-N        PAL          480p@59.94Hz 480p@60Hz   
		           576p         720p@60Hz    720p@59.94Hz 720p@50Hz   
		           1080i@50Hz   1080i@60Hz   1080i@59.94H

```

Try to use my .xprofile and change the appropriate names and numbers. VGA1 is for my second monitor and LVDS1 is for my laptop. 

```
xrandr --output VGA1 --mode 1024x768 --rate 60

#Laptop left extra Monitor right
xrandr --output LVDS1 --left-of VGA1

#Laptop right extra Monitor Left
#xrandr --output VGA1 --left-of LVDS1

```

---

### Post by Mariane on 2011-06-04
The outputs shown above were with the second monitor plugged in. I have xrandr version 1.3.3 and RandR version 1.3.

No xrandr command which uses --output functions except "xrandr --output 0x2b8" or "xrandr --output default" (which does nothing but just shows it recognises the name). Whatever other name I try to give to the output it says "warning: output XXX not found; ignoring". 

I tried a lot of names. In my xorg.conf the identifiers were "Monitor0" and "Monitor1". In the "gnome-display-properties" the identifiers are "alan:0.0" and "alan:0.1". 

```

xrandr --screen 1 --verbose

```

Gives:

```

xrandr: Failed to get size of gamma for output default
Screen 1: minimum 320 x 240, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 (0x307) normal (normal) 0mm x 0mm
        Identifier: 0x306
        Timestamp:  18370
        Subpixel:   unknown
        Clones:    
        CRTC:       0
        CRTCs:      0
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
  1680x1050 (0x307)   88.2MHz *current
        h: width  1680 start    0 end    0 total 1680 skew    0 clock   52.5KHz
        v: height 1050 start    0 end    0 total 1050           clock   50.0Hz
  1440x900 (0x2ba)   66.1MHz
        h: width  1440 start    0 end    0 total 1440 skew    0 clock   45.9KHz
        v: height  900 start    0 end    0 total  900           clock   51.0Hz
  1400x1050 (0x308)   76.4MHz
        h: width  1400 start    0 end    0 total 1400 skew    0 clock   54.6KHz
        v: height 1050 start    0 end    0 total 1050           clock   52.0Hz
  1360x768 (0x2bc)   55.4MHz
        h: width  1360 start    0 end    0 total 1360 skew    0 clock   40.7KHz
        v: height  768 start    0 end    0 total  768           clock   53.0Hz
  1360x768 (0x309)   56.4MHz
        h: width  1360 start    0 end    0 total 1360 skew    0 clock   41.5KHz
        v: height  768 start    0 end    0 total  768           clock   54.0Hz
  1280x1024 (0x30a)   72.1MHz
        h: width  1280 start    0 end    0 total 1280 skew    0 clock   56.3KHz
        v: height 1024 start    0 end    0 total 1024           clock   55.0Hz
  1280x1024 (0x30b)   73.4MHz
        h: width  1280 start    0 end    0 total 1280 skew    0 clock   57.3KHz
        v: height 1024 start    0 end    0 total 1024           clock   56.0Hz
  1280x960 (0x30c)   70.0MHz
        h: width  1280 start    0 end    0 total 1280 skew    0 clock   54.7KHz
        v: height  960 start    0 end    0 total  960           clock   57.0Hz
  1152x864 (0x30d)   57.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   50.1KHz
        v: height  864 start    0 end    0 total  864           clock   58.0Hz
  1152x864 (0x30e)   58.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   51.0KHz
        v: height  864 start    0 end    0 total  864           clock   59.0Hz
  1152x864 (0x30f)   59.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   51.8KHz
        v: height  864 start    0 end    0 total  864           clock   60.0Hz
  1152x864 (0x310)   60.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   52.7KHz
        v: height  864 start    0 end    0 total  864           clock   61.0Hz
  1024x768 (0x2c5)   48.8MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   47.6KHz
        v: height  768 start    0 end    0 total  768           clock   62.0Hz
  1024x768 (0x311)   49.5MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   48.4KHz
        v: height  768 start    0 end    0 total  768           clock   63.0Hz
  1024x768 (0x312)   50.3MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   49.2KHz
        v: height  768 start    0 end    0 total  768           clock   64.0Hz
  960x600 (0x313)   37.4MHz
        h: width   960 start    0 end    0 total  960 skew    0 clock   39.0KHz
        v: height  600 start    0 end    0 total  600           clock   65.0Hz
  960x540 (0x314)   34.2MHz
        h: width   960 start    0 end    0 total  960 skew    0 clock   35.6KHz
        v: height  540 start    0 end    0 total  540           clock   66.0Hz
  840x525 (0x2ca)   29.5MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   35.2KHz
        v: height  525 start    0 end    0 total  525           clock   67.0Hz
  840x525 (0x2cb)   30.0MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   35.7KHz
        v: height  525 start    0 end    0 total  525           clock   68.0Hz
  840x525 (0x2cc)   30.4MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   36.2KHz
        v: height  525 start    0 end    0 total  525           clock   69.0Hz
  840x525 (0x2cd)   30.9MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   36.8KHz
        v: height  525 start    0 end    0 total  525           clock   70.0Hz
  832x624 (0x2ce)   36.9MHz
        h: width   832 start    0 end    0 total  832 skew    0 clock   44.3KHz
        v: height  624 start    0 end    0 total  624           clock   71.0Hz
  800x600 (0x2cf)   34.6MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   43.2KHz
        v: height  600 start    0 end    0 total  600           clock   72.0Hz
  800x600 (0x2d0)   35.0MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   43.8KHz
        v: height  600 start    0 end    0 total  600           clock   73.0Hz
  800x600 (0x2d1)   35.5MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   44.4KHz
        v: height  600 start    0 end    0 total  600           clock   74.0Hz
  800x600 (0x2d2)   36.0MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   45.0KHz
        v: height  600 start    0 end    0 total  600           clock   75.0Hz
  720x450 (0x315)   24.6MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock   34.2KHz
        v: height  450 start    0 end    0 total  450           clock   76.0Hz
  700x525 (0x316)   28.3MHz
        h: width   700 start    0 end    0 total  700 skew    0 clock   40.4KHz
        v: height  525 start    0 end    0 total  525           clock   77.0Hz
  700x525 (0x317)   28.7MHz
        h: width   700 start    0 end    0 total  700 skew    0 clock   41.0KHz
        v: height  525 start    0 end    0 total  525           clock   78.0Hz
  680x384 (0x318)   20.6MHz
        h: width   680 start    0 end    0 total  680 skew    0 clock   30.3KHz
        v: height  384 start    0 end    0 total  384           clock   79.0Hz
  680x384 (0x319)   20.9MHz
        h: width   680 start    0 end    0 total  680 skew    0 clock   30.7KHz
        v: height  384 start    0 end    0 total  384           clock   80.0Hz
  640x480 (0x31a)   24.9MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   38.9KHz
        v: height  480 start    0 end    0 total  480           clock   81.0Hz
  640x480 (0x31b)   25.2MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   39.4KHz
        v: height  480 start    0 end    0 total  480           clock   82.0Hz
  640x480 (0x31c)   25.5MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   39.8KHz
        v: height  480 start    0 end    0 total  480           clock   83.0Hz
  640x480 (0x31d)   25.8MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   40.3KHz
        v: height  480 start    0 end    0 total  480           clock   84.0Hz
  512x384 (0x31e)   16.7MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   32.6KHz
        v: height  384 start    0 end    0 total  384           clock   85.0Hz
  512x384 (0x31f)   16.9MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   33.0KHz
        v: height  384 start    0 end    0 total  384           clock   86.0Hz
  400x300 (0x320)   10.4MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   26.1KHz
        v: height  300 start    0 end    0 total  300           clock   87.0Hz
  320x240 (0x321)    6.8MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   21.1KHz
        v: height  240 start    0 end    0 total  240           clock   88.0Hz
  320x240 (0x322)    6.8MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   21.4KHz
        v: height  240 start    0 end    0 total  240           clock   89.0Hz

```

which is infuriating because it shows xrandr knows about the second monitor: the resolution it gives for it is the right one. 

Of course I had great hopes in:

[/code]
xrandr --output 0x306
[/code]

but it says (again):

[/code]
xrandr: Failed to get size of gamma for output default
warning: output (null) not found; ignoring
[/code]

Even though the verbose of screen 1 tells me 0x306 is the name of the second monitor! (This is how I found out that the name of the first monitor is 0x2b8 ). 

I wrote these 2 names instead of Monitor0 and Monitor1 in xorg.conf and rebooted, but it didn't help. I don't know how to change the names in gnome-display-properties, they are displayed but not editable. 

Comments: 

With the name 0x306 I get the error "warning: output (null) not found; ignoring", with other names I get the error "warning: output XXX not found; ignoring". Does it mean that it somehow recognises 0x306 but considers it to be null?

Whatever I do I get the error "xrandr: Failed to get size of gamma for output default". According to this page: 
[http://www.photoscientia.co.uk/Gamma.html](http://www.photoscientia.co.uk/Gamma.html)
the value should be 1.8 but I didn't manage to guess the correct syntax for setting gamma. 

Mariane

---

### Post by COKEDUDE on 2011-06-05
> **Mariane said:**
> The outputs shown above were with the second monitor plugged in. I have xrandr version 1.3.3 and RandR version 1.3.

No xrandr command which uses --output functions except "**xrandr --output 0x2b8**" or "xrandr --output default" (which does nothing but just shows it recognises the name). Whatever other name I try to give to the output it says "warning: output XXX not found; ignoring". 

**I tried a lot of names. In my xorg.conf the identifiers were "Monitor0" and "Monitor1". In the "gnome-display-properties" the identifiers are "alan:0.0" and "alan:0.1". **

```

xrandr --screen 1 --verbose

```

Gives:

```

xrandr: Failed to get size of gamma for output default
Screen 1: minimum 320 x 240, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 (0x307) normal (normal) 0mm x 0mm
        Identifier: 0x306
        Timestamp:  18370
        Subpixel:   unknown
        Clones:    
        CRTC:       0
        CRTCs:      0
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
  1680x1050 (0x307)   88.2MHz *current
        h: width  1680 start    0 end    0 total 1680 skew    0 clock   52.5KHz
        v: height 1050 start    0 end    0 total 1050           clock   50.0Hz
  1440x900 (0x2ba)   66.1MHz
        h: width  1440 start    0 end    0 total 1440 skew    0 clock   45.9KHz
        v: height  900 start    0 end    0 total  900           clock   51.0Hz
  1400x1050 (0x308)   76.4MHz
        h: width  1400 start    0 end    0 total 1400 skew    0 clock   54.6KHz
        v: height 1050 start    0 end    0 total 1050           clock   52.0Hz
  1360x768 (0x2bc)   55.4MHz
        h: width  1360 start    0 end    0 total 1360 skew    0 clock   40.7KHz
        v: height  768 start    0 end    0 total  768           clock   53.0Hz
  1360x768 (0x309)   56.4MHz
        h: width  1360 start    0 end    0 total 1360 skew    0 clock   41.5KHz
        v: height  768 start    0 end    0 total  768           clock   54.0Hz
  1280x1024 (0x30a)   72.1MHz
        h: width  1280 start    0 end    0 total 1280 skew    0 clock   56.3KHz
        v: height 1024 start    0 end    0 total 1024           clock   55.0Hz
  1280x1024 (0x30b)   73.4MHz
        h: width  1280 start    0 end    0 total 1280 skew    0 clock   57.3KHz
        v: height 1024 start    0 end    0 total 1024           clock   56.0Hz
  1280x960 (0x30c)   70.0MHz
        h: width  1280 start    0 end    0 total 1280 skew    0 clock   54.7KHz
        v: height  960 start    0 end    0 total  960           clock   57.0Hz
  1152x864 (0x30d)   57.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   50.1KHz
        v: height  864 start    0 end    0 total  864           clock   58.0Hz
  1152x864 (0x30e)   58.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   51.0KHz
        v: height  864 start    0 end    0 total  864           clock   59.0Hz
  1152x864 (0x30f)   59.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   51.8KHz
        v: height  864 start    0 end    0 total  864           clock   60.0Hz
  1152x864 (0x310)   60.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   52.7KHz
        v: height  864 start    0 end    0 total  864           clock   61.0Hz
  1024x768 (0x2c5)   48.8MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   47.6KHz
        v: height  768 start    0 end    0 total  768           clock   62.0Hz
  1024x768 (0x311)   49.5MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   48.4KHz
        v: height  768 start    0 end    0 total  768           clock   63.0Hz
  1024x768 (0x312)   50.3MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   49.2KHz
        v: height  768 start    0 end    0 total  768           clock   64.0Hz
  960x600 (0x313)   37.4MHz
        h: width   960 start    0 end    0 total  960 skew    0 clock   39.0KHz
        v: height  600 start    0 end    0 total  600           clock   65.0Hz
  960x540 (0x314)   34.2MHz
        h: width   960 start    0 end    0 total  960 skew    0 clock   35.6KHz
        v: height  540 start    0 end    0 total  540           clock   66.0Hz
  840x525 (0x2ca)   29.5MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   35.2KHz
        v: height  525 start    0 end    0 total  525           clock   67.0Hz
  840x525 (0x2cb)   30.0MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   35.7KHz
        v: height  525 start    0 end    0 total  525           clock   68.0Hz
  840x525 (0x2cc)   30.4MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   36.2KHz
        v: height  525 start    0 end    0 total  525           clock   69.0Hz
  840x525 (0x2cd)   30.9MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   36.8KHz
        v: height  525 start    0 end    0 total  525           clock   70.0Hz
  832x624 (0x2ce)   36.9MHz
        h: width   832 start    0 end    0 total  832 skew    0 clock   44.3KHz
        v: height  624 start    0 end    0 total  624           clock   71.0Hz
  800x600 (0x2cf)   34.6MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   43.2KHz
        v: height  600 start    0 end    0 total  600           clock   72.0Hz
  800x600 (0x2d0)   35.0MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   43.8KHz
        v: height  600 start    0 end    0 total  600           clock   73.0Hz
  800x600 (0x2d1)   35.5MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   44.4KHz
        v: height  600 start    0 end    0 total  600           clock   74.0Hz
  800x600 (0x2d2)   36.0MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   45.0KHz
        v: height  600 start    0 end    0 total  600           clock   75.0Hz
  720x450 (0x315)   24.6MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock   34.2KHz
        v: height  450 start    0 end    0 total  450           clock   76.0Hz
  700x525 (0x316)   28.3MHz
        h: width   700 start    0 end    0 total  700 skew    0 clock   40.4KHz
        v: height  525 start    0 end    0 total  525           clock   77.0Hz
  700x525 (0x317)   28.7MHz
        h: width   700 start    0 end    0 total  700 skew    0 clock   41.0KHz
        v: height  525 start    0 end    0 total  525           clock   78.0Hz
  680x384 (0x318)   20.6MHz
        h: width   680 start    0 end    0 total  680 skew    0 clock   30.3KHz
        v: height  384 start    0 end    0 total  384           clock   79.0Hz
  680x384 (0x319)   20.9MHz
        h: width   680 start    0 end    0 total  680 skew    0 clock   30.7KHz
        v: height  384 start    0 end    0 total  384           clock   80.0Hz
  640x480 (0x31a)   24.9MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   38.9KHz
        v: height  480 start    0 end    0 total  480           clock   81.0Hz
  640x480 (0x31b)   25.2MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   39.4KHz
        v: height  480 start    0 end    0 total  480           clock   82.0Hz
  640x480 (0x31c)   25.5MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   39.8KHz
        v: height  480 start    0 end    0 total  480           clock   83.0Hz
  640x480 (0x31d)   25.8MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   40.3KHz
        v: height  480 start    0 end    0 total  480           clock   84.0Hz
  512x384 (0x31e)   16.7MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   32.6KHz
        v: height  384 start    0 end    0 total  384           clock   85.0Hz
  512x384 (0x31f)   16.9MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   33.0KHz
        v: height  384 start    0 end    0 total  384           clock   86.0Hz
  400x300 (0x320)   10.4MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   26.1KHz
        v: height  300 start    0 end    0 total  300           clock   87.0Hz
  320x240 (0x321)    6.8MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   21.1KHz
        v: height  240 start    0 end    0 total  240           clock   88.0Hz
  320x240 (0x322)    6.8MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   21.4KHz
        v: height  240 start    0 end    0 total  240           clock   89.0Hz

```

which is infuriating because it shows xrandr knows about the second monitor: the resolution it gives for it is the right one. 

**Of course I had great hopes in:**

[/code]
xrandr --output 0x306
[/code]

but it says (again):

[/code]
xrandr: Failed to get size of gamma for output default
warning: output (null) not found; ignoring
[/code]

Even though the verbose of screen 1 tells me 0x306 is the name of the second monitor! (This is how I found out that the name of the first monitor is 0x2b8 ). 

I wrote these 2 names instead of Monitor0 and Monitor1 in xorg.conf and rebooted, but it didn't help. I don't know how to change the names in gnome-display-properties, they are displayed but not editable. 

Comments: 

With the name 0x306 I get the error "warning: output (null) not found; ignoring", with other names I get the error "warning: output XXX not found; ignoring". Does it mean that it somehow recognises 0x306 but considers it to be null?

Whatever I do I get the error "xrandr: Failed to get size of gamma for output default". According to this page: 
[http://www.photoscientia.co.uk/Gamma.html](http://www.photoscientia.co.uk/Gamma.html)
the value should be 1.8 but I didn't manage to guess the correct syntax for setting gamma. 

Mariane

You have to tell it what you want it to do. The command line does exactly what you tell it and nothing more. 

This selects the 0x2b8 screen. 
```
xrandr --output 0x2b8
```

This selects the 0x2b8 screen and changes the resolution and refresh rate. 
```
xrandr --output 0x2b8 --mode 800x600 --rate 60
```


This is why I want to see the output of these commands. Just copy and paste it like you see it. Don't add **--screen 1** **--screen 0** or anything extra. 

```
xrandr --verbose
xrandr
```

Like I said above you gotta tell it what to do. 


And take a look at my .xprofile. You gotta change the appropriate names and numbers. VGA1 is for my second monitor and LVDS1 is for my laptop.

```
xrandr --output VGA1 --mode 1024x768 --rate 60

#Laptop left extra Monitor right
xrandr --output LVDS1 --left-of VGA1

#Laptop right extra Monitor Left
#xrandr --output VGA1 --left-of LVDS1
```

---

### Post by Mariane on 2011-06-07
xrandr --verbose: 
```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 (0x2be) normal (normal) 0mm x 0mm
        Identifier: 0x2bd
        Timestamp:  19103
        Subpixel:   unknown
        Clones:    
        CRTC:       0
        CRTCs:      0
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
  1440x900 (0x2be)   64.8MHz *current
        h: width  1440 start    0 end    0 total 1440 skew    0 clock   45.0KHz
        v: height  900 start    0 end    0 total  900           clock   50.0Hz
  1440x900 (0x2bf)   66.1MHz
        h: width  1440 start    0 end    0 total 1440 skew    0 clock   45.9KHz
        v: height  900 start    0 end    0 total  900           clock   51.0Hz
  1360x768 (0x2c0)   54.3MHz
        h: width  1360 start    0 end    0 total 1360 skew    0 clock   39.9KHz
        v: height  768 start    0 end    0 total  768           clock   52.0Hz
  1360x768 (0x2c1)   55.4MHz
        h: width  1360 start    0 end    0 total 1360 skew    0 clock   40.7KHz
        v: height  768 start    0 end    0 total  768           clock   53.0Hz
  1152x864 (0x2c2)   53.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   46.7KHz
        v: height  864 start    0 end    0 total  864           clock   54.0Hz
  1152x864 (0x2c3)   54.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   47.5KHz
        v: height  864 start    0 end    0 total  864           clock   55.0Hz
  1152x864 (0x2c4)   55.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   48.4KHz
        v: height  864 start    0 end    0 total  864           clock   56.0Hz
  1152x864 (0x2c5)   56.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   49.2KHz
        v: height  864 start    0 end    0 total  864           clock   57.0Hz
  1024x768 (0x2c6)   45.6MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   44.5KHz
        v: height  768 start    0 end    0 total  768           clock   58.0Hz
  1024x768 (0x2c7)   46.4MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   45.3KHz
        v: height  768 start    0 end    0 total  768           clock   59.0Hz
  1024x768 (0x2c8)   47.2MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   46.1KHz
        v: height  768 start    0 end    0 total  768           clock   60.0Hz
  1024x768 (0x2c9)   48.0MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   46.8KHz
        v: height  768 start    0 end    0 total  768           clock   61.0Hz
  1024x768 (0x2ca)   48.8MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   47.6KHz
        v: height  768 start    0 end    0 total  768           clock   62.0Hz
  960x600 (0x2cb)   36.3MHz
        h: width   960 start    0 end    0 total  960 skew    0 clock   37.8KHz
        v: height  600 start    0 end    0 total  600           clock   63.0Hz
  960x540 (0x2cc)   33.2MHz
        h: width   960 start    0 end    0 total  960 skew    0 clock   34.6KHz
        v: height  540 start    0 end    0 total  540           clock   64.0Hz
  896x672 (0x2cd)   39.1MHz
        h: width   896 start    0 end    0 total  896 skew    0 clock   43.7KHz
        v: height  672 start    0 end    0 total  672           clock   65.0Hz
  840x525 (0x2ce)   29.1MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   34.6KHz
        v: height  525 start    0 end    0 total  525           clock   66.0Hz
  840x525 (0x2cf)   29.5MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   35.2KHz
        v: height  525 start    0 end    0 total  525           clock   67.0Hz
  840x525 (0x2d0)   30.0MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   35.7KHz
        v: height  525 start    0 end    0 total  525           clock   68.0Hz
  840x525 (0x2d1)   30.4MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   36.2KHz
        v: height  525 start    0 end    0 total  525           clock   69.0Hz
  840x525 (0x2d2)   30.9MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   36.8KHz
        v: height  525 start    0 end    0 total  525           clock   70.0Hz
  832x624 (0x2d3)   36.9MHz
        h: width   832 start    0 end    0 total  832 skew    0 clock   44.3KHz
        v: height  624 start    0 end    0 total  624           clock   71.0Hz
  800x600 (0x2d4)   34.6MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   43.2KHz
        v: height  600 start    0 end    0 total  600           clock   72.0Hz
  800x600 (0x2d5)   35.0MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   43.8KHz
        v: height  600 start    0 end    0 total  600           clock   73.0Hz
  800x600 (0x2d6)   35.5MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   44.4KHz
        v: height  600 start    0 end    0 total  600           clock   74.0Hz
  800x600 (0x2d7)   36.0MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   45.0KHz
        v: height  600 start    0 end    0 total  600           clock   75.0Hz
  800x600 (0x2d8)   36.5MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   45.6KHz
        v: height  600 start    0 end    0 total  600           clock   76.0Hz
  800x600 (0x2d9)   37.0MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   46.2KHz
        v: height  600 start    0 end    0 total  600           clock   77.0Hz
  800x600 (0x2da)   37.4MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   46.8KHz
        v: height  600 start    0 end    0 total  600           clock   78.0Hz
  800x600 (0x2db)   37.9MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   47.4KHz
        v: height  600 start    0 end    0 total  600           clock   79.0Hz
  800x600 (0x2dc)   38.4MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   48.0KHz
        v: height  600 start    0 end    0 total  600           clock   80.0Hz
  800x512 (0x2dd)   33.2MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   41.5KHz
        v: height  512 start    0 end    0 total  512           clock   81.0Hz
  720x450 (0x2de)   26.6MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock   36.9KHz
        v: height  450 start    0 end    0 total  450           clock   82.0Hz
  720x400 (0x2df)   23.9MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock   33.2KHz
        v: height  400 start    0 end    0 total  400           clock   83.0Hz
  700x525 (0x2e0)   30.9MHz
        h: width   700 start    0 end    0 total  700 skew    0 clock   44.1KHz
        v: height  525 start    0 end    0 total  525           clock   84.0Hz
  700x525 (0x2e1)   31.2MHz
        h: width   700 start    0 end    0 total  700 skew    0 clock   44.6KHz
        v: height  525 start    0 end    0 total  525           clock   85.0Hz
  700x525 (0x2e2)   31.6MHz
        h: width   700 start    0 end    0 total  700 skew    0 clock   45.1KHz
        v: height  525 start    0 end    0 total  525           clock   86.0Hz
  700x525 (0x2e3)   32.0MHz
        h: width   700 start    0 end    0 total  700 skew    0 clock   45.7KHz
        v: height  525 start    0 end    0 total  525           clock   87.0Hz
  680x384 (0x2e4)   23.0MHz
        h: width   680 start    0 end    0 total  680 skew    0 clock   33.8KHz
        v: height  384 start    0 end    0 total  384           clock   88.0Hz
  680x384 (0x2e5)   23.2MHz
        h: width   680 start    0 end    0 total  680 skew    0 clock   34.2KHz
        v: height  384 start    0 end    0 total  384           clock   89.0Hz
  640x512 (0x2e6)   29.5MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   46.1KHz
        v: height  512 start    0 end    0 total  512           clock   90.0Hz
  640x512 (0x2e7)   29.8MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   46.6KHz
        v: height  512 start    0 end    0 total  512           clock   91.0Hz
  640x512 (0x2e8)   30.1MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   47.1KHz
        v: height  512 start    0 end    0 total  512           clock   92.0Hz
  640x480 (0x2e9)   28.6MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   44.6KHz
        v: height  480 start    0 end    0 total  480           clock   93.0Hz
  640x480 (0x2ea)   28.9MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   45.1KHz
        v: height  480 start    0 end    0 total  480           clock   94.0Hz
  640x480 (0x2eb)   29.2MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   45.6KHz
        v: height  480 start    0 end    0 total  480           clock   95.0Hz
  640x480 (0x2ec)   29.5MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   46.1KHz
        v: height  480 start    0 end    0 total  480           clock   96.0Hz
  640x480 (0x2ed)   29.8MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   46.6KHz
        v: height  480 start    0 end    0 total  480           clock   97.0Hz
  640x480 (0x2ee)   30.1MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   47.0KHz
        v: height  480 start    0 end    0 total  480           clock   98.0Hz
  640x400 (0x2ef)   25.3MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   39.6KHz
        v: height  400 start    0 end    0 total  400           clock   99.0Hz
  640x350 (0x2f0)   22.4MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   35.0KHz
        v: height  350 start    0 end    0 total  350           clock  100.0Hz
  576x432 (0x2f1)   25.1MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   43.6KHz
        v: height  432 start    0 end    0 total  432           clock  101.0Hz
  576x432 (0x2f2)   25.4MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   44.1KHz
        v: height  432 start    0 end    0 total  432           clock  102.0Hz
  576x432 (0x2f3)   25.6MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   44.5KHz
        v: height  432 start    0 end    0 total  432           clock  103.0Hz
  576x432 (0x2f4)   25.9MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   44.9KHz
        v: height  432 start    0 end    0 total  432           clock  104.0Hz
  576x432 (0x2f5)   26.1MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   45.4KHz
        v: height  432 start    0 end    0 total  432           clock  105.0Hz
  576x432 (0x2f6)   26.4MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   45.8KHz
        v: height  432 start    0 end    0 total  432           clock  106.0Hz
  576x432 (0x2f7)   26.6MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   46.2KHz
        v: height  432 start    0 end    0 total  432           clock  107.0Hz
  512x384 (0x2f8)   21.2MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   41.5KHz
        v: height  384 start    0 end    0 total  384           clock  108.0Hz
  512x384 (0x2f9)   21.4MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   41.9KHz
        v: height  384 start    0 end    0 total  384           clock  109.0Hz
  512x384 (0x2fa)   21.6MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   42.2KHz
        v: height  384 start    0 end    0 total  384           clock  110.0Hz
  512x384 (0x2fb)   21.8MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   42.6KHz
        v: height  384 start    0 end    0 total  384           clock  111.0Hz
  512x384 (0x2fc)   22.0MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   43.0KHz
        v: height  384 start    0 end    0 total  384           clock  112.0Hz
  416x312 (0x2fd)   14.7MHz
        h: width   416 start    0 end    0 total  416 skew    0 clock   35.3KHz
        v: height  312 start    0 end    0 total  312           clock  113.0Hz
  400x300 (0x2fe)   13.7MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   34.2KHz
        v: height  300 start    0 end    0 total  300           clock  114.0Hz
  400x300 (0x2ff)   13.8MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   34.5KHz
        v: height  300 start    0 end    0 total  300           clock  115.0Hz
  400x300 (0x300)   13.9MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   34.8KHz
        v: height  300 start    0 end    0 total  300           clock  116.0Hz
  400x300 (0x301)   14.0MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   35.1KHz
        v: height  300 start    0 end    0 total  300           clock  117.0Hz
  400x300 (0x302)   14.2MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   35.4KHz
        v: height  300 start    0 end    0 total  300           clock  118.0Hz
  360x200 (0x303)    8.6MHz
        h: width   360 start    0 end    0 total  360 skew    0 clock   23.8KHz
        v: height  200 start    0 end    0 total  200           clock  119.0Hz
  320x240 (0x304)    9.2MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   28.8KHz
        v: height  240 start    0 end    0 total  240           clock  120.0Hz
  320x240 (0x305)    9.3MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   29.0KHz
        v: height  240 start    0 end    0 total  240           clock  121.0Hz
  320x240 (0x306)    9.4MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   29.3KHz
        v: height  240 start    0 end    0 total  240           clock  122.0Hz
  320x240 (0x307)    9.4MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   29.5KHz
        v: height  240 start    0 end    0 total  240           clock  123.0Hz
  320x200 (0x308)    7.9MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   24.8KHz
        v: height  200 start    0 end    0 total  200           clock  124.0Hz
  320x175 (0x309)    7.0MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   21.9KHz
        v: height  175 start    0 end    0 total  175           clock  125.0Hz

```

xrandr: 
```

Screen 0: minimum 320 x 175, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0*    51.0  
   1360x768       52.0     53.0  
   1152x864       54.0     55.0     56.0     57.0  
   1024x768       58.0     59.0     60.0     61.0     62.0  
   960x600        63.0  
   960x540        64.0  
   896x672        65.0  
   840x525        66.0     67.0     68.0     69.0     70.0  
   832x624        71.0  
   800x600        72.0     73.0     74.0     75.0     76.0     77.0     78.0     79.0     80.0  
   800x512        81.0  
   720x450        82.0  
   720x400        83.0  
   700x525        84.0     85.0     86.0     87.0  
   680x384        88.0     89.0  
   640x512        90.0     91.0     92.0  
   640x480        93.0     94.0     95.0     96.0     97.0     98.0  
   640x400        99.0  
   640x350       100.0  
   576x432       101.0    102.0    103.0    104.0    105.0    106.0    107.0  
   512x384       108.0    109.0    110.0    111.0    112.0  
   416x312       113.0  
   400x300       114.0    115.0    116.0    117.0    118.0  
   360x200       119.0  
   320x240       120.0    121.0    122.0    123.0  
   320x200       124.0  
   320x175       125.0 

```

I tried to install the latest nouveau driver but failed. Then I went to Nvidia site and located the driver for my card (GeForce 9300 M GS): 
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

This driver's file is called NVIDIA-Linux-x86_64-270.41.19.run

I followed the instructions here to install it: 
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

This didn't change anything apparent. 

I tried another monitor. This didn't help (though the monitor functions normally with another computer). I also tried another cable, VGA this time. This helped. 

Gnome: I can see the background picture and the menu bar at the top on the external monitor. If I open a program window by clicking on this bar the window opens on the external monitor. The mouse cursor goes from screen to screen but I cannot drag one window from one screen to another. 

KDE: I can see the background picture only. No menu bar (task bar of whatever it's called) on it. If I right-click on it and in "Desktop settings" I choose "Activity/Folder view" my icons appear there. I clicked on a .jpg file and it opened but with an incomplete window. This window lacks the top bar (with the name of the program) and the little "_" and "x" buttons to minimise or close. This window cannot be dragged or resized at all, not even within the confines of the second monitor. 

So I could use it - kind of. I would need to create icons on the desktop which would be pointers to the programs I would like to see running there. For example associate one type of video file with vlc, and leave this video in the desktop folder. But this is obviously not working properly.

I am using kdm display manager, do you think it would be worth it to try switching to gdm? 

To use xrandr I would need to know the port names with an Nvidia driver. You say on your wiki page that VGA is called VGA by Intel driver UMS, VGA1 by Intel driver KMS, VGA-0 by radeon driver, but what is it called by Nvidia drivers? 

Mariane

---

### Post by Mariane on 2011-06-09
Switching from kdm to gdm is easy: 

```

sudo dpkg-reconfigure gdm

```

And then click enter if gdm is selected when you are asked to chose between gdm and kdm. 

The second monitor remains unchanged. 

Mariane

---

